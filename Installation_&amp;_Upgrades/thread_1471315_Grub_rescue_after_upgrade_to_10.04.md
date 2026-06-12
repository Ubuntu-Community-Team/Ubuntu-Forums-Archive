---
title: "Grub rescue after upgrade to 10.04"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by serialbox on 2010-05-03
I have a laptop running Windows 7 and had Ubuntu 9.10 on dual boot.

Everything was working fine until I was prompted to upgrade Ubuntu from 9.10 to 10.04.

I did the upgrade from the updater inside Ubuntu, and after completing the upgrade I cannot boot in to either Windows 7 or Ubuntu.

As soon as I reboot my computer, I get a
"grub rescue" prompt and an error, "no such device"

This happened immediately after completing the upgrade.  

Can someone please point me in the direction in order to get my computer to be able to boot up again?  I have copies of both 9.10 and 10.04 Live CD.

Windows 7 was installed first, and Ubuntu 2nd.. but I dont know enough about mounting and such to know which partition contains windows and which has ubuntu.  hd0 vs hd1?

Right now I am completely locked out of both operating systems on my computer.



Any help would be appreciated.

Thanks

---

### Post by Wilson423 on 2010-05-03
Started new thread:
[http://ubuntuforums.org/showthread.php?p=9229593#post9229593](http://ubuntuforums.org/showthread.php?p=9229593#post9229593)

---

### Post by bcbc on 2010-05-03
> **serialbox said:**
> I have a laptop running Windows 7 and had Ubuntu 9.10 on dual boot.

Everything was working fine until I was prompted to upgrade Ubuntu from 9.10 to 10.04.

I did the upgrade from the updater inside Ubuntu, and after completing the upgrade I cannot boot in to either Windows 7 or Ubuntu.

As soon as I reboot my computer, I get a
"grub rescue" prompt and an error, "no such device"

This happened immediately after completing the upgrade.  

Can someone please point me in the direction in order to get my computer to be able to boot up again?  I have copies of both 9.10 and 10.04 Live CD.

Windows 7 was installed first, and Ubuntu 2nd.. but I dont know enough about mounting and such to know which partition contains windows and which has ubuntu.  hd0 vs hd1?

Right now I am completely locked out of both operating systems on my computer.



Any help would be appreciated.

Thanks
Please run and post between code tags (press # above) the output of the [bootinfoscript]("bootinfoscript.sourceforge.net/").

This will tell us what we need to know. You could also try and recall where you installed grub2 (did it prompt you to select all partitions?).

---

### Post by bcbc on 2010-05-03
> **Wilson423 said:**
> I have the exact same problem also. except I put 10.04 on a different drive and now the windows drive is giving me the Grub Rescue prompt. 

Mine started with a broken install on the Ubuntu drive, so I made a install jump drive and formated the Ubuntu drive and reinstalled... this somehow corrupted my windows drive and is blocking the HP recovery just after POST.
I can boot off the jump drive only now. I can still see all the information in the windows drive. I just cannot boot that drive.

Any clues?

Run the bootinfoscript - it would be better to create a new thread and post your results there, and then edit your post above with a link to the new thread. That way it won't get confusing - although it may seem like the same problem, it may not be.

---

### Post by serialbox on 2010-05-03
> **bcbc said:**
> Please run and post between code tags (press # above) the output of the [bootinfoscript]("bootinfoscript.sourceforge.net/").

This will tell us what we need to know. You could also try and recall where you installed grub2 (did it prompt you to select all partitions?).


During the upgrade process, it asked me where to install grub to, and because I didn't know which drive contained windows and which contained ubuntu, I installed it to ALL the drives listed, .. If i remember correctly was something like

hda
hda1
hda2
hda3

There was a "help" link that said, "if you are unsure where to install it, select all of them"

I will boot off of the LiveCD and then run the bootinfo script and post the results later.  

Is there anything else I may need?  Once I leave my office I have no computer until I can boot into my laptop at home so i want to make sure I burn whatever I need here at the office to take home with me.

Thanks for the help

---

### Post by bcbc on 2010-05-03
> **serialbox said:**
> During the upgrade process, it asked me where to install grub to, and because I didn't know which drive contained windows and which contained ubuntu, I installed it to ALL the drives listed, .. If i remember correctly was something like

hda
hda1
hda2
hda3

There was a "help" link that said, "if you are unsure where to install it, select all of them"

I will boot off of the LiveCD and then run the bootinfo script and post the results later.  

Is there anything else I may need?  Once I leave my office I have no computer until I can boot into my laptop at home so i want to make sure I burn whatever I need here at the office to take home with me.

Thanks for the help

Well that pooched the windows bootsector for sure. Many people have fallen foul of that 'helpful' comment. Good news is that it should be fully fixable.

Now I am just curious whether you installed using wubi, since that might explain why you can't boot anything right now (normally people that did that can still boot ubuntu). But the bootinfoscript will tell all if you can't remember.

In addition to the 10.04 liveCD, you also may need your windows 7 rescue/install disk disk. You can create one from a working version of windows 7, or download one from [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/"). It's a good idea to have one of these around anyway.

PS was there anything else in the upgrade that stands out as unusual?

---

### Post by serialbox on 2010-05-03
> **bcbc said:**
> Well that pooched the windows bootsector for sure. Many people have fallen foul of that 'helpful' comment. Good news is that it should be fully fixable.

Now I am just curious whether you installed using wubi, since that might explain why you can't boot anything right now (normally people that did that can still boot ubuntu). But the bootinfoscript will tell all if you can't remember.

In addition to the 10.04 liveCD, you also may need your windows 7 rescue/install disk disk. You can create one from a working version of windows 7, or download one from [here]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/"). It's a good idea to have one of these around anyway.

PS was there anything else in the upgrade that stands out as unusual?

first i want to thank you for helping.. i really appreciate it.. i am screwed until I can get this fixed.

If wubi is the windows installer for Ubuntu then yes, that's what I used.

The only other odd thing that happened during the upgrade was that I ended up in an infinite loop during the grub installation/upgrade when it was trying to find my partitions.  Had to ^C to stop it from happening, but I read on a forum that it was ok to do that because the installer would ask me about that info later, which it did, when i selected all.

and yes.. that 'helpful' tip seems to be what screwed me :P

I've got my Win 7 original CD but for some reason I cant even boot off of that anymore.  After loading the system files (gray progress bar), my screen goes black and all I see is my mouse pointer and the system hangs.  This all happened after the failed ubuntu upgrade

I'll deal with Windows later, and if I can't save it, no big deal.  I just need at least one of these OS's to boot up so I can back up my data.

---

### Post by arichards11 on 2010-05-03
Hi,

I fell in the same trap with the upgrade and that "help" message saying to select all drives.  When the machine boots up, I get Grub, but it does not go anywhere.....I tried erasing the ubuntu 9 partition and installing fresh in that same partition to see if it would see my windows partition, but the problem remained the same (yes, it was obvious, but I had to try).  Ok, I see that the post says this is fixable but could someone PLEASE do a "step by step" on how to fix this?  I already tried the Windows 7 rescue disk and it says there is nothing wrong with my system!

Could I get a step by step even to know my partition names?  I actually had Windows XP, Windows 7 and ubuntu 9 working beautifully until idiot me decided to upgrade! Why couldn't I have left well enough ALONE!  I am freaked out and upset at myself......please help  :confused:

Thanks GREATLY to anyone that can help.

---

### Post by bcbc on 2010-05-03
> **serialbox said:**
> first i want to thank you for helping.. i really appreciate it.. i am screwed until I can get this fixed.

If wubi is the windows installer for Ubuntu then yes, that's what I used.

The only other odd thing that happened during the upgrade was that I ended up in an infinite loop during the grub installation/upgrade when it was trying to find my partitions.  Had to ^C to stop it from happening, but I read on a forum that it was ok to do that because the installer would ask me about that info later, which it did, when i selected all.

and yes.. that 'helpful' tip seems to be what screwed me :P

I've got my Win 7 original CD but for some reason I cant even boot off of that anymore.  After loading the system files (gray progress bar), my screen goes black and all I see is my mouse pointer and the system hangs.  This all happened after the failed ubuntu upgrade

I'll deal with Windows later, and if I can't save it, no big deal.  I just need at least one of these OS's to boot up so I can back up my data.

The ^C is a known issue for upgrading a wubi install to 10.04. I did one myself, and it shouldn't cause you any grief.

Not being able to boot a dvd/cd would be a problem. You will probably have to figure out the BIOS key to change boot options on the fly, or go into BIOS and change the order. Search on google with your computer model if you can't get into BIOS settings.

Once you can boot from the live CD you can backup your data. Boot using the Ubuntu Live CD and mount your windows partition. Copy all your files onto an external usb drive etc.
Note that your wubi install of ubuntu is contained within a file c:\ubuntu\disks\root.disk (or change c: to whatever drive you installed it on). You can copy this file in its entirety or 'loop mount' it and copy selected data from it.

Loopmount wubi install:
After booting the live CD and mounting your windows partition, find the path to the wubi file. This will be /media/<xxx>/ubuntu/disks/root.disk replacing <xxx> with your windows7 label or UUID. Mount it as follows:
```
sudo mount -o loop /media/<xxx>/ubuntu/wubi/root.disk /mnt
```
Now you can browse and backup your ubuntu files under /mnt

The fix...
For most people I am suggesting [this fix]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector"), however, you need to repair the MBR as well, so you might as well use [microsoft's page]("http://support.microsoft.com/kb/927392") for help. The following commands repair the bootsector as well as the MBR:
```
Bootrec.exe /FixMbr
Bootrec.ext /FixBoot

```
This should have you booting windows, and hopefully ubuntu as well. If you can't boot ubuntu, post back here.

PS if you are not sure of something, or something out of the ordinary happens don't ignore it. Post back here for help. It's better to ask first than try and fix something else later.

---

### Post by bcbc on 2010-05-03
> **arichards11 said:**
> Hi,

I fell in the same trap with the upgrade and that "help" message saying to select all drives.  When the machine boots up, I get Grub, but it does not go anywhere.....I tried erasing the ubuntu 9 partition and installing fresh in that same partition to see if it would see my windows partition, but the problem remained the same (yes, it was obvious, but I had to try).  Ok, I see that the post says this is fixable but could someone PLEASE do a "step by step" on how to fix this?  I already tried the Windows 7 rescue disk and it says there is nothing wrong with my system!

Could I get a step by step even to know my partition names?  I actually had Windows XP, Windows 7 and ubuntu 9 working beautifully until idiot me decided to upgrade! Why couldn't I have left well enough ALONE!  I am freaked out and upset at myself......please help  :confused:

Thanks GREATLY to anyone that can help.
First - it doesn't sound like you have wubi, so don't follow my previous advice. Second, you should start you own thread (just because it gets confusing with multiple issues and everyone starts replying). But anyway... as you figured, reinstalling ubuntu will not help you. You need to recover the boot sector of windows. Try this [link]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector"). If you are unsure, run the bootinfoscript (link above somewhere), create a new thread, post the results there, and then edit your post above with a link to your new thread so I can find it.

---

### Post by SINternet on 2010-05-03
Had the same thing but after my first attempt I just had a blinking cursor when I selected Win 7. Ubuntu booted just fine.

I selected all devices for Grub.

I then (with the Windows 7 DVD) booted and started the repair.
Selected Command prompt after a failed automatic repair.

Type the following;
bootrec /fixmbr
bootrec /fixboot
bootrec /scanos
bootrec /rebuildbcd

This should get you back your Win 7.

Now. I then attempted another 9.10 install. Upgraded and this time only selected the Ubuntu partition. I ended up with the grub recovery prompt.

I recovered my Win 7 and will install 9.10 but WILL NOT UPGRADE.

---

### Post by Wilson423 on 2010-05-03
Worked for me.. Thanks much SINternet
Also posted fix on my issue thread.

/salute

---

### Post by serialbox on 2010-05-04
> **bcbc said:**
> The ^C is a known issue for upgrading a wubi install to 10.04. I did one myself, and it shouldn't cause you any grief.

Not being able to boot a dvd/cd would be a problem. You will probably have to figure out the BIOS key to change boot options on the fly, or go into BIOS and change the order. Search on google with your computer model if you can't get into BIOS settings.

Once you can boot from the live CD you can backup your data. Boot using the Ubuntu Live CD and mount your windows partition. Copy all your files onto an external usb drive etc.
Note that your wubi install of ubuntu is contained within a file c:\ubuntu\disks\root.disk (or change c: to whatever drive you installed it on). You can copy this file in its entirety or 'loop mount' it and copy selected data from it.

Loopmount wubi install:
After booting the live CD and mounting your windows partition, find the path to the wubi file. This will be /media/<xxx>/ubuntu/disks/root.disk replacing <xxx> with your windows7 label or UUID. Mount it as follows:
```
sudo mount -o loop /media/<xxx>/ubuntu/wubi/root.disk /mnt
```
Now you can browse and backup your ubuntu files under /mnt

The fix...
For most people I am suggesting [this fix]("http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector"), however, you need to repair the MBR as well, so you might as well use [microsoft's page]("http://support.microsoft.com/kb/927392") for help. The following commands repair the bootsector as well as the MBR:
```
Bootrec.exe /FixMbr
Bootrec.ext /FixBoot

```
This should have you booting windows, and hopefully ubuntu as well. If you can't boot ubuntu, post back here.

PS if you are not sure of something, or something out of the ordinary happens don't ignore it. Post back here for help. It's better to ask first than try and fix something else later.

Thanks.  I tried your fix, and although I did see the BackupBS option and was able to save everything, when I rebooted, I still got the grub rescue prompt.  It felt like I was on the right track but oh well.

For some stupid reason I cannot boot off of my Win7 CD, or any windows OS cd for that matter.  After the Windows logo appears, I get a black screen and just my mouse cursor appears.  I left it like that for an hour and nothing progressed. 

Id think it was a problem with my cd drive but I CAN boot off of the Ubuntu Live CD, just not windows, which means I cannot get in to run bootrec.exe.  

Since I can boot off of the ubuntu CD, i'll try to mount my windows drive and backup my stuff.  The only real important stuff is my 20gb of music Ive collected over the years, then I'll do a fresh ubuntu install without dual boot.

---

### Post by arichards11 on 2010-05-04
Your advice worked.....that sourceforge link recovered my w7 MBR.....awsome! Thank you so much!!:popcorn:

---

### Post by bcbc on 2010-05-04
> **serialbox said:**
> Thanks.  I tried your fix, and although I did see the BackupBS option and was able to save everything, when I rebooted, I still got the grub rescue prompt.  It felt like I was on the right track but oh well.

For some stupid reason I cannot boot off of my Win7 CD, or any windows OS cd for that matter.  After the Windows logo appears, I get a black screen and just my mouse cursor appears.  I left it like that for an hour and nothing progressed. 

Id think it was a problem with my cd drive but I CAN boot off of the Ubuntu Live CD, just not windows, which means I cannot get in to run bootrec.exe.  

Since I can boot off of the ubuntu CD, i'll try to mount my windows drive and backup my stuff.  The only real important stuff is my 20gb of music Ive collected over the years, then I'll do a fresh ubuntu install without dual boot.

OK - I have seen some advice about installing lilo that should allow you to boot windows again (assuming the testdisk repair did fix your windows bootsector). I haven't used lilo lately, but installed it and checked the manual. 

Boot from livecd, go to terminal.
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
``` 

Note, this option will boot the partition marked active. You can check this by looking for the * under the boot column from the output of 
```
sudo fdisk -l
```
Make sure this is your windows partition. Reboot.

---

### Post by serialbox on 2010-05-04
> **bcbc said:**
> OK - I have seen some advice about installing lilo that should allow you to boot windows again (assuming the testdisk repair did fix your windows bootsector). I haven't used lilo lately, but installed it and checked the manual. 

Boot from livecd, go to terminal.
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
``` 

Note, this option will boot the partition marked active. You can check this by looking for the * under the boot column from the output of 
```
sudo fdisk -l
```
Make sure this is your windows partition. Reboot.

Thanks again.. That boot script you posted yesterday will tell me which partition is my windows one right?

I only ever had 1 main partition that had Windows on it, then used wubi to install ubuntu dual boot so I shouldn't have too many partitions to choose from.

---

### Post by bcbc on 2010-05-04
> **serialbox said:**
> Thanks again.. That boot script you posted yesterday will tell me which partition is my windows one right?

I only ever had 1 main partition that had Windows on it, then used wubi to install ubuntu dual boot so I shouldn't have too many partitions to choose from.

It'll be the one with the /bootmgr /bootbcd etc. files in it as per the bootinfoscript.

---

### Post by serialbox on 2010-05-04
> **bcbc said:**
> It'll be the one with the /bootmgr /bootbcd etc. files in it as per the bootinfoscript.

Ok.. I tried LILO on the partition that appeared to be Win7 as per the bootinfo script, and got the error below.  I even tried it on all parittions, /dev/sda1, sda2, sda3

```

ubuntu@ubuntu:~/Downloads$ sudo lilo -M /dev/sda1 mbr
Fatal: /dev/sda1 is not a master device with a primary parition table

```

here is the output of the bootinfo script.


```

ubuntu@ubuntu:~/Downloads$ cat RESULTS.txt 
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #256 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 9742616 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /bootmgr /boot/bcd

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr.mbr /wubildr

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /ubuntu/winboot/wubildr.mbr /ubuntu/winboot/wubildr 
                       /ubuntu/disks/root.disk /ubuntu/disks/swap.disk

sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1               2,048    20,482,047    20,480,000  27 Hidden HPFS/NTFS
/dev/sda2    *     20,482,048   254,451,711   233,969,664   7 HPFS/NTFS
/dev/sda3         254,451,712   488,394,751   233,943,040   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/loop1       defbedfe-f1f8-4f78-a9f3-52b326abd13e   ext4                                     
/dev/sda1        EAEE-EB49                              vfat       PQSERVICE                     
/dev/sda2        1E5A005C5A003357                       ntfs       Acer                          
/dev/sda3        446E86846E866E8C                       ntfs       DATA                          
/dev/sda: PTTYPE="dos" 
error: /dev/sdb: No medium found

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)

=======Devices which don't seem to have a corresponding hard drive==============

sdb 


```


I just tried it on /dev/sda and got a 'success' message, so im going to reboot and pray lol

```

The Master Boot Record of  /dev/sda  has been updated.


```

---

### Post by serialbox on 2010-05-04
ok...

THANK YOU

LILO on /dev/sda restored my mbr and I now get the option to boot into win7 or ubuntu.

however..... I must have messed up the boot records for ubuntu, because when I try to start that up, I get a black screen with an error.  Is there a simple way now to restore the ubuntu boot record?  If you need to see the screenshot of the error I'll grab it later and post it.

Now if only I can find a helpful person like you on a Windows forum so I can actually load up windows and get past the black screen with hardware i/o error.  hardware error doesn't make sense since ubuntu works.. must be a driver issue

---

### Post by bcbc on 2010-05-04
> **serialbox said:**
> ok...

THANK YOU

LILO on /dev/sda restored my mbr and I now get the option to boot into win7 or ubuntu.

however..... I must have messed up the boot records for ubuntu, because when I try to start that up, I get a black screen with an error.  Is there a simple way now to restore the ubuntu boot record?  If you need to see the screenshot of the error I'll grab it later and post it.

Now if only I can find a helpful person like you on a Windows forum so I can actually load up windows and get past the black screen with hardware i/o error.  hardware error doesn't make sense since ubuntu works.. must be a driver issue
So, if I understand you correctly, you get to see the windows menu to boot either windows or ubuntu, but neither option actually works?

I can understand the ubuntu not working. According to the bootinfoscript your ubuntu file system is toasted:
> sda3/Wubi: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: wrong fs type, bad option, bad superblock on /dev/loop1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I honestly don't know how you would recover from this - you can try running chkdsk on your windows partition. Hopefully you have a backup of the c:\ubuntu\disks\root.disk file.

If you can figure out why you can't boot the windows7 dvd maybe you can fix windows as well. Hopefully I misunderstood you and you can boot windows.

---

### Post by oscillate on 2010-05-05
HI, I have a similar problem with slightly different circumstances. I have one disk with two partitions, the larger is the main Windows XP segment and the other is a smaller one I made to hold the ubuntu installed through wubi. I'm now stuck at the "grub rescue>" prompt when booting up.

I was upgrading to 10.04 last night and the installation hung for hours at a point where it said '14 minutes remaining'. I had to restart, at which point I could not get back into ubuntu. I entered the recovery mode and selected 'fix broken packages', in that process the grub installer asked me where to install, I did not know which partition it belonged on and selected all (thanks, message). Now on a fresh boot it immediately goes to the "grub rescue>" prompt and that's where I am.

Are the steps I should take similar, and if so what should I do differently since it's WinXP and not Win7? Have I lost everything, or is it likely I can recover? 

I'm currently downloading the ubuntu live disk and will run the bootinfoscript when I can if that would help.

Thanks so much in advance.

---

### Post by serialbox on 2010-05-05
> **bcbc said:**
> So, if I understand you correctly, you get to see the windows menu to boot either windows or ubuntu, but neither option actually works?

I can understand the ubuntu not working. According to the bootinfoscript your ubuntu file system is toasted:

I honestly don't know how you would recover from this - you can try running chkdsk on your windows partition. Hopefully you have a backup of the c:\ubuntu\disks\root.disk file.

If you can figure out why you can't boot the windows7 dvd maybe you can fix windows as well. Hopefully I misunderstood you and you can boot windows.

That's right.  I get the Windows boot menu to load either ubuntu or windows but neither actually loads.  The windows issue started before the ubuntu problem I was having so that's nothing new. When selecting Windows I get the error below in the screenshot.  Even booting off of my Win7, WinVista and WinXP CD hangs the system with a black screen and no error.

[http://img687.imageshack.us/img687/3457/photoocq.jpg](http://img687.imageshack.us/img687/3457/photoocq.jpg)

The ubuntu error I get now when choosing ubuntu to boot is related to not being able to mount the drive.  But as you said it looks like it's toast.

The most important thing is I can at least back my files up now, and start over again.  It is impossible to get good help like this for Windows related issues

I cant thank you enough for your detailed help.

---

### Post by bcbc on 2010-05-05
> **oscillate said:**
> HI, I have a similar problem with slightly different circumstances. I have one disk with two partitions, the larger is the main Windows XP segment and the other is a smaller one I made to hold the ubuntu installed through wubi. I'm now stuck at the "grub rescue>" prompt when booting up.

I was upgrading to 10.04 last night and the installation hung for hours at a point where it said '14 minutes remaining'. I had to restart, at which point I could not get back into ubuntu. I entered the recovery mode and selected 'fix broken packages', in that process the grub installer asked me where to install, I did not know which partition it belonged on and selected all (thanks, message). Now on a fresh boot it immediately goes to the "grub rescue>" prompt and that's where I am.

Are the steps I should take similar, and if so what should I do differently since it's WinXP and not Win7? Have I lost everything, or is it likely I can recover? 

I'm currently downloading the ubuntu live disk and will run the bootinfoscript when I can if that would help.

Thanks so much in advance.
First backup your data if you haven't already done so.

To fix the boot sector for windows... first confirm it is broken and then fix (instructions in link): [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

If you are truly running a wubi install you also need to replace the grub bootloader in the MBR (master boot record) with the windows bootloader (only if running wubi). You can either use the windows repair method (run fixmbr for xp) or install lilo from within ubuntu (you can use a live CD for this):
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

Either method will get windows booting. Then you can worry about the wubi ubuntu after that.

---

### Post by oscillate on 2010-05-05
> **bcbc said:**
> First backup your data if you haven't already done so.

Thanks, I'll be running the bootinfoscript soon.
Do I need to back up the WinXP data, i.e. everything, as well? I don't have much in the ubuntu install.

---

### Post by bcbc on 2010-05-05
> **serialbox said:**
> That's right.  I get the Windows boot menu to load either ubuntu or windows but neither actually loads.  The windows issue started before the ubuntu problem I was having so that's nothing new. When selecting Windows I get the error below in the screenshot.  Even booting off of my Win7, WinVista and WinXP CD hangs the system with a black screen and no error.

[http://img687.imageshack.us/img687/3457/photoocq.jpg](http://img687.imageshack.us/img687/3457/photoocq.jpg)

The ubuntu error I get now when choosing ubuntu to boot is related to not being able to mount the drive.  But as you said it looks like it's toast.

The most important thing is I can at least back my files up now, and start over again.  It is impossible to get good help like this for Windows related issues

I cant thank you enough for your detailed help.

You're very welcome - I'm sorry we couldn't resolve your issues.

---

### Post by serialbox on 2010-05-05
> **bcbc said:**
> You're very welcome - I'm sorry we couldn't resolve your issues.

No problem.  At the very least you helped me restore the MBR so I can begin troubleshooting my windows problems. 

thanks again

---

### Post by oscillate on 2010-05-05
Well, I've burned half a dozen livecds and keep getting the same error when trying to start it up, every single command the initializer tries to run fails with "Input/output error" (grep, rm, sed, chroot, anything & everything), finally ending with "Target filesystem doesn't have /sbin/init"... I've tried all different configurations of the boot line all with the same results. If I can't even load the livecd, how am I supposed to fix the boot record?

EDIT: Found an old ubuntu 7 cd, running that livecd successfully...

EDIT2: Ran testdisk and followed instructions on the linked page above, up to BackupBS. Rebooted to primary hard drive, with exact same problem as before: "grub rescue>" prompt. Will try to run 'sudo update-grub' from livecd now.

EDIT3: started new thread: [http://ubuntuforums.org/showthread.php?t=1474156](http://ubuntuforums.org/showthread.php?t=1474156)

---

