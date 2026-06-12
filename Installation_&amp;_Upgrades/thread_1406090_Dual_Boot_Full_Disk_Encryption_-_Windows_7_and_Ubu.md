---
title: "Dual Boot Full Disk Encryption - Windows 7 and Ubuntu 9.10"
date: 2010-02-13
forum: Installation &amp; Upgrades
---

### Post by rhololkeolke on 2010-02-13
Hi,
I've been wanting to do this for a while and after upgrading some of my pc components I decided I would finally try to dual boot with full disk encryption on both windows 7 and Ubuntu 9.10.  I managed to encrypt the windows drive with truecrypt and that worked.  I installed Ubuntu 9.10 using the alternate cd and everything but /boot is in an encrypted LVM.  Each OS is on a separate SATA drive the windows is on sda1 and ubuntu /boot is sdb1.  To setup the dual boot I started out following the tutorial [http://ubuntuforums.org/showthread.php?t=761530](http://ubuntuforums.org/showthread.php?t=761530) but its for XP and versions of ubuntu that use grub not grub 2.  I ran dd as posted and saved the files it produced from truecrypt.  I then ran into some problems with grub reinstallation so I simply reinstalled Ubuntu 9.10 from scratch again.  This put grub 2 on the computer.  I've managed to get it to add a Windows 7 option.  However, when the option is selected truecrypt comes up and says that the bootloader is corrupted and that I need to use the repair CD I burned before I encrypted the drive.  My question is does anyone have any experience dual booting using Truecrypt on Windows 7 and LUKS/dm-crypt on Ubuntu 9.10 with grub 2?  And how would I get the boot menu to work?  I'd rather not reinstall but if I have to I have images from right before I encrypted so it wouldn't be the end of the world.

---

### Post by felixdzerzhinsky on 2010-04-12
> **rhololkeolke said:**
> Hi,
I've been wanting to do this for a while and after upgrading some of my pc components I decided I would finally try to dual boot with full disk encryption on both windows 7 and Ubuntu 9.10.  I managed to encrypt the windows drive with truecrypt and that worked.  I installed Ubuntu 9.10 using the alternate cd and everything but /boot is in an encrypted LVM.  Each OS is on a separate SATA drive the windows is on sda1 and ubuntu /boot is sdb1.  To setup the dual boot I started out following the tutorial [http://ubuntuforums.org/showthread.php?t=761530](http://ubuntuforums.org/showthread.php?t=761530) but its for XP and versions of ubuntu that use grub not grub 2.  I ran dd as posted and saved the files it produced from truecrypt.  I then ran into some problems with grub reinstallation so I simply reinstalled Ubuntu 9.10 from scratch again.  This put grub 2 on the computer.  I've managed to get it to add a Windows 7 option.  However, when the option is selected truecrypt comes up and says that the bootloader is corrupted and that I need to use the repair CD I burned before I encrypted the drive.  My question is does anyone have any experience dual booting using Truecrypt on Windows 7 and LUKS/dm-crypt on Ubuntu 9.10 with grub 2?  And how would I get the boot menu to work?  I'd rather not reinstall but if I have to I have images from right before I encrypted so it wouldn't be the end of the world.

I am interested in this also. One option may be to revert to Legacy Grub.Then the old how to's should work. I would prefer to stick with Grub2. 

[http://brettshaffer.com/blog/linux/downgrade-grub-2/](http://brettshaffer.com/blog/linux/downgrade-grub-2/)

---

### Post by rhololkeolke on 2010-04-12
I have gotten both operating systems installed with full disk encryption.  What I ended up doing is installing Windows and encrypting the disk with truecrypt.  After encrypting the entire drive and burning the recovery disk I installed Ubuntu.  Grub was installed to the MBR and after booting into Ubuntu I installed grub to the /boot partition that I made on my hard drive.  I then went back and reinstalled the Truecrypt loader from the restoration disk.  Now it comes up to the Truecrypt password prompt.  If I type in the password for the windows encryption it boots into windows.  If I want to boot into Ubuntu I press escape and GRUB loads allowing me to boot into Ubuntu provided that I type the right password.

---

### Post by felixdzerzhinsky on 2010-04-13
Thanks.Useful post. That will work for a lot of people.

 For me I usually prefer to default to Ubuntu rather than XP. So I will keep looking .

---

### Post by Deirty on 2010-04-14
Did you use Grub or Grub2? I read something about changing it out and just want to make sure it was grub2. Thanks for the hard work that went into this Also i found it hard to find a How to (step by step) for windows xp/ubuntu 9.10 and wanted to know if you or someone else would make a step by step How to for this.  The only other How to i found said something about expert mode from the install cd/dvd but the new ubuntu doesn't have that choice anymore.

Also you said "After encrypting the entire drive and burning the recovery disk I  installed Ubuntu."
You mean you just the partition you made for windows? Sorry if this seems like a new question.

Thank you

> **rhololkeolke said:**
> I have gotten both operating systems installed with full disk encryption.  What I ended up doing is installing Windows and encrypting the disk with truecrypt.  After encrypting the entire drive and burning the recovery disk I installed Ubuntu.  Grub was installed to the MBR and after booting into Ubuntu I installed grub to the /boot partition that I made on my hard drive.  I then went back and reinstalled the Truecrypt loader from the restoration disk.  Now it comes up to the Truecrypt password prompt.  If I type in the password for the windows encryption it boots into windows.  If I want to boot into Ubuntu I press escape and GRUB loads allowing me to boot into Ubuntu provided that I type the right password.

---

