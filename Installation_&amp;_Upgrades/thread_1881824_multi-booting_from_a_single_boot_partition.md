---
title: "multi-booting from a single boot partition"
date: 2011-11-16
forum: Installation &amp; Upgrades
---

### Post by Cyclane on 2011-11-16
Hi all,

Just a question from me. Here and there I've seen people multi-booting linux from one single boot partition. I was wondering how this is possible and how I would perform this? Google didn't give me anything useful.

---

### Post by Gatemaze on 2011-11-16
In brief you need multiple partitions on your hard drive. This topic has been published like a trillion times, search in forums and google for things like installing ubuntu along windows.

---

### Post by raja.genupula on 2011-11-16
2 ways 
1...by using virtual box we can run two OS's from one boot partition and we can access the other partition with out restarting the PC.
2...while installing ubuntu choose the option as install along with windows . from this multi-booting can be done from single boot partition but to switch OS we need to make restart.

---

### Post by Mark Phelps on 2011-11-16
> **Cyclane said:**
> Hi all,

Just a question from me. Here and there I've seen people multi-booting linux from one single boot partition. I was wondering how this is possible and how I would perform this? Google didn't give me anything useful.

You question is unclear ...

Are you trying to use a single boot partition to boot different Linux versions?

Or, are you trying to use a single boot partition to boot Linux AND boot Windows?

Because, if the latter is the case, the answer is NO.

Windows boot loader files must be stored in a Windows filesystem partition; they can not be stored in a Linux filesystem partition. 

GRUB is stored in the Linux filesystem but all it does for Windows is hand off boot to the partition identified in the GRUB configuration file.  It does not actually BOOT Windows; the Windows boot loader does that.

Furthermore, if you force the installation of Linux boot files into a Window 7 "boot" partition, you will "break" the Windows 7 boot -- as it then becomes confused due to the similarity of Linux and Windows directory and file names.

As to dual-boot between Linux and Windows 7, do NOT use the side-by-side, slider option offered in the Ubuntu installer. Doing so risks corrupting the Win7 OS partition and rendering it unbootable.

---

### Post by larrypg on 2011-11-16
Hello,

I am probably not understanding your question correctly but are you asking if you can use Ubuntu within Windows?  If that is the question then the answer is yes as a wubi install.

---

### Post by Cyclane on 2011-11-16
Wow I didn't think my question was that unclear.

First of all: I don't remember mentioning windows a single time. So let's make this clear my question doesn't have anything to do with windows.

I'll make it a little more specific. I have encountered the following situation multiple times, but now I'm wondering how it's possible. Let's say we have 3 partitions, all on the same HD 2 of them booting linux distros and 1 with the purpose of being mounted as /boot```

/dev/sda1    boot partition
/dev/sda2    Ubuntu
/dev/sda3    OpenSuse

```

I've seen people having a folder Ubuntu and a folder Opensuse within sda1 with the contents of /boot for each specific distro. And I've also seen 1 case where both distro's use sda1 in it's whole for both distro.

So my question: How is this possible and how would I do this?

---

### Post by Cyclane on 2011-11-17
So anyone knows how to do this?

---

### Post by oldfred on 2011-11-17
It is my understand /boot should never be shared. Too much chance of conflict. But you can do a /boot/grub only partition that is just grub2 from one distribution that gives a grub menu to boot from the boot folders in other partitions. kernels & boot files then are still with each install.

Herman has info on both grub & grub2 partitions
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition")
Chainbooting grub2, install to partition & Make CD or floppy - saikee
[http://www.justlinux.com/forum/showthread.php?threadid=152790](http://www.justlinux.com/forum/showthread.php?threadid=152790)
Herman on separate grub partition:
[http://ubuntuforums.org/showthread.php?t=1320270](http://ubuntuforums.org/showthread.php?t=1320270)

---

### Post by cwsnyder on 2011-11-17
What he said.  The only case where I have seen a partition table similar to the indicated is with a VERY small /dev/sda1 which just contains the boot sector and some GRUB files.  Even then the only partitions usually _shared_ is a swap partition and/or a /data partition.

---

### Post by Cyclane on 2011-11-17
Ahh ok that's what I thought and thus why I asked. Thank you for the information.

---

### Post by lswb on 2011-11-17
Something that worked well for me when I was playing with different distributions a few years ago was to install grub as oldfred suggests, but on a small partition with a gparted live or similar distribution. 4 or 5GB is plenty. Then on the other partitions with other distributions, install grub (or whatever boot loader they use) only on to that partition, On main boot-up grub menu-list, it is easy to install chainloader commands to the other distributions and partitions and set default to the one you use most often. A big advantage of a separate grub partition is that your separate distributions will only change their own partition's grub configuration when there's a kernel upgrade.

---

