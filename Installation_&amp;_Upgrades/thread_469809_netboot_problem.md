---
title: "netboot problem"
date: 2007-06-10
forum: Installation &amp; Upgrades
---

### Post by maarten80 on 2007-06-10
I'm trying to install ubuntu feisty on a PIII 700MHz 256RAM laptop. Unfortunately it does not have a cd-rom or floppy disk :(

first tried the usb-stick approach, but bios does not support booting from an usb stick (doh)

I am now trying the netboot approach as in this topic
[https://help.ubuntu.com/community/Installation/FromWindows]("https://help.ubuntu.com/community/Installation/FromWindows")

Everything fine so far, but when I choose the Install Ubuntu option on boot I get this error message:

"Windows 2000 could not start because the following file is missing or coorupt:
<windows 2000 root>\system32\ntoskrnl.exe
Please re-install a copy of the above file.

Strange since I would think that the linux installer does not want to use something from windows...

Booting in windows is still fine though, so nothing seems to be wrong with the mentioned file...

I get the same error when trying to install from the iso on the harddisk as mentioned here
[http://ubuntuforums.org/showthread.php?t=98451]("http://ubuntuforums.org/showthread.php?t=98451")


[ps I have no access to a windows cd, the laptop is secondhand, with win2000 still/preinstalled]

hope anyone can help

thanks,
maarten

---

### Post by Vadi on 2007-06-10
Hello,

I ran into the same problem, when I was trying to install Wubi. It turned out that it was improperly thinking that the machine had windows 98 installed on it, not 2000, and installed the stuff for a 98 machine. Which isn't working on 2000.

I tried installing this netboot, and it worked for me - try it out, it might for you also.

[http://cutlersoftware.com/ubuntusetup/wubi/downloads/experimental/wubi-7.04-netboot.exe](http://cutlersoftware.com/ubuntusetup/wubi/downloads/experimental/wubi-7.04-netboot.exe)

---

### Post by logos34 on 2007-06-10
> I am now trying the netboot approach as in this topic
[https://help.ubuntu.com/community/In...on/FromWindows](https://help.ubuntu.com/community/In...on/FromWindows)

Everything fine so far, but when I choose the Install Ubuntu option on boot I get this error message:

"Windows 2000 could not start because the following file is missing or coorupt:
<windows 2000 root>\system32\ntoskrnl.exe
Please re-install a copy of the above file.

Strange since I would think that the linux installer does not want to use something from windows...

I think I know that the problem is...when you download **initrd.gz** and **linux**, there's a discrepancy with the latter which ends up with an ".htm" suffix.  Just rename it "linux".

EDIT: Well I just double checked and the above comments related to another glitch.  I too had the problem with 'ntoskrnl', but fixed it somehow...it was something simple just can't remember for the life of me exactly what...That 'linux" will prevent you from decompressing the startp kernel, however, unless you take off the .htm suffix from the file or else make the path in the menu.lst read:

> kernel   (hd0,0)/boot/linux**.htm** vga=normal ramdisk_size=14972 root=/dev/rd/0 rw --

Note: the htm suffix appears if you look at in linux but not windows unless you change the default settings to show file type extensions.

I know that for the successful netboot install I used the initrd.gz and linux from the Feisty (rather than Breezy) archive, and I extracted grldr and menu.lst from the most recent grub4dos tarball.

---

### Post by maarten80 on 2007-06-11
@ vadi: thanks for the suggestion, but I would like to do a full linux install instead of wubi
Although I read somewhere that migrating from wubi would be possible in the future.

@logos34: I will check it this evening, but I'm pretty certain that the linux has no htm extension.

I'm glad you say it has a simple fix, maybe if you digg a little deeper :D

I too used the feisty files and the files from the latest grub4dos

Could the fact that the disk is NTFS be of any problem?

thank you for the quick answers!

---

### Post by maarten80 on 2007-06-11
I checked all files and the looked ok. Still the same error.

I am now trying the windows server install via pxe (which the laptop does support)

will report how that goes...

---

