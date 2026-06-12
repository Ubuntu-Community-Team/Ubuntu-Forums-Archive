---
title: "Gcc"
date: 2006-09-11
forum: Installation &amp; Upgrades
---

### Post by MiniMoNK on 2006-09-11
Hey guys, I just threw Ubuntu 6.06 on my laptop the other day, went fine not having too many troubles with it, most if it was just plug and play. However, I threw Ubuntu on there to do some development stuff, it's very compact. I was shocked that I didn't have the gcc compiler on there. Anyone have a link on where I could get the source for it?

---

### Post by PCalitrack on 2006-09-11
Why not just search for it?

> aptitude search gcc
> $ aptitude search gcc
p   colorgcc                        - Colorizer for GCC warning/error messages  
i   gcc                             - The GNU C compiler                        
p   gcc-2.95                        - The GNU C compiler                        
p   gcc-2.95-doc                    - Documentation for the GNU compilers (gcc, 
p   gcc-3.3                         - The GNU C compiler                        
i   gcc-3.3-base                    - The GNU Compiler Collection (base package)
p   gcc-3.3-doc                     - Documentation for the GNU compilers (gcc, 
p   gcc-3.4                         - The GNU C compiler                        
p   gcc-3.4-base                    - The GNU Compiler Collection (base package)
p   gcc-3.4-doc                     - Documentation for the GNU compilers (gcc, 
i   gcc-4.0                         - The GNU C compiler                        
i   gcc-4.0-base                    - The GNU Compiler Collection (base package)
p   gcc-4.0-doc                     - Documentation for the GNU compilers (gcc, 
p   gcc-4.0-locales                 - The GNU C compiler (native language suppor
p   gcc-avr                         - The GNU C compiler (cross compiler for avr
p   gcc-doc                         - Documentation for the GNU C compilers (gcc
v   gcc-docs                        -                                           
p   gcc-h8300-hms                   - The GNU C/C++ cross-compilers for the Hita
p   gcc-m68hc1x                     - GNU C compiler for the Motorola 68HC11/12 
p   gcc-snapshot                    - A SNAPSHOT of the GNU Compiler Collection 
p   gcc272                          - The GNU C compiler.                       
p   gcc272-docs                     - Documentation for the gcc compiler (gcc272
p   lib64gcc1                       - GCC support library (64bit)               
i   libgcc1                         - GCC support library                       
p   pocketpc-gcc                    - The GNU C compiler for Pocket PC      

Looks like it is there so install it:
> sudo apt-get install gcc

I think that should do it. I have gcc on mine anyways... I'm sure you will install it by accident somewhere along the line during configuration of the system. Good luck.

Actually, I think "build-essential" comes with gcc. So you could just do sudo apt-get install build-essential

---

### Post by dog on 2006-09-11
> **MiniMoNK said:**
> Hey guys, I just threw Ubuntu 6.06 on my laptop the other day, went fine not having too many troubles with it, most if it was just plug and play. However, I threw Ubuntu on there to do some development stuff, it's very compact. I was shocked that I didn't have the gcc compiler on there. Anyone have a link on where I could get the source for it?


try sudo apt-get install build-essential for all the stuff you need for development.




dog

---

