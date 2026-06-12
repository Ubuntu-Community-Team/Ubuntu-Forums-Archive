---
title: "Problem installing 64bit ubuntu 8.04"
date: 2008-09-14
forum: Installation &amp; Upgrades
---

### Post by theGreatest on 2008-09-14
Hi!
Im trying to install linux for the very first time, the 64bit version of 8.04 LTS Hardy Heron.
Ive downloaded and burned the iso file to a cd.
But no matter what I do, this happens:

If choose to try ubuntu without doing any changes to my machine, or if I try to install, or if i try to check cd for defects, this happens:

It loads the linux kernel, ubuntu logo shows ut with a bar underneath that slides back and forth, indicating some work.

After that, this appears on the screen:

[189.728510] Buffer I/O error on device fd0, logical block 0
[201.875087] Buffer I/O error on device fd0, logical block 0
[227.217149] Buffer I/O error on device fd0, logical block 0
.
.
.
etc.
[6**.******] Buffer I/O error on device fd0, logical block 0

BusyBox v.1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in Shell (ash)
and that i should type help for a list of built in commands.

Ive burned the iso file twice on different cd's, once on max speed, and once on low speed (8x).

Has anyone here had this problem? I've got vista 64bit on the other partition, and left 80GB for linux.

---

### Post by Pumalite on 2008-09-14
Try disabling floppy in BIOS

---

### Post by theGreatest on 2008-09-18
I have disabled floppy in bios, and i do not get the error on device fd0 lines.

But i jumped then directly to:

BusyBox v.1.1.3 (Debian 1:1.1.3-5ubuntu12) Built-in Shell (ash)
and that i should type 'help' for a list of built in commands.

(initframs)_

I then tried editing boot parameters with [ this method ](https://help.ubuntu.com/community/BootParameters)

Both removing quiet splash-- or replacing it with any of the commands listed (irqpoll, acpi=off etc.) gave the exact same result.

It seemed like it detected a whole lot of hardware, it runs through alot of lines, on one of them i guess, im not sure because it was going really fast, i read the word "failed".
On one line i did register this message: usb 4-2: device not accepting address 2, error -71

I have one usb device connected, wich is a bluetooth reciever for a logitech MX revolution mouse, and a MX 5500 keyboard.
It seems though that it registeres the mouse and keyboard and that they are from logitech...

any ideas on what is going wrong? as you see, I cannot even get to start installing.

---

### Post by Pumalite on 2008-09-18
Boot Knoppix Live CD:
[http://www.knopper.net/knoppix-mirrors/index-en.html](http://www.knopper.net/knoppix-mirrors/index-en.html)
And post:
lshw

---

