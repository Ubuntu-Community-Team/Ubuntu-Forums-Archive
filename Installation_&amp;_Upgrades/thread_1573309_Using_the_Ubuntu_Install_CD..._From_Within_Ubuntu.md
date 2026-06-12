---
title: "Using the Ubuntu Install CD... From Within Ubuntu?"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by defab on 2010-09-12
Hello Everybody,

So here is my situation:

[LIST]
[*]I am unable to boot from a CD
[*]I am unable to boot from a Flash Drive
[*]I have Ubuntu installed with Wubi, and can boot into it successfully
[*]I have a Ubuntu Installation CD
[*]I have created a partition into which I'd like to install Ubuntu.
[/LIST]

Is it possible to boot into my current Wubi Ubuntu installation, and then launch the Ubuntu installer from the installation CD, and then direct this installation to the empty partition I have waiting?

Basically, I think my question is this: Does anybody know what file to run manually from the CD in order to launch the installer?

Thanks in advance!
defab

---

### Post by Wakawakamush on 2010-09-12
Did you try using a live usb?

---

### Post by defab on 2010-09-12
Yes, I can't boot from a USB.

---

### Post by Rubi1200 on 2010-09-12
This guide by forum member bcbc might have the answer:
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by wilee-nilee on 2010-09-12
Having a computer that you can't boot a cd or thumb with is trouble waiting to happen, that can't be fixed.

Why wont the computer boot these?

---

### Post by DemonBob on 2010-09-12
> **wilee-nilee said:**
> Having a computer that you can't boot a cd or thumb with is trouble waiting to happen, that can't be fixed.

Why wont the computer boot these?


Believe it or not, but alot of older computers can't boot cd's. Windows 95/98 computers required you to create a boot floppy, which loaded cd-rom drivers. So you could boot the install disk.

---

### Post by wilee-nilee on 2010-09-12
> **DemonBob said:**
> Believe it or not, but alot of older computers can't boot cd's. Windows 95/98 computers required you to create a boot floppy, which loaded cd-rom drivers. So you could boot the install disk.

I am familiar with limitations, it is if this is the case. I am trying to find out, if maybe like about 90% of the people who say they can't boot a cd just don't know how to use a key-prompt to bring up the boot from menu. We see many people who put their cd first in bios and it is bypassed to the hd rather then booting the disc, or they are just missing screen prompts.

I have said all I need to you about this it is the OP problem not mine.

---

### Post by defab on 2010-09-12
> **Rubi1200 said:**
> This guide by forum member bcbc might have the answer:
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

Thanks! That worked perfectly.

[QUOTE=wilee-nilee]Having a computer that you can't boot a cd or thumb with is trouble waiting to happen, that can't be fixed.

Why wont the computer boot these?[/QUOTE]

[QUOTE=wilee-nilee]I am familiar with limitations, it is if this is the case. I am trying to find out, if maybe like about 90% of the people who say they can't boot a cd just don't know how to use a key-prompt to bring up the boot from menu. We see many people who put their cd first in bios and it is bypassed to the hd rather then booting the disc, or they are just missing screen prompts.

I have said all I need to you about this it is the OP problem not mine.[/QUOTE]

My BIOS does not allow me to boot from USB.

My BIOS allows me to boot from CDs, but when I tried a known-good Ubuntu CD, it gave me an error at the splash screen. With enough tinkering, it probably could've worked, but I wanted to try this first, especially since it turned out, as I expected, to be pretty straightforward.

If I ever get into trouble, I can always take out my HDD and look at it on a friend's computer.

Anyway, thanks again. The migration worked flawlessly.
defab

---

### Post by Rubi1200 on 2010-09-12
Glad it worked for you :D

---

### Post by wilee-nilee on 2010-09-12
Glad you got your setup transfered.

Here is the deal the process of installing the bootloader for Ubuntu, can be done from inside the OS as you did, or with a live cd. 

So there are two ways to do this first just ask for some help on getting the regular Live cd to boot. Second there is a program that will allow your computer to boot from a USB.
[http://www.plop.at/en/bootmanager.html](http://www.plop.at/en/bootmanager.html)

Being able to boot a cd/dvd/thumb is about the most basic tool you should have. Not having this available makes it much more difficult to help you. You were lucky this time, wait tell you can't boot for some reason, your going to have to be able to boot something other then the HD.

---

