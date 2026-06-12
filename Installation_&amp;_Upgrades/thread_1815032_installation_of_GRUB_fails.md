---
title: "installation of GRUB fails"
date: 2011-07-30
forum: Installation &amp; Upgrades
---

### Post by chedderslam on 2011-07-30
Reposting from general help as no response.

Installing to encrypted LVM on hardware RAID array.


When it asks where to install GRUB, it defaults to /dev/mapper

I have tried /dev/mapper, /dev/boot, /dev/sda1, /boot.

raid array with:
boot
encrypted lvm
swap
home

I am not sure what to put there.

---

### Post by YesWeCan on 2011-07-30
When what asks? The alternate install CD installer?

What it usually means is which partition or MBR do you want to install Grub's boot code to. One would normally choose an MBR and specify it like /dev/sda. So what is the device name of your hardware RAID?

You haven't given much detail. When you say "hardware RAID" do you mean a proper h/w RAID or do you mean a fake RAID? (see: [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto))

---

### Post by chedderslam on 2011-07-30
Sorry for the lack of detail.

11.04 alternate i386.

hardware raid - 2x80gig striped, 2x160gig mirrored.

This is what it looks like in the partition set up screen(hand typed):
```

LVM VG raidone, LV biggie - 160.0 GB Linux device-mapper (linear)
   #1   160.0 GB K ext4
LVM VG raidzero, LV home - 151.5 GB Linux device-mapper (linear)
   #1   151.5 GB K ext4   /home
LVM VG raidzero, LV root - 4.4 GB Linux device-mapper (linear)
   #1   4.4 GB K ext4   /
LVM VG raidzero, LV swap - 3.8 GB Linux device-mapper (linear)
   #1   3.8 GB K swap   swap
Serial ATA RAID sil_bhahebddajcd (stripe) - 160.0 GB Linux device-mapper (striped)
   #1   primary   368.8 MB   K ext2   /boot
   #2   primary   159.7 GB   K crypto   (sil_bhahebddajcd2_crypt)
Serial ATA RAID sil_bhahebddajcd2_crypt (partition #2_crypt) - 159.7 GB Linux device
   #1   159.7 GB   K lvm
Serial ATA RAID sil_bhahebddbgbh (mirror) - 160.0 GB Linux device-mapper (mirror)
   #1   primary   160.0 GB   K  crypto   (sil_bhahebddbgbh1_crypt)
Serial ATA RAID sil_bhahebddbgbh1_crypt (partition #1_crypt) - 160.0 GB Linux device
   #1   160.0GB   K lvm
```


I hope that clarifies.

Also if anyone can comment on the filesystems, sizes, or anything else that I can change to increase performance,  I would appreciate it.

3Ghz P4, 3.5 gigs ram

---

### Post by YesWeCan on 2011-07-30
Can exit the installer for a moment and run [COLOR="Navy"]sudo fdisk -l[/COLOR] that will show the disk device names. I'm not quite sure what the installer labels are indicating here, there is a lot of device mapping going on.

---

### Post by chedderslam on 2011-07-30
disk /dev/dm-7:4399 MB
disk /dev/dm-8:3795 MB
disk /dev/dm-9:151.5 GB
disk /dev/dm-10:160.0 GB

Thank you for the help so far.

---

### Post by chedderslam on 2011-07-31
ok, after going back to the partition menu, then returning to the step where it tries to install GRUB, it now tries installing GRUB without giving me an option of where to install it.

It now ends up showing:
Unable to install GRUB /dev/mapper/sil_bhahebddajcd

This is a fatal error.

I go back to the menu, try again, and the same thing

---

### Post by Quackers on 2011-07-31
Things are greatly complicated with RAID and LVM.
Which raid array have you installed Ubuntu to? The striped set or the mirrored set? And is that the array your bios boots from?

---

### Post by chedderslam on 2011-07-31
This is a fresh install.

I am trying to install to the striped set, which is what I would boot from.

---

### Post by Quackers on 2011-07-31
It seems to be trying to install grub to the correct mbr. I don't know why it's having a problem, but in fairness I am no expert where RAID/LVM is concerned.
Have you tried to install grub manually from a live cd?

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by YesWeCan on 2011-07-31
> **chedderslam said:**
> disk /dev/dm-7:4399 MB
disk /dev/dm-8:3795 MB
disk /dev/dm-9:151.5 GB
disk /dev/dm-10:160.0 GB

Thank you for the help so far.
That's the output of fdisk -l?

Well, this looks very much to me like a fakeRAID rather than a hardware RAID. With a hardware RAID, as I understand it, a RAID array should appear as a single disk device and show up in fdisk as such. FakeRAID, however, requires Ubuntu to use its dmraid driver and results in device mappings.

I am also not expert in this area. But I would double check what sort of RAID you have and how to install to it.

FYI fakeRAID is a system for enabling Windows to do software RAID. It is completely unecessary for linux which normally uses a different system called mdadm. I believe Ubuntu can be coaxed into using fakeRAID if you want it to. If you are not intending to use Windows then you may be better off disabling all RAID in your bios and removing the RAID metadata info from your disks, then installing Ubuntu and setting up the mdadm RAID arrays in the partitioner.
To remove the fakeRAID metadata from a disk sdx:
sudo dmraid -E -r /dev/sdx

---

### Post by chedderslam on 2011-07-31
This is a hardware raid set up through a raid card.  It is not a top of the line raid card, so the performance benefits are negligible, but I would like to use it as it is already hooked up.

The output of fdisk -l is showing the 4 logical volumes created in LVM.

---

### Post by YesWeCan on 2011-07-31
I can't help you with this.
I don't know enough about how Ubuntu is working with your RAID card.
What is your RAID card - mfr, product #?

---

