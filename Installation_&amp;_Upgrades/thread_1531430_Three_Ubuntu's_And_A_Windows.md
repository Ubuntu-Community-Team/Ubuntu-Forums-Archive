---
title: "Three Ubuntu's And A Windows"
date: 2010-07-15
forum: Installation &amp; Upgrades
---

### Post by Gene393 on 2010-07-15
Hi, I recently had to factory default my windows 7 desktop computer, I didnt reinstall windows 7 for quite a while but I did reinstall ubuntu, however, when I factory defaulted, it didnt remove my previous ubuntu installation, but it did remove grub, so when I reinstalled ubuntu, I now have 2 installations, then when I reinstalled 7, I got rid of grub again so I reinstalled ubuntu and now Ive got 3 installs of it, can someone please tell me how to get rid of two of the ubuntu installs without ruining my third ubuntu install and windows

---

### Post by HenneBaby02 on 2010-07-15
> **Gene393 said:**
> Hi, I recently had to factory default my windows 7 desktop computer, I didnt reinstall windows 7 for quite a while but I did reinstall ubuntu, however, when I factory defaulted, it didnt remove my previous ubuntu installation, but it did remove grub, so when I reinstalled ubuntu, I now have 2 installations, then when I reinstalled 7, I got rid of grub again so I reinstalled ubuntu and now Ive got 3 installs of it, can someone please tell me how to get rid of two of the ubuntu installs without ruining my third ubuntu install and windowsBy factory default do you mean reformatting your hard drive and re installing windows 7 ? and what do you mean by 3 ubuntus ?

EDIT: either way, ur safest bet b4 u get to deep into installing programs in windows 7, u shuld just delete all partitions on your harddrive and then re install windows 7 and then install ubuntu INSIDE windows 7 by either mounting the iso or using Wubi installer.

OR

put ur windows 7 disk in or usb whichever u use to install and wen u get to the partitions screen just delete all partitions except the NTFS or C:\ or whichever windows 7 is installed too ( BUT do be careful deleting partitions if your computer has a recovery mode partition)

hope this helps

---

### Post by AceRoom on 2010-07-15
Why use Wubi? I thought that operating systems installed through Wubi are a little slower than done from LiveCD/LiveUSB.

Anyway, the OP doesn't need to remove all partitions and reinstall everything. 

Check out which drives contain what OS by booting into your Ubuntu (One you want working). You can mount them and find out. Delete the ones containing the other two Ubuntu distributions and make a new partition in that space or extend one of your other partitions. 

If you're resizing partitions, backup your data first. So I guess it's better to just make new partitions for regular data in the place of the other two Ubuntu distros. 

Then update grub.

---

### Post by Gene393 on 2010-07-15
> **AceRoom said:**
> Why use Wubi? I thought that operating systems installed through Wubi are a little slower than done from LiveCD/LiveUSB.

Anyway, the OP doesn't need to remove all partitions and reinstall everything. 

Check out which drives contain what OS by booting into your Ubuntu (One you want working). You can mount them and find out. Delete the ones containing the other two Ubuntu distributions and make a new partition in that space or extend one of your other partitions. 

If you're resizing partitions, backup your data first. So I guess it's better to just make new partitions for regular data in the place of the other two Ubuntu distros. 

Then update grub.

Hi, just got some things to clear up

1. All three ubuntu partitions are the same version
2. I installed them by booting the disk on startup and choosing the install option
3. By factory defaulting I mean ho;ding Alt+F10 at the startup screen
4. I would prefer if I could just uninstall 2 of the ubuntus 'cos ones got java and flash and other updates which take forever to download in this country 'cos I've used up my months broadband

---

### Post by AceRoom on 2010-07-15
I don't really know what alt-F10 does. I don't have that option on my comp, at least I don't think I do. 

Anyway, can you boot into the Ubuntu that has Java? If not, boot into any and run update-grub in a terminal. Hopefully, it should detect all the different operating systems. Now boot into the Ubuntu that has all the programs that you need and delete the other two partitions containing Ubuntu.

---

### Post by Gene393 on 2010-07-15
> **AceRoom said:**
> I don't really know what alt-F10 does. I don't have that option on my comp, at least I don't think I do. 

