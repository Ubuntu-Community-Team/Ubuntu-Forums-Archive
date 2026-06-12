---
title: "re-install after de-install does not work"
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by dieter-erich on 2010-05-18
Hi, I am new here and may possibly ask stupid questions. Please forgive me!

I had a WUBI 9.04 installation smoothly running together with WinXP on an eee netbook. Due to a number of problems (amongst others installing motif libraries) I decided to upgrade to 10.04 and start from scratch. 

However, the upgrade always ended with an error message. I found out that this is a known bug so I wanted went to uninstall 9.04 and re-install 10.04. 

Despite all WUBI files appearing to have been removed after uninstall from WinXP system manager / software /, after installation of 10.04 the boot menu still shows the list of the kernels I had before and it crashes (seemingly because the corresponding files are not there any more). 

Is there an easy way of COMPLETELY remove the old installation to start from scratch?
I have the impression that there is somewhat sitting in the MBR that was not overwritten by the new installation. 

I have tried many times with little difference but always end up with the same problem.

Thanks a lot for hints, D-E

---

### Post by oldfred on 2010-05-18
Welcome to the forums.

I do not have wubi, but I believe the uninstall does not always house clean boot.ini which is the menu windows presents on boot. Not sure if it is a hidden file in windows as I see it in my Ubuntu link to my XP. 

Do not use gedit to edit it as linux uses different line endings and will mess it up. If from Ubuntu you can use nano. Or use any windows editor.

Remove the extra ubuntu entry in boot.ini.

---

### Post by dieter-erich on 2010-05-18
Hi odfried,
  thanks for welcoming me and your suggestion! The problem does not consist in removing the entry in boot.ini. I can delete it and it does not show up any more in the boot menu. Maybe I should be more precise:

1) I installed WUBI 9.04 
2) I did some kernel updates that resulted in a growing list of entries of kernel versions to choose from for booting
3) I uninstalled WUBI 9.04
4) I installed WUBI 10.04
5) When booting, the boot manager shows me the same list as in 2 and NOT the new kernel corresponding to 10.04. It seems as if something (grub, linux MBR) were remaining after the uninstall and not replaced by the files corresponding to 10.04. 

I want to get rid of this trash to have a clean and functional install of 10.04.
Do I really have to make a fixmbr from a WinXP install disk?
Where are these infos (list of kernels been) stored?
Thanks all for suggestions!
DE

---

### Post by oldfred on 2010-05-18
Wubi is a full install just running inside a windows NTFS partition, so I think you can do all of this.

You must have said keep old grub's menu.lst so it did not get updated. To boot you need the new kernel in menu.lst and will have to manually add it if you cannot boot.

Unless you also are having windows problems you do not need to run fixboot or fixmbr. FixMBR just puts the windows boot loader back into the MBR but if you can boot you already have that.

To fix menu.lst. You have several choices. If you get the grub menu,  manually edit the line to allow one boot and fix from inside. Use liveCD and chroot into your system (but I am not 100% sure how to chroot into a wubi install). Or use liveCd and edit menu.lst with the new corrected stanza. Houseclean old kernels, then run sudo update-grub to write a new menu.lst. 

We need to know what new kernels you have installed to and can go from there:

From a liveCD
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by dieter-erich on 2010-05-19
Thanks a lot!
I do not remember having ever seen the option "keep old grub's menu.lst". Is there a way of getting rid of it easily? How do I get to the screen with this choice? I do not care to do the installation again! 
 
So far I have removed everything looking like wubi* from my harddisk - no avail. I'd like to rather weep out everything and start anew. Where is menu.lst stored? I do not understand why it is still there after deleting all traces of Wubi under WinXP?
 
Having this said, I still tried to modify the menu.lst by choosing Wubi from the boot menu and trying to edit the first kernel entry (there are many because of previous updates):
 
