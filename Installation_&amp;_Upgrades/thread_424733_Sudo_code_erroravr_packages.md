---
title: "Sudo code error/avr packages"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by TeamMicron on 2007-04-27
I am a beginner at using ubuntu/linux and need help.  I am trying to install the avr environment onto my box in order to compile C code onto my AVR board.  Here are the command lines and corresponding errors: 
 * sudo chmod 666 /dev/parport0 /etc/apt/sources.list
* sudo apt-get update
*sudo apt-get install avr-libc avrdude avra gcc-avr

  After "apt-get install" command, I get an error reading "Couldn't find package avr-libc". What am I doing incorrectly.  Thanks for your help.

---

### Post by lfmorrison on 2007-04-30
> **TeamMicron said:**
> I am a beginner at using ubuntu/linux and need help.  I am trying to install the avr environment onto my box in order to compile C code onto my AVR board.  Here are the command lines and corresponding errors: 
 * sudo chmod 666 /dev/parport0 /etc/apt/sources.list
* sudo apt-get update
*sudo apt-get install avr-libc avrdude avra gcc-avr

  After "apt-get install" command, I get an error reading "Couldn't find package avr-libc". What am I doing incorrectly.  Thanks for your help.

It "just worked" for me.  Remember that gcc-avr and related packages are part of the "universe" repository.  You have to make sure that "Community-maintained Open Source software (universe)" is checked under "System->Administration->Software Sources" before apt-get will be able to locate them.

Beware that the gcc-avr package appears to be slightly out of date relative to the other popular distributions of the AVR toolchain (FreeBSD ports, WinAVR) right now.  That means you won't have support for some of the newer AVR product lines (ATmega640/1280/2560/1281/2561, ATtiny25/45/85, ATtiny24/44/84, ATtiny261/461/861, etc).

If you don't need support for those devices right away, then you can probably stick with the packaged tools for now, and then update to the newer versions as they become available.

Otherwise, it's also possible to download the source code of current versions of the major components (binutils 2.17, gcc 4.1.2, avr-libc 1.4.5) and then reuse most of the patches from the FreeBSD ports to compile your own totally up-to-date toolchain from scratch.

---

