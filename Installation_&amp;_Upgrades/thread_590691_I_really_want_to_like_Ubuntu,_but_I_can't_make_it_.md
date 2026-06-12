---
title: "I really want to like Ubuntu, but I can't make it install ANYTHING"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by lookmomimonlinux on 2007-10-25
a friend of mine installed breezy onto my pc and i never really used it but now i downloaded the iso to the latest version and when i popped in the cd it read....



The following problems were found on your system:


W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)






PLEASE, if anyone can help solve this, point me in the right direction, or give me a clue as to what is going on here i would be very grateful. i don't want to have to switch back to windows but if i'm unable to install something as simple as a flash player i have no use for this. i am willing to be patient in learning how to use ubuntu, i just need a hand.

---

### Post by gtdaqua on 2007-10-25
the latest is version 7.10 Gutsy Gibbon. Breezy is too old!  Probably not suppored now (not sure). Downoad the 7.04 Feisty Fawn or 7.10 version. 7.04 is more stable in my opinion give that 7.10 is fairly new.

---

### Post by lookmomimonlinux on 2007-10-25
i would love to update to something more current, but i am unable. how do i fix these problems in order to?

---

### Post by aysiu on 2007-10-25
Yes, Breezy is no longer supported, as you can see here:
[http://us.archive.ubuntu.com/ubuntu/dists/](http://us.archive.ubuntu.com/ubuntu/dists/)

Apart from the LTS (Long-Term Support) releases (of which there is only one right now--6.06), Ubuntu releases are supported for only 18 months. Breezy was released in October 2005. It is now October 2007, 24 months later.

---

### Post by aysiu on 2007-10-25
> **lookmomimonlinux said:**
> i would love to update to something more current, but i am unable. how do i fix these problems in order to?
If you have the latest ISO (Ubuntu 7.10), burn it to CD (using Breezy, just right-click the ISO file and select *Write to Disc*). Then reboot with the CD in your drive, and (if your BIOS is set to boot from CD first instead of hard drive first) you should be able to install the latest version over Breezy.

---

### Post by gtdaqua on 2007-10-25
Confirmed that Breezy is obsolete.
Read [here]("https://help.ubuntu.com/community/UpgradeNotes").

You can go to [www.ubuntu.com]("www.ubuntu.com") and download the latest ISO image for desktops.

---

### Post by lookmomimonlinux on 2007-10-25
alright, well how do i start from scratch/install this iso cd for 7.10 if i am unable to do anything with breezy. i apologize if that is a retarded question. i have no knowledge of any of this.

---

### Post by lookmomimonlinux on 2007-10-25
thanks, i'll give it a try. but will i be able to save my files on breezy?

---

### Post by lookmomimonlinux on 2007-10-25
My BIOS must not be set to boot from cd first because it just started breezy up like it wasnt in the drive. How do i set it to boot from the cd?

---

### Post by lookmomimonlinux on 2007-10-25
Can anyone help me with this, please?

---

### Post by aysiu on 2007-10-25
> **lookmomimonlinux said:**
> My BIOS must not be set to boot from cd first because it just started breezy up like it wasnt in the drive. How do i set it to boot from the cd?
When your computer boots up, there may be an indicator about changing the boot sequence with a certain key. If it doesn't tell you what key to use, you can try Delete, F12, or Escape.

---

### Post by lookmomimonlinux on 2007-10-25
Can anyone help me with this please?

---

### Post by PointyWombat on 2007-10-25
It depends on what bios you have with your PC, but essentially, you'll ned to hit a key (delete, esc, or an F key) when you're booting up to get you into your PCs BIOS. From there you'll need to look for something which allows you to select your first boot device. You'll see optons like CDROM, DISK, FLOPPY, ...  set your first boot device to CDROM, and second boot device to DISK... save and exit. It'll reboot and if you have a CD in the drive, it'll read that as the first boot device and continue on to load the Ubuntu kernel.

Good luck.

---

### Post by jenhsun on 2007-10-25
1. Connect to the internet
2. In your terminal type

gksu "update-manager -c -d"

---

