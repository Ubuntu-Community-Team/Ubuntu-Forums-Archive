---
title: "Problem with GRUB"
date: 2006-06-05
forum: Installation &amp; Upgrades
---

### Post by makrothumeo on 2006-06-05
Alright, I reinstalled Ubuntu (using the" alternate" distro of Ubuntu) today and for some reason it installed LILO instead of GRUB. I've tried to install GRUB, but I can't figure out how. I go through the "grub-install" process and it places files in the Boot folder, but when I start grub from the terminal it gives me a bunch of errors. Everything I see says I am doing everything right, it's just not working for me.

So I have a few question:
1. Does GRUB support XFS?
2. Is there any way to force Ubuntu to install GRUB when installing from the disk?
3. Is there a specific reason why it installed LILO instead of GRUB?

---

### Post by Nordoelum on 2006-06-05
1. Don't know.
2. Read next section.
3. Because I think the new 6.06 release is using LILO instead of GRUB. That is what I have experienced.

Ed1t: Have you readed this? [http://ubuntuforums.org/showthread.php?t=76652](http://ubuntuforums.org/showthread.php?t=76652)

---

### Post by krokodil on 2006-06-05
I mucked about for a couple of hours before managing to install Dapper. The install would crash each time it got to installing Grub on a pure XFS system.

Finally I setup a separate /boot partition with ext3 (stopped Dapper install from crashing) and in my BIOS settings changed my drive (200GBs SATA) to "Large", stopped me getting Grub Error 17.

I also disconnected my backup drive for the install but have reconnected it and rebooted successfully a few times since.

---

### Post by krokodil on 2006-06-07
I filed my bug here:

[https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/48583](https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/48583)

And there is a bug that says that the installer should inform users of the problem with Grub and XFS (like the Breezy installer does):

[https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/47848](https://launchpad.net/distros/ubuntu/+source/ubiquity/+bug/47848)

---

### Post by makrothumeo on 2006-06-07
Thanks for the info guys! Hopefully this bug is cleared up soon, as it is slightly annoying to need a seperate boot partition. No biggy though.

Seems that Ubuntu Alternate uses LILO while the regular version uses GRUB. That's kinda dissipointing to me because I prefer the alternate setup process but LILO doesn't detect my Windows install right off that bat like GRUB (at least during the Ubuntu install).

---

