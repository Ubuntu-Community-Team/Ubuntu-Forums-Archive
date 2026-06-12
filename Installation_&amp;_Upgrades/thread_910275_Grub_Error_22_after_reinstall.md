---
title: "Grub Error 22 after reinstall"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by spy604 on 2008-09-04
Hello,

I am a linux newb and decided to give it a go. dual booted xp and 7.10, everything went fine. upgraded to 8.04 and it ran worse than 7.10 (may be my fault by messig with stuff, ati drivers etc), so i decided to do a reinstall of 7.10. install went smooth but on reboot I get a grub error 22, no menu at all...

any suggestions on where to start? I'm at work right now so I'll have to try it when I get home.

---

### Post by Bazirker on 2008-09-04
I just screwed up my system too, same error...I dual boot XP and Ubuntu 8.04, and XP died on me and required a reinstall, so I did, and it screwed up my MBR.  I pulled out my live cd, reinstalled grub, and while grub appears to work and recognizes everything the way it should, I get error 22 when I try to boot Ubuntu.  Error 22 tells me that the partition doesn't exist, although the partition is definetly still there when I take a look at my hard drive using my gparted live cd.

Halp?  spy604, if I figure out how to fix it, I'll post back here and let you know.

---

### Post by spy604 on 2008-09-04
thanks, my problem is that i dont even get a grub menu, so i cant even get into windows right now. of course theres always the live cd, and my wife's laptop, its more of an annoyance really.

---

### Post by caljohnsmith on 2008-09-04
From the Live CD, please post the output of:
```
sudo fdisk -lu
```
Find which is your Ubuntu partition in the form "sdaX" from the above command, mount it, and then print the menu.lst:
```
sudo mount /dev/sdaX /mnt
cat /mnt/boot/grub/menu.lst

```
Also post the output of:
```
sudo grub
grub> find /boot/grub/stage1
```
That should give us a good place to start to figure out your Grub problem. :)

---

### Post by Bazirker on 2008-09-04
I don't know about that error, I just fixed mine (tell you about that in a sec), but try reinstalling grub as per [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows).  Maybe that will fix your error.

I just fixed my error 22.  I had to boot my machine, and once grub opened, select my Ubuntu install and edit it but typing 'e'.  Once in the edit mode, I edited the line containing the location of the partition on my drive...in my case, I changed (hd0,3) to (hd0,2).  It was a guess and check, and I got lucky first try.

EDIT:  You have to edit the grub file to make this change permanent... something like sudo gedit /boot/grub/menu.lst and then change the (hd0,x) entry there and save.

Hope this helps  :)

---

### Post by Crafty Kisses on 2008-09-05
You can try using SuperGRUB to repair it > supergrub.forjamari.linex.org

---

### Post by notanxious on 2008-09-14
Kudos to Bazirker. I had been struggling with this error for a while. I two had to use the 'e' option to edit the boot from (hd0,0) to (hd0,1). Funny that super grub couldn't automatically fix this issue. 

THanks again

---

