---
title: "Install Questions - RAID0 Dual Boot"
date: 2014-11-21
forum: Installation &amp; Upgrades
---

### Post by skygunner58201 on 2014-11-21
Alright.  I'm not completely new to Ubuntu.  However, I have no idea where to start on this.  My computer, a custom AMD build, is running Windows 7 64bit on a RAID0 config.  I want to install Ubuntu but have no idea how to keep my RAID.  Is this possible, or should I just install my spare SSD and install it separately over there?

---

### Post by skygunner58201 on 2014-11-21
Anybody with an idea?  At all?

---

### Post by oldfred on 2014-11-21
Forum etiquette is to only bump once per 24 hrs.

I do not recommend RAID 0, so I would install to your other SSD if that is an option. 
You then have to use Something Else and usually better to partition in advance with gparted.

Desktop installer does not have full RAID support. With 12.04 there was the alternative installer that you could use to install RAID and LVM. They discontinued the alternative installer and said later they would add that to the desktop installer. I do see LVM as an option on the current installer, but not RAID yet. I have seen some posts where the installer now does seem to see RAID in some cases, but grub usually does not correctly install and had to be fixed after install. Or use server install and add desktop.

       Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)
parted (3.0) completely removes filesystem creation and modification support, except for filesystem probing to determine what's in a partition.
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
User who installed fakeRAID
How to install Ubuntu 14.04 in software RAID 1 with Intel Z87 chipset mobo controller
[http://ubuntuforums.org/showthread.php?t=2229126](http://ubuntuforums.org/showthread.php?t=2229126)

Is system UEFI or BIOS?
With Ubuntu on its own drive you can use gpt partitioning whether UEFI or BIOS, but Windows only boots from gpt with UEFI. Both Windows & Ubuntu only boot from MBR(msdos) partitioned drives with BIOS.

---

### Post by skygunner58201 on 2014-11-21
Well, I installed to the ssd.  I just installed using the install alongside option.  Grub then have an error saying couldn't install to default location.  I installed it to the ssd as well and grub sees both windows on the raid0 and Ubuntu on the ssd.  Works beautifully and it reads my raid drive in Ubuntu just fine.

---

