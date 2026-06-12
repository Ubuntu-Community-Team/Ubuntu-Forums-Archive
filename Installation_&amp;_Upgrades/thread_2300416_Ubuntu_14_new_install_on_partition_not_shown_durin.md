---
title: "Ubuntu 14 new install on partition not shown during grub boot picks"
date: 2015-10-25
forum: Installation &amp; Upgrades
---

### Post by cliff5 on 2015-10-25
I have an old desktop with one 80 GB HDD. (hd0)
I have a rock-solid Ubuntu 9.10 on one 35 GB partition (hd0,6) that i want to leave be. 
I installed new Ubuntu 14 LTS on the other 35 GB partition (hd0,1). from a live DVD. Some minor errors but seemed to go OK.

Now, when I reboot the computer, the "GNU Grub version 1.97~beta4 " screen shows only the old ubuntu 9 boot options, and does not show any options from the other partition. 

When i look at gparted from LiveDVD ubuntu14  or old ubuntu 9, both show (hd0,1) as having the boot flag. but grub doesn't seem to see that flag or it doesn't seem to matter.

How can i get grub to give me boot options for the new install on (hd0,1)? Do i have to do something with the master boot record?

Thanks

---

### Post by yancek on 2015-10-25
The boot flag is meaningless, or at least not needed with any Linux.  Do you have only 9.10 and 14.04 installed and no other OS?  Windows does need the boot flag. 

> Now, when I reboot the computer, the "GNU Grub version 1.97~beta4 " screen shows only the old ubuntu 9 boot options,

That's the bootloader for 9.10.  If you can boot 9.10, do that and open a terminal and run:  sudo update-grub.  You apparently installed Grub to the partition on which you have 14.04.  If you watch the output you should see an entry indicating 14.04 was detected.  Reboot and give a try.  If you can boot 14.04, you can then install Grub from 14.04 to the MBR or leave the old Grub.  I'm sure you know 9.10 hasn't been supported for over 4 years?

---

### Post by cliff5 on 2015-10-25
> **yancek said:**
> terminal and run:  sudo update-grub. 

this worked perfectly! boot into 14 is fine. Thanks, simple fix.

  > **yancek said:**
> I'm sure you know 9.10 hasn't been supported for over 4 years?

the old machine is 1.8 GHz single core and 1GB ram. 9.1 is snappy and 14 is laggy. 9.1 is OK for offline stuff and my old programs, 14 is for some new stuff to try.

---

