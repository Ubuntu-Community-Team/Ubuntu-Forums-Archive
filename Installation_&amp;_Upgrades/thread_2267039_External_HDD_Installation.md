---
title: "External HDD Installation"
date: 2015-02-26
forum: Installation &amp; Upgrades
---

### Post by holysword on 2015-02-26
Hey there, 
I am trying to install Ubuntu 14.04 LTS in my external HDD but its kinda... not working. The BIOS simply complains that there is no OS in it.
I've managed to install in a second external HDD (a Seagate 2TB USB 3.0), but not in the one I wanted to install (a Samsung 640GB USB 2.0). Is there any restriction on that? I'm pretty sure I booted from USB 2.0 memory sticks and all for quite a long time.

PS: Yes, I am sure I am installing the bootloader in the correct device.

---

### Post by oldfred on 2015-02-26
What system & model. Is it older BIOS or newer UEFI?

Post link to summary report, you can use live installer.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by holysword on 2015-02-27
> **oldfred said:**
> What system & model. Is it older BIOS or newer UEFI?

Post link to summary report, you can use live installer.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
It is not UEFI, its a HP pavillion dv7 from 2010. I would guess that the installer encounters an error and does not install GRUB, but also don't say anything. I would crawl into grub.conf myself but I tried and that looked like ancient runes to me (I never knew a grub.conf could be so long...) so maybe when I have more time to invest in that... but I honestly doubt the problem lies in grub.conf, since the BIOS won't even find it.

I'll chech Boot-Repair. As a second test I'll try to install another OS in the same hard drive to figure out if it could be something with the device itself. I'll let you know.

---

### Post by ubfan1 on 2015-02-27
Take a look at the grub.cfg file that the installer generates.  With the live media present at the creation of the grub.cfg, sometimes the disks get enumerated one way, and without the live media, they get enumerated differently (typically one less in letter or number). Bug 384633 still might be a problem.  You can just edit the grub commands, changing sdc to sdb (or sdb to sda etc.) and hd2 to hd1, and see if you can get a successful boot. If so, immediately run sudo update-grub to fix things up, since the live media will no longer be present.

---

### Post by sudodus on 2015-02-27
Many HP computers have problems to boot from installed systems / grub. What you can do is chainload from an older version of grub to your current system. See this link, particularly post #1 and #7
[URL="http://ubuntuforums.org/showthread.php?t=2196858"]
Howto help USB boot drives[/URL]

---

### Post by holysword on 2015-02-27
> **ubfan1 said:**
> Take a look at the grub.cfg file that the installer generates.  With the live media present at the creation of the grub.cfg, sometimes the disks get enumerated one way, and without the live media, they get enumerated differently (typically one less in letter or number). Bug 384633 still might be a problem.  You can just edit the grub commands, changing sdc to sdb (or sdb to sda etc.) and hd2 to hd1, and see if you can get a successful boot. If so, immediately run sudo update-grub to fix things up, since the live media will no longer be present.

> **sudodus said:**
> Many HP computers have problems to boot from installed systems / grub. What you can do is chainload from an older version of grub to your current system. See this link, particularly post #1 and #7
[URL="http://ubuntuforums.org/showthread.php?t=2196858"]
Howto help USB boot drives[/URL]
Thank you both for the suggestions, I will read it and try some things.

---

### Post by oldfred on 2015-02-27
Also how large is / (root) partition. 
Some BIOS when booting from USB devices, do not want any files beyond a certain point on drive. It is like an old BIOS issue of no boot files beyond 137GB, but still present on newer BIOS when using external USB devices.
If possible install with / of 25GB at beginning of drive and use rest of drive as /home or data partition(s).

---

