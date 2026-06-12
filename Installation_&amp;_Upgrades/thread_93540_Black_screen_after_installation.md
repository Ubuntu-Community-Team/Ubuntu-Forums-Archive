---
title: "Black screen after installation"
date: 2005-11-22
forum: Installation &amp; Upgrades
---

### Post by XeroXer on 2005-11-22
Hi there!
I got Ubunto from a friend who thought I should try it out.
And because I just bought a "new" laptop I thought why not run it on that.
First I hade some problems with the live cd but I thought that it might just be that one.
So today I decided to install it to the fullest.
The installation goes without ay problems and it reboots without the cd and continues the installation process.
But when the computer goes or its first startup of Ubuntu I just get a black screen.
I hear some sounds so something is happening but nothing on the screen at all.

I tried installing it again and I get the same problem again.
I am using Ubuntu version 5.04 for Intel x86.
The computer is a P4 1.4 Ghz with 256 Mb RAM...

---

### Post by kalin on 2005-11-22
Sounds like a refresh rate problem.

1. You might try the newer and better version - Ubuntu 5.10,  get it here:
[http://www.ubuntulinux.org/download/](http://www.ubuntulinux.org/download/).

2. Can you tell us what's the model of the laptop / video card / LCD.

3. Try to get to the contents of the following files:
/var/log/Xorg.0.log
/etc/X11/xorg.conf

You can get to those using the terminal. To get to the text console login from the blank screen simply press Ctrl+Alt+F1. Type "less file-name" to see the contents of each of those files (replace file-name with the above).

---

### Post by XeroXer on 2005-11-22
1. I am downloading the new version as we speak so we will se later.

2. Dell Inspiron 2200 - Intel Celeron Processor at 1.4Ghz - 256MB DDR RAM - 40GB HD - 14" XGA TFT active-matrix display

3.I don't know what's important but I found some stuff. Please tell me if you would like something special...

_/var/log/Xorg.0.log_
...
ServerLayout "Default Layout"
|-->Screen "Default Screen" (0)
|    |-->Monitor "Generic Monitor"
|    |-->Device "Intel Corporation Intel Default Card"
|-->Input Device "Generic Keyboard"

_/etc/X11/xorg.conf_
...
FontPath "unix/:7100"
FontPath "/usr/lib/X11/fonts
.....

---

### Post by kalin on 2005-11-22
Someone else has had the same problem, there's a quick workaround posted also:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=11283](https://bugzilla.ubuntu.com/show_bug.cgi?id=11283)

It's part of a more generic issue, the cause is a buggy BIOS:
[https://bugzilla.ubuntu.com/show_bug.cgi?id=2827](https://bugzilla.ubuntu.com/show_bug.cgi?id=2827)

Breezy (Ubuntu 5.10) might deal better with this issue though.

---

### Post by XeroXer on 2005-11-22
I now have the 5.10 installed and it works perfectly. :-)
Thanks for all the help...

---

### Post by kalin on 2005-11-22
np, have fun :)

---

### Post by root@localhost on 2005-11-26
Sorry to hijack this topic, but I'm having this same problem, even after I upgraded to Ubuntu 5.10. I have two video cards in the computer, one in the motherboard and one in a PCI slot, and would like to use the non-integrated card, which is made by ATI. The computer in question is a 1.7GHz Celeron with 768MB of RAM on a 15" flat panel monitor. 

I know it can display graphics, because it will load everything, but for some reason it will not bring up the login screen. I get a black screen with a white cursor in the top left. 

Thanks.

---

