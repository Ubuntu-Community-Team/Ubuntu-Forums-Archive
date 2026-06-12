---
title: "GRUB fails to install, fatal error @94%"
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by Ettery on 2007-12-11
I know a number of people have reported similar errors, but they have not had solutions, so I have attempted to collect as much info as I can.

I am installing Ubuntu 7.10 on a basic desktop, 3Ghz Intel P4, 1Gb RAM 2xHDD.  I boot into the live CD, then attempt the install from the desktop link.  

I have an existing Win XP installation which I want to keep.

**Here is my fdisk -l info (OS allocations indicated on the right):**

[FONT="Courier New"]
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfa17fa17

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         765     6144831    b  W95 FAT32			BOOT
/dev/sda2             766       14593   111073410    f  W95 Ext'd (LBA)	
/dev/sda5             766       13513   102398278+   7  HPFS/NTFS			Win XP
/dev/sda6           13514       14547     8305573+   e  W95 FAT16 (LBA)			Ubuntu /
/dev/sda7           14548       14593      369463+  82  Linux swap / Solaris		Ubuntu SWAP

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x4473f5ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       30401   244196001    7  HPFS/NTFS
[/FONT]
  
**Here is my (manual) partitioner setup:**

[IMG]http://bp2.blogger.com/_cUdfETl4GxM/R17uygiAL7I/AAAAAAAAAA4/WGWD_fHDkKk/s1600/ubuntu-partition-Install.png[/IMG]

**and here is what the Installer said before formatting:**

[IMG]http://bp1.blogger.com/_cUdfETl4GxM/R17u9QiAL8I/AAAAAAAAABA/TGlPNErTl0k/s1600/Screenshot-Install2.png[/IMG]



Then at 94% the header was "Installing GRUB boot loader" and the action "Running "grub-install (hd0)"...


Then the dreaded: "Executing grub-install (hd0) failed."  "This is a fatal error."

And with that the install dies and I am shunted back into the running Ubuntu live.

Please HELP!  I've love to be running Ubuntu, but always seem to have problems.

---

### Post by Pumalite on 2007-12-11
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Ettery on 2007-12-11
Hi Pumalite -

Thanks for the response.  I've looked through the links you've posted, and as far as I can see I have followed the dual-boot install guides to the letter.  A couple of questions:

1) Can you see anything wrong with the install details I have posted?
2) If I attempt to manually install GRUB now, will UBUNTU work, given that the install failed at 94%?

What I really need is for someone to look at the details and say: hey, your config is wrong in <such and such> - fix it like this.

Thanks...

---

### Post by Pumalite on 2007-12-11
Hello Ettery:
It call my attention your formatting. Linux has a learning curve like all OS's. One has to read experiment and learn. I gave you the best links in the matter at hand. Of course you have to make sure you have a good iso to start with and that you have the right hardware. It might turn out that you need some boot parameters (I don't know that yet). Your specs would help too. I think if you press 'Esc' during the process, you can see where Ubuntu gets stuck. That would help too.

---

