---
title: "unable to install Ubuntu 20.04 (focal fossa) to SSD"
date: 2023-02-11
forum: Installation &amp; Upgrades
---

### Post by businesstek on 2023-02-11
Simple facts:
* after install to SSD, reboot takes me to GRUB rescue
* grub rescue always shows the boot directory is empty. 
* however, when using the liveCD, I can see the boot directory is not actually empty. All the files GRUB needs seem to be there.

What's happening?

additional info that may be helpful:
* my system is BIOS only boot, no UEFI possible.
* no matter what choices I make (e.g. use MBR or use GPT partitions), installing to a thumb drive ALWAYS WORKS. I even installed to the thumb using a single GPT partition and it still worked.
* however, no mater what choices I make installing to SSD, it never works. Already tried adding a dedicated BIOS boot partition with the bios_grub flag set.
* boot-repair has not worked.
* I was able to clone the thumb drive (single GPT partition) to the SSD and then resized the partition. It worked (booted), but caused other problems (snap store would not run).
* I know the SSD hardware is fine because I had Ubuntu installed on it while using on a system that did support UEFI. There were no problems. Also, no problems reported by fsck.
* it's odd that grub rescue seems to be missing many commands. It does not even understand 'exit'

---

### Post by oldfred on 2023-02-11
Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version over somewhat older ISO with your USB installer  or any working install.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

it stops at the grub> prompt, that is the full GRUB 2 command shell. That means GRUB 2 started normally and loaded the normal.mod module (and other modules which are located in /boot/grub/[arch]/), but it didn&#8217;t find your grub.cfg file. The grub rescue> mode is more limited, with no history and no tab-completion.

---

### Post by businesstek on 2023-02-12
I am sorry but your instructions seem somewhat ambiguous; need confirmation that I understand.

Are you telling me to run boot-repair and have it upload the report? Then post the link to the report to this thread (instead of posting the report to the forum)?

(just fyi) my LiveCD does not have boot-repair, so any time I want to run boot-repair I need to install via PPA. I use [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) "2nd option : install Boot-Repair in Ubuntu" instructions which I presume means I'm using the latest version.

---

### Post by QIII on 2023-02-12
In oldfred's post, he references some urls.  In the first listed, you will see that you are offered a dialog box that asks if you want to upload to paste bin.  Click yes.  Post the URL to the output in your next post here on the forums.

When people give you links to instructions, it is best to read them.

Please do not post the entire output here.

---

### Post by vendax on 2023-02-12
You could be having cabling errors. Check your SSD "SMART" data for UDMA_CRC_ERROR_COUNT - the raw value should be 0.

Check with:
```
sudo apt install smartmontools
sudo smartctl -s on -A **/dev/sda**
```

replace **/dev/sda** with the name of your SSD, check with command: [B]lsblk
[/B]
You could post the output of that smartctl command here and i will provide feedback.

---

### Post by businesstek on 2023-02-12
ubuntu@ubuntu:~$ sudo smartctl -s on -A /dev/sda
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-42-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")


/dev/sda: Unknown USB bridge [0x0781:0x55b7 (0x4004)]
Please specify device type with the -d option.


Use smartctl -h to get a usage summary

---

