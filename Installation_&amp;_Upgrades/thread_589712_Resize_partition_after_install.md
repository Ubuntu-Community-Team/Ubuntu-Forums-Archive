---
title: "Resize partition after install"
date: 2007-10-24
forum: Installation &amp; Upgrades
---

### Post by ascus4 on 2007-10-24
I had to clean reinstall Gutsy after my initial install went bad.  I booted off the live CD and hit install.
It all went well.

The problem is that it didn't overwrite my existing Gutsy installation.  It created a new partition and installed it there.  I now have two installs of 7.10 on my laptop.  

I want to merge the partition that contains my first install into the partition that contains my new install....or at least delete everything in the first install partition so I can utilitize the diskspace. 

It won't let me do either.  Gparted shows them all locked with padlock symbol and resize button grayed out.

Selecting all files in filemanager and trying to delete shows the move to trash button also grayed out.

Is their a way I can accomplish this?

Thank you in advance.

---

### Post by mikewhatever on 2007-10-24
You have to use gparted from the live cd. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by vanadium on 2007-10-24
Probably, you can use gparted also from the ubuntu install CD, but you need to unmount the partitions before you can do something with them (right-click). Then you can delete one partition, move the other (slow proces!!!) and resize that to fill all available space.

Because nowadays UUIDs are used in fstab, that probably will still work. However, you will need to do manual changes to /etc/menu.lst for the bootloader "grub" to find your correct partition again.

Otherwise said: what you want to do is not that trivial. A safer approach for you would be to delete all files on the "old' Ubuntu partition, and mount that in your new Ubuntu installation to be used for data storage. Alternatively, you could just reinstall the whole system, using the entire disk this time. Quite a fast solution, especially compared to moving partitions. however, you would loose all your customizations. Needles to say, before you attemtp any of all this, back up your personal data files to a safe location.

---

### Post by ascus4 on 2007-10-24
It's all set.  I used Gparted from the live CD and it's good to go.  55 gigs on the windows side and 53 gigs on the Linux side.  Just what I wanted.

Thanks for the responses folks.  I appreciate it.

---

### Post by vanadium on 2007-10-25
You didn't need to change anything in grub after removing a partition?

---

### Post by ascus4 on 2007-10-25
Grub went corrupt for the same reason I had to reinstall Gutsy.  It apparently reinstalled Grub at the same time because it worked.

---

### Post by ascus4 on 2007-10-25
No.  Grub still worked.

---

