---
title: "IDE/SATA Boot Problem, Cannot Load OS"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by Dyus36 on 2007-05-13
Hi,

Im kinda new to linux, iv been playin with it for a wile now and iv pritty much taught myself the basics using the guids/posts/wikis floating around. iv managed to get things the way i like them and even install a few games that were keeping me tethered to windows (which iv finally ditched).

at first i was dual booting between Ubuntu Feisty and XP until i decided i didnt want windows anymore at all so i did a clean wipe and install of Ubuntu, which worked out perfectly until recentely. i have 2 hard drives in my tower, 1 is a 40GB IDE drive that i was using to save everything important from xp (music, movies, documents, pictures, ect) and my 250GB SATA drive which Ubuntu currently occupies. a few days ago i decided i didnt want the IDE there anymore seeing as it had served its purpose so i removed it while the pc was off, when i turned it back on it wouldnt load ubuntu instead i got a error telling me there was no OS to load. so i pluged the IDE back in and it loaded fine, in addition i cannot load ubuntu without having the live CD in my disc drive, i have to boot from cd, select boot first HDD then GRUB loads ubuntu. 

can anyone tell me how to fix this? most importantly the only loading with the CD thing, the 40GB of space isint hurting me but the constant use of my CD drive at boot is, i contstantly forget to keep it in the drive when i reboot :D

any help much appreciated

---

### Post by logos34 on 2007-05-13
Use the Live cd to reinstall grub to the mbr of sata drive. Make sure it is set first in hard disk boot order in your bios.  

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
(section 'Re-install Grub with Live CD')

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub)
(first section)

---

### Post by confused57 on 2007-05-13
You can first try installing grub to the mbr of your Ubuntu drive, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
Using the link, you would:
```
sudo grub
find /boot/grub/stage1
```
this should return something like "root (hdx,y)", then enter:
```
root (hdx,y)
setup (hdx)
quit
```
Your 250 Gb SATA drive is probably (hd1) & grub is currently installed on your IDE drive(hd0).

Now go into bios and change your 250 Gb drive to boot before your IDE drive(try booting without your Ubuntu cd in the drive), you should get a grub menu at boot, if you do, highlight your Ubuntu entry, press "e", then change root from (hdx,y) to (hd0,y), then press "b" to boot.  This change is temporary, so it won't affect your current setup...if it works, it can be made permanent in your /boot/grub/menu.lst.

---

