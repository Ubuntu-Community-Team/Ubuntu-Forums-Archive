---
title: "automatic grub2 choice on remote reboot"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by ricoPan on 2010-01-10
I'm trying to figure out if I can do a remote reboot (eg over ssh) and specify a new grub2 os choice for the next boot only (once), in order to boot windows remotely once, but then back to linux on the next reboot.  

I found this related post for grub, but won't work for grub2 ( I never tried it with grub for a remote reboot).

[http://sidvind.com/wiki/GRUB:_Boot_another_OS_once](http://sidvind.com/wiki/GRUB:_Boot_another_OS_once)

which suggests changing the default menu option with the once flag:

[root@localhost ~]# echo "savedefault --default=2 --once" | grub --batch
[root@localhost ~]# reboot

I'm just starting to work with grub2 and am not at all clear whether I can do anything similar.

BTW Ubuntu karmic and windows 7.

thanks.

---

### Post by tobias81 on 2010-03-11
I'm looking basically for exactly the same thing ...

In my case I have a remote machine that I re-instelled using deb-bootstrap and I wanna try to boot into it just once and if something goes wrong reboot back into the old system... (obviously if something DOES go wrong I can't reconfigure anything)

does anybody have a good idea on how to do this

PS: there is absolutely no way that I can get phisical access to this machine ;/

---

### Post by chngtrn on 2010-06-22
Here are the steps you need to do to achieve what you wanted.

1. Modify /etc/default/grub like below
        GRUB_DEFAULT=saved
2. Re-generate /boot/grub/grub.cfg as root
        grub-mkconfig > /boot/grub/grub.cfg
3. Set your default OS to boot everytime, replace 0 with 1 for second OS, etc.
        sudo grub-set-default 0
4. Set a different OS to boot into once only, replace 1 with 2 if you want to boot 3rd OS, etc.
        sudo grub-reboot 1
5. (Optional) Change the entry below in /boot/grub/grub.cfg so that GRUB doesn't stay at the boot screen waiting for input after an abnormal shutdown.
From:
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi

To:
if [ ${recordfail} = 1 ]; then
  set timeout=1
else
  set timeout=1
fi

---

### Post by al3azef on 2011-03-29
Here's the simple and complete answer: 
 
**Important note:** Configuration changes are normally made to */etc/default/grub* and to the custom files located in */etc/grub.d*. The */boot/grub/grub.cfg* file should not be edited by the user; changes to this file are made by configuration scripts. After editing */etc/default/grub*, you need to run **sudo update-grub** for your changes to take effect on the next boot. 
[IMG]https://help.ubuntu.com/community/Grub2?action=AttachFile&do=get&target=info.png[/IMG]  Some of the most common changes, such as the default OS/kernel and menu  timeout, can be changed from within a GUI app called StartUp-Manager.  See the community doc [StartUpManager]("https://help.ubuntu.com/community/StartUpManager") for information about how to install and use this application. 
 
**/etc/default/grub (file)**

 
[LIST]
[*]The  main configuration file for changing default settings. Upon  installation, the following lines are available for alteration by the  user: 
[*]***GRUB_BACKGROUND*** - Sets the background image, enter the full path to the image here. See splash image configuration above for further details. 
[*]***GRUB_DEFAULT*** - Sets the default menu entry. Entries may be numeric, a complete menuentry quotation, or "saved" 

[LIST]
[*]**GRUB_DEFAULT=0** Sets the default menu entry by menu position. As in GRUB, the first "menuentry" in *grub.cfg* is 0, the second is 1, etc. 
[*]**GRUB_DEFAULT="xxxx"**  An exact menu entry, including the quotation symbols, may also be used.  In this case, location in the menu will not matter. Example: **GRUB_DEFAULT="Ubuntu, Linux 2.6.31-9-generic"** 
[*]**GRUB_DEFAULT=saved** 

[LIST]
[*]The information in this section applies to GRUB 1.98 and later. 
[*]Enables the "grub-reboot" and "grub-set-default" commands to set the default OS. 
[*]The default OS will *not* be set by an interactive selection of an OS from the menu. 
[*]**grub-set-default** Sets the default boot entry until changed. 

[LIST]
[*]The format is **sudo grub-set-default X**, with **X** being the menu entry position (starting with 0 as the first entry) or the exact menu string. Examples: sudo grub-set-default 3 or sudo grub-set-default "Ubuntu, Linux 2.6.32-15-generic" 
[*]To obtain the existing menu entry choice number (starting from 0) or the menu entry "string", run grep menuentry /boot/grub/grub.cfg 
[/LIST]
[*]**grub-reboot** This command sets the default boot entry *for the next boot only*. The format of the command is the same as for grub-set-default (see above). 
[/LIST]
[/LIST]
[/LIST]



for the complete Guide refer to  [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) Section "Configuration GRUB2"

---

### Post by TimmGood on 2011-04-08
Thanks for the info - exactly what I was looking for.  But, on the case exposed with a dual linux/Windows OS (and grub2 as boot loader), is there any way when I've booted on Windows to reboot next time on linux?  Should I try to map the ext4 partition in Windows and manually modify the config files (since obviously update-grub or grub-mkconfig cannot be used there)? Any idea?  Regards Timm

---

