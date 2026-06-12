---
title: "cannot install ubuntu on my UEFI computer despite following instructions"
date: 2014-01-27
forum: Installation &amp; Upgrades
---

### Post by cedrickabongo on 2014-01-27
Hi,

I have bought a new computer that come with windows 8 pre-installed and EUFI instead of the old BIOS. 
I have followed the instructions [here]("https://help.ubuntu.com/community/UEFI") on how to install ubuntu but still I can't install. I wand a dual boot windows 8/ ubuntu

1. when using gparted to resize partitions and create a new partition to be used for ubuntu, the resize button is disabled for all the partitions.
2. I used the "shrink" option on windows disk manager and had a free space for ubuntu but when i run the ubuntu installations from the dvd, it does not pick up the partition table. so i am stuck


can someone help please[URL="https://help.ubuntu.com/community/UEFI"]


[/URL][URL="https://help.ubuntu.com/community/UEFI"]
[/URL]

---

### Post by oldfred on 2014-01-27
What computer is this? Is it an Ultrabook with small SSD, Intel SRT and RAID?

Post this from terminal in live installer.

sudo parted -l

---

### Post by cedrickabongo on 2014-01-28
Hi,

thank you for you reply. below is the output of sudo parted -l

 Error: The backup GPT table is not at the end of the disk, as it should be.
This might mean that another operating system believes the disk is smaller.
Fix, by moving the backup to the end (and removing the old backup)?
Fix/Ignore/Cancel?

---

### Post by fantab on 2014-01-28
That error could mean that you have some sort of RAID enabled.
Check in your UEFI for HDD SATA Mode, usually there are three options: IDE, AHCI and RAID. Tell us what mode it is set to.
Also check for [**IntelSRT**]("http://www.intel.com/p/en_US/support/highlights/sftwr-prod/imsm") (Smart Response Technology), If you find it enabled then disable it. On some computers IntelSRT is controlled by its software, so if you don't find it in UEFI then check under Windows programs for it.

---

### Post by oldfred on 2014-01-28
Backup gpt table should be at end of drive.

I would also see what gdisk says.
 sudo apt-get install gdisk
sudo gdisk -l /dev/sda

And if using gdisk to make fixes:
sudo gdisk /dev/sda
Command (? for help):

 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by cedrickabongo on 2014-01-28
I fixed it. switched to legacy mode and activated RAID as SATA MODE. 
installed everything then run boot-repairer choosing the remomended option.

solved!

thank guys because through your responses I figured out what to do.

---

### Post by fantab on 2014-01-28
Hmmmm, interesting!

---

### Post by oldfred on 2014-01-28
I am surprised that worked. Normally turning RAID on in BIOS creates more issues not less.
And legacy mode is BIOS not UEFI. 
But some systems do need legacy mode on, but still boot with UEFI as Intel i915 driver has some issues.

---

