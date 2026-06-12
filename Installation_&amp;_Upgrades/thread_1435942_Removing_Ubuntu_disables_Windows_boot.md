---
title: "Removing Ubuntu disables Windows boot"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by arnoldreinders on 2010-03-22
I installed ubuntu 9.10 besides windows xp. It was not a clean install, it is several times upgraded since 8.1. I wanted to install 64 bit ubuntu, but the boot disk was not recognized by the installer. I removed Ubuntu 9.10 with GPartEd to create unallocated space on which to install 64-bit ubuntu. In doing so I removed the Grub info and cannot boot windows any more. 

Is there any way to boot clean Windows again?

Regards, Arnold

---

### Post by byStanderone on 2010-03-22
...just go on with your pending karmic install on the unallocated partition, and karmic will take care of the grub installation. you will be able to boot the other 'os' of course providing that all the needed system files are ok.

---

### Post by coffeecat on 2010-03-22
As a point of information, when you remove the Ubuntu root partition, you remove grub stage 2 with it, which leaves grub stage 1 orphaned on the mbr. As byStanderone says, by reinstalling Ubuntu, grub stage 1 will be reinstalled to the mbr pointing to wherever the new grub stage 2 is.

However, if you ever need to reinstate the Windows MBR in order to be able to boot straight into Windows XP, you need to run FIXMBR from the repair console of the XP installation disc. This needs to be a Microsoft disc, not a manufacturer's restore disc which (usually) doesn't have the repair console. For those without a Microsoft disc, the easiest way I know to repair the Windows MBR is to use [SuperGrubDisk]("http://www.supergrubdisk.org/"). Even if you have no intention of abandoning Ubuntu/Linux, SuperGrubDisk is a useful thing to have around for dealing with various booting problems.

---

### Post by arnoldreinders on 2010-03-22
Thanks very much guys for your suggestions. I have some troubles to follow your advice.
> **bystanderone]..just go on with your pending karmic install on the unallocated  partition, and karmic will take care of the grub installation. you will  be able to boot the other 'os' of course providing that all the needed  system files are ok[/QUOTE]


