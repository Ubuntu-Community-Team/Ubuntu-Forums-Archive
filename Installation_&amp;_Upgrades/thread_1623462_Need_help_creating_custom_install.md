---
title: "Need help creating custom install"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by Adrastus on 2010-11-16
[FONT=Arial][SIZE=2]Hi all,

I'm trying to install some version of Linux (at this point I'm not picky about which) to an old Sony PCG-505VE:[/SIZE][/FONT]  [FONT=Arial][SIZE=2]

Operating System: Microsoft Windows 98 (4.10, Build 2222) A [/SIZE][/FONT] [FONT=Arial][SIZE=2]
System Model: G23R2.0.0/ENU (Phoenix)
BIOS: EPP revision 9.00
Processor: Intel Celeron, MMX, ~333MHz
Memory: 64MB RAM
Hard Drive: 6 GB
CD-ROM (external): (PCGA-CD51) Toshiba XM-1902B ATAPI PC-Card

I found out that the only way to successfully run even a live CD requires the following command in the boot options:[/SIZE][/FONT] [FONT=Arial][SIZE=2]

 Ide2=0x180,0x386[/SIZE][/FONT]  [FONT=Arial][SIZE=2]

 However, this only works with a kernel that actively rescans (not sure that's the correct terminology) the hardware because the Vaio BIOS automatically re-maps the Cardbus CD-ROM to appear as IDE at /dev/hde instead of /dev/hdc (please see the following post for details written by people who actually understand this: [/SIZE][/FONT]  [FONT=Arial][SIZE=2][http://ubuntuforums.org/showthread.php?t=390309 ]("http://ubuntuforums.org/showthread.php?t=390309")).   I confirmed this with DSL which uses the 2.4 kernel (I haven't tried any other kernel versions besides 2.6 and 2.4).


 So, my question is, can anyone help me, or point me to a good guide to, create an install CD with a 2.4 kernel, Debian OS, X.org, and maybe the IceWM window manager?  If it's possible, it might even work to install Debian via floppy disk and then use aptitude for the environment and window manager, which I'm currently trying to figure out[/SIZE][/FONT][FONT=Arial][SIZE=2].

 I figure that once I get it installed I can just update the kernel...[/SIZE][/FONT]  [FONT=Arial][SIZE=2]

I'm a new user and I don't have much experience with shell commands, but I can copy-paste as well as the next guy.  Any help you all can give would be greatly appreciated.[/SIZE][/FONT]  [FONT=Arial][SIZE=2]


 --Adrastus[/SIZE][/FONT]

---

### Post by Adrastus on 2011-04-13
For anyone who is interested or is trying to install Linux on this model of machine, Debian Lenny works for a command line install (I used the Net installation CD) and then Xorg and any window manager or desktop environment can be installed manually with apt-get.

---

