---
title: "ubuntu gutsy and xp on two separate drives"
date: 2007-12-26
forum: Installation &amp; Upgrades
---

### Post by jmorales on 2007-12-26
Hey guys, Ive been using Ubuntu for the better part of the year. I had 2 ide hdd on my old machine and just recently bought all new parts including a new SATA hdd. I didnt hook up my old drives and thus and running this machine with a clean install of Ubuntu. So as far as the system is concerned, there are no other hdd or os on it. One of the old drives has XP and i would like to be able to dual boot into it. Ive been reading up on GRUB editing and all that but it seemed in most of those cases, someone wanted to partition their drives or have both os's on the same drive. I was curious if there was a way to do what I need to since my situation has both systems on their own drives.

cliffs:
1) XP on one drive (not hooked up)
2) Ubuntu on another drive (main and only drive installed right now)
3) Want to have choice of which system to boot at startup

Thanks in advance. Ive been scouring the thread with search on the topics but couldn't find a situation quite like mine. Thanks again :)

Jaime

---

### Post by jmorales on 2007-12-27
Please correct me if I'm wrong, but the way I see it, I simply need to somehow make GRUB ask me what OS I want to load since I have Ubuntu on my main SATA drive and XP on a secondary IDE drive.

---

### Post by vek on 2007-12-27
Maybe this will help?
[http://ubuntuforums.org/showthread.php?t=650580](http://ubuntuforums.org/showthread.php?t=650580)
If grub is installed, editing its menu.lst should allow you to specify which HDDs the various operating systems are on.  

Windows hates being installed on the non-primary drive, but if you temporarily make the drive primary, install it (be careful, it will blow away your MBR and remove grub WITHOUT asking you, so be ready to use a LIVECD or something to put grub back on), and then switch it back to secondary, and then update grubs menu.lst to point to that hd instead of the original for the windows install, you should be ok...

Grub keeps its list of OS's and HD's to load them from in its menu.lst file in the grub folder (usualy in /boot afaik)

If you already have a full install of XP on the other drive and just want to 'activate' it, probably all you have to do is add it to the end of grub's menu.lst as outlined in the above post.

---

### Post by jmorales on 2007-12-27
Yeah I've been reading that thread you posted as you replied. Ive learned a lot over just the past couple of days researching this issue. like  you said in your last paragraph, I do already have xp installed on the other drive and want to "activate" it ie make ir read/writeable in ubuntu. is this what you were talking about adding to the end of the menu.lst? 

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 

of course id have to change root to sd0 since my main drive (ubuntu) is SATA. and then figure out how to install my other drives

---

### Post by meierfra on 2007-12-27
> is this what you were talking about adding to the end of the menu.lst? 

yes.


> of course id have to change root to sd0 

No.. (hd1,0) Just means the first partition on the second hard drive. (Grub stars counting at zero).. It does not matter whether you drive is IDE, SATA or whatever. 


You also need to change "hiddenmenu" to "#hiddenmenu" so that the grub menu appears at boot up.

You also might  change "timeout 3" to "timeout 10" to increase the time to pick Windows before the computer automatically boots into Ubuntu.

> 
then figure out how to install my other drives
???


For further help, post the output of

```
sudo fdisk -l
```

and 

```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by jmorales on 2007-12-27
> **meierfra said:**
> yes.




No.. (hd1,0) Just means the first partition on the second hard drive. (Grub stars counting at zero).. It does not matter whether you drive is IDE, SATA or whatever. 


You also need to change "hiddenmenu" to "#hiddenmenu" so that the grub menu appears at boot up.

You also might  change "timeout 3" to "timeout 10" to increase the time to pick Windows before the computer automatically boots into Ubuntu.


???


For further help, post the output of

```
sudo fdisk -l
```

and 

```
gksudo gedit /boot/grub/menu.lst
```


ok i feel confident enough that I under stand that. as to your "???" what i meant was that my windows machine had 2 hdd. one 80gb original and a second 300gb for just extra data storage. And by figure out I meant since they are both ide install as in what configuration with the cable since my mobo only has one ide connector.

as far as the output of sudo fdisk -l , my other disks right now are not plugged in. but i will still post it for just the primary drive if it is needed.  Thank you guys for your help.

---

### Post by meierfra on 2007-12-27
> But i will still post it for just the primary drive if it is needed. 

No, that is not needed

---

### Post by jmorales on 2007-12-27
> **meierfra said:**
> No, that is not needed

ok cool. thank you. i just did it out of curiousity myself and you probably already know what i saw. just my 1 sata drive thats actually plugged in. i was going to try to do it now but im going to wait until this weekend. have a new case for the computer coming in that will be a lot more roomy and "messing around" friendly because mine is very cramped right now and cables everywhere.

---

### Post by jmorales on 2008-01-03
Hey guys, I'm back. I finally put everything together in the new case. I edited my menu.lst file with the chainloader command. here is the output of fdisk -l

```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000ee2e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29645   238123431   83  Linux
/dev/sda2           29646       30401     6072570    5  Extended
/dev/sda5           29646       30401     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8ace8ace

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        9729    78148161    7  HPFS/NTFS

Disk /dev/sdc: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9f3363a2

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       36483   293049666    7  HPFS/NTFS

```

and gksudo gedit /boot/grub/menu.lst

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f8a0850f-68b4-461d-b9f7-a6b97b7fa34c ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=f8a0850f-68b4-461d-b9f7-a6b97b7fa34c ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1 

```

I downloaded the super grub disk and tried to put it on a usb flash drive, but am unfamiliar with doing that so I'm not completely sure I did it right. I could not get into the super grub menu and when I chose to boot xp from the list, it went into the xp splash screen but then I got an error message about the drives and partitions

---

### Post by shakyone on 2008-01-18
jmorales,

      I am reading your post.  It has been two weeks.  Did you find a resolution? 

      I have done the dual boot two operating systems with two IDE drives, and it worked with the GRUB edits you did in your last post.  But it was a little easier, with GRUB on the linux drive in the Master IDE cable Position, the BIOS never looks at the NTLoader on the MBR of the Windows drive, until GRUB points it there per the commands you wrote in the Menu.lst file.  I am not a Guru with SATA drives, but I do want to know what you did.

     Some suggestions.  Disconnect the Ubuntu drive and point the BIOS to the XP drive.  Does it boot?

     If yes, repeat the same for the Ubuntu Drive.  Does it boot? If yes, then both your GRUB on the linux drive and NTLDR on the XP drive are intact, and that is good.

     At this point, I would suggest you shut down, reconnect the drives, and enter the BIOS again.  Now set the BIOS so ONLY the Ubuntu SATA drive is a boot hard drive, remove the XP drive from the list of boot options in the BIOS.  Power down.  Disconnect the XP drive then restart.  Does it go into Ubuntu?  if so then you should be on track.  Shut down, reconnect the XP drive and boot again to verify you can get into Ubuntu.  Now from either the Live CD or from your normal Ubuntu (not running off of LiveCD) command line open up your menu.lst file "gksudo gedit /boot/grub/menu.lst" from the command line will do it.   Make sure you save a copy of the original menu.lst so you can always create a new menu.lst starting with your original.  To be conservative, I wouldn't make but one or two changes at a time & be sure to write down what you changed, so you can change it back if you have problems.

    You said the Chainloader entry was set to remap the drives as shown below:

map (hd0) (hd1)
map (hd1) (hd0)

     But I am not certain that is correct for SATA drives.  I am guessing a little here, but I think you need to change it to something like

map (sda) (sdb)
map (sdb) (sda)

or something like this:

(hd0) /dev/hdb (you can also try sdb here)
(hd1) /dev/hda (you can also try sda here)

instead of the hd0 and hd1 stuff.  

There is also a post for an IDE and SATA dual boot how to:  [http://ubuntuforums.org/showthread.php?t=46003&highlight=dual+boot+sata](http://ubuntuforums.org/showthread.php?t=46003&highlight=dual+boot+sata)

in it, it edits the menu.lst XP chainloader section to look like this:

title		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
savedefault
chainloader	+1

I am not sure what the rootnoverify (hd1,0) does, but it is worth a try.

No guarantees on how it works, but it shouldn't take long to try it out.    I only suggest the above because I thought the sda refers to SATA drives.  I know hd0 and hd1 should work, but it is just a guess.  Also make sure none of your USB drives are connected when you boot, that can confuse things.  

If none of this works, let me know what happens, maybe we can find some more answers.   I would love to hear how it works out.  As I start ordering parts for my new computer in the next couple months, and using two SATA drives is my preferred dual boot method.

If you look down the page on the ide and SATA post, there is a user named Kattumaram that seemed to do what you are trying, but with three SATA drives, unfortunantely he only made the one post to say he got it working.  He said he edited the menu.lst IAW the following:

now look for an entry (near the end) that reads like something like this:

title Microsoft Windows XP Professional
root (hd1,0)
savedefault
chainloader +1

and change it to this:

title Microsoft Windows XP Professional
root (hd1,0)
map (hd1,hd0)
map (hd0,hd1)
chainloader +1

His configuration was:
"... three HDDs, all SATA, when I attempted to dual- boot, XP and Ubuntu, each on a different drive.. XP Pro is on HD2 (sdc), Ubuntu on HD1(sdb) and two NTFS primary partitions are on HD0 (sda). The MBR is on HD0 (sda). I installed GRUB to (sda) during the installation of Ubuntu on HD1(sdb) per the above instructions and then made changes in the /BOOT/GRUB menu.lst to get XP onto the menu....works like a charm.....took me only two days to get it all configured."

I hope one of these solutions gets you in the right direction.  

If the solution was a combination of editing of your Menu.lst and BIOS changes, please post what worked.  I did not see much else in the forums for this setup.

Good luck.

Shakyone.

---

### Post by jmorales on 2008-01-18
Thanks for your reply. I actually managed to "fix" my xp drives using an xp recovery console disc. I ended up formatting the main xp drive and the dual boot grub menu was working perfectly except for that xp wouldnt load. i would get an ntldr not found or something like that. restart. so i just stayed on my ubuntu drive for a while. last night i tried the fixmbr that ive read in xp recovery console and it wiped out grub. so i couldnt boot into gutsy. so i reinstalled grub as per a nice how to on here, but thats when my problems got worse. it now seems like theres a filesystem issue as it load very very slowly and eventually just goes into a forced fsck and never stops. it was going all night. i searched on here quite a bit this morning and i think i found some answers. i hoe they work because i really am not in the mood to have another unbootable drive and lose all my data. 

phew!

---

