---
title: "Can I see Grub setting from WinXP??"
date: 2007-01-08
forum: Installation &amp; Upgrades
---

### Post by orionMX on 2007-01-08
Is it possible to see or edit Grub setting form Windows.  I want to install AMD64 over top of x86 version of Ubuntu.  Should I format Linux partitions with say Partition Magic, would I be able to see Grub in Windows?  Could I then install AMD64 version into same Linux partitions and be able to dual boot without troubles?  Would GRUB even need to be edited?
All newb questions but learning all the way....

thanks

---

### Post by loserboy on 2007-01-08
are you saying you want to install the 64bit version of ubuntu over the 32bit version?

if so you can just use the 64bit livecd and and format during the install, also i think there is a way to install the 64bit kernal and stuff without reinstalling  but i dont know much about that.

---

### Post by loserboy on 2007-01-08
when you install the 64bit version grub will know what you did and make the right changes (i think)

---

### Post by r.stiltskin on 2007-01-08
Not sure what you mean by the "grub setting".  Do you mean the grub boot menu?  That's located in /boot/grub/menu.lst, in your Linux partition, so you can't access it from Windows.  But there's no reason to.

Yes, grub/menu.lst needs to be edited because you'll be running a different kernel.  But the installer can rewrite it & reinstall it the same as it did for your first installation.  If you're careful not to screw up your Windows partition(s) you should be OK.

If your /home is on it's own partition, you don't even have to reformat it (unless you want to).  You can just mount it in the new filesystem without disturbing your data.

It's also not clear why you want to use Partition Magic -- you shouldn't need that unless you're going to resize some Windows partitions.

---

### Post by orionMX on 2007-01-08
Thank you. All good info.  The learning curve flattens again.

---

