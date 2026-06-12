---
title: "Dual Boot help PLEASE"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by kubstix on 2007-01-19
I am trying to create a dual boot image for the programming class at our high school.  We just received new HP DC5700 (Yes its the dreaded 965 chipset.  80GB SATA Drive, SATA DVD DRIVE, Onboard Intel Video).  I have installed XP succesfully.   The partitions that are going to be created are a 25GB NTFS Partition for Windows, a 20GB Partition for the AM Class (NTFS), a 10GB Partition for the PM Class (NTFS), and that leaves a roughly 20-22GB left for Ubuntu.  I have all the partitions created for NTFS, and just a RAW partition available for Ubuntu.  First, I had to edit the kernel with (linux all-generic-ide pci=nommconf) otherwise im left with a frozen install (black screen with blinking cursor).  This command worked fine and initialized the install sequence.  I picked the freespace partition and let ubuntu do its thing with automatically creating the swap file partition, ect.  The install finished without a hitch and it detected the presence of XP and asked to install GRUB on the XP partition.  I agreed and that installed without a problem.  The reboot fully initialized GRUB without a problem, was able to successfully boot into XP without any problems.  However, when picking Ubuntu, it says Starting up .... and just hangs.  Ive let it go for a good 20 minutes and it seems thats where its staying.  Can someone help me out?  **ALSO**im first running this as a test system, so the only partitions are a 68GB NTFS partition and a 9GB Linux partition.  If i can get some help and get successfully booted.....then I will go ahead and redo with all the class partitions.  Thanks for help guys.

GRUB

Ubuntu Installation
root    (HD0,1)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/sda2 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot


XP Installation
root    (HD0,0)
savedefault
makeactive
chainloader +1

---

### Post by teust on 2007-01-19
Hi kubstix,  I'm having the exact same problem.  I think ubuntu is struggling with my hardware but no sure how to resolve it.  I tried these cheat codes but no joy, may be worth a shot for you though.  [http://www.knoppix.net/wiki/Cheat_Codes](http://www.knoppix.net/wiki/Cheat_Codes).  Please let me know if you have any success with getting it up and running.:)

---

### Post by kubstix on 2007-01-19
Are you also running the 965 intel chipset?  Im almost 100% positive the problem is related to the SATA drives....being the DVD/CD Drive as well.  I tried everything possible.  I know for a fact Fedora 6 works perfectly because of the newer kernel adding support.  But lets face it, Ubuntu is the best form of linux out there and I really want the kids using it.  Please feel free to post if you find a solution as well.  If i come across anything I will gladly send you a PM as well.

---

### Post by confused57 on 2007-01-19
> **kubstix said:**
> Are you also running the 965 intel chipset?  Im almost 100% positive the problem is related to the SATA drives....being the DVD/CD Drive as well.  I tried everything possible.  I know for a fact Fedora 6 works perfectly because of the newer kernel adding support.  But lets face it, Ubuntu is the best form of linux out there and I really want the kids using it.  Please feel free to post if you find a solution as well.  If i come across anything I will gladly send you a PM as well.

Maybe you could add the boot cheatcodes to your kernel line in grub...you can do this by highlighting the Ubuntu entry in the grub menu at boot, press "e" for edit and add the options to the kernel & try to boot...don't worry, this only temporary...if it works, then you can make the change permanent in your /boot/grub/menu.lst.

I did a forum search and someone had success with the boot option **irqpoll** on their i975.

---

### Post by kubstix on 2007-01-19
Wow, i just edited my GRUB kernel and I am now in Ubuntu.  Woohooo


BTW, I added GRUB commands to the kernel (linux all-generic-ide pci=nommconf) and it booted no problem.

---

### Post by confused57 on 2007-01-19
> **kubstix said:**
> Wow, i just edited my GRUB kernel and I am now in Ubuntu.  Woohooo


BTW, I added GRUB commands to the kernel (linux all-generic-ide pci=nommconf) and it booted no problem.

Great, I knew it "should" work...this could be a possible solution for anyone with the 965 chipset wanting to use Linux.

---

### Post by kubstix on 2007-01-19
This very well could be the solution for all users with 965 chipset trying to install Ubuntu.  There seems to be problems with the 965 chipset due to completely removing IDE controllers.  I also read my DVD drive and network probably wont be detected either.  Ubuntu seemed to detect both without a problem.  Thanks everyone for there help.  BTW this is the solution for regular installs as well, not just dual booting.

---

