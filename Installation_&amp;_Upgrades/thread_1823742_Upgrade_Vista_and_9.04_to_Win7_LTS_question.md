---
title: "Upgrade Vista and 9.04 to Win7 LTS /question"
date: 2011-08-12
forum: Installation &amp; Upgrades
---

### Post by gyozu on 2011-08-12
I have gotten to the point where I want to upgrade a dual boot setup from Vista/9.04 to Win7/LTS or Natty. This is on a 64bit system.

The Win 7 upgrade will be done with upgrade discs from HP rather than a fresh install. With this setup, if I have to reinstall Win 7, I first have to restore Vista the redo the Win 7 upgrade.

I have backed up all my information to a separate HD.

I was just wondering if anyone knew if the Win 7 upgrade would install in the existing partition or would it go back to occupying the whole hard drive?

Also, I plan to do the Win 7 upgrade first then Ubuntu. Will I have trouble accessing the GRUB menu or will everything work after I install Ubuntu?

I am wondering what sort of reboot problems I might run into as Windows has to stop and restart a couple of times during the upgrade process.

---

### Post by gordintoronto on 2011-08-12
Once Win 7 is done, you can fresh install Natty into your Linux partition, and it will look after Grub.

This isn't a good place to get reliable answers about Windows. I *think* the Windows upgrade will stay within its partition, and it might wipe out Grub, but I'm not sure of either of those things.

While you are at it, I suggest you break your Linux partition into root and home, unless you are very tight for disk space.

---

### Post by JRV on 2011-08-12
I think the Windows upgrade will stay within its partition, and it **will** wipe out Grub.

It is best to do a fresh install instead of trying to upgrade Ubuntu.

Backup.

Install W7 first, then install Ubuntu 10.04.

---

### Post by Mark Phelps on 2011-08-14
> **gyozu said:**
> The Win 7 upgrade will be done with upgrade discs from HP rather than a fresh install. With this setup, if I have to reinstall Win 7, I first have to restore Vista the redo the Win 7 upgrade.
After you have done the Win7 upgrade, save yourself a lot of grief later and do the following:
1) Download and install the FREE version of Macrium Reflect (MR)
2) Use the MR option to create and burn a Linux Boot CD
3) Image off the Win7 partition to an external drive

NOW, if you have to restore Win7 down the road, you can do it directly -- without having to reinstall Vista and do the upgrade again.

Also, use the Win7 backup feature to create and burn a Win7 Repair CD.  That will come in handy later should you need to repair the Win7 Boot Loader.

> I was just wondering if anyone knew if the Win 7 upgrade would install in the existing partition or would it go back to occupying the whole hard drive?
When you go to do the upgrade, you should get a screen listing the existing partitions on your drive.  Just select the Vista partition -- and it will overwrite that one.

> I am wondering what sort of reboot problems I might run into as Windows has to stop and restart a couple of times during the upgrade process.

Good question -- and one for which I don't have an answer.  If GRUB is installed to your MBR now, it's possible that upon reboot, the Win7 upgrade will fail.

---

### Post by gyozu on 2011-08-15
Thank you for your advice. I plan to give everything a try this week. I will keep notes and return with my adventures.

---

