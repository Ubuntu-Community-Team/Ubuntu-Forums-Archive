---
title: "Cloned dual-boot Windows and Ubuntu SSD: Ubuntu boots to terminal"
date: 2018-06-23
forum: Installation &amp; Upgrades
---

### Post by samtx2 on 2018-06-23
I had a 120 GB SSD with dual booted Windows 10 and Ubuntu 16.04 set up and working great installed in my Dell Inspiron 3543. I tried to clone the SSD into a larger 256 GB SSD. I wanted the same dual boot setup but I resized the partitions to give Ubuntu about 94 GB and Windows 120 GB. I used the free version of Acronis True Image HD 2015 program that you can download from the Crucial support website.

Then I couldn't boot into the Grub boot loader. So I ran boot-repair and I am able to boot to the Grub menu, but there is a problem when I try and boot into Ubuntu. Booting into Windows 10 is fine.

Now when I try and boot into Ubuntu, instead of taking about 20 seconds and booting to the desktop, it now takes about 100 seconds and boots to a full-screen terminal asking me for my login and password. I am able to log in successfully, but I don't know how to get back to the desktop or fix the Ubuntu boot issue.

The boot-repair help file is here: paste.ubuntu.com/p/N8W5WgHgwz


Thank you for the help.

---

### Post by oldfred on 2018-06-23
It looks like you have a new UUID for /?

       Line 120
From blkid
/dev/sda5 [COLOR=#ff0000]       7939f73d-48c1-3a6e-d4f9-520bb251cf6d[/COLOR]   ext4       Ubuntu

Line 620, from your fstab
# / was on /dev/sda5 during installation
UUID=[COLOR=#ff0000]65b604da-2361-44d6-bac6-f8abe9a89414[/COLOR] /               ext4    errors=remount-ro 0       1

From live installer mount / & edit fstab to have correct UUID.

---

