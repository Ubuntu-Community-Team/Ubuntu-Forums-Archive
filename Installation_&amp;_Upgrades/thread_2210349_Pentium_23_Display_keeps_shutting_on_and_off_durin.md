---
title: "Pentium 2/3: Display keeps shutting on and off during boot."
date: 2014-03-10
forum: Installation &amp; Upgrades
---

### Post by hunter86_bg on 2014-03-10
I was trying to prove to my colleagues  how Linux can bring up to life our old Windows 98 PC at work. So , having in mind the restrictions I had to comply - Low ram: 384 MB, 6GB of space on HDD and old Pentium 2 (maybe 3) Processor I chose "Lubuntu 13.10 (Saucy Salamander)" alternate version. Installation went fine and it came the moment of truth. 
    First,I'm new to GRUB2 ( i'm used with the older grub) but it sounds strange it doesn't show the grub menu - it just boots /no matter which arrow on the keyboard I press/.
    Second ,Lubuntu start booting and at a certain time it starts to kill our old CRT Display and start it again. I guess it was trying to setup the X server.

So,my questions are:
1.How to enter GRUB2's menu so I can edit the runlevel I jump into / I assume adding the runlevel number after the kernel entry would do the job/
2.How to enter into VESA mode?!? I assume I have to rescue the system in order to do that / I'm not used to the debian systems/
3. Is there a text-base web browser - like the "elinks" package in CentOS?

Thanks in advance for your posts. I would be happy to get any help before I go to work tomorrow.

---

### Post by mörgæs on 2014-03-10
Though Linux can make old hardware blossom again there's a lower limit, and I'm afraid you have promised a bit too much. Anyway, if you want to experiment here are some answers.

1) If there's only one option in GRUB the menu does not show by default. Repeatedly pressing Shift during boot calls forward the menu.
2) adding Vesa codes: [http://ubuntuforums.org/showthread.php?t=361236&page=83&p=12292664&viewfull=1#post12292664](http://ubuntuforums.org/showthread.php?t=361236&page=83&p=12292664&viewfull=1#post12292664)
3) Lynx

---

### Post by grahammechanical on 2014-03-10
Several things have to happen before we get to a desktop user interface in any Linux distribution. Different components have to over control and then hand over control to other components. And this is what you are seeing. At certain points the video signal to the monitor is stopped and then started again as one component handed over control to another component.

1) The motherboard Basic Input Output System (BIOS) does its tests and then l&#959;oks for an operating system to load. It finds the Boot Loader (Grub) and loads it.
2) The Grub boot loader reads its configuration files and looks for Linux kernel image to load. When it finds a Linux kernel image Grub stops working.
3) The Linux kernel image starts to load and looks for a video display server to load. It finds XServer and runs that and then continues to load Linux.
4) The XServer looks for a Display Manager to take the operating system from a Linux command line OS to a Graphical User Interface OS.
5) The Display Manager (Gnome Display Manager for Kubuntu. Light Display Manager for Ububntu and the other flavours) presents a graphic log in screen and hands over to the Desktop Environment with its User Interface.
6) The Desktop Environment is Gnome for Ubuntu; KDE for Kubuntu; Xfce for Xubuntu and LXDE for Lubuntu.

So there is a lot of handing of control from one component to another. This can be hidden by splash screens but not always. Oh, at some point a video driver compatible with the video adapter has to be used instead of the XServer's basic video display.

I am amazed that with all these components that are separate software projects the OS works as good as it does. And at a very agreeable price.

Regards.

---

### Post by hunter86_bg on 2014-03-12
I know how Linux is working. It was strange to me when grub had several entries with default timeout of 10s - not to show at all.Second, i got only the splash untill X server is trying to take control.Maybe it seems that PC is on or below the minimum. I think to try another distro and see if it gets improved.

---

### Post by tgalati4 on 2014-03-12
Give TinyCore a spin.  It's possible that GRUB2 is invoking a video mode beyond what your graphics can handle.  There is a way to set it to VGA or VESA, but you will have to search for it, or disable the graphical boot altogether.  You can run Ubuntu (painfully) on a PIII, 500 MHz PC, but you need RAM, lots of it.  512 MB minimum, 768 MB is better.  TinyCore is better suited for your hardware.

---

