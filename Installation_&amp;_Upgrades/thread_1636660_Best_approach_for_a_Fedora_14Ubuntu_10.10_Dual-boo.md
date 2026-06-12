---
title: "Best approach for a Fedora 14/Ubuntu 10.10 Dual-boot?"
date: 2010-12-03
forum: Installation &amp; Upgrades
---

### Post by ccarrow14 on 2010-12-03
Hello.

I plan to do a fresh install of Ubuntu 10.10, and I would like to dual-boot it with Fedora 14.

My last experience with Fedora's installation program was not good. It erased my Windows 7 partition without me telling it to. :/

Any tips? I'm thinking of installing Fedora first and letting it take over the hard drive, then using Ubuntu's good installation program to try and dual-boot...

Also, are there any specific precautions I should worry about?

---

### Post by coffeecat on 2010-12-03
A few thoughts from someone who has had many occasions to grind his teeth over Fedora's - um - quirks. :)

If you leave the Fedora installer to its own devices it will create a separate boot partition, which you may or may not find useful; personally I find it an unnecessary complication. More of a nuisance it will make the root partition a LVM one, which makes subsequent life difficult.

Next bit of Fedora nonsense is that when it installs grub (still on legacy grub) it will only detect Windows (if present). It ignores any other Linux installations on the same drive.

Last point - if you plan to share data between Fedora and Ubuntu be aware that the default UID of the first created user will be 500 in Fedora and 1000 in Ubuntu, leading to permissions problems.

This is what I suggest.

1 Set up your partitions beforehand with Gparted in the Ubuntu live CD. Fedora will happily work on a single ext4 partition, but you have to coax it a little in the installer.

2 Now boot up with the Fedora install disc and choose the equivalent of Ubuntu's 'advanced' manual option at the partitioning stage. This way you can force Fedora to use the partition(s) you want, rather than what its devs want.

3 When you are setting up the user account (during the first reboot iirc) you can set the UID to 1000. I can't remember the details, but I did manage this OK.

4 Now you'll have a single-booting Fedora with a hidden legacy grub menu. The next step is to boot up with the Ubuntu live CD, choose manual/advanced at the partitioning stage and install Ubuntu to whichever pre-prepared partitions you intend for it. Ubuntu, being a superior distro :wink: will pick up the presence of Fedora and give you a dual-boot grub menu.

Good luck!

---

### Post by Rubi1200 on 2010-12-03
I haven't used Fedora for some time now (last one I dual-booted was 11 or 12 I think), but my experience was similar.

In any event, I highly recommend you follow the advice posted by coffeecat and install Ubuntu AFTER sorting things out with Fedora.

Good luck!

---

