---
title: "Uninstall Ubuntu on laptop and keep bootloader?"
date: 2005-08-07
forum: Installation &amp; Upgrades
---

### Post by wreckingcru on 2005-08-07
Hi,

I just got a test box from work to play with - so I want to use that as my primary linux box. I currently have a laptop with a dual boot winxp/ubuntu set up.

Obviously, the GRUB bootloader helps me decide what OS to pick right now. I have a 60 gb hdd that I partitioned 20 off for ubuntu. 

Now, I want to uninstall ubuntu and free up that space for my winXP side. I thought I could just use Partition Magic to kill off that partition and/or merge it with the other one.

But I'm wondering what happens to the bootloader? Since there is no more linux, there will be no more GRUB? Hence, how do I revert back to a direct boot up sequence into Windows without worrying about getting stuck at boot up without a boot record?

Or do I have this completely wrong? Does GRUB stll exist in the hardware even if i uninstall Ubuntu and continues to detect all available OSes?

Please help a semi-newbie. 
Thanks!

---

### Post by SqdnGuns on 2005-08-07
Wipe out the linux partitions then boot up to either a floppy or cd that has M$ fdisk on it then run fdisk /mbr

I may be forgetting something there,,,,,,,,,,Google is your friend and you'll get a quicker answer.

---

### Post by wreckingcru on 2005-08-08
Hmm, Interesting..
I guess what I wanna do - to be safe...is to restore the boot loader to only windows ...i.e., just like a regular windows load sequence, and then i can delete the linux partition...

Can I do that?

---

