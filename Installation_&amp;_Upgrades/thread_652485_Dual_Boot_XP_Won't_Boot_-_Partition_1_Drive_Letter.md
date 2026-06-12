---
title: "Dual Boot: XP Won't Boot - Partition 1 Drive Letter unknown, Ubuntu is fine.."
date: 2007-12-28
forum: Installation &amp; Upgrades
---

### Post by AlexsAntidote on 2007-12-28
I've been searching all over for a solution, but none have worked for me...

First the specs:
Acer Aspire 9300 Notebook
AMD Turion 64 x2 Mobile Technology TL-50 1.6 GHz
1 GB RAM
384 MB NVIDIA GeForce Go 7300
120 GB HDD

Pre-installed with Windows Vista Home Premium
2 partitions, one with Vista the other "data" (but looked empty)
1 hidden partition (more on that later)

I installed Windows XP Professional on the second partition. So after that I had:
C: (vista)
D: (XP)
(hidden partition)

(because I didn't want to bother with dual-booting as i hate vista, It only booted XP)

I installed Ubuntu - 7.10 and it runs great!

However, XP will not boot from grub.... Here's the problem.
When attempt to load XP it starts the Acer eRecovery which then tells me the following error: "partition 1 drive letter unknown" and reboots.

After some searching and messing around I decided to put in the XP install disk and go as far as to see how it views the partitions. here's what I get:
[part 1] -: (EISA utilities) 8001 MB           ---- Acer eRecovery
[part 2] C: (Acer) <ntfs> 37561 MB         ---- Windows Vista
[part 3] F: (unknown) <fat32> 14358 MB  ---- Ubuntu
[part 5] G: (unknown) <fat32> 675 MB    ---- Swap
[part 4] D: (Custom) <ntfs> 52425 MB     ---- Windows XP

So the problem is with the EISA partition which is the Acer eRecovery. Apparently when windows XP is supposed to boot it is somehow set to boot from the eRecovery which ends with the error as it does not recognize the drive letter for part. 1.

I also tried to boot Vista (out of curiosity) and it stops with the error: missing or corrupt file: (windows root)/windows/system32/ntoskrnl.exe

I really don't care about the vista error, but would really like to fix the XP boot so my wife can use the laptop too....

Does anyone know how this can be fixed or bypassed? I've tried changing the grub menu.lst so that xp will boot from (hd0,4) as well as tried (hd0,5) but looking at it now I should probably try (hd0,3) but I really don't think that's the problem, I think the problem is with the EISA or Acer eRecovery partition... 

Does anyone know if I should just remove that partition and if so will it work? or can I somehow assign a letter to the -: partition?

I know if I delete that partition then I cannot get it back, and Acer charges money to reinstall it as well as wiping out the whole drive, and that's not an option for me. I don't think I'll ever use the eRecovery, so if it will work I'll remove it, but I really don't want to do it just because I can...

Any help in this would be greatly appreciated! (I don't want my wife blaming Ubuntu / Linux for "ruining" the computer lol).

---

### Post by empthollow on 2007-12-28
i am not familiar with acer recovery.  if you check /boot/grub/menu.lst your windows boot should look something like this:
```
# title		Windows 95/98/NT/2000
root		(hd0,0)
makeactive
chainloader	+1
```
the hd0 refers to the master hard drive and the 0 refers to the first partition which is probably listed in ubuntu as /dev/hda1.  you can check this by running the following command:
```
sudo fdisk -l
```
this will list all the partitions but probably win xp is usually the first. grub always subtracts 1 from the  ubuntu device name.  If you cannot get it to boot correctly my guess would be that something went wrong in the partitioning process.  Unfortunatly since i am unfamiliar with acer recovery i don't know what to suggest.  my only thought is that the acer recovery program is running because it is not recognizing the device and it does not see a windows boot sector on that partition.  i would just for fun try using (hd0,0) as root.  Hope this helps:mad:

---

### Post by ijason on 2007-12-28
you can use Partimage to save the Acer recovery partition to later re-build it if you need it. although, getting the boot list back to the "original" condition might be a more daunting task. that way you could delete the recover partition if need be, and free up space. google partimage to get to their site and see what the program can do for you :)

and, yes, what **empthollow** said... check your boot list and try adjusting the "root (hd0,0)" to different values, it sounds like you're actually booting the recovery partition when you want to boot the xp partition, "root (hd0,1)" may work.

---

### Post by AlexsAntidote on 2007-12-28
Thank you both for your help.

Just to clarify: I had already tried changing the menu.lst in grub, I just hadn't tried all of the available partitions.

So here's what happens when I try the following:
(hd0,0) - Acer eRecovery initializes, XP boot screen appears, then returns to Acer eRecovery and displays the error mentioned in the original post.
(hd0,1) - This attempts to load vista, which results in a different error also mentioned in the OP - missing or corrupt system file: (windows root)/windows/system32/ntoskrnl.exe
(hd0,2) - error 12 (i can't remember the exact wording, but it does not recognize the device or something) - this is the root for Ubuntu
(hd0,3) - error 12 .... - this is the windows XP partition...
(hd0,4) - error 12 .... - this is the swap for Ubuntu...

I will do a search for partimagic and see what I can find out... However, from the looks of things I'm still going to have to figure out how to create a boot record for Windows XP as the Acer eRecovery partition seems to be where it is located, and I think that if i simply remove it then it will also remove the XP boot record... Unless the XP boot record is located elsewhere and the acer erecovery is bypassing it somehow...

I don't know enough about this subject to really figure it out on my own... so I appreciate your guys' help!

---

### Post by AlexsAntidote on 2007-12-28
maybe this will help also...
==========================================================
*************:~$ sudo fdisk -l
[sudo] password for *********:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7f457f45

-- Device - Boot -- Start --------- End ------- Blocks -------- Id ---------- System
/dev/sda1 - * ----------- 1 -------- 1020 ----- 8193118+ --- 12 --------- Compaq diagnostics
/dev/sda2 ---------- 1021 -------- 5895 --- 39158437+ ---- 7 --------- HPFS/NTFS
/dev/sda3 ---------- 7722 ------ 14592 --- 55191307+ ----- f --------- W95 Ext'd (LBA)
/dev/sda4 ---------- 5896 -------- 7721 --- 14667345 ----- 83 --------- Linux
/dev/sda5 ---------- 7808 ------ 14592 --- 54500481 ------- 7 --------- HPFS/NTFS
/dev/sda6 ---------- 7722 -------- 7807 -------  690732 ----- 82 --------- Linux swap / Solaris

Partition table entries are not in disk order
========================================================

---

### Post by Craigus on 2007-12-28
See if the supergrub boot disk can sort it out:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by Partyboi2 on 2007-12-28
```
 I installed Windows XP Professional on the second partition. So after that I had:
C: (vista)
D: (XP)
(hidden partition)
```
I might be wrong in this, but I think you are trying to boot xp from a hidden partition and its not going down so well with grub. If you were to unhide the partition that might work.

---

### Post by AlexsAntidote on 2007-12-28
> **Craigus said:**
> See if the supergrub boot disk can sort it out:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

I got supergrub and have been messing around in it, but so far I'm just getting the same results as when I manually changed settings in /boot/grub/menu.lst

---

### Post by AlexsAntidote on 2007-12-28
> **Partyboi2 said:**
> ```
 I installed Windows XP Professional on the second partition. So after that I had:
C: (vista)
D: (XP)
(hidden partition)
```
I might be wrong in this, but I think you are trying to boot xp from a hidden partition and its not going down so well with grub. If you were to unhide the partition that might work.

Quite possibly... Since fdisk -l detected a 6th partition that wasn't showing up in either grub or the windows xp fdisk, that might be the problem...

My question is how do I unhide a hidden partition? I'm looking for it in supergrub and cannot find it. I suppose I could try it in grub but I don't really know what I'm doing here...

For the most part I'm a linux noob but i am familiar with a lot of the concepts and terms, so if you could just point me in the right direction it would be greatly appreciated

---

### Post by Partyboi2 on 2007-12-29
How did you hide it in the first place? I have heard partition magic can hide and unhide it.

---

### Post by AlexsAntidote on 2007-12-29
> **Partyboi2 said:**
> How did you hide it in the first place? I have heard partition magic can hide and unhide it. Not sure what linux program can do it. I will have a look around and let you know if I find one.

I didn't do it on purpose that's for sure!

I wish I could edit the MBR so that it didn't go to the Acer eRecovery but rather the original XP boot record instead... It never loaded Acer eRecovery prior to the installation of Ubuntu...

I tried adding some hide and unhide commands in /boot/grub/menu.lst just based off of what i found at -->[ http://ubuntuforums.org/archive/index.php/t-59412.html]("http://ubuntuforums.org/archive/index.php/t-59412.html")

I'll post here later if it works... if not, I'm going to bed and will give it another go tomorrow...

---

### Post by empthollow on 2007-12-29
i'm not very familiar with windows recovery but i know that there are some commands like fixmbr for repairing the master boot record.  this can be accessed if you boot off of the windows disk and choose console durring the setup process.  i'm not sure about hidden or unhidden partitions but you could try fixmbr on the windows disk and then reinstall grub from a live cd and that might fix your problem.

---

### Post by AlexsAntidote on 2007-12-29
> **empthollow said:**
> i'm not very familiar with windows recovery but i know that there are some commands like fixmbr for repairing the master boot record.  this can be accessed if you boot off of the windows disk and choose console durring the setup process.  i'm not sure about hidden or unhidden partitions but you could try fixmbr on the windows disk and then reinstall grub from a live cd and that might fix your problem.

Yeah the adjustments I made last night didn't work, so I'll give this a try next. I saw an option for this when messing around in supergrub. I think I will try that as well. I'll let you guys know what happens when I get a chance, if I don't totally mess everything up.

---

### Post by AlexsAntidote on 2007-12-29
Ok, so I managed to fix it... well at least well enough to load XP... It's ugly but I can work with it...

here's what I did:
I inserted the windows XP disk and proceeded to repair my installation of XP. It took several attempts to finish it, and another 40 minutes to re-install all the system files and drivers... (haven't bothered with windows update yet) but at least all of my files are still there and most of my settings are still the same!

Now here's some notes of interest if you've been helping me out or just reading the above posts:
I had to load windows from the Vista boot option from Grub!
The Windows XP boot option in grub still loads Acer eRecovery... 

The difference? the Vista is set to boot from (hd0,1) while the XP is set to boot from (hd0,0).

So as I stated before, the Acer eRecovery is installed on the 1st partition... And since windows successfully boots from the second partition (which is actually where vista is installed) it's a good thing I didn't remove vista! Though I think I can safely remove the eRecovery partition if I really wanted to.

Now I just have to figure out how to clean up the bootcfg on windows since I initially messed around with that in the command prompt from the windows disk before i decided to recover and added entries that don't do anything lol!

After reflecting on this whole mess I think the problem was complicated but most likely the following:
since I initially had Acer eRecovery and Vista and then proceeded to install XP, that equated to 3 partitions... when I installed Ubuntu I repartitioned the partition which Vista was installed on, and thus was located prior to the windows XP partition, so when I added another partition in between Vista and XP then somehow it must have confused XP into thinking something was wrong...

I think if I ever did this again I would just do a complete reformat and install Ubuntu first then XP and go through the hastle of reloading all my data...

Thanks to all for your help, I learned a lot and it works... I appreciate all of the advice, even if it didn't directly result in a solution, it was helpful nonetheless.

take care!

---