[QUOTE=coffeecat said:**
> As a point of information, when you remove the Ubuntu root partition, you remove grub stage 2 with it, which leaves grub stage 1 orphaned on the mbr. As byStanderone says, by reinstalling Ubuntu, grub stage 1 will be reinstalled to the mbr pointing to wherever the new grub stage 2 is.


Thanks for the explanation. This makes me understand the boot process better. The problem is that the Karmic installers do not recognize the hard disk. When booting from the CDRom GPartEd recognizes the disk, when running the installer it does not recognize the disk.  My  foolish idea was that the installer would recognize the disk when removing karmic  32-bit, but I removed a little bit more and the disk is still not recognized. :icon_frown:

> **coffeecat said:**
>  However, if you ever need to reinstate the Windows MBR, you need to run FIXMBR from the repair console of the XP installation disc. For those without a Microsoft disc, the easiest way I know to repair the Windows MBR is to use [SuperGrubDisk]("http://www.supergrubdisk.org/"). Even if you have no intention of abandoning Ubuntu/Linux, SuperGrubDisk is a useful thing to have around for dealing with various booting problems.

I gave it a try, booted from CDROM but I have trouble understanding the Wiki and the output of the program differs with the examples in the Wiki (I got only the command prompt), so I am not sure what to do. I have tried versions 0.95.., 0.9799 and SG2 1.30. Alas I have no Fixmbr. Any suggestions?

Regards, Arnold

---

### Post by wojox on 2010-03-22
Boot computer using Windows XP (Windows 2000) setup disc / CD / DVD. Next, type the following commands:
# fixmbr
# exit

---

### Post by coffeecat on 2010-03-22
> **arnoldreinders said:**
> When booting from the CDRom GPartEd recognizes the disk, when running the installer it does not recognize the disk.  My  foolish idea was that the installer would recognize the disk when removing karmic  32-bit, but I removed a little bit more and the disk is still not recognized.

I don't understand that. The installer partitioner uses the same backend as Gparted (iirc). Can you give us some more details? Even better, boot up from the live CD and post a screenshot of the Gparted window and explain what you are trying to install where. If you're having trouble with the installer, it may be better to prepare your partitions in Gparted first and then choose the 'manual' option at the partitioning stage of the installer.

> **arnoldreinders said:**
>  I gave it a try, booted from CDROM but I have trouble understanding the Wiki and the output of the program differs with the examples in the Wiki (I got only the command prompt), so I am not sure what to do. I have tried versions 0.95.., 0.9799 and SG2 1.30. Alas I have no Fixmbr. Any suggestions?

I see what you mean about the wiki. It's quite appalling and just about useless. Use either the 0.95 version or the 0.9799. I'm using 0.9783. When I boot from it I get a brief orange menu which gives the single choice "Super Grub Disk" for a second only, and then goes straight on to the main SGD menu with about nine choices. You should not be getting a command prompt unless you press the 'c' key. Boot with the CD, don't press any key until you get to the 9-10 choice menu which starts with 'Choose Language and HELP". Further down the list are two entries:

```
!WIN!                                                                  :(((
WIN => MBR & !WIN!         :(((((((((((((((((((((((((((((((((((((((((((((((
```

A bit childish, but it works. The first of these boots you into Windows. The second repairs the Windows MBR and then boots into Windows. If you do the second and reboot from Windows without the SGD CD, Windows will boot up just fine. I've done experimental repairs of XP, Vista and Windows 7 with this successfully.

---

### Post by coffeecat on 2010-03-22
> **wojox said:**
> Boot computer using Windows XP (Windows 2000) setup disc / CD / DVD. Next, type the following commands:
# fixmbr
# exit

But the OP says:

> **arnoldreinders said:**
> Alas I have no Fixmbr. Any suggestions?

I would take that to mean no Windows disc.

---

### Post by arnoldreinders on 2010-03-22
Thanks for all your suggestions! I see that in discussing the problems, too many problems pop up, so let me try to be more clear.

1. Fixmbr. I *do* have an XP setup disk, there is no file fixmbr on it. I don't see a way to get to the command prompt. The only way for a command prompt appears to be the Recovery panel that i cannot access. The administrator password is not the same as the password of the administrator so I can't login. 

2. i use SGD 0.97-os.1 which i burnt from super_grub_disk_0.9799.iso. There is no such thing as orange flashing or menu. I get the prompt immediately witout me even *looking* at the keyboard. That's different from the wiki. I tried typing !WIN! but the command is not recognized. For the other commands I really need help which is not yet available.

3. The mystery of the disappearing disk started it all, but for the moment I will leave it until I can boot windows again. I will start it in a separate thread because it's so weird. And thanks for the suggestion to provide screendumps of GParted and the installer. I will certainly do that.

Thanks again for all your help .

Arnold

---

### Post by Calash on 2010-03-22
[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

Check Option 2 on the list.  Depending on the version of XP (SP1 or SP2) the menu may be worded differently but pressing R should get you to a command prompt that will list your installs (assuming they are not damaged beyond repair).  You will need to know the local admin password and then you will be in.


Once you are in, type fixmbr and say yes to it.  They type Exit to reboot.

---

### Post by arnoldreinders on 2010-03-22
> **Calash said:**
> [http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)
Check Option 2 on the list.  Depending on the version of XP (SP1 or SP2) the menu may be worded differently but pressing R should get you to a command prompt that will list your installs (assuming they are not damaged beyond repair).  You will need to know the local admin password and then you will be in.

Thanks Calash, i have tried the R option but i don't know the administrator password :oops: I thought it was the same as mine as I am the only user and administrator.

---

### Post by handyman510a on 2010-03-22
[QUOTE=arnoldreinders;9007843]I installed ubuntu 9.10 besides windows xp. It was not a clean install, it is several times upgraded since 8.1. I wanted to install 64 bit ubuntu, but the boot disk was not recognized by the installer. I removed Ubuntu 9.10 with GPartEd to create unallocated space on which to install 64-bit ubuntu. In doing so I removed the Grub info and cannot boot windows any more. 

Is there any way to boot clean Windows again?

Regards, Arnold
Use the xp disc from boot up select repair boot section and that should do the trick

---

### Post by byStanderone on 2010-03-23
...thanks for the follow-thru, coffeecat

---

### Post by coffeecat on 2010-03-23
> **arnoldreinders said:**
> 2. i use SGD 0.97-os.1 which i burnt from super_grub_disk_0.9799.iso. There is no such thing as orange flashing or menu. I get the prompt immediately witout me even *looking* at the keyboard. That's different from the wiki. I tried typing !WIN! but the command is not recognized. For the other commands I really need help which is not yet available.

I've just downloaded the super_grub_disk_0.9799.iso, burnt it to disk and booted with it. I get precisely the same as with the earlier version I was using: brief orange menu which goes directly to the main menu with the !WIN! choices. I said nothing about flashing orange, by the way. Which makes me think you have either a bad burn or a corrupted download. Try re-downloading and reburning.

There's no point typing '!WIN!' at a grub prompt. That's a menu entry, not a grub command.

---