Anyway, can you boot into the Ubuntu that has Java? If not, boot into any and run update-grub in a terminal. Hopefully, it should detect all the different operating systems. Now boot into the Ubuntu that has all the programs that you need and delete the other two partitions containing Ubuntu.

Im in the ubuntu partition I want to keep, how do I delete the other partitions?

Heres what it came up with when i did update-grub

Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.31-22-generic
Found initrd image: /boot/initrd.img-2.6.31-22-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
ls: cannot access /media/SHAUN'S: No such file or directory
ls: cannot access /media/SHAUN'S: No such file or directory
Found Windows Vista (loader) on /dev/sda1
Found Ubuntu 9.10 (9.10) on /dev/sda11
Found Windows 7 (loader) on /dev/sda2
Found Ubuntu 9.10 (9.10) on /dev/sda5
Found Ubuntu 9.10 (9.10) on /dev/sda9
done

---

### Post by Gene393 on 2010-07-15
> **AceRoom said:**
> I don't really know what alt-F10 does. I don't have that option on my comp, at least I don't think I do. 

Anyway, can you boot into the Ubuntu that has Java? If not, boot into any and run update-grub in a terminal. Hopefully, it should detect all the different operating systems. Now boot into the Ubuntu that has all the programs that you need and delete the other two partitions containing Ubuntu.

It doesnt say Alt-F10 on the startup menu but when you turn the computer on, at the screen when you change the boot pref for when you boot ubuntu from the cd, you can hold Alt-F10 to return the computer to its default state, but for some reason, it wont get rid of ubuntu

---

### Post by Gene393 on 2010-07-15
Just in case you hadn't realised, the titles meant to be a play on Three Funerals and a Wedding

---

### Post by AceRoom on 2010-07-15
Do you know how to find which partitions contain which OS?
Like sda1, sda2, hda1...

