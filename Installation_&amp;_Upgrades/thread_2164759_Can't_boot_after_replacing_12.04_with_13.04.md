---
title: "Can't boot after replacing 12.04 with 13.04"
date: 2013-08-01
forum: Installation &amp; Upgrades
---

### Post by 1aunchpad-nct on 2013-08-01
I installed 13.04 on a system that was previously running, and had only ever run, XBMCbuntu (Ubuntu 12.04 base). I chose the erase 12.04 and install 13.04 option in the installer. The installation completed without any reported problems but the new system will not boot. I get the error

"Reboot and select proper boot device or Insert Boot Media in selected Boot device and press a key"

Clearly the boot areas were not properly set up on the disk. (The BIOS is set to boot from the one and only disk in the system.)

I tried boot-repair. It appeared to complete successfully but afterwards I still get the same error. The boot-repair log is at paste.ubuntu.com/5922722.

boot-repair reported that my computer is in legacy mode and recommended changing to EFI mode. I have a ZBox Nano with American Megatrends  BIOS v 4.6.4.0. It states that it is uEFI 2.1 compliant. However I have been unable to find out how to change the Nano to EFI mode.

I tried to manually install GRUB but got an error telling me the disk does not have a boot-grub partition.

I then tried to reinstall 13.04, picking "Something else" in the installer and I looked at the partition table. The partitions are as follows:

       1MB free space
     98MB FAT32
       0MB free space
62200MB ext4 (but marked as not used)
       0MB free space
  1772MB swap

I tried to change the 1MB of free space to a boot-grub partition but when I click the OK button the partition editor reports, unhelpfully, "Unable to satisfy all the constraints of the partition" and does nothing.

So I tried to create a new partition table but the boot-grub option no longer appears in the "Use as" menu. It only appears when editing the existing partition table. See above.

Then I tried gparted from the LiveCD/USB. It does not show the free space areas and I couldn't find a way to make a boot-grub partition.

I am in desperate need of help to fix my system. I am unimpressed by the 13.04 install managing to so screw up boot on a simple single boot system.

Question 1: How to change my ZBox Nano to EFI mode?

Question 2: If I continue in legacy non-EFI mode, how can I create the necessary boot-grub partition, given the issues described?

Question 3: If I continue in legacy non-EFI mode do I need the 98MB FAT 32 partition for the EFI System Partition?

Question 4: One of the threads I read while trying to fix this said when making a new partition table just to specify / and swap. Is that true? In other words, if I create a new partition table with just those 2 partitions and tell the installer to "continue", will it create the other partition(s) necessary for boot?

---

### Post by 1aunchpad-nct on 2013-08-01
Question 5: Is there a way invoke the same install option I had when the system was brand new. I.e., erase the disk and start over.

---

### Post by oldfred on 2013-08-01
Your install is in UEFI mode. You have an efi partition with grub (and the left over Microsoft) efi files. And your install in sda2. You swap is in sda3.

If you go into UEFI/BIOS and choose the ubuntu entry, can you not boot. Or does it boot to a black screen. Try holding shift key and see if you get menu. Some with UEFI use escape key instead.

What video card/chip are you using. Generally nomodeset works if you have the black screen issue.

---

### Post by 1aunchpad-nct on 2013-08-01
> **oldfred said:**
> Your install is in UEFI mode. You have an efi partition with grub (and the left over Microsoft) efi files. And your install in sda2. You swap is in sda3.
What left over Microsoft EFI files? Windows has never been installed on this computer, only Ubuntu 12.04.

> If you go into UEFI/BIOS and choose the ubuntu entry, can you not boot. Or does it boot to a black screen.
How do I "go into UEFI/BIOS?" If I press the DEL key during power-on I get the UEFI/BIOS settings menu. Is that what you mean? The boot menu priority list in that only shows the hard drive and list it by its model name.

> Try holding shift key and see if you get menu. Some with UEFI use escape key instead.
I'll try when I get home.

> What video card/chip are you using. Generally nomodeset works if you have the black screen issue.
I don't have a black screen issue. I can't boot. I get the "Reboot and select proper boot device ..." message described in the OP. It's an AMD chip.

---

### Post by oldfred on 2013-08-01
Is this not your pastebin? It shows Microsoft boot files in the efi partition?
[http://paste.ubuntu.com/5922722/](http://paste.ubuntu.com/5922722/)

---

### Post by 1aunchpad-nct on 2013-08-04
> **oldfred said:**
> Is this not your pastebin? It shows Microsoft boot files in the efi partition?
[http://paste.ubuntu.com/5922722/](http://paste.ubuntu.com/5922722/)
Yes that is my pastebin. I have no idea why it shows remnants of Microsoft boot files. The box was shipped to me new from the manufacturer and came with out OS. I installed XBMCbuntu 12.04 on it. Then recently I tried to installed Ubuntu 13.04 resulting in the issues documented here.

However, the problem has become moot. I reinstalled 13.04 for a fourth time. After this time it worked. The difference between this and previous attempts was that I attempted to reformat the disk first. I hoped reformatting might destroy the old partitions and force the installer create new ones. Even though the reformat did not complete (it exited with some sort of time-out related to moving objects (???)) it seems to have done the trick. The current pastebin at [http://paste.ubuntu.com/5949281/](http://paste.ubuntu.com/5949281/) shows very different partitions. Thankfully now the system boots 13.04.

I don't think I'm alone in having had problems after installing 13.04 on top of 12.04, judging by other threads I've seen while researching my own issue.

---

### Post by oldfred on 2013-08-04
You now have installed in the CSM/Legacy/BIOS mode that UEFI has to emulate the 30 year old BIOS. If system runs with that mode you are fine. UEFI is a lot more complex, partially as it supports many new features. But the main issue has been Secure Boot that Windows 8 has as a standard.

I tend to prefer to use gpt with UEFI based systems, even if booting in BIOS mode. But then if you ever wanted Windows you could only boot Windows from gpt partitioned drive with UEFI. And both systems need to be either UEFI or both BIOS.

---

