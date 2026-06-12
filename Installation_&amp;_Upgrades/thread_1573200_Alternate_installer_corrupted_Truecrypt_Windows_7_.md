---
title: "Alternate installer corrupted Truecrypt Windows 7 install"
date: 2010-09-12
forum: Installation &amp; Upgrades
---

### Post by slny on 2010-09-12
Summary: alternate install CD wrote grub to boot sector without asking during attempt to install Ubuntu to an encrypted LVM partition on a dual boot Windows 7 and Ubuntu 10.04 setup

I had a disk with Windows 7 on it with two partitions, a 100mb windows recovery partition and another with 200gb or so for Windows (out of a total 500gb drive).  I did a system partition encryption using Truecypt 7.0 (not full disk since I wanted to put Linux on the machine as well as a dual boot configuration).  

This worked fine.

I then attemped to install an encrypted Ubuntu 10.04 installation using the alternate installer CD.  I created a regular ext4 /boot partition and then another encrypted LVM to house root and swap.  I then saved the partition changes.  After this, I quit and tried to boot into Windows first before continuing the Linux install to make sure it was still good.

Unfortunately, it failed to boot.  The Truecrypt bootloader loaded fine and after I entered my passphrase, I got the grub rescue prompt and some error saying no bootable partition found.

It seems that grub installed itself even though I didn't get to the part of the install where it asked where to install it.  Also, if grub wanted to install itself to someplace other than boot, wouldn't it have installed itself to the MBR?  Apparently it didn't otherwise the Truecrypt bootloader wouldn't have come up.  Where exactly did grub install itself?  Is it the boot sector of the Windows partition?  If so, why did it do this?

I'm currently decrypting the drive using the Truecrypt recovery CD and hope to be able to recover.

Any insight is appreciated.

Thanks.

---

### Post by slny on 2010-09-13
Turns out I was mistaken, grub was never written anywhere.

I accidentally marked /boot as bootable when creating my partitions thus making the windows partition not bootable.  Truecrypt bootloader then failed to boot windows because of this.

The grub-rescue prompt threw me off.  So it looks like Truecrypt bootloader is based off grub?

---

### Post by TheFacebookAteMyMommy on 2010-09-21
I just fought the TrueCrypt-EncryptedWindows-Linux-DualBoot beast and came out on top. in the end, it turned out to be very easy. i'm not sure that what i've got here is pertinent to your matter, but maybe it'll help, or perhaps someone else. here's what i did:

1. install windows. (although the truecrypt hidden OS setup *does* work, i'm going to skip over that option here because it works fine and has no bearing on this matter)

2. install truecrypt, and encrypt the entire windows system partition (be sure to create the rescue disk and keep it handy). reboot, make sure windows works fine, then proceed.

3. install ubuntu (10.04 is the current LTS). at the very last screen of the install, right after the bit about partitions & where to install it - there's a button labeled "Advanced", and that's where i chose to install the bootloader to /sda3 (the partition boot record), rather than /sda (the master boot record). this is key. (you might be installing to something different, like /sda2, or /hd2, or whatever. pay attention to the previous screen where it ID's them. the trick is, you're not installing to the MASTER BootRecord, you're installing to the PARTITION BootRecord.

reboot, and at the truecrypt prompt, hit [ESC] and the truecrypt bootloader should/will recognize your new linux install as a bootable partition.

WHAT IF:
- no truecrypt prompt? means you probably over-wrote it with linux install. no problem - use rescue disk to re-install it, then use ubuntu live cd to get in & re-install grub to the partition, not to the MBR. i think i had to mount /dev/sda3 to /mnt, then ran a command like: sudo grub-install --root-directory=/mnt /dev/sda3 --force

- hitting [ESC] at TrueCrypt prompt gives error: "No bootable partitions found" - means what it says. just use the ubuntu live cd to get in & re-install grub as described above.

Hope that helps you or someone else. I'm sure as heck bookmarking this for myself to come back to in 6 months when i run into the same problem :)

Result:
Acer Aspire 5000
WinXP (encrypted w/TrueCrypt)
WinXP encrypted/hidden OS
Ubuntu 10.04

---

### Post by vic_xyz on 2011-11-14
I've did exactly the same mistake by marking the /boot as bootable ...I'm sorry that I didn't read your post before:(


So, finally, how did you solve it ?
Decrypt system partition and start over ?


Thanks!
> **slny said:**
> Turns out I was mistaken, grub was never written anywhere.

I accidentally marked /boot as bootable when creating my partitions thus making the windows partition not bootable.  Truecrypt bootloader then failed to boot windows because of this.

The grub-rescue prompt threw me off.  So it looks like Truecrypt bootloader is based off grub?

---

### Post by slny on 2011-11-14
Hmm, I don't recall exactly.  Try booting with a gparted boot CD and marking your windows/truecrypt partition as bootable.


> **vic_xyz said:**
> I've did exactly the same mistake by marking the /boot as bootable ...I'm sorry that I didn't read your post before:(


So, finally, how did you solve it ?
Decrypt system partition and start over ?


Thanks!

---

