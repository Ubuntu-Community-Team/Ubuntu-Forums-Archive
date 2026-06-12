---
title: "Dual Boot on 2 HDs - XP refuses to boot"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by eager2know on 2007-07-24
Hello everyone. 
I know there is about a dozen posts on dual boot, but having read thru all of them I still haven't got the answer.

I have two HDDs: 
Primary SATA 300GB - Ubuntu Drive (partitioned automatically during install)
Secondary IDE 80GB - WinXP Drive (2 partitions namely C: and D: drives in windows)
Both OS were installed separately. Both OS boot normally via BIOS hd priority setting. 
I edited my menu.lst file and added section for booting XP from grub:

[FONT="Courier New"]
              title                Windows XP Professional, SP2
              rootnoverify (hd1,0)
              makeactive
              savedefault
              map               (hd0,0) (hd1,0)
              map               (hd1,0) (hd0,0)
boot[/FONT]

[FONT="Courier New"]fdisk -lu [/FONT]shows SATA drive as [FONT="Courier New"]sda[/FONT] and IDE one as [FONT="Courier New"]sdb[/FONT]

All options on grub list except XP boot just fine. However when I select the XP there are two ways it goes:
1: if map lines are present, I get **Windows could not start because the following file is missing or corrupt: <winnt root>\System32\ Ntoskrnl.exe** error and forced to reboot
2: if map is omitted process halts after [FONT="Arial"]**Starting up ... **[/FONT]is displayed.

I fiddled with different howtos from various posts for a day, and couldn't get around this problem. I can go into BIOS and just change the HD boot order to start either one of the OS, but it seems like a real hassle if you need to do it several times a day or more. 

Please, if anyone had a similar configuration and found a solution you'll just bring joy back into my life.
Thanks in advance for any hint, link, post, reply, etc...:)

---

### Post by Pumalite on 2007-07-24
Windblows likes to be sda. You could switch the drives and use Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
to reinstall Grub.

---

### Post by MrHippocampus on 2007-07-24
This is what I use in a similar setup

```

title Windows XP
rootnoverify (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1

```

I would also check to see if the file its referring to is actually there (sounds stupid i know but its worth a try).

---

### Post by eager2know on 2007-07-24
Thanks for the pointers. Actually I have that [FONT="Courier New"]chainloader +1[/FONT] line in my menu.lst file. I just forgot to include it im my post. I did check and this file is indeed there. I mentioned that each OS boots ok when I select the hd boot order.

I guess I'll have to give it a shot with a SuperGrub link. Meanwhile if you any other ideas I'd be more than happy to read them.

TNX

---

### Post by Pumalite on 2007-07-24
I mentioned that each OS boots ok when I select the hd boot order.

This would mean that Grub is not installed in MBR. ( I think ).

---

### Post by eager2know on 2007-07-24
I guess it's not. Pardon me for silly question: Is there one MBR per disk or one per machine?:confused:

---

### Post by Pumalite on 2007-07-24
One per machine. When you install>Step 7> Advanced Tab>Set to (hd0,0)

---

### Post by eager2know on 2007-07-25
Thank you for your support Pumalite.
I've got the SGD. Now I've tried various options. SGD boots my XP from the second HDD. What I dont understand is what to do next. How can I set up the dual boot so that it works like with SGD? Or SGD is the only way I can have a dual boot? Could you please take me step by step? I am total noob in this so I need a little guidance. 
:)
thx.

---

