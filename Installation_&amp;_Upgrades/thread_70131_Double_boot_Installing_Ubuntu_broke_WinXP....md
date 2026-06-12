---
title: "Double boot: Installing Ubuntu broke WinXP..."
date: 2005-09-29
forum: Installation &amp; Upgrades
---

### Post by Elrohir on 2005-09-29
so, today I went for the double boot (One side Win, other side Ubuntu)... when I wanted to boot WinXP, the following error came up:

Missing File:
C:\Windows\System32\hal.dll

is there a way to fix this? can it be manually copied to the other partition? :confused:

I believe his is important: Win partition is NTFS... :???:

---

### Post by manicka on 2005-09-29
This may help

[http://www.lostcoders.net/posts-p36055.htm](http://www.lostcoders.net/posts-p36055.htm)

---

### Post by Elrohir on 2005-09-29
tried it... no go... after loading everything the CD needs, an Handler Exception Error appears...

SESSION3_EXCEPTION_ something...

then it asks to reboot...

so, any other idea? :(

---

### Post by Elrohir on 2005-09-29
anyone?

---

### Post by GTvulse on 2005-09-29
[QUOTE=Elrohir]anyone?[/QUOTE]
Hmmm.. That's a sign of a major change in hardware or a completely foobarred registry database, so major that Windows NT doesn't know how to handle it itself. When it is installed Windows takes a snapshot of the underlying hardware records it in the registry and always uses that information when you boot up the machine to load the needed drivers. On the other hand, the Linux kernel does on-the-fly hardware detection using a dynamic HAL detector and still boots up faster.... 

Not all is lost. Boot up the Ubuntu CD in rescue mode (type rescue at the boot prompt) follow the drill and mount your ubuntu partition. After you get access to root, and assuming your Ubuntu root is located in hda2, do the following:
```

parted /dev/hda set boot 2 on
grub-install /dev/hda2

```
When you reboot your machine, you should see the grub menu and be able to boot up to Ubuntu, at least. You can rescue your Windows files from there to backup on CD/DVD[1]. To mount your NTFS partition, I'd suggest the command I use:
```

sudo mkdir /media/windows
sudo mount -t ntfs -o ro,umask=022,utf8 /dev/hda1 /media/windows

```
This will have your windows partition to show up as en entry in the Places menu.

[1] That's a story for another day, but you can use Nautilus CD/DVD burner for least complications. Open a file explorer window, select "go"/"CD/DVD Creator" and use it as if using the builtin Windows XP CD burner.

---

### Post by dbott67 on 2005-09-29
**[COLOR="RoyalBlue"]EDIT: It looks like dradul beat me to the punch by 2 minutes.  You may just want to confirm the output of fdisk vs. boot.ini before taking any drastic measures./EDIT[/COLOR]**

Sometimes this error message can be caused by a misconfigured boot.ini file.  This may have been caused during the partitioning of your hard drive when installing Ubuntu.

I take it you can still boot into Ubuntu, correct?  If so, boot up and print out your partition table information by typing **sudo fdisk -l /dev/hda**.  Next, [mount your NTFS partition]("http://www.ubuntuguide.org/#mountunmountntfs") in Ubuntu and open your boot.ini file in a text editor.  *[COLOR="Red"]While you're here, you may want to backup your data, just in case.[/COLOR]*

Does the boot.ini information match the fdisk -l output?

For example, if I type **sudo fdisk -l /dev/hda** I get:
```
Disk /dev/hda: 100.0 GB, 100030242816 bytes
16 heads, 63 sectors/track, 193821 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Device Boot Start End Blocks Id System
/dev/hda1 * 1 58156 29310561 7 HPFS/NTFS
/dev/hda2 58156 154881 48749242+ f W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/hda3 154881 193816 19623397+ 83 Linux
Partition 3 does not end on cylinder boundary.
/dev/hda5 58157 153160 47881701 7 HPFS/NTFS
/dev/hda6 153160 154881 867478+ 82 Linux swap / Solaris
```

hda is Hard Disk A (or disk one); hda1 is the FIRST partition on Hard Drive  1.  In this example, it's also the NTFS partition (aka a Windows XP partition).

The boot.ini file should contain similar information (i.e. that Windows XP is located on the same partition of the same drive as listed in fdisk above.  If not, this is the problem).  Post the output "sudo fdisk -l /dev/hda", as well as the contents of your boot.ini file.

-Dave

---

### Post by Elrohir on 2005-09-30
ok, here's what I can do...

I can boot into Ubuntu, but not into XP (Ubuntu broke XP didn't give the hint?)...

here's my Fdisk info...

```
Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2442    19615333+  83  Linux
/dev/hda2            2443        2550      867510    5  Extended
/dev/hda3   *        2551        4997    19655527+   7  HPFS/NTFS
/dev/hda5            2443        2550      867478+  82  Linux swap / Solaris
```

and hell no! it doesn't look at all to the boot.ini file...

```
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

so, anyway, how do I restore the file for WinXP to load?

---

### Post by dbott67 on 2005-09-30
[QUOTE=Elrohir]ok, here's what I can do...

I can boot into Ubuntu, but not into XP (Ubuntu broke XP didn't give the hint?)...

here's my Fdisk info...

```
Disk /dev/hda: 41.1 GB, 41110142976 bytes
255 heads, 63 sectors/track, 4998 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2442    19615333+  83  Linux
/dev/hda2            2443        2550      867510    5  Extended
/dev/hda3   *        2551        4997    19655527+   7  HPFS/NTFS
/dev/hda5            2443        2550      867478+  82  Linux swap / Solaris
```

and hell no! it doesn't look at all to the boot.ini file...

```
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(3)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(3)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

so, anyway, how do I restore the file for WinXP to load?[/QUOTE]

> and hell no! it doesn't look at all to the boot.ini file...

LOL! :)  I should have clarified that the boot.ini looks *different*, but the information is the same (i.e. similar to spoken language where "hello" in English = "bonjour" in French but they mean the same thing).

The short answer is this: the last line of your boot.ini says go to the SECOND partition, while the line above it says go to the third partition.

The long answer is this: Breaking down what boot.ini says (into English):

(Note: here's the confusing part --- the boot.ini uses 2 numbering conventions: ordinal numbers (i.e. numbers that start counting at 0) and cardinal numbers (i.e. numbers that start counting at 1).

So, an example would be:

```
multi(<A>)disk(<B>)rdisk(<C>)partition(<D>)

A is the ordinal number for the boot adapter. The first adapter, which is usually the boot adapter, is 0. 

B provides disk-parameter information. In a multi syntax line, this variable is always 0 because the multi syntax uses the INT 13 call instead of a self-discovery method.

C is an ordinal number that specifies the disk attached to the adapter; the number can range from 0 to 3, depending on the number of drives on the adapter. 

D specifies the partition number; the first possible number is 1 (as opposed to adapters and drives, which begin numbering with 0).

```

In your case, the linux fdisk command lists your NTFS partition as hda3 (the 3rd partition on the first hard disk).  The boot.ini lists it as being:
```

multi(0)disk(0)rdisk(0)partition(3)
```
which is (reading it from right to left): the ***third*** partition on the first disk (rdisk=0) on the first adapter (multi=0).  This is good (it means that both systems are reading it as the same information).

However, the next line is reading it as:
```

multi(0)disk(0)rdisk(0)partition(2)
```
which is (reading it from right to left): the ***second*** partition on the first disk (rdisk=0) on the first adapter (multi=0).  This is bad.  We need to edit your boot.ini to remove that last line (the one the says):

```
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

In Ubuntu, copy your boot.ini to a floppy disk and remove the last line (as noted above).  Then, Using your XP install CD, boot to recovery mode and copy over the boot.ini from the floppy to the root of your NTFS partition (typically C).

Hope this helps.  Keep us posted.

-Dave

---

### Post by Elrohir on 2005-09-30
I'll try to do this... 

by "recovery mode" you mean ASR, ARS or whatever? cuz the main problem is when I try to boot through CD-ROM, some memory dumping thing happens and never loads... only loads the drivers needed... then, blue screen of death... :(

I'll try though ARS (Automatic Rescue System??)...

---

### Post by dbott67 on 2005-09-30
I've never used ASR (automated system recovery) before.  I believe it can be used to get the system up & running so that you can begin a restore procedure.

If the system keeps blue-screening, I would just try [NTFS4DOS]("http://www.datapol.de/dpe/freeware/"), which is a freeware program that can be used to read & write to an NTFS partition.  Just download the utility, run the setup & create a boot floppy as per the instructions.

After booting, you should be able to edit the C:\boot.ini file.

-Dave

---

### Post by oneybm on 2005-09-30
Actually you really don't have to go through all of that to get the Windows partition back.  If all you want to do is edit the boot.ini file in XP you can do so a bit simpler.  Take the XP CD and boot from it.  Once you get to where it asks if you want to install or whatever, you can hit R to go to the recovery console.  Once you are in the recovery console it will asks you what installation you want to work with, you have to hit 1 and then enter I believe.  After it does that it will want to know what the administrator password is.  Typically most people have no idea what this is, try just hitting enter and that usually works.  The next part is where it gets interesting.  You can either just type fixboot and hit enter and it will fix your boot.ini so that it automatically loads windows and removes anything in your MBR (master boot record) that points to anything else.  The other option would be to type edit boot.ini and hit enter.  That should go ahead and open the MS DOS editor with boot.ini already loaded.  From there you can edit and save it.

Hope some of that helps and its not 100% accurate as I am at work and havin gto do this from memory.  It's been awhile since I was in the recovery console.

---

### Post by dbott67 on 2005-09-30
> Actually you really don't have to go through all of that to get the Windows partition back.
You do if you want to also preserve the Ubuntu/grub installation.  Fixmbr (or fdisk /mbr) is an option if he can boot from the CD, but it also blows away grub.  I'm trying to preserve both the Windows AND Ubuntu installation, that's all.

The reason I'm recommending the NTFS4DOS is that whenever he boots from the CD, he gets a Blue Screen of Death:
> the main problem is when I try to boot through CD-ROM, some memory dumping thing happens and never loads... only loads the drivers needed... then, blue screen of death...
NTFS4DOS might allow him to quickly edit the boot.ini file (preserving his XP installation) as well as saving GRUB from getting nuked via fixmbr.


-Dave

---

### Post by rippon on 2005-10-01
Same thing happened to me except no missing file.
It is like it doesnt know where to boot to.
I am lost as to how I should fix it. 
Working through  suggestions.

I made a thread in this forum if anyone wants to check it out, I wrote down the numbers it gave me.
Thank you,
Dan Rippon

---

### Post by Elrohir on 2005-10-03
ok, back online... tried to do the NTFS4DOS thingy, no go... some error reding NTFS or something... cant recall... :mad:

now I'll format my HD and begin clean... again... lol... ;-)

---

### Post by kingsidy on 2005-10-03
i got the same error a few month back when i tried to add more space to my ubuntu install by deleting a hidden partition. I could boot into ubuntu but i could not into windows. I think that for windows to boot properly it has to be install in the first partition of the hard drive. I think that in your post it seemed to be the other way around. If you install linux in front of window then windows would not start. 

The way i fixed that problem was a fresh install. I repartiioned my hard drive leaving windows in the first partition and ubuntu right after. I think that your situation is similar to mine. So u might have to do a fresh install of everything. If you do, make sure that you install windows first and ubuntu after

---

### Post by Elrohir on 2005-10-03
you're correct... I'm on it...:???:

---

### Post by Elrohir on 2005-10-04
ok, so I did a fresh install (spent all night on it, I may need a cup of coffee now)... everything works correctly, GRUB loads WinXP w/o problems, no hal.dll corrupt message... :cool:

---

