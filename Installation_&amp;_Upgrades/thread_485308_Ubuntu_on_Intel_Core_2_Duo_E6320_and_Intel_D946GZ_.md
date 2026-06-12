---
title: "Ubuntu on Intel Core 2 Duo E6320 and Intel D946GZ motherboard"
date: 2007-06-26
forum: Installation &amp; Upgrades
---

### Post by mikkanu on 2007-06-26
I hve just built a new system with an Intel E6320 Core 2 Duo processor based on an Intel D946GZ (D946GZISSL to be more specific) motherboard. I've tried installing Ubuntu 6.06 LTS and Ubuntu 7.04 without much success. I've done some reading on the forum and although there were a couple of posts on the issue, none were very specific to my problem and all were rather old.

So far I'm quite in the same spot. Ubuntu 7.04 won't boot on my machine. The Live CD hangs at some point with sporadic error messages (which I can provide upon request).

I spoke with a representative from Intel about the issue and they basically told me to go $%#$ myself. I'd really like to get Ubuntu to work on my machine.

P.S. I've tried installing a raw debian distro and that worked (except it couldn't configure my NICs).

The system configuration:
 Intel D946GZISSL socket LG775 mother board
 Intel Core 2 Duo E6320 1.86Ghz processor,
 2 x 1Gb Dual Channel RAM, Patriot DDR2 667 modules
 On-board Intel-based video adapter
 1 on-board NIC
 1 Linksys NIC
 1 x SATA II newer generation WD 250Gb Hard-drive

.. i must mention, I have tried different CD-ROM/ DVD-ROM drives and different hard drives.


Please help. I'm also pretty new to the whole Linux experience although I have extensive experience with computers.

Thank you!!

---

### Post by dabl on 2007-06-26
Miky, Ubuntu Feisty should work on that system.

Here are some pointers:

1. Verify your new hardware is all functioning.  Use an old Win XP or Win95 CD or something that you are comfortable with, just install it quickly and confirm that the hard drive and video card are seen by the motherboard, the monitor works, you got sound, CD ROM drive works, RAM passes memtest 86, etc., just so we don't have to wonder if the hardware works.

2. Download the ISO image and burn a GParted live CD, from here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Boot the GParted live CD to partition your hard drive.  You need a 10GB "/", a 1.5GB /{swap}, and the rest of your drive for /home.  Set the bootable flag on the 10GB partition. You don't need to format them with GParted.

3. Download the ISO image and burn the Ubuntu 7.04 Alternate Install CD. It provides a better user-directed installation process.  Follow the prompts, set the 10GB partition to be mounted as "/", the 1.5GB partition to be the swap, and the big partition to be /home.  I like reiserfs filesystem format, but ext3 is actually more popular.  (swap is its own format).

4. Follow the installation instructions and you should come up with a Ubuntu system.  Any residual problems will probably be all about the video display, which can be resolved by searching the forum.

Good luck with it!  :D

Good luck with it!

---

### Post by mikkanu on 2007-06-27
Dabl, 

Thanks for the info.

I'll try that as soon as I get home from work. I have tried installing Debian on the machine, and I've tried IPCop last night. Both installations work to some extent. They couldn't configure the network interfaces. However, I've booted the system with a Knoppix Live CD and that worked fine + detected and configured my NICs properly.

I'll give it another shot with WinXP tonight and then I'm going to try to get the GParted and the Alternate install to see how those work.

Thanks a bunch!

---