### Post by Pumalite on 2007-07-25
Off the top of my head ( I haven't tried it ), I would offer this: Let windblows be sda (thay would make it the 'de facto' MBR) and then use Super Grub to install Grub to MBR (hd0.0)

---

### Post by eager2know on 2007-07-26
Well, I've tried using SGD, but I have to admin it takes me less keystrokes and effort to switch operation systems using bios rathen than SGD. One last resort I am thinking of is to reinstall XP somehow so that GRUB MBR is the only one on my system. It's not much effort for me to run unattended install of XP.

Do you have any thoughts as to how I can install windows on that second IDE drive perhaps using grub as its boot loader?

Any ideas? Anyone?

:confused:

---

### Post by avr_freak on 2007-07-26
This work fine in my pc...

> title Windows XP
rootnoverify (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1


Thanks

---

### Post by Custom_Cowboy on 2007-07-26
I have same setup but had XP hard drive as secondary, actually secondary master behind my cdrom, when I installed Feisty, Near end of install it went looking for other o/s and came back with my windows drive added to boot menu. I understand you installed without your windows hard drive, maybe a fresh install with both hard drives present and windows as secondary. I am new to family and this is as far as I can help at the moment. All the best

---

### Post by MQMike on 2007-07-26
I think you have to re-install GRUB to the MBR of the Ubuntu drive.  That is the first drive in BIOS to boot up, right?

I have a How-To on this:
How To GRUB Methods - Toolkit
[http://kubuntuforums.net/forums/index.php?topic=3081671.0](http://kubuntuforums.net/forums/index.php?topic=3081671.0)

First, you get into Ubuntu, get a Terminal, get a GRUB prompt (sudo grub), and at that GRUB prompt, grub>, you re-install GRUB:

grub> root (hd0, 0)     #Ubuntu is in (hd0, 0), right?
grub> setup (hd0)
grub> quit
$ exit

Next, get into Ubuntu and edit the boot menu (/boot/grub/menu.lst) with root privileges and File-Save, File-Exit when you are done editing.  Edit menu.lst to include a valid entry for Windows.  Do as the guys have suggested:

title Windows XP
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1, 0)
makeactive
chainloader +1

This usually does the trick for folks.

Re-boot to test it.
(All details are in the How-To.  The posts following the first post have other techniques, such as changing the default OS, etc.)

Remember, GRUB numbers hard drives and partition starting from zero.    So the first hard drive is (hd0), the first partition is partition 1.  Etc.

---

### Post by Custom_Cowboy on 2007-07-26
If each drive will boot when its first in line then o/s should be ok. I have two hard drives with XP on secondary master behind my cdrom. Both were present at install of feisty on all of hda and it found XP on hdc near end of install. My boot menu is a little different in that  it has                              #  title Microsoft Windows XP Home Edition
root		(hd1,0)  not rootnoverify  (hd1,o)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
This puts XP as second hard drive (hd1) in boot order but third in order reported from fdisk ie hdc

---

### Post by eager2know on 2007-07-26
Hey MQMike, thanks for pitching in. 
I've pretty much tried all editing suggestions on my menu.lst. Wouldn't work. 

So, maybe you're right about reinstalling GRUB. Do you think if I reinstall, it will see my XP disk, just as if I were to reinstall Ubuntu alltogether? I really wouldn't want to reinstall Ubuntu though, because I've already copied and configured so much stuff on it, that I don't want to waste. Both systems work just fine, when selected as primary drive from bios. 

I'll give it a shot when I get home tonight.

---

### Post by eager2know on 2007-07-26
Another small question I have is what should my device.map look like? Because right now it only has one line that lists my hd0.

---

### Post by MQMike on 2007-07-26
“So, maybe you're right about reinstalling GRUB. Do you think if I reinstall, it will see my XP disk, just as if I were to reinstall Ubuntu alltogether? “

Yes.
And re-installing does not hurt anything (unless you install it to the Windows MBR, then it overwrites the Windows bootloader NTLDR, but even then you can restore that using the Windows CD, etc.)

As for device.map, Oh Gosh, let’s try not to have to mess with that, it’s another story.  (The GRUB you see, the one we are dealing with right here, does not refer to that device.map on boot-up;  but the grub in the grub shell does use the device.map – see the GRUB manual for all this technical stuff!)
GRUB, GNU GRUB Manual 0.97 at:  [http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)

---

### Post by MQMike on 2007-07-26
BTW,
In almost ALL cases, there’s no need to re-install Ubuntu to fix GRUB bootloader problems.  (Assuming the install was good; ie, checksum was ok and Check CD for Defects passed ok, no corruption, etc.).  All we need to get at are those /boot and /boot/grub files contained in the root files of Ubuntu (and GRUB does that automatically for us when we use the GRUB commands).  In fact, people worry about where to have the installer put GRUB when they are installing Ubunbtu.  Fact is, it doesn’t really matter – you can always manually fix this afterwards by re-installing GRUB (from a Live CD if  necessary) wherever you want it by using a few basic GRUB commands.  You can even copy those GRUB files wherever you want them, and make a separate GRUB-boot partition and then install GRUB from that to the MBR of the first (BIOS-) drive (see the How-To, scroll down to the post that covers that subject).

---

### Post by eager2know on 2007-07-26
OK, it seems I've exhausted all possible approaches. no joy with the latest grub update scenario. I will have to use bios to set drive order i guess. Another true fact of this sad life. :(
In case someone wants to take a look at my drive info it's below:

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   612976139   306488038+  83  Linux
/dev/sda2       612976140   625137344     6080602+   5  Extended
/dev/sda5       612976203   625137344     6080571   82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    40965749    20482843+   7  HPFS/NTFS
/dev/sdb2        40965750   156280319    57657285    f  W95 Ext'd (LBA)
/dev/sdb5        40965813   156280319    57657253+   7  HPFS/NTFS

---

### Post by MQMike on 2007-07-26
That's puzzling.  Looks like Ubuntu is on (hd0, 0) and XP on (hd1, 0), as suspected.
Don't know why the re-install and editing the menu.lst didn't work . . .?
Did you get anything?  Any messages, etc, when you re-booted?  Any clues?

---

### Post by eager2know on 2007-07-31
I keep reading stuff about linux in general and many sources when talking about hdd setup refer to them as hda hdb, and when SCSI devices are described they're shown as sda sdb. Now I don't have any SCSI disks on my machine: only SATA and IDE. Why then do they show up as sda and sdb???

Anyone? Any thoughts on that?:)

---

### Post by MQMike on 2007-07-31
In the past, in Ubuntu, hard drives were hdx for IDE/PATA HDs and sdx for SATA HDs.
Now, with 7.04 I believe, both IDE/PATA drives and SATA drives are labeled sdx.  SCSI’s, I’m pretty sure, have always been labeled the same as SATAs, with the sdx notation.

reasoning behind this::
[https://wiki.ubuntu.com/LibAtaForAtaDisks](https://wiki.ubuntu.com/LibAtaForAtaDisks)

---

