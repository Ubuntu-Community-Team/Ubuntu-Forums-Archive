---
title: "How to create a multiboot system with several OS?"
date: 2010-09-25
forum: Installation &amp; Upgrades
---

### Post by atti84it on 2010-09-25
Hello everybody! I've been looking for the answer both on the web and this forum but I couldn't find it; I hope you can help me.

How can I put Ubuntu, Encrypted Ubuntu (Luks + LVM), Backtrack and eventually WinXP on the same drive with a Grub2 as a bootloader?

I'm a bit confused about partitioning; I suppose that I need only **one** /boot partition to store the kernel of the encrypted Ubuntu, while the other distros will have their /boot within each partition, like this:
1) 500 Mb; /boot for the encrypted Ubuntu on partition #2
2) 10Gb; Luks + LVM Ubuntu
3) 10Gb; clear Ubuntu (whose /boot is in same partition #3)
4) 2Gb; Backtrack
5) [Win..]

In this case, will the update-grub command find and recognize correctly all the OSs or should I edit something in the "40_custom" file?

Thank you very much!!

---

### Post by atti84it on 2010-09-25
could anybody answer this? thanks!

---

### Post by uteck on 2010-09-26
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)
Section 6 talks about other OSs and adding entries, but here is the bit that intrestes you;

"When "update-grub" or "update-grub" is executed, Grub 2 will search for linux kernels and other Operating Systems. What and where is looks is based on the files contained in /etc/grub.d folder.
10_linux searches for installed linux kernels on the same partition.
30_os-prober Searches for Linux and OS's on other partitions and includes them in the menu."

But since the config files are in /etc of the 'primary' OS, if you run update-grub from another Linux, you may not see the results when you reboot, so you may need to boot into the main OS and run update-grub there.

Or so I think Grub2 works based on my limited work with it.

---

### Post by jagannathahm on 2010-09-26
> **atti84it said:**
> Hello everybody! I've been looking for the answer both on the web and this forum but I couldn't find it; I hope you can help me.

How can I put Ubuntu, Encrypted Ubuntu (Luks + LVM), Backtrack and eventually WinXP on the same drive with a Grub2 as a bootloader?

I'm a bit confused about partitioning; I suppose that I need only **one** /boot partition to store the kernel of the encrypted Ubuntu, while the other distros will have their /boot within each partition, like this:
1) 500 Mb; /boot for the encrypted Ubuntu on partition #2
2) 10Gb; Luks + LVM Ubuntu
3) 10Gb; clear Ubuntu (whose /boot is in same partition #3)
4) 2Gb; Backtrack
5) [Win..]

In this case, will the update-grub command find and recognize correctly all the OSs or should I edit something in the "40_custom" file?

Thank you very much!!
I use a boot loader called gag 4.10 This can be installed via floppy disk or cd and can handle 9 operating systems It is easy to use just follow on screen instructions

---

### Post by grahammechanical on 2010-09-26
I think it is correct to say that any Windows Operating system should be installed first.

A Ubuntu installation will create a GRUB menu and list the Operating Systems that it finds. I dual boot but not between Windows and Ubuntu so I cannot comment on that but I do find that the last Ubuntu OS installed is listed at the top of the menu. It is the same with kernel updates. The last OS to have its kernel updated will be place at he top of the GRUB Menu list. There is a way to customise this menu but GRUB2 is designed to make it very difficult for the user to mess things up.

Another point. At the moment only 4 primary partitions are allowed by GRUB. You would need to put some of these OSes in an Extended Partition.

I would suggest that you install Windows first, then install Ubuntu, create the partitions as part of the installation process. Then install the other OS giving each its mount point but not allowing the installation to format the other partitions.

I hope this helps a little bit.

Regards

---

### Post by atti84it on 2010-09-26
ok thanks everybody for answering me!

---

