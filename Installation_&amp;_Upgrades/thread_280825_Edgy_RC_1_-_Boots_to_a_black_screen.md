---
title: "Edgy RC 1 - Boots to a black screen"
date: 2006-10-20
forum: Installation &amp; Upgrades
---

### Post by ctsdownloads on 2006-10-20
Well, much like Edgy Beta, Edgy RC 1 produces a black screen when booting off of the CD. 

I am able to get to the loading/splash screen, but after that - nothing.

I am running an ASUS board, AMD64 processor and a NVIDIA gt6600 AGP card. I also have two monitors attached on the same single video card, was using twin view in Dapper without any issues. But with Edgy, nothing.... ](*,) 

Any help would be GREATLY appreciated.

---

### Post by ctsdownloads on 2006-10-20
Forgot to mention: The screen boots black in all graphic modes, including safe mode.

---

### Post by ctsdownloads on 2006-10-22
Anyone else dealing with this problem? Anyone at all?

---

### Post by Kateikyoushi on 2006-10-22
You could try to add some options at boot.
At menu F6 then start with these options

Boot: linux noapic
Boot: linux pci=irqroute
Boot: linux pci=noacpi
Boot: linux acpi=off
Boot: linux pci=acpi
Boot: linux nolapic
Boot: linux framebuffer=false
Boot: linux irqpoll

---

### Post by Peter2007 on 2006-10-28
Hello,

I experienced the same problem with RC and the "normal" release.
I tried a litte bit and got it to work. Here is my "workaround".
Works with x86 and ATI X700 mobile.

Change to console


> Ctrl+Alt+F6

and install another driver for graphics


> sudo apt-get install xorg-driver-fglrx

Then configure in the xorg.conf with

> sudo vim /etc/X11/xorg.conf

the following parameter 

> Section "Device" 
Identifier "Name of graphics card" 
Driver "fglrx" <--- former "ati" 
BusID "PCI:1:0:0" 
EndSection

Change back to not available graphic interface with

> Ctrl+Alt+F7

and restart the xserver with

> Ctrl+Alt+Backspace


Now you should see the graphical interface.
After installation you have to install again the
driver in the same way as described.


Maybe it works. Worked for me.

Peter

---

### Post by Rory on 2006-10-29
This sounds like a very similar issue to a bug I've filed (see below):

I am now referring to it as the "Ubuntu Black Screen of Death"

See this bug report and if you’re experiencing the same issue, please report in the bug so Ubuntu Devs can get a sense of the severity of this issue.  They have yet to acknowledge this bug, filed one week ago, despite many people noting they are experience similar issues.



 Bug Report:
[https://launchpad.net/distros/ubuntu/+bug/67487](https://launchpad.net/distros/ubuntu/+bug/67487)
 

Ubuntu Forums Thread:
[http://ubuntuforums.org/showthread.php?p=1686198&posted=1#post1686198](http://ubuntuforums.org/showthread.php?p=1686198&posted=1#post1686198)

---

### Post by Aikon- on 2006-10-29
> **Peter2007 said:**
> Hello,

I experienced the same problem with RC and the "normal" release.
I tried a litte bit and got it to work. Here is my "workaround".
Works with x86 and ATI X700 mobile.

Change to console

[...]

Now you should see the graphical interface.
After installation you have to install again the
driver in the same way as described.


Maybe it works. Worked for me.

Peter

Hmm... except that when I reach the blank screen where X should be loading, no combination of keystrokes results in any effect. i.e. ctrl-alt-f2 doesn't get me to the console, ctrl-alt-backspace doesn't restart X etc.

---

### Post by Rory on 2006-10-29
Yes, same with me.  Ctrl+Alt+F1 through F6 do not bring up Console.  

See bug report:
[https://launchpad.net/distros/ubuntu/+bug/67487](https://launchpad.net/distros/ubuntu/+bug/67487)

If this seems like you, please add your voice to the bug report.  This appears to be a broad-based issue.

---

