---
title: "Can't get laptop to boot into ubuntu"
date: 2015-05-05
forum: Installation &amp; Upgrades
---

### Post by peter191 on 2015-05-05
Hello.

I recently installed Ubuntu on a Toshiba Dynabook R632 laptop.  My old SSD died, I bought a new SSD and decided to install Ubuntu instead of Windows this time around.

I created a LiveUSB stick and installed Ubuntu, everything seemed to work OK, but when I restart my laptop, I get stuck on the dynabook loading screen, it never reaches grub or any other loading screen.

I installed and ran boot repair using the liveUSB, it errored out with this message:

[http://paste.ubuntu.com/10989336/](http://paste.ubuntu.com/10989336/)

When I check the files from the LiveUSB they show up, however it seems to refuse to boot off of the hard disk.  Also when I try accessing the boot menu using F12, the hard disk appears but, again, if I pick my SSD from the pulldown, it just gets stuck on the Dynabook loading screen.

If I try switching to CSM boot instead, I get an error message saying: "No bootable device -- insert boot disk and press any key".

Any help would be greatly appreciated... thank you very much.

---

### Post by dino99 on 2015-05-05
be sure that the ubuntu OS partition (/ aka root) has the 'boot' flag set; check it with gparted live

---

### Post by Bucky Ball on 2015-05-05
Welcome.

> **peter191 said:**
> 
If I try switching to CSM boot instead ...

Stick with the mode you installed in. Anything else will create chaos, as you've discovered.

This might sound silly, but ... when you reboot, is the install disk/USB unplugged (should be) and you have changed the BIOS to boot from the hard drive? Had to ask ... ;)

* Ok, just had a look at your bootinfo. You need to be booting in UEFI as that is the mode you installed Ubuntu in. You don't have to and might be easier if you didn't, but let's stick to it for a while ...

---

### Post by grahammechanical on 2015-05-05
The errors that I see are all pointing to sdb which Boot Repair lists as having a GUID Partition Table (GPT). Is it usual for a USB memory stick to have GPT?

> Warning: /dev/sdb contains GPT signatures, indicating that it has a GPT table.  However, it does not have a valid fake msdos partition table, as it should.  Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?
Error: The primary GPT table is corrupt, but the backup appears OK, so that will be used.


Could this be the situation? Ubuntu is installed in EFI but the live session is not running in EFI mode. Boot repair is having trouble mounting sdb. What was this 15 GB USB used for previously? There may be information left on it that is confusing Boot Repair.

> grub-probe: error: cannot find a GRUB drive for /dev/sdb1.  Check your device.map.
Adding boot menu entry for EFI firmware configuration
mount: /dev/sdb2 already mounted or /mnt/boot-sav/sdb2 busy
mount /dev/sdb2 : Error code 32
mount -r /dev/sdb2 /mnt/boot-sav/sdb2
mount: /dev/sdb2 already mounted or /mnt/boot-sav/sdb2 busy
mount -r /dev/sdb2 : Error code 32

All this may be incidental to the original problem but it certainly causes confusion. Well, it sure is confusing me. This is an important bit.

> =================== Recommended repair
The default repair of the Boot-Repair utility will reinstall the grub-efi-amd64-signed of sda2, using the following options:        sda1/boot/efi,
Additional repair will be performed: unhide-bootmenu-10s repair-filesystems   use-standard-efi-file rename-ms-efi

And this

> Reinstall the grub-efi-amd64-signed of sda2
Installing for x86_64-efi platform.
Installation finished. No error reported.

Regards.

---

### Post by peter191 on 2015-05-06
Hey guys, 

I figured out my own issue.  Basically my /EFI directory had a different structure from what my Toshiba laptop expected.  I instead altered it to mirror what was on the USB stick's /EFI folder and it worked.  Guess my laptop model is finicky WRT the structure of the EFI folder:

I fixed it by following the instructions in this blog post here:

[http://linuxontoshiba.blogspot.jp/](http://linuxontoshiba.blogspot.jp/)

Basically I copied the /EFI/ubuntu folder into /EFI/boot and then copied the missing BOOTx64.EFI file in.  Then things worked.  Success!

---

### Post by Bucky Ball on 2015-05-06
Excellent work! Don't worry, it's not just your EFI that is finnicky. EFI is a special feature they've added for Linux users! It's like a guessing game becaues it can be tweaked to be unique to a particular computer manufacture. Neat fun when you're trying to install Linux, huh? :|

It matters not much whether you use UEFI, but you're there, so cool. There are no partition limitations with EFI install. With the older mode you are limited to four partitions per physical drive. 

Enjoy the OS, the learning curve and the forums. Please mark the thread as solved (second link in my signature) to help future travelers. Thanks. ;)

---

