---
title: "dual boot ubuntu and vista seperate drives"
date: 2007-03-05
forum: Installation &amp; Upgrades
---

### Post by xegitalian19xx on 2007-03-05
Hello all,

I've been doing some google searching and some forum searching as well and haven't quite found what Im looking for.  I'd like to dual boot ubuntu and vista using two seperate drives.  I already have ubuntu installed on one drive and would not like to reformat it.  Is there any way i could do this.  running my games through wine just doesn't quite cut it.....any help is greatly appreciated.

thanks

---

### Post by saphil on 2007-03-06
Sadly the preferred order to load a dual-boot system is Windows-first.  I have not loaded Vista, but have dual-booted Win2K, 2K3 and XP with various Linuxes.  Since you are where you are, there is no easy way to get where you want to be exept to burn your /home/~ folder to a cd and start again.  Remember when you do the install of the Linux that you have to use manual partitioning.  If you just hit "next" 47 times, it will over-write your Windows installation.

---

### Post by confused57 on 2007-03-06
> **xegitalian19xx said:**
> Hello all,

I've been doing some google searching and some forum searching as well and haven't quite found what Im looking for.  I'd like to dual boot ubuntu and vista using two seperate drives.  I already have ubuntu installed on one drive and would not like to reformat it.  Is there any way i could do this.  running my games through wine just doesn't quite cut it.....any help is greatly appreciated.

thanks
You should have no problems setting up a dual boot this way:
[http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot](http://www.ubuntuforums.org/showthread.php?t=179902&highlight=dualboot)

You might want to read this link:
[http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx](http://www.commonmancomputing.com/y/Learn/DualBootVistaandLinux/tabid/62/Default.aspx)

---

### Post by rsambuca on 2007-03-06
Nah, you don't have to start over.  Just install Vista to your second drive, and then use the ubuntu liveCD to restore grub to the MBR.

---

