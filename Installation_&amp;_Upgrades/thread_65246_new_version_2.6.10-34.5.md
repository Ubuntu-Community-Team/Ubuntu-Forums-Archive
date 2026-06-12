---
title: "new version 2.6.10-34.5"
date: 2005-09-13
forum: Installation &amp; Upgrades
---

### Post by xjlx on 2005-09-13
Can anyone tell me what this means/why it happened/how to fix it?
E: /var/cache/apt/archives/linux-image-2.6.10-5-386_2.6.10-34.5_i386.deb:  unable to install new version of `./lib/modules/2.6.10-5-386/kernel/drivers/cdrom/cm206.ko': Is a directory

---

### Post by mlomker on 2005-09-13
[QUOTE=xjlx]Can anyone tell me what this means/why it happened/how to fix it?
E: /var/cache/apt/archives/linux-image-2.6.10-5-386_2.6.10-34.5_i386.deb:  unable to install new version of `./lib/modules/2.6.10-5-386/kernel/drivers/cdrom/cm206.ko': Is a directory[/QUOTE]

That's a bit odd.  Have you tried looking deleting that file?

You could always **rm -fr /lib/modules/2.6.10-5-386/kernel/drivers/cdrom** but that's a bit aggressive.

---

### Post by xjlx on 2005-09-13
I haven't tried to do anything yet, what is the difference between deleting it and rm -fr ?

---

### Post by xjlx on 2005-09-13
Preconfiguring packages ...
Selecting previously deselected package linux-image-2.6.10-5-386.
(Reading database ... 66400 files and directories currently installed.)
Preparing to replace linux-image-2.6.10-5-386 2.6.10-34.4 (using .../linux-image-2.6.10-5-386_2.6.10-34.5_i386.deb) ...
The directory /lib/modules/2.6.10-5-386 still exists. Continuing as directed.
Unpacking replacement linux-image-2.6.10-5-386 ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.10-5-386_2.6.10-34.5_i386.deb (--unpack):
 unable to stat `./lib/modules/2.6.10-5-386/kernel/drivers/cdrom' (which I was about to install): Input/output error
Searching for GRUB installation directory ... found: /boot/grub .
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Testing for an existing GRUB menu.list file... found: /boot/grub/menu.lst .
Searching for splash image... none found, skipping...
Found kernel: /boot/vmlinuz-2.6.10-5-386
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.10-5-386_2.6.10-34.5_i386.deb

I don't know if that helps or not

---

### Post by mlomker on 2005-09-13
I would try deleting the directory altogether, which is what this command would do from a terminal prompt:

**sudo rm -fr /lib/modules/2.6.10-5-386/kernel/drivers/cdrom**

Then run the update again.  The bad news is that I can't tell you for certain if that'll leave you in a bad spot or not...I've never seen this problem.

---

### Post by xjlx on 2005-09-13
thanks for your help, I just went ahead and reinstalled because I didn't have anything on the drive of any real value, and ever since I had left the overclocking on 10% in my bios from when i booted to my windows drive, ubuntu acted strangely.

---

