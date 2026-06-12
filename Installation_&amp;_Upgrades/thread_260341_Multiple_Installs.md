---
title: "Multiple Installs?"
date: 2006-09-18
forum: Installation &amp; Upgrades
---

### Post by Caepio on 2006-09-18
I have successfully installed and upgraded Ubuntu, but now at the boot screen, there is an ever growing list of operating systems from which to choose. What's with this? Is there some way to edit this? Am I making the situation worse by upgrading?

At this point, I have at least 6 choices, not including Windows 2000.

Thanks.

---

### Post by lha on 2006-09-19
> **Caepio said:**
> I have successfully installed and upgraded Ubuntu, but now at the boot screen, there is an ever growing list of operating systems from which to choose. What's with this? Is there some way to edit this? Am I making the situation worse by upgrading?

At this point, I have at least 6 choices, not including Windows 2000.

Thanks.

Grub's configuration file is /boot/grub/menu.lst. To see some help with the options, run
```
man update-grub
```
To reduce the number of choices you see, you can either remove old kernels with Synaptic or replace
```
# howmany=all
```
with
```
# howmany=2
```
in menu.lst and run
```
update-grub
```

---

### Post by PaulSales on 2007-08-02
I have a similar problem.  I have a "production"  Ubuntu system which was installed first, well after XP,    I deleted a partition andI managed to render my laptop unbootable, not even XP. 

 I installed a second Ubuntu system from the CD.  This corrected the boot problem, could now boot either the "production" system, the second installed system,   or XP     Again messed up something rendering the laptop unbootable and installed a 3rd instance.

All is now working as it should, can boot XP and any one of the 3 Unbuntu systems.

I moved my /home directory on the "production" system to a partition of it's own.

However I notice that the boot menu display all 4 systems and also the production system & new /home. The menu.lst on the 3rd install of Ubuntu shows all possible bootable systems, including one for the system with the new /home partition, .

However the menu,lst on the first "production" system I installed does not show the two other Ubuntu systems.  Nor the option of booting with the new /home partition.

What I want to do is remove the 2nd & 3rd instances of Ubuntu.  But if I do this I will loose the entry in menu.lst that points to the new /home partition.

Hope I have made my problem clear

I am new to Linux, so have probably dug my own hole.  Any suggestions would be appreciated.

---

### Post by lha on 2007-08-07
Usually, menu.lst contains no reference to /home. File system information is kept in /etc/fstab.

It seems to me you need to reinstall grub so that grub uses menu.lst from your production system. Then, you can remove Ubuntus 2&3. Afterwards, your production Ubuntu should still use the /home partition it is using now.

I recommend you to look at your menu.lsts and fstabs to find out what settings can be adjusted within those files. You can find many threads on fstab and reinstalling grub in these forums.

---

