---
title: "Fresh install of lucid does not boot"
date: 2010-04-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by shaggy999 on 2010-04-21
Setup:

Intel Q6600 @ 2.40 GHz
6 GB RAM
nVidia 8800 GTX
Dual 15" 1024x768 Monitors
80 GB SATA

Installaion Method: amd64-alternate-beta2

I wiped my hard drive and installed lucid using a custom partition layout using lvm + encryption. Everything installed fine, I rebooted and it asked me for my password. After I enter I password it states the drive is unlocked successfully and then the OS just sits there. It does not respond to any keyboard commands.

So I reinstalled using the "guided" encryption partitioning and had the exact same result. Thinking it might be an issue with lvm or encryption I wiped the entire drive and used basic guided partitioning. No lvm or encryption or anything fancy. Everything is default values.

It installs perfectly fine but seems to hang a few seconds into bootup.

What should I do?

---

### Post by dino99 on 2010-04-21
if you have an other OS installed (or from booted cd), you can chroot it and grab info into logs. 
Follow this howto:

[http://ubuntuforums.org/showthread.php?t=1263030&page=2](http://ubuntuforums.org/showthread.php?t=1263030&page=2)

---

### Post by shaggy999 on 2010-04-21
I have no other OS installed. As I mentioned I used the guided "use entire drive" option. How do I get a terminal from the alternate cd? I don't have the live cd and don't really want to download a new disc.

---

### Post by dino99 on 2010-04-21
same problem with recovery boot mode ? edit the boot line and remove "quiet splash" and add nomodeset and/or acpi=off and/or lapic=off and/or apic=off

from [https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Boot%20options%20hidden%20by%20default%20on%20Desktop%20and%20Netbook%20CDs](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Boot%20options%20hidden%20by%20default%20on%20Desktop%20and%20Netbook%20CDs)

Encrypted partitions must be listed in /etc/fstab

Users who have configured any encrypted partitions in /etc/crypttab to start at boot time (i.e., not using the noauto option) should make sure that the filesystems on these volumes are listed in /etc/fstab. Otherwise, the passphrase prompt is not guaranteed to be displayed at boot time.

---

### Post by shaggy999 on 2010-04-21
As I stated above I re-installed with NO ENCRYPTION OR LVM. This is NOT my problem. My problem is that on a COMPLETELY DEFAULT install Ubuntu does not boot. I can't seem to edit the grub line or enter recovery mode because by default grub2 just straight up boots into Ubuntu and doesn't give me a moment to press any key to change into a different boot mode.

---

### Post by ronparent on 2010-04-21
For your situation: Hold the left <shift> key down immediately after your bios screen goes off. This will bring up the grub menu from which you can edit your boot options. If it doesn't come up then you probably hold the key down sooner. Have fun.

---

### Post by shaggy999 on 2010-04-25
I have been going insane for the past few days but I finally figured it out. After installing lucid dozens of times in both desktop and alternate versions I gave up and decided to install Windows 7. That install failed about 5 times. Then I tried to install Vista and that failed. On a hunch I pulled a set of RAM chips out and everything works fine now. Got Lucid + Win7 installed finally installed.

What's really weird is that karmic installs perfectly fine with the ram added.

---

### Post by frantid on 2010-04-26
Check your bios for "memory hole remapping" options.  I ran into similar problems going to 4 gig of memory.

---

