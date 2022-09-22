# Simulador x86 16-bit

A simulator of a 16-bit CPU. This project has been developed for educational
purposes to support the teaching of operating systems.

The simulator is based on a [previous
project](https://github.com/Schweigi/assembler-simulator) made by Marco
Schweighauser. This project reuses the instruction parsing mechanism, based on
the use of regular expressions, and extends the original instruction set with
new instructions to handle byte-mode accesses, interrupts, dual-mode execution,
system calls and exceptions. It has been fully written in Typescript using
Angular 2+ and [PrimeNG](https://www.primefaces.org/primeng/) and uses
[CodeMirror](https://codemirror.net) as a component for code editing. It also
uses the [angular-split](https://github.com/bertrandg/angular-split) module to
split the different panel views. The GitHub link icon on the uppermost right
corner of the application is a [GitHub
corner](https://github.com/tholman/github-corners).

You can try it online [here](https://ruiz-jose.github.io/arq-x86-angular/) TUDW-ARQ.

You can try it online [here](https://parraman.github.io/asm-simulator/) original.

## Features

- A 16-bit big-endian CPU.
- Two modes of operation: supervisor & user. Each mode of operation
  has its own SP register.
- 4 general purpose registers, which can be accessed in word or byte modes.
- 1024 bytes of memory.
- A Memory Protection Unit (MPU).
- 16-bit input/output address map which can be accessed using IN/OUT instructions.
- An interrupt controller that supports up to 16 interrupt sources.
- A programmable 16-bit timer.
- Three input/output devices:
  - Visual display with a resolution of 16x16.
  - Textual display of 2x16 characters.
  - 3x4-keys numeric keypad.
- Inline memory editing.
- Execution breakpoints.

## Simulator's architecture

The architectural description of the simulator comprises the following components:

###### Core components

- CPU (`CPUService`): simulates the Central Processing Unit.
- Memory (`MemoryService`): simulates the memory map. It allows the different
  input/output devices to map memory regions (e.g. framebuffers).
- I/O Registers Map (`IORegMapService`): simulates the input/output registers
  map. The different devices can use it to define different registers and map
  them.
- IRQ Controller (`IRQCtrlService`): simulates the interrupt controller.
- Timer (`TimerService`): implements the 16-bits timer.

###### Input/Output 

- Visual Display (`VisualDisplayComponent`): visual display of 16x16 pixels. It
  can be accessed through a framebuffer defined as a memory region.
- Keypad (`KeypadComponent`): a numeric keypad.
- Textual Display (`TextualDisplayComponent`): a 16 characters textual display.

###### View components

- CPU Registers View (`RegistersViewComponent`): component that displays the contents of the CPU registers.
- Memory view (`MemoryViewComponent`): component that visualizes the contents
  of the memory map. It also allows to edit the value of the cells inline.
- I/O Registers View (`IORegistersViewComponent`): component that displays the I/O registers map.

## License
**The MIT License**

Copyright (c) 2017-2018 Pablo Parra

Original ISA Copyright (c) 2015 Marco Schweighauser

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.
