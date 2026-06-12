---
title: "How to make GRUB beep when menu displays?"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by ridgeland on 2007-07-30
I want GRUB to beep (or play a sound file) when it displays the menu.

Why?  I want to use timeout 10, not comment it out.  But when I want to go to another OS and say 'reboot' it takes a while for it to shutdown, then boot again.  While the PC is doing that I see something on TV and I miss the GRUB menu and it's back in the default OS (Ubuntu) when I wanted a different Linux, (usually a clone of Ubuntu I use as a sandbox to test new packages).

Obvious solutions: 
1 - Pay attention during all the reboot process.
2 - comment out timeout so the menu stays up until a choice is made.

I tried Google and searches in forums.  
In the GRUB manual it says:
pause message
add <^G> to message (Ascii 7) to get a beep.
If I put ---  pause "Hello World" <^G> --- After a title line in GRUB then it will pause until a keystroke and display "Hello World <^G>" --- no beep but this is a pause after the menu selection not on displaying the menu.  before a title line and it does nothing, gets ignored.
<^G> does not generate a beep.  What is the right code?

I know this is a trivial question but Linux is about making the OS do whatever you want it to do.  Maybe someone has done this already.

---

### Post by kwiwii on 2007-08-27
>  sudo gedit /boot/grub/menu.lst 

There are a whole lot of options there.

Here is an explanation: [http://ubuntu-tutorials.com/2006/12/29/tweaking-grub-ubuntu-510-6061-610/]("http://ubuntu-tutorials.com/2006/12/29/tweaking-grub-ubuntu-510-6061-610/")

Just make sure you back the file up so if you screw up you can go back to the old one

>     sudo cp /boot/grub/menu.lst /boot/grub/menu.lst-backup 

---

### Post by ridgeland on 2007-08-27
If there is something in the tutorial about making GRUB beep or play a sound file I cannot find it.  Can you?

---

### Post by kwiwii on 2007-08-28
No I dont think it will beep but you can cancel the countdown or make it longer.

---

