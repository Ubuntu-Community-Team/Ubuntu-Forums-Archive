---
title: "Need help dual-booting Windows and Ubuntu"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Popple3 on 2007-10-21
I want to install Ubuntu 7.10 on my laptop alongside Vista. I have dual-booted XP and 6.06 on my old computer, however I have encountered a problem on my laptop.

My laptop has one hard drive (as you'd expect) but already has 3 partitions on it. The Vista boot partition, a system recovery partition (which I dont want to lose) and a data partition (which I cant delete because of Acer's recovery system... Or so I've read anyway!)
Ubuntu (6.06 anyway) needed two partitions (a boot partition and a swap partition) and hard drives are limited to 4 partitions, while I need 5.
Is there a way around this?

---

### Post by logos34 on 2007-10-21
Shrink your vista boot/system partition or data using vista's disk mgmt tool, then create an **extended** partition out of the freed up space.  Install ubuntu / and /swap inside as logical partitions.

[http://tldp.org/HOWTO/Partition/partition-types.html#types](http://tldp.org/HOWTO/Partition/partition-types.html#types)

---

### Post by Popple3 on 2007-10-21
Thanks a million!
Just one more question.....
I only have a 6.06 CD at the moment, and I don't have broadband. My friend is burning 7.10 for me and I should have it soon. If I install 6.06 now, is it easy to upgrade with the 7.10 CD later, or would it make more sense to just wait and do a clean install of 7.10 when I get it?

---

### Post by 4Foot on 2007-10-21
I think you will find that you need to be using 7.04 to upgrade to 7.10. Although I assume that a fresh install of 7.10 over 6.6 will be OK.

Good luck with that.

4Foot

---

### Post by Popple3 on 2007-10-21
I kinda realised that after I posted. :roll:
I'll just wait then, probably the easiest way.
Thanks!

---

### Post by Sef on 2007-10-21
> I think you will find that you need to be using 7.04 to upgrade to 7.10. Although I assume that a fresh install of 7.10 over 6.6 will be OK.

Both are correct.

Note: Hardy Heron, 8.04, will be an LTS (Long Term Stable). and there are rumors that you can upgrade directly from Dapper Drake, 6.06 to Heron.

---

### Post by Popple3 on 2007-10-21
Sorry to be a pain in the ***, but I've just stumbled upon something interesting. Rather than install GRUB on the MBR I'd like to install it on the Ubuntu partition and then use EasyBSD to add it to Windows' bootloader.
I know you need an alternate text-based install CD to do this.
Basically what I want to know is, is the alternate CD relatively easy to install with?
I'm not very experienced at Ubuntu (or any Linux distro) so a tutorial would be very useful.

---

### Post by logos34 on 2007-10-21
actually you can use the live cd to do that -- when you come to the '[Ready to install']("http://img519.imageshack.us/my.php?image=feistydual18cv5.png") screen click on the 'Advanced' button lower right and change the grub location to '(hd0,x)', where x=linux root partition #.  Or use '/dev/sdax' format.

---

### Post by Popple3 on 2007-10-21
Wel that makes it much easier! :D
Thanks for your great help!
So, just be sure:
1) Shrink my data partition
2) Create a new Extended partition
3) Create Logical partitions for / and /swap
4) On the "Ready to install" screen click advanced and set the location to the Ubuntu root partition
5) Install
6) Boot into Vista
7) Use EasyBSD to add Ubuntu to the Vista bootloader
8) Reboot and select Ubuntu
9) In GRUB select Ubuntu
10) It boots into Ubuntu

This all right, yeah?

---

### Post by logos34 on 2007-10-21
yep, that's it.  

Just remember that grub starts counting at 0, so if your ubuntu root partition is logical partition sda6, for instance, you would use '(hd0,5)'.  Or '/dev/sda6'.  

more on grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)

---

### Post by Popple3 on 2007-10-23
I got an Ubuntu 7.10 disc today, went to install it, but then got stumped when I got to step 4 of the installation
[IMG]http://i119.photobucket.com/albums/o142/Popple3/install.png[/IMG]
When I click forward, it comes up saying that I haven't defined a partition for the root, but there is no option to do this. Help..... Please...

---

### Post by logos34 on 2007-10-24
> **Popple3 said:**
> I got an Ubuntu 7.10 disc today, went to install it, but then got stumped when I got to step 4 of the installation

When I click forward, it comes up saying that I haven't defined a partition for the root, but there is no option to do this

Click 'Edit Partition' button and change mount point for sda5  to '/'

---

