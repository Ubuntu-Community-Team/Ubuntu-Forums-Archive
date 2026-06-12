---
title: "Please need help! Installing ubuntu"
date: 2006-11-23
forum: Installation &amp; Upgrades
---

### Post by lango80 on 2006-11-23
Hi,

I am a fresh newbie with Linux so I really really appreciate help. In fact this is my first try. Hope you guys can help me out. I am having problems installing ubuntu on the following machine:

IBM NetVista -
Intel Celeron 633MHz
512MB SDRAM
20GB HHD
SIS630 chipset w/integrated vga, sound, lan
NEC CD-ROM DRIVE:282 (info from WinXP device manager)


I have tried to run the live cd with the commands vga=771 and debian-installer/frambruffer=false. I always end up with this message:

...
[..numbers..] ac97 codec read timeout [..numbers..]
Activating swap.
mount: function not implemented
checking file systems.
fsck 1.39

After that I get into the Linux commands prompt I think (ubuntu@ubuntu:~$). I am a newbie so I don't know what to do here. I have tested the cd on another computer and it works fine. Do I have to download the "Alternate CD". I really don't want to touch the command prompt in Linux yet as this is my first installation.

In advance, thanks for any help!

---

### Post by john_spiral on 2006-11-23
What happens if you use the default live cd options?

---

### Post by bigken on 2006-11-23
dont be frightened of the alternate cd its not that bad ;)

---

### Post by lango80 on 2006-11-23
I have tried "Start or Install", "Start Ubuntu in safe graphicsmode", also tried F4 (changing resolution) and F6 with various options - boot: live vga=771 fb=false

Whatever option I use, it gives me the same message back and I am thrown to the linux command line. Both kubuntu and ubuntu haven't worked for me on this computer. 

Since I had no luck with ubuntu, I thought I could try my luck with gentoo. No luck with the installation there either, but I think I know why my install is failing now.

Gentoo gave me a message "failed to start the x-server (your graphical interface". I clicked yes for a diagnose and could read the error "virtual screen too big for memory; 1875k needed, 1532k available". Think that explains my problems.

I also read on the forums here somewhere that many integrated vga cards have a very bad bios or so, with further information that one should put the memory size for those vga devices to 4MB (or was it 8MB) or greater. Unfortunatly the integrated vga card on this computer is fixed to 2MB.

Now I wonder, if I run the "Alternate install", will it solve my problems? Will I encounter the problems later when linux is loading? I would really appreciate any information here.

In advance, thanks.

---

### Post by confused57 on 2006-11-23
When you get to the console(ubuntu@ubuntu$), enter:
```
sudo dpkg-reconfigure xserver-xorg
```

You can probably select the default values for most of the selections, but at the section for video driver, try selecting "sis" as the video driver.
Here's an excellent guide to doing this:
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)

Add: Another way might be to add a cheatcode when you bootup the desktop live cd:
```
xmodule=sis
```

---