### Post by businesstek on 2023-02-12
[COLOR=#000000][[COLOR=#000000]vendax[/COLOR]]("https://ubuntuforums.org/member.php?u=2176355") [/COLOR]
[IMG]https://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-online.png[/IMG]  here is what I got

```
ubuntu@ubuntu:~$ sudo smartctl -s on -A /dev/sda
smartctl 7.1 2019-12-30 r5022 [x86_64-linux-5.4.0-42-generic] (local build)
Copyright (C) 2002-19, Bruce Allen, Christian Franke, www.smartmontools.org


/dev/sda: Unknown USB bridge [0x0781:0x55b7 (0x4004)]
Please specify device type with the -d option.


Use smartctl -h to get a usage summary

```

SSD confirmed identified as sda

---

### Post by businesstek on 2023-02-12
Replying to oldfred. Here is the pastebin link:

[https://paste.ubuntu.com/p/T8JR4Ch7PS/](https://paste.ubuntu.com/p/T8JR4Ch7PS/)

---

### Post by businesstek on 2023-02-12
[[IMG]https://ubuntuforums.org/customavatars/avatar628170_61.gif[/IMG]]("https://ubuntuforums.org/member.php?u=628170")[COLOR=#000000][[COLOR=#990303]QIII[/COLOR]]("https://ubuntuforums.org/member.php?u=628170")
[/COLOR]


Thank  you for the confirmation.

---

### Post by oldfred on 2023-02-12
You show old MBR(msdos) partitioning.
But you have both grub installed to MBR for BIOS boot and in fstab mount of ESP - efi system partition for UEFI boot.
Default boot mode in UEFI/BIOS settings must match how grub is installed.

And how you boot live installer UEFI or BIOS is both how it installs and how it repairs. Choice to boot USB flash drive may not be what you have as default in UEFI/BIOS. But you must have the choice match default setting. Or change setting before rebooting.
Do you want UEFI or BIOS boot? Then always boot in that mode & make that default setting in UEFI/BIOS settings.
Then be sure to boot live installer in that mode & run the fix in Boot-Repair that reinstalls grub.

---

### Post by businesstek on 2023-02-13
oldfred: For the system I'm trying to install on, there is no option to boot in UEFI mode. I'm left wondering how EFI ever came into the picture. I was not given any boot mode choices during install. I don't understand enough about what you describe to be clear on what I should do next. I'll have spend more time studying the link you provided. I appreciate your help, and the learning process is enjoyable. Thank you.

---

### Post by tea for one on 2023-02-13
I was a bit surprised to see an extended partition in the boot-repair report but, nevertheless, how about a different approach?
Back up any data before trying this.

This is an installation with only one partition:-
Boot into a “Try Ubuntu” live session in legacy mode.
Open Gparted and create a msdos partition table.
Open the installer
Installation type = Something else
Select free space and click the + sign
Create _one_ Primary partition with Ext4 file system and Mount point = / (system root)
Install bootloader to device _not_ to a partition (e.g sda _not_ sda1)
(i.e. do not let the installer "Erase Disk and Install")
If you see a message/warning about ESP not found, ignore it and continue the installation.
The installer will show that only one partition is to be created and formatted.

If your PC is not UEFI capable, can you tell us the make, model, age etc?

Perhaps Lubuntu or Xubuntu may be worth a shot?
(Lubuntu uses a different installer)

---

### Post by tea for one on 2023-02-13
> **businesstek said:**
>  For the system I'm trying to install on, there is no option to boot in UEFI mode. I'm left wondering how EFI ever came into the picture. I was not given any boot mode choices during install.
When you install in BIOS mode and select the "Erase and Install" option, you get an both an ESP and bios_grub.
This is a feature of the current Ubuntu installer.

In UEFI mode, the installer will not create a bios_grub partition.

---

### Post by MAFoElffen on 2023-02-13
> **tea for one said:**
> When you install in BIOS mode and select the "Erase and Install" option, you get an both an ESP and bios_grub.
This is a feature of the current Ubuntu installer.

In UEFI mode, the installer will not create a bios_grub partition.
It will create bios-grub partition... If the disk is partitioned as GPT and booted as CSM (Legacy). Note that oldfred noted that the disk was partitioned as MBR (msdos)... "Erase & Install" will go as per the partition type that is there already.

Just a note and observation.

---

### Post by vendax on 2023-02-13
@businesstek

Could you describe how you connect your SSD? Is it via a USB to SATA controller, or via a USB cable?

What kind of SSD is it, brand and model? Can you do the following: reboot fresh and do execute in a terminal:

```
sudo dmesg | grep sda
```

---

### Post by businesstek on 2023-02-13
@tea for one

confirmed "try ubuntu" legacy mode...
```

ubuntu@ubuntu:~$ if test -d /sys/firmware/efi;then echo efi;else echo bios;fi
bios

```
used gparted to delete all partitions
used gparted to create a new partition table, type: msdos
opened installer and selected 'something else'
done: "one Primary partition with Ext4 file system and Mount point = / (system root)"
done: Install bootloader to device not to a partition (e.g sda not sda1)
(confirmed) "The installer will show that only one partition is to be created and formatted."
make/model: HP Pavilion p6520y purchased in 2010


after reboot I'm dropped off at grub rescue. "/boot/grub/i386-pc/normal.mod not found"
* grub rescue> ls (hd0,1)/boot/ shows an empty directory.
* Rebooted using the live cd.
* Mounted the SSD to take a look at the boot directory. The directory is full of files. Confirmed 'boot/grub/i386-pc/normal.mod' exists.
* Unmounted the SSD 
* installed boot-repair and generated a report. 
Here the is boot-repair summary: [https://paste.ubuntu.com/p/nMXvmJnxqx/](https://paste.ubuntu.com/p/nMXvmJnxqx/)

---

### Post by oldfred on 2023-02-13
Report looks normal and should work.

There used to be issues where boot files were far into drive. But your system should be newer than that old issue.
But you could try a smaller / of 40 or 50GB at beginning of drive and make rest of drive as /home.
Not sure what else to suggest. Others may have something.

---

### Post by tea for one on 2023-02-13
Did you try the default boot repair?

Does your 2010 motherboard support a large ssd (Disk sda: 931.49 GiB)?

I would also echo oldfred's comment and try the one partition installation again but limit the size to 50GB?

You never know..............;)

---

### Post by businesstek on 2023-02-13
@vendax here is the info you requested:

* I connect using a usb (ver 2.0 HP Pavilion p6530y limitation) 

SSD is a 1TB Sandisk G drive: [https://www.westerndigital.com/products/portable-drives/sandisk-professional-g-drive-usb-3-2-ssd#SDPS11A-001T-GBANB](https://www.westerndigital.com/products/portable-drives/sandisk-professional-g-drive-usb-3-2-ssd#SDPS11A-001T-GBANB)
```

ubuntu@ubuntu:~$ sudo dmesg | grep sda
[    2.857188] sd 7:0:0:0: [sda] 1953459617 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.857660] sd 7:0:0:0: [sda] Write Protect is off
[    2.857662] sd 7:0:0:0: [sda] Mode Sense: 37 00 10 00
[    2.858181] sd 7:0:0:0: [sda] Write cache: enabled, read cache: enabled, supports DPO and FUA
[    2.858564] sd 7:0:0:0: [sda] Optimal transfer size 1048576 bytes
[    2.889983]  sda: sda1
[    2.895729] sd 7:0:0:0: [sda] Attached SCSI disk
[    4.043745] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[  387.809725] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)

```

---

### Post by MAFoElffen on 2023-02-13
What happens if you use Gparted to erase the partitions and add a GPT partition, instead of an MBR (msdos) partition table? Then close down / reboot and choose "Erase all and install"?

That way it has a GPT Partition table which works better on large drives (for a number of reasons).

At this point, you lose nothing in trying that...

---

### Post by businesstek on 2023-02-13
@oldfred

> **oldfred said:**
> Report looks normal and should work.

There used to be issues where boot files were far into drive. But your system should be newer than that old issue.
But you could try a smaller / of 40 or 50GB at beginning of drive and make rest of drive as /home.
Not sure what else to suggest. Others may have something.

I thought this to be an  improbable solution as well since the HDD that comes standard with the computer is 1TB. Guess what? I created 32GB partition, left the rest as free space, and Ubuntu installed just fine (with no boot issues). If possible, I'd like to  have everything in one partition. Would you please elaborate on "that old issue?" I would like to research it further as it seems to have something to do with the way the system is handling USB.

---

### Post by businesstek on 2023-02-13
> **tea for one said:**
> Did you try the default boot repair?

Does your 2010 motherboard support a large ssd (Disk sda: 931.49 GiB)?



At this point, I believe that's got to be the problem. Thank you!

---

### Post by businesstek on 2023-02-13
> **MAFoElffen said:**
> What happens if you use Gparted to erase the partitions and add a GPT partition, instead of an MBR (msdos) partition table? Then close down / reboot and choose "Erase all and install"?

Just FYI. I did try that originally, but the results where the same. I ended going with MBR because it's supposed to be more stable / less likely fail on older systems.

---

### Post by oldfred on 2023-02-13
If system originally came with a 1TB drive, it should not be the old issue.
The old issue goes back years and has multiple versions. 
It related to BIOS limits and drive sizes. And often then appeared when users put a larger drive into system than BIOS was designed for.

I found this which goes back further than I remember. And your system should not be part of this type of issue.
[https://tldp.org/HOWTO/Large-Disk-HOWTO-4.html](https://tldp.org/HOWTO/Large-Disk-HOWTO-4.html)

Perhaps a BIOS bug? Do you have latest available firmware for BIOS? It may still be available on line, if vendor has updates.

---

### Post by businesstek on 2023-02-14
As the problem I'm having apparently has nothing to do with Ubuntu per se, I am marking this thread as solved.

Thank you everyone for helping me isolate the problem and for expanding my knowledge of available tools!

---