it says GNU GRUB version 1.98-ubuntu5
set root=(hd0,1)
seach --no-floppy --fs-uuid --set d498435098432ff2
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /boot/vmlinuz-2.6.31-20-generic root=/dev/sda1 loop=/ubuntu/disks\
/root..disk ro quiet splash
initrd /boot/initrd.img-26.31.20
 
As I understand it, the old kernel does not fit to the new version 10.04 and I simply must replace the version name. How do I know what vmlinuz is present in 10.04? 
 
I have tried to replace the two occurrances of vmlinuz-2.6.31.... with vmlinuz-2.6.32-generic ... ´but on entering CTRL-x for booting I just get 
 
"initrd /boot/initrd.img-2.6.32-generic"
and nothing happens.... 
D-E

---

### Post by oldfred on 2010-05-19
You should use tab and it will complete if the remaining entry is unique or until it is not.

You can use  the linked version to the current:
linux /vmlinuz root=/dev/sd[COLOR=DarkRed]a5[/COLOR] ro
initrd /initrd.img

the above is for standard installs not wubi so I so not know if the entry is somewhat different. 

The boot info script will tell us what is where.

---

### Post by darkod on 2010-05-19
Same as oldfred, I'm not sure how to find the kernels and where to edit for wubi. If you had a dual boot, it would be easy.

The 10.04 kernel is I think 2.6.32-21, but to make sure, you can try typing:

linux /boot/vmlinuz-2.6.32 and then hit TAB to fill out the rest.

However, are you sure you can use

linux /boot.... for wubi? Wasn't it something like:

linux (loop)....

---

### Post by oldfred on 2010-05-19
With wubi you have to mount the ntfs partition first then mount the wubi partition from inside the ntfs partition.

I think the loop mount is for mount ISO files, not sure about wubi.

this is a script to save to mount wubi, you still have to edit for the correct partition.
[Script] Mount Wubi Disk from Linux 
mount ntfs partition first:
[http://ubuntuforums.org/showthread.php?t=1037874](http://ubuntuforums.org/showthread.php?t=1037874)

---

### Post by dieter-erich on 2010-05-19
Hi guys, thanks for the input. However: tab completion does not work - so I do not find which kernel is contained in WUBI 10.04. I also forgot, in my previous post, the first line, which is "insmod ntfs". I suppose this is to specify the file system. In any case, I entered the commands previously posted (now including insmod ntfs as the first one) one by one in the GRUB console replacing the version of the kernel but just got 'filesystem not found'. I am somewhat desparate :-((. Nobody can tell me how to simply get rid of the WUBI trash from within WinXP so that I can do a new installation? I'd really like to find the place where this stuff is located. Would things make much easier....
D-E

---

### Post by darkod on 2010-05-19
> **dieter-erich said:**
> Hi guys, thanks for the input. However: tab completion does not work - so I do not find which kernel is contained in WUBI 10.04. I also forgot, in my previous post, the first line, which is "insmod ntfs". I suppose this is to specify the file system. In any case, I entered the commands previously posted (now including insmod ntfs as the first one) one by one in the GRUB console replacing the version of the kernel but just got 'filesystem not found'. I am somewhat desparate :-((. Nobody can tell me how to simply get rid of the WUBI trash from within WinXP so that I can do a new installation? I'd really like to find the place where this stuff is located. Would things make much easier....
D-E

This is as much as I can help:
[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

There are instructions for the automated method, and manual.

---

### Post by oldfred on 2010-05-20
The boot info script parses your system for most things related to booting. Several versions ago it was updated to inculde extra info on wubi installs, so it goes into the wibi and lists information from there also.

---

### Post by dieter-erich on 2010-05-25
Hi, 
systematically searching for wubi*, ubuntu*, and grub* in Windows and deleting all entries with some resemblance to these file names finally allowed me to get rid of all residues left over from the previous wubi installation. After that, I could seamlessly re-install the newest version of wubi. Apparently, the uninstall routine does not correctly remove all references to the previous install. Anyhow, I am back at the beginning!
Thanks for your input, D-E

---