If you don't know which partitions are which, 
Open up gparted. You can mount and unmount from there. Unmount everything but the root partition (It won't allow you to unmount it anyway). Mount one at a time. You should be able to find which ones contain your other Ubuntu partitions. 
If you do, open up gparted (It's not installed by default so you may need to install it). The options there should be clear. Delete the two unwanted partitions and create a new to use as a data partition. 

If you don't know which partitions are which, 
Open up gparted. You can mount and unmount from there. Unmount everything but the root partition (It won't allow you to unmount it anyway). Mount one at a time. You should be able to find which ones contain your other Ubuntu partitions.

---

### Post by Gene393 on 2010-07-15
> **AceRoom said:**
> Do you know how to find which partitions contain which OS?
Like sda1, sda2, hda1...

If you don't know which partitions are which, 
Open up gparted. You can mount and unmount from there. Unmount everything but the root partition (It won't allow you to unmount it anyway). Mount one at a time. You should be able to find which ones contain your other Ubuntu partitions. 
If you do, open up gparted (It's not installed by default so you may need to install it). The options there should be clear. Delete the two unwanted partitions and create a new to use as a data partition. 

If you don't know which partitions are which, 
Open up gparted. You can mount and unmount from there. Unmount everything but the root partition (It won't allow you to unmount it anyway). Mount one at a time. You should be able to find which ones contain your other Ubuntu partitions.

Thanks, what do you mean by making a new to use as a data partition?

---

### Post by Gene393 on 2010-07-15
Ok, found that in sda4, ive got 4 linux-swaps and 4 ext4's, not sure which one is the one im using now but they have the size of each partition next to it

---

### Post by AceRoom on 2010-07-15
Well, the space currently occupied by your other two partitions must go somewhere other than wasted. If you use Windows as well, you can make that space into an NTFS partition which can be accessed both by Windows and Linux (Provided you have ntfs-3g). In that partition, you can whatever kind of data (Documents, Music, Videos, whatever) you want and you'll be able to access it from both operating systems. In fact, you can even install Windows software on it.

This IMO is a lot safer than extending your other partitions which can sometimes cause havoc on the data (i.e. You current say 30 GB Ubuntu partition can be made into 60 GB or so, provided that the two "spaces" are physically adjacent.

Again, I recommend the first option. 

If you don't have Windows, you might as well make that into an ext4 partition to store data.
--------------------
Sorry, forgot that you do. Right, so go with ntfs.

---

### Post by Gene393 on 2010-07-15
> **AceRoom said:**
> Well, the space currently occupied by your other two partitions must go somewhere other than wasted. If you use Windows as well, you can make that space into an NTFS partition which can be accessed both by Windows and Linux (Provided you have ntfs-3g). In that partition, you can whatever kind of data (Documents, Music, Videos, whatever) you want and you'll be able to access it from both operating systems. In fact, you can even install Windows software on it.

This IMO is a lot safer than extending your other partitions which can sometimes cause havoc on the data (i.e. You current say 30 GB Ubuntu partition can be made into 60 GB or so, provided that the two "spaces" are physically adjacent.

Again, I recommend the first option. If you don't have Windows, you might as well make that into an ext4 partition to store data.
Thanks, do you think you could give me a step by step walkthrough on how to do that?

---

### Post by AceRoom on 2010-07-15
Sorry, missed a lot of you replies. You can delete **ALL BUT ONE** of the linux swap files. 

In gparted, which partition is mounted as **/** i.e. as root.
Under the mount point column, you'll see /
That is the partition the current Ubuntu is using (This is the one you want to keep, right?)

You can delete two of sda11, sda5, sda9. The one that you don't delete is the one you found mounted as root.

---

### Post by Gene393 on 2010-07-15
> **AceRoom said:**
> Sorry, missed a lot of you replies. You can delete **ALL BUT ONE** of the linux swap files. 

In gparted, which partition is mounted as **/** i.e. as root.
Under the mount point column, you'll see /
That is the partition the current Ubuntu is using (This is the one you want to keep, right?)

You can delete two of sda11, sda5, sda9. The one that you don't delete is the one you found mounted as root.
Ive got one in sda4 called /dev/sda5 ext4, its got the / symbol, does this mean I can delete all other partitions in sda4 except one linux-swap, then do i make new ntfs partitions?

also, will this mess up grub and make the rescue failed thing come up 'cos that happened to me once

---

### Post by AceRoom on 2010-07-15
Post a screenshot of the gparted page as is.

You should be able to delete all other ext4 partitions and all but one swap. Let me look at the screenshot before I confirm. 

In addition, post the output of:
```
sudo fdisk -l
```

---

### Post by Gene393 on 2010-07-15
> **AceRoom said:**
> Post a screenshot of the gparted page as is.

You should be able to delete all other ext4 partitions and all but one swap. Let me look at the screenshot before I confirm. 

In addition, post the output of:
```
sudo fdisk -l
```

Ok, heres the output of the fdisk thing

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x10a166f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        2437    19573760   27  Unknown
/dev/sda2   *        2437       62017   478575616    7  HPFS/NTFS
/dev/sda3           62017       70123    65106548+   7  HPFS/NTFS
/dev/sda4           77506      121601   354201120    5  Extended
/dev/sda5           92271      109018   134528278+  83  Linux
/dev/sda6          120473      121601     9068661   82  Linux swap / Solaris
/dev/sda7           77506       83504    48186904+  83  Linux
/dev/sda8           91666       92270     4859631   82  Linux swap / Solaris
/dev/sda9          109019      120000    88212883+  83  Linux
/dev/sda10         120001      120472     3791308+  82  Linux swap / Solaris
/dev/sda11          83505       91326    62830183+  83  Linux
/dev/sda12          91327       91665     2722986   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdd: 499.4 GB, 499405291520 bytes
255 heads, 63 sectors/track, 60715 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00021968

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       60716   487699456    b  W95 FAT32
Note: sector size is 4096 (not 512)

Disk /dev/sde: 7952 MB, 7952142336 bytes
217 heads, 32 sectors/track, 279 cylinders
Units = cylinders of 6944 * 4096 = 28442624 bytes
Disk identifier: 0x20202020

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1         280     7765508    b  W95 FAT32
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 32)
Partition 1 has different physical/logical endings:
     phys=(120, 216, 32) logical=(279, 126, 32)
shaun@Deep-Thought:~$ 

and heres the screen shot
Im hoping this screenshot works, I wasnt sure how to attach it
[IMG]file:///home/shaun/Desktop/Screenshot.png[/IMG]

---

### Post by Gene393 on 2010-07-15
I'm running Ubuntu 9.10 Karmic Koala

---

### Post by AceRoom on 2010-07-15
sda1, sda2, sda3 are the drives you access from Windows and one of them contains the Windows OS. 

sda4 is an extended partition. All your other partitions are a part of sda4. 

A hard disk can only have four primary partitions and they get the numbers 1-4. All subsequent numbers are extended partitions.

sda7 is your currently used partition. sda8, your currently used swap file. 

**What is on sda5? There's seems to be a lot of data stored there. **

You can safely delete sda10, sda6, sda12.

---

### Post by Gene393 on 2010-07-15
> **AceRoom said:**
> sda1, sda2, sda3 are the drives you access from Windows and one of them contains the Windows OS. 

sda4 is an extended partition. All your other partitions are a part of sda4. 

A hard disk can only have four primary partitions and they get the numbers 1-4. All subsequent numbers are extended partitions.

sda7 is your currently used partition. sda8, your currently used swap file. 

**What is on sda5? There's seems to be a lot of data stored there. **

You can safely delete sda10, sda6, sda12.

sda5 is my other major ubuntu installation from before I factory defaulted so its got alot of installed files and things

after I delete sda5, sda 10, sda 6 and sda 12, do I mak partitions as ntfs's?

---

### Post by sxmaxchine on 2010-07-15
completely wipe the entire drive then install the OS

---

### Post by Gene393 on 2010-07-15
heres a new screenshot, i hope I havent stuffed something up, when i try to delete 6 it says to delete something else with a number higher then 6

---

### Post by Gene393 on 2010-07-15
should I delete all partitions under sda4 except sda 7 and 8, then on the unallocated partitions, right click and choose new and make them ntfs's?

---

### Post by AceRoom on 2010-07-15
Do you want to keep sda5 and sda7 or just the one you're using now? If you don't want sda5, delete sda5 and sda9. 
```
update-grub
```
Reboot and delete the swap which isn't used. Then make new partitions. If you want, you post your gparted screenshot after.

---

### Post by Gene393 on 2010-07-15
> **AceRoom said:**
> Do you want to keep sda5 and sda7 or just the one you're using now? If you don't want sda5, delete sda5 and sda9. 
```
update-grub
```Reboot and delete the swap which isn't used. Then make new partitions. If you want, you post your gparted screenshot after.

I want to keep the one Im using now, the windows 7 partition and the windows vista loader partition, should I just reboot now from what Ive done with the last screenshot I posted, then post a new screenshot?

---

### Post by AceRoom on 2010-07-15
In that, delete all the unmounted ext4 and swap partitions except the ones currently used i.e. sda5, sda9, sda6. If sda6 doesn't get deleted, continue. Then update-grub. Reboot and try deleting the swap which isn't used.

Then post a screen.

---

### Post by Gene393 on 2010-07-15
> **AceRoom said:**
> In that, delete all the unmounted ext4 and swap partitions except the ones currently used i.e. sda5, sda9, sda6. If sda6 doesn't get deleted, continue. Then update-grub. Reboot and try deleting the swap which isn't used.

Then post a screen.
At the moment I'm posting from the ubuntu disc demo mode, When I rebooted the grub rescue thing came up, at the moment Im making the new partitions tto see if that will help, will reboot and post if that works

---

### Post by Gene393 on 2010-07-15
No, didnt work, please can you help, this has happened to me before and I had to completely wipe everything that time, and even that didnt get rid of my past ubuntu installations, and it still wont let me delete sda 5 and 6

Heres a new screenshot, this is from the ubuntu disc demo mode after rebooting after filling in the unallocated partitiopns

---

### Post by AceRoom on 2010-07-15
Try unmounting sda6 or sda8. Then you should be able to delete one of them. Doesn't matter which one you delete. Either one will do.

What happens when you try to delete sda5?

Otherwise instead of deleting, try formating sda5.

---

### Post by Gene393 on 2010-07-15
> **AceRoom said:**
> Try unmounting sda6 or sda8. Then you should be able to delete one of them. Doesn't matter which one you delete. Either one will do.

What happens when you try to delete sda5?

Otherwise instead of deleting, try formating sda5.

I tried formatting sda 5, its just doing it now, sda 6 and 8 dont have an unmount option, they have a swapoff option where unmount should be, is this the same as unmount?

in sda 4 I now have my ubuntu partition I want, and 2 linux-swaps, if I can delete one of them and get my pc to boot again then it will be fine

---

### Post by Gene393 on 2010-07-15
can someone please post some help, this is really annoying

---

### Post by Gene393 on 2010-07-15
please, we've been working on this for about 4 hours now, we can't give up

---

### Post by AceRoom on 2010-07-15
Yeah, that should do. Since this is just a swap parition, it isn't really mounted. So swapoff either one (Whichever one you prefer). Then you should be able to delete it. Once you're done deleting all the extra partitions, you can make new ones.

Did sda5 get deleted?

---

### Post by Gene393 on 2010-07-15
> **AceRoom said:**
> Yeah, that should do. Since this is just a swap parition, it isn't really mounted. So swapoff either one (Whichever one you prefer). Then you should be able to delete it. Once you're done deleting all the extra partitions, you can make new ones.

Did sda5 get deleted?

sda5 got formatted to an ntfs thing

Ive now got 1 ext4
                  1 linux-swap
                  1 formatted sda
                   and a bunch of ntfs's
and 1 unallocated partition
 all of these are in partition 4

---

### Post by Gene393 on 2010-07-15
I just created a new partition in the unallocated partition, its now an ntfs

---

### Post by AceRoom on 2010-07-15
Try booting it now.

---

### Post by Gene393 on 2010-07-15
heres a screenshot of my current gparted screen

---

### Post by AceRoom on 2010-07-15
Theoretically speaking, your lone Ubuntu partition should work right now. Try booting into it and ```
update-grub
```.

---

### Post by AceRoom on 2010-07-15
If grub doesn't work and let you boot into Ubuntu, 
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

This is allow you to reinstall grub from the live CD.

---

### Post by Gene393 on 2010-07-15
> **AceRoom said:**
> Theoretically speaking, your lone Ubuntu partition should work right now. Try booting into it and ```
update-grub
```.

I have, it still went to the grub rescue thing, Im still running it from the demo disc at the moment, you dont think it could be something to do with grub looking in sda blah blah blah for th install of ubuntu that it installed with 'cos I deleted that. At the moment, this is what I'm doing [-o<

---

### Post by Gene393 on 2010-07-15
when I run update-grub from th cd I get this

grub-probe: error: cannot find a device for /.

---

### Post by AceRoom on 2010-07-15
In that case, reinstall grub from the live cd. The link I posted tells you how.

Are you booting with the disc inside the drive?

---

### Post by AceRoom on 2010-07-15
Try this:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

-----------------
You won't be able to run update-grub from the cd.

---

### Post by Gene393 on 2010-07-15
just trying that link, its not going well so far

---

### Post by AceRoom on 2010-07-15
Go to terminal
```
sudo mount /dev/sda7 /mnt/
sudo grub-install --root-directory=/mnt /dev/sda
sudo umount /mnt

```

This is from the guide pointed to from the site. I'll actually be leaving now to head home. Might not be able to reply for a while.

Basically, you'll need to reinstall grub and you're through.

---

### Post by AceRoom on 2010-07-15
Any luck?

---

### Post by AceRoom on 2010-07-15
Finally, you can remove some of the smaller ntfs partitions and resize the other ones to fill that space.

---

### Post by Gene393 on 2010-07-15
> **AceRoom said:**
> Any luck?
Sort of, it didnt fix grub but it did make it so when you load, it goes to the same thing that happens when you type sudo grub into the terminal, just trying the instructions from the link into grub now

---

### Post by Gene393 on 2010-07-15
Right, followed the instructions in the link Aceroom gave me and put this into grub, which, because of the code Aceroom told me to use before, now runs as if you had typed sudo grub into terminal, they worked and I now think that I may have grub reinstalled, now, if grub really has reinstalled, I just need to find out how to get grub back to normal, any ideas?

---

### Post by Gene393 on 2010-07-15
Icouldnt be bpthered fixing it prperly so i just reinstalled ubuntu to get grub, and loaded my old one from there, now I've just got 4 gb extra on my system, which i could easily get back if I cleaned out some stuff onmy windows partition

Thanks to all of you for helping

---

### Post by AceRoom on 2010-07-16
Meaning you still have two Ubunus? You can combine the large number of smaller ntfs partitions if you want.

---

