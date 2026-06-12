---
title: "recent Lucid update bonked my Grub2"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by coiske on 2011-03-19
I'm running 64bit Lucid LTS.  I've had grub2 for ages, but a recent routine software update suddenly gave me grub2 trouble.

-The update ended with "dpkg: error processing grub-pc (--configure):
 subprocess installed post-installation script returned error exit status 10"

-Running "sudo dpkg-reconfigure grub-pc" only resulted in a warning that this package was broken or not fully installed.  (Without giving me any option to fix things.)

-So I ended up purging and reinstalling grub-pc and grub-common

-I was expecting to get a "where do you want to install grub2 to?" config screen as part of the reinstallation process.  But instead, I got a screen saying "You chose not to install GRUB to any device....[explanation of why this is bad]...Continue without installing GRUB?"   I tried selecting "<No>", but that didn't do anything.  I was only allowed to select "<Yes>".   Grrr.   I most certainly didn't choose to avoid installing grub2 anywhere, even though the config screen was strangely assuming this (and not letting me correct that assumption.)

-I finally ended up manually installing grub using "sudo grub-install --force /dev/sda3".

-This installed grub2 fine.  But I'm worried that next time grub2 gets updated, it's not going to automatically install it to the right place.  (I'm pretty sure that only happens if you were able to use the package config screens  to say where you want it.)  So I tried running "sudo dpkg-reconfigure grub-pc," but this just gives me the same "You chose not to install GRUB" config screen I saw during installation, with no way to select "<No>"

I'd love any tips on how to get dpkg-reconfigure to actually ask me WHERE I'd like to put grub, as it should.  (So my preference will persist across software updates.)

Thanks!

---

