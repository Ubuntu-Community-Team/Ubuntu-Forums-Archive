---
title: "BusyBox 1.1.3 boot error fix for hardy heron Ubuntu 8.04"
date: 2008-10-25
forum: Installation &amp; Upgrades
---

### Post by cantormath on 2008-10-25
[SIZE=2]
[/SIZE][SIZE=2]_**The Issue**_
The live cd was hanging while booting for installation.
The error when boot disk:
busybox v1.1.3(debian 1:1.1.3-5ubuntu12) built in shell (ash)[/SIZE][SIZE=2]

_**Fix**_
[/SIZE][SIZE=2]Put CD in
boot to install menu
press F6
replace "[/SIZE][SIZE=2][I]splash quiet --"
[/I]with [/SIZE][SIZE=2]all_generic_ide pci=routeirq

**Note**: you may only need to replace [/SIZE][SIZE=2]"[/SIZE][SIZE=2]*splash quiet --" with *[/SIZE][SIZE=2]all_generic_ide[/SIZE][SIZE=2]
[/SIZE][SIZE=2]
hit enter

After install:
you need to set "all_generic_ide" in your kernel parameter one more time on first boot after you install.

press esc 
press e
go down one row, press e, you are going to edit the kernel boot parameter...
[/SIZE][SIZE=2]replace "[/SIZE][SIZE=2]*splash quiet --" with *[/SIZE][SIZE=2]"all_generic_ide", no quotes. 
press enter
press b

computer should boot up.

after boot up, go into /boot/grub/menu.lst and change the kernel boot option the same way.  Each time the updates include a kernel update, you will need to do this..

I have seen this problem on two Dell workstations.

Hope this helps someone.

Note: I believe this works with gutsy also.
[/SIZE]            [SIZE=2]
[/SIZE]

---

### Post by phamtuanamd on 2009-04-04
"all_generic_ide floppy_=off irqpoll_". What it mean?
"...ide pci=routeirq" what it mean?

---

### Post by c64 on 2009-10-23
Thanks cantormath it worked for me! I was unable to start installation of 8.04(and lower versions) because of BusyBox problem. After applying the changes to options you suggested, i installed ubuntu 8.04. I compiled a new kernel(2.6.20.15-custom) and it also worked well after doing changed to grub menu(gksudo gedit /boot/grub/menu.lst).

ps: i don't need to do such changes for ubuntu versions higher than 8.04.

---

### Post by Francewhoa on 2010-03-11
Same here. **The following worked for me** [http://ubuntuforums.org/showthread.php?p=8952609#post8952609](http://ubuntuforums.org/showthread.php?p=8952609#post8952609)

---

