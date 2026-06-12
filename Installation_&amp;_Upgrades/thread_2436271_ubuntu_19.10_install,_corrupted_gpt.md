---
title: "ubuntu 19.10 install, corrupted gpt?"
date: 2020-02-03
forum: Installation &amp; Upgrades
---

### Post by sunblox on 2020-02-03
I decided to switch my hp Elitebook 840 G5 to Ubuntu 19.10 from Windows 10 (i bought the Laptop with no OS preinstalled, if that matters)

Now after installing Ubuntu (full install, formatting the SSD with no dual boot) upon rebooting i get this messeage in UEFI: "GPT Recovery: HDD GPT was found corrupted and has been recovered automatically. No further action required."

And trying to boot Ubuntu just goes to GNU GRUB version 2.04. with no way to get into Ubuntu.
After looking around for a while i tried using gdisk and got this messeage: 

Partition table scan:
  MBR: MBR only
  BSD: not present
  APM: not present
  GPT: not present


***************************************************************
Found invalid GPT and valid MBR; converting MBR to GPT format
in memory. THIS OPERATION IS POTENTIALLY DESTRUCTIVE! Exit by
typing 'q' if you don't want to convert your MBR partitions
to GPT format!
***************************************************************
commands -v and -w tell me that the secondary and last partition overlap by 33 blocks and that this has to be fixed in a different application.

Now, I have to be honest: I have absolutely no Idea what any of this means, how to fix it and if it even matters: In fact, a big reason why i chose Ubuntu in the first place is because the installation was supposed to be easy...

Any way that I can get my Computer running again?

---

### Post by CelticWarrior on 2020-02-03
Just boot a live session, then open Gparted, select the intended target drive and, in the Device menu choose New Partition table and select GPT. This will delete all previous partitions and data within which shouldn't be a problem at this point.

Now make sure you're booting the USB installation media in UEFI mode (not required for the previous cleanup step but absolutely necessary to properly install in the recommended UEFI mode. You can also disable Legacy/CSM in UEFI settings in order to assure you're booting in the correct mode.

Install as usual and it should work fine this time.

PS - The Ubuntu installation is very easy but like what happens with the installation of ANY OS, a certain know-how is required.

---

### Post by oldfred on 2020-02-03
Was Windows in BIOS boot mode? As that uses MBR partitioning. But Windows converts a gpt drive to MBR incorrectly. It leaves the backup gpt partition table. MBR has no backup, or one of the advantages of using gpt.
Windows requires gpt for UEFI installs, but Ubuntu will install in UEFI boot mode to MBR drives (perhaps it should not).

If system is newer UEFI hardware, better to install in UEFI boot mode to gpt partitioned drive.
Some HP are not particularly friendly to booting anything other than Windows in UEFI boot mode. Some some do use BIOS. You can if only Ubuntu use gpt with BIOS install, but have to have a tiny 1 or 2MB unformatted partition with bios_grub flag. 

I would also update UEFI from HP. Some have posted that then it reduces some of the issues with Ubuntu.

---

### Post by sunblox on 2020-02-03
Thanks for the reply and sorry for my snark, Im getting kind of frustrated at this point.

I did everything you said, yet nothing changed: Still the same error message in UEFI upon reboot after installing, looking at GParted it seems all my partitions went back to the state they were in before as well. It seems the automatic gpt recovery just sets everything back as soon as i reboot

---

### Post by CelticWarrior on 2020-02-03
What exactly did you try in Gparted?

---

### Post by oldfred on 2020-02-03
Post these, similar but each has a bit of different info:
sudo parted -l
sudo fdisk -lu
sudo gdisk -l /dev/sda  # if your device is sda

---

### Post by sunblox on 2020-02-03
Issue solved, thanks everyone!

Here's what happened:

HP put a fail-safe gpt recovery into the UEFI Settings, all I had to do was go into the UEFI Menu in Security -> Hard Drive Utilities -> Uncheck "Save/restore GPT System of Hard Drive"

Then I went into the live-boot, did the formatted the drive with GParted as a gpt, installed again, and now it works.

So in short I thought it was an issue with the installation process when in reality HP just (perhaps correctly) thought that I didn't know what i was doing

---

### Post by CelticWarrior on 2020-02-03
> **sunblox said:**
> HP put a fail-safe gpt recovery into the UEFI Settings, all I had to do was go into the UEFI Menu in Security -> Hard Drive Utilities -> Uncheck "Save/restore GPT System of Hard Drive"

Nice to know, thanks for the feed back.
I've learned a new thing today :D

---

