---
title: "HELP - I Can't acces my laptop after installing UBUNTU on USB"
date: 2008-11-09
forum: Installation &amp; Upgrades
---

### Post by azv31 on 2008-11-09
[LEFT]Hello guys!

First of all sorry if somebody already asked this, if there is a solution for this please point me in the right direction.

HERE'S MY PROBLEM.

Today I visited the Ubuntu site and realized there was a new version available for download 8.10, so i said to myself "I got get this one" so i did, after that I installed Ubuntu on a USB stick, following the on-screen steps, I chose the right options and all that until I got to the last option "Boot Loader", I chose advanced and I remember there were many option from which 
[LIST]
[*]Windows Vista longhorn (sd1 , I think?)
[*]Windows Vista longhorn (sd2, I think)
[*]USB Rally (the one where I installed UBUNTU)
[/LIST]
I chose the first option "Windows Vista Longhorn" and the UBUNTU started to install on the usb stick, after installation was done it asked me to restart the computer, eject CD and press enter, I did. And here is where the problem started.
The computer restarted normally but it never loads Windows vista nor UBUNTU, I can't boot to CD, can't access safe mode, I can't boot to anything I only get a BLANK screen with a cursor line. **I am only able to acces the BIOS settings.**
 PLEASE HELP, what can I do?
[B]
I should clear out that I had UBUNTU (previous version)on the same USB stick before so I can guarantee it worked before, the only difference is that in "Boot loader option" i just left it as default[/B]


This my laptop information

Gateway FX
4GB RAM
64BIT
Windows Vista Home Premium


Thank you in advance!


[/LEFT]

---

### Post by melojo on 2008-11-09
> **azv31 said:**
> [LEFT]Hello guys!

First of all sorry if somebody already asked this, if there is a solution for this please point me in the right direction.

HERE'S MY PROBLEM.

Today I visited the Ubuntu site and realized there was a new version available for download 8.10, so i said to myself "I got get this one" so i did, after that I installed Ubuntu on a USB stick, following the on-screen steps, I chose the right options and all that until I got to the last option "Boot Loader", I chose advanced and I remember there were many option from which 
[LIST]
[*]Windows Vista longhorn (sd1 , I think?)
[*]Windows Vista longhorn (sd2, I think)
[*]USB Rally (the one where I installed UBUNTU)
[/LIST]
I chose the first option "Windows Vista Longhorn" and the UBUNTU started to install on the usb stick, after installation was done it asked me to restart the computer, eject CD and press enter, I did. And here is where the problem started.
The computer restarted normally but it never loads Windows vista nor UBUNTU, I can't boot to CD, can't access safe mode, I can't boot to anything I only get a BLANK screen with a cursor line. **I am only able to acces the BIOS settings.**
 PLEASE HELP, what can I do?

This my laptop information

Gateway FX
4GB RAM
64BIT
Windows Vista Home Premium


Thank you in advance!


[/LEFT]
Can you see the gateway logo screen when booting?
If so try pressing esc or f10 when you see the logo.  This should give you boot options for gateway.

---

### Post by azv31 on 2008-11-09
Yes i can see the gateway logo and I can see the boot options as well but as i  mentioned before, I Can't boot a live cd or any other CD, just a blank screen appears.

---

### Post by melojo on 2008-11-09
When booting from the live cd can you see the ubuntu options menu?

---

### Post by azv31 on 2008-11-09
**[size="4"]cant't boot to any cd[/size]**

---

### Post by melojo on 2008-11-09
> **azv31 said:**
> **[size="4"]cant't boot to any cd[/size]**

are you saying that you do not have a menu when trying to boot from the cd, not after its done booting but before?  If you can get to the installation menu you are able to pass options to the kernel.  Your problem I believe is a video driver problem.  But you have to be able to pass options to the kernel.  No reason to type bold or shout just trying to understand your situation.  How long have you been using linux?

---

### Post by azv31 on 2008-11-09
I'm a new user to the whole LINUX world!

before this goes further I just wanted to make sure you understand that I cannot boot any cd, even though I can access the boot options. I think the problem is that the laptop is not booting from the right source but i just can't figure out how to fix it!

---

### Post by melojo on 2008-11-09
> **azv31 said:**
> I'm a new user to the whole LINUX world!

before this goes further I just wanted to make sure you understand that I cannot boot any cd, even though I can access the boot options. I think the problem is that the laptop is not booting from the right source but i just can't figure out how to fix it!

Can you get to the ubuntu menu? the one in the thumbnail.  If so then you booted from the cd to the menu here is where you pass options to the kernel to help load ubuntu in some cases.

---

