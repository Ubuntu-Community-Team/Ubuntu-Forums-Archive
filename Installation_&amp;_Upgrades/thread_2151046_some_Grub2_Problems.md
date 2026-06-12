---
title: "some Grub2 Problems"
date: 2013-06-03
forum: Installation &amp; Upgrades
---

### Post by abdorefky on 2013-06-03
when i bought my  laptop it came with ubuntu pre-installed on it and the grub menu was hiddin , but u can  activate it by shift .
now i have removed that ubuntu and installed new  ubuntu , and i found that grub menu appear even when i have only ubuntu ,  i have hidden the menu by removing the # before " GRUB_HIDDEN_TIMEOUT=0  "

now what i want is :
[B]
(1) : i want to make the start  up very fast [/B]. ( i wait something like 10 sec before the ubuntu logo  appear and after that with 1 sec the login screen appear ) [B]

(2) : i would like to change the debian photo that appear on the back of the grub !!! what bring it there any way 

(3) : the recovery partition is not detected 
[/B]
------------------------------------------------------------------------------------------------------------------------------------------------------------------ 
addtional information

i have 3 partitions 2  of them with strange boot flags .** could this flags slow the booting ? **

[IMG][[IMG]http://imageshack.us/a/img90/8581/screenshotat20130415135.th.png[/IMG]]("http://imageshack.us/photo/my-images/90/screenshotat20130415135.png/")[/IMG]


here is my /etc/default/grub
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1" 



```

ty

---

### Post by byStanderone on 2013-06-03
...perhaps you can just uninstall grub, since you are using only one os

---

### Post by oldfred on 2013-06-06
You need grub even if only booting one system as that is the boot loader.

You show no recovery partition, but show the Dell utilities partition which often just has some tools specific to Dell and usually only with Windows.

I do not use back ground images but this explains how.
 How to: Create a Customized GRUB2 Screen that is Maintenance Free.- Cavsfan
[https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen](https://help.ubuntu.com/community/MaintenanceFreeCustomGrub2Screen)
[http://ubuntuforums.org/showthread.php?t=2076205](http://ubuntuforums.org/showthread.php?t=2076205)
Older thread
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

Speed depends a lot on what is loading. If it was Ubuntu pre-installed then the vendor may have optimized it to not load nor search for devices that your system does not have and maybe other settings. For instance I turned off bluetooth on my desktop as I do not have that. But you really have to know your system. What version was it before. If a lighter weight version of Ubuntu it also may have been quicker.

Did you document old system and its configuration?

---

### Post by abdorefky on 2013-06-11
i tried to remove the DIAG and LBA flags , but still the same . 
how can i be sure that there is nothing making delay for the start up
could the old IPL and the new IPL mixed ? or new IPL is written once installed new grub ?
i had the recovery detected before on the last grub before i install 12.04 .** how to detect it ?**

about the debian photo , i think if i installed the grub from live cd . it will goes back to default .

---

