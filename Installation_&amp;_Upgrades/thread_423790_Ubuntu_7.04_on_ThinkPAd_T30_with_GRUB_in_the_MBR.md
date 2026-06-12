---
title: "Ubuntu 7.04 on ThinkPAd T30 with GRUB in the MBR"
date: 2007-04-26
forum: Installation &amp; Upgrades
---

### Post by mantu on 2007-04-26
Hi, I have a ThinkPad T30 with Windows XP Pro and I'd like to install Ubuntu 7.04 in dual-boot using the Desktop CD. As you probably know, ThinkPads (and many other notebooks) have a hidden partition where they store system recovery data. The Ubuntu Desktop CD automatically install GRUB in the MBR so I'm afraid that I will not longer be able to boot the system recovery software after installing Ubuntu. Am I right? Or will the GRUB menu have an option to boot the IBM system recovery software (in addition to Windows and Ubuntu)?
Thanks
Mantu

Note: I know that the Alternate CD let you install GRUB where you want to, but I'd like to use the Desktop CD since I can't download the Alternate CD at the moment.

---

### Post by kagashe on 2007-04-26
> **mantu said:**
> Hi, I have a ThinkPad T30 with Windows XP Pro and I'd like to install Ubuntu 7.04 in dual-boot using the Desktop CD. As you probably know, ThinkPads (and many other notebooks) have a hidden partition where they store system recovery data. The Ubuntu Desktop CD automatically install GRUB in the MBR so I'm afraid that I will not longer be able to boot the system recovery software after installing Ubuntu. Am I right? Or will the GRUB menu have an option to boot the IBM system recovery software (in addition to Windows and Ubuntu)?
Thanks
Mantu

Note: I know that the Alternate CD let you install GRUB where you want to, but I'd like to use the Desktop CD since I can't download the Alternate CD at the moment.
Desktop CD also gives you option to install Grub elsewhere but it is tricky to do it. I don't remember exactly but at some stage there is an "Advance" tab on the screen, perhaps, when it asks you to confirm the user, time zone etc. but just before formatting stage. If you click on that "Advance" tab you get the alternate option to install Grub.

I can also help you to confirm whether you can have the Windows recovery option if you post the contents of "boot.ini" file located at the root of c:/drive.

kagashe

---

### Post by mantu on 2007-04-26
> I can also help you to confirm whether you can have the Windows recovery option if you post the contents of "boot.ini" file located at the root of c:/drive.

```
[boot loader]
timeout=30
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS
[operating systems]
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn
```

Indeed I'm speaking about the IBM Factory Restore tool (hidden partition). Not sure it is listed in boot.ini. When I start my ThinkPad, an IBM welcome screen let me access the bios or the Factory Restore procedure (in case I need to reinstall Windows and drivers). If I don't press the right keys, the boot procedure continues with the Windows welcome screen.

---

### Post by kagashe on 2007-04-26
> Indeed I'm speaking about the IBM Factory Restore tool (hidden partition). Not sure it is listed in boot.ini. When I start my ThinkPad, an IBM welcome screen let me access the bios or the Factory Restore procedure (in case I need to reinstall Windows and drivers). If I don't press the right keys, the boot procedure continues with the Windows welcome screen.

You are right. It is not listed in boot.ini. If booi.ini has multi boot option (like Windows XP and Windows 98 ) these options are available after you select "Windows" in Grub.

You will still get the IBM welcome screen before the Grub menu appears and I think that the Factory Restore procedure should work because it can always access c:/ drive as before. However, the Factory restore might rewrite the MBR and erase the Grub.

kagashe

---

### Post by mantu on 2007-04-26
> You will still get the IBM welcome screen before the Grub menu appears
In practice the welcome screen is not loaded from the hard drive, it's embedded in the ThinkPad hardware. Right?

> I think that the Factory Restore procedure should work because it can always access c:/ drive as before. However, the Factory restore might rewrite the MBR and erase the Grub.
So, correct me if I'm wrong, the Factory Restore tool will erase the entire hard drive (Linux partitions icluded) and will reinstall Windows.

---

### Post by kagashe on 2007-04-26
> In practice the welcome screen is not loaded from the hard drive, it's embedded in the ThinkPad hardware. Right?
Yes. It seems so, otherwise there would have been an entry in the boot.ini file.

