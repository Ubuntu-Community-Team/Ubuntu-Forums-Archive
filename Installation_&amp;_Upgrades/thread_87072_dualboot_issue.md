---
title: "dualboot issue"
date: 2005-11-07
forum: Installation &amp; Upgrades
---

### Post by salladen on 2005-11-07
I recently did fresh installation of Kubuntu. Because I wanted it to dualboot with win xp (for gaming purposes) later I set up the partioning as follows on hda 120G:
1 : empty partion (wich i later installed win xp on) 20G
2 : rootfilesystem partion 15G
3 : swap 1.5G
4 : home-directory (remaining space)

All went great installing Kubuntu and setting up the system as I wanted it. I then installed win xp on the first partion, installed the apps and games and this also went well. But now only win xp boots. The windows Disk Management tool shows all 4 partions. I searched this forum and found [http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub+boot](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub+boot) 
walked through the steps using my installation cd, when I got to step 4 (Mount your appropriate linux partions) there was only one big partion instead of the ones I earlier had mounted, why? cannot skip and only install grub either since it wants the disk partioned first.

what to do?  is there another bootloader I can use ?

thanks for a great distro and forum.

---

### Post by salladen on 2005-11-08
eventually I got hold of an live-cd and followed the steps to fix my problem.

as suspected I didnt find any grub installations.

tryed:
grub-install (hd0)

/dev/mapper/casper-snapshot does not have any corresponding BIOS drive

what does it meen ?

---

### Post by Cufishing on 2005-11-08
In a nutshell: WinXP is the holder of the MBR, therefore it must be installed first. If not, you end up with what you have.

I do not belive there is a fix for this, as Grub indentifies winxp from the Ubuntu install, nit vice versa.

Here is a link, the first line pretty much sums it up.

[https://wiki.ubuntu.com/WindowsDualBootHowTo?highlight=%28boot%29%7C%28dual%29](https://wiki.ubuntu.com/WindowsDualBootHowTo?highlight=%28boot%29%7C%28dual%29)

---

### Post by oskude on 2005-11-08
hi,

i had/have similar problems and i normally fix this with knoppix: mount /, chroot, mount /boot, reinstall grub in MBR (or something like that). but my cdburner is broke and i dont have any (good) bootable linux cd atm (i only have breezy netinstall).

i came up with this atm (but havent tried) start with a livecd like knoppix, partition the disk, install windows and then install ubuntu so its the last who messes with MBR and windows is also automaticly added in the grub boot menu...

well, my (very lazy) workaround atm was to install ubuntu again after windows :)

wouldnt this be a good "start flag" for the install cd, having something like "restore_grub" and then couple questions, where to install grub, wheres /boot, should we auto-detect other os and add them to boot list, etc...

on the same throw: is it still advisable to use a small /boot partiotion as the first partition ? (cause of that beyond 1024cylinder boot thing... or so)
or other way: if grub is in MBR we can boot kernel from everywhere ?

cheers
osku[de]

---

### Post by salladen on 2005-11-08
thanks for your replys. 

I eventually managed to fix the problem. without having to reinstall any os.  (joy).

my solution: 
asked a friend if he could help.

now everything works perfectly and i've learned jack.  :)

thanks again for a good forum .

---

### Post by Cufishing on 2005-11-08
[QUOTE=salladen]thanks for your replys. 

I eventually managed to fix the problem. without having to reinstall any os.  (joy).

my solution: 
asked a friend if he could help.

now everything works perfectly and i've learned jack.  :)

thanks again for a good forum .[/QUOTE]
Please share. What and how did your friend do?

---

### Post by salladen on 2005-11-08
it didnt seem to be that hard. 
from a live-cd (gentoo 2005.0, if it matters) he mounted in and did the following.
put grub in mdr grub-install (hd0)  (i guess)
in grub:
root (hd0,1)    my / partion  (hda2)
setup (hd0,1)
quit...
rebooted

booting with grub now worked but it was pointing at a nother partion then specified

booted from live-cd once again, edited /boot/grub/menu.lst 
rebooted
and it worked... almost

seems that the winxp installation messed things up. /etc/fstad had changed, dont ask me why.  fixed that and now the dualbooting is fully functional.

thanks again all.   :smile:

---