> So, correct me if I'm wrong, the Factory Restore tool will erase the entire hard drive (Linux partitions icluded) and will reinstall Windows.It may not erase the entire drive but it will certainly restore the MBR replacing Grub.

Let us find out the location of the "restore partition" on the hard drive.
Boot into Live CD desktop. Open GParted and post what partitions you see on the screen. Windows can't hide any partition from GParted.

kagashe

---

### Post by mantu on 2007-04-26
> Let us find out the location of the "restore partition" on the hard drive.
Boot into Live CD desktop. Open GParted and post what partitions you see on the screen. Windows can't hide any partition from GParted.

/dev/hda (37,26 GiB)

--> /dev/hda1    ntfs     35.58  (boot)
--> /dev/hda2    fat32  1,68     (hidden, lba) 


That's my only hard drive.

---

### Post by kagashe on 2007-04-26
> --> /dev/hda1 ntfs 35.58 (boot)
--> /dev/hda2 fat32 1,68 (hidden, lba) 
It seems you are going to face problems in "Factory Restore" afterwards.

For installing Linux you are going to resize hda1 and create two more partitions (one for root and another for swap). This will change the partition # of hda2 where the backup files for Windows restore reside. The "Factory Restore" procedure will fail to access the back up files thereafter.
 You may seek help from the OEM telling that you are going to create more partitions on the hard drive.

I also have a solution which may or may not work.

Decide how much you are going to keep for Windows on c:/ (hda1) and resize. The balance will go to unallocated.
Create a FAT 32 partition of approx 1.68 GB (exactly matching the size of the present hda2) using the space immediately after hda1. Linux will allot it the # hda2.
Copy the contents of present hda2 to the new hda2.

Resize the balance space to create the required partitions (/ and swap) and create the partitions.

Proceed with the install.

Since the partition # for Windows back up stays the same it may work.

kagashe

---

### Post by mantu on 2007-04-26
thanks for your tips ;)

---

### Post by kagashe on 2007-04-26
> **mantu said:**
> thanks for your tips ;)
You are welcome.

See this page regarding how Linux was installed on similar machine:
[http://empl.home.cern.ch/empl/thinkpad.html]("http://empl.home.cern.ch/empl/thinkpad.html")

The following paras are relevant to you:
> partition - this system ships with a recovery partition (about 1.7Gbyte) rather than recovery CDs in addition to the large main partition occupied by W$/XP. Before booting into W$/XP the first time, this main partition is formatted as FAT32 Window95 like. There is no extra partition for hibernation, instead you will find a large file under W$/XP for this purpose. Lets presume you like to keep a smaller W$/XP partition next to your Linux setup, say about 10Gbyte, preserve the recovery option and implement suspend-to-disc  under Linux in the more traditional way.

>  NOTE  write down your partition table on a sheet of paper! W$/XP might overwrite your table on boot. Don't panic. You might save all your file systems if you simply re-create the identical table under linux anew. If W$/XP recognizes your modified partition table (ie the boot sector still looks dos'ish) the IBM recovery procedure will re-install W$/XP for you in the smaller partition - again, this takes a while, in the order of an hour. You can trigger this by pressing Fn F11 which needs to be enabled in the BIOS, as long as you have not installed a Linux boot manager.

I think what they are suggesting here is nearly the same as I told you. After creating the partitions if you boot into Windows it will recognize the modified partition table and the recovery procedure will re-install the recovery partition on new hda2.

kagashe

---

### Post by mantu on 2007-04-26
> For installing Linux you are going to resize hda1 and create two more partitions (one for root and another for swap). This will change the partition # of hda2 where the backup files for Windows restore reside. The "Factory Restore" procedure will fail to access the back up files thereafter.

Is it really necessary to change the partition # of hda2?
I'm planning the following partition table and, as you can see, the hidden partititon remains into hda2:

/dev/hda (37,26 GiB)

--> /dev/hda1 ntfs (windows resized)
--> /dev/hda2 fat32 1,68 GiB (hidden, lba)
--> /dev/hda3 ext3 (root)
--> /dev/hda5 swap (swap)
--> /dev/hda6 fat32 (shared area)

(hda1, hda2 and hda3 are primary partitions)
(hda5 and hda6 are logical partitions)

As you can see the hidden partition remain in hda2 (placed at the end of the disk).

The IBM welcome screen should give me access to hda2 to restore the system (GRUB is not yet loaded).
Then GRUB (installed in MBR) should give me access to Ubuntu and Windows.

---

