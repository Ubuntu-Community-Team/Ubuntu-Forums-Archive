---
title: "Dual Booting Ubuntu with Windows XP"
date: 2010-09-02
forum: Installation &amp; Upgrades
---

### Post by JackSkellington87 on 2010-09-02
I want to try out Ubuntu since a friend let me play around with the OS and I liked it, but when I searched the web about dual-booting, I saw that there could be a risk partitioning memory for Ubuntu. My friend says that I need at least 30 gigs to run Ubuntu, but when I put the installation disc, it said that my hard drive only has 10 gigs available, since the rest is taken up by Windows XP. I was wondering if someone could give me advice on partitioning the hard drive for Ubuntu. I also found what is called Wubi that is like a program that you can install and uninstall on XP. I was also wondering if this is a good idea as well? Thanks for helping out a Ubuntu newbie

---

### Post by JackSkellington87 on 2010-09-02
bump

---

### Post by wilee-nilee on 2010-09-02
On the Ubuntu live cd is a partition manager named gparted take a screenshot of it and post it. Use the Ubuntu cd in a booted form for this.

---

### Post by garvinrick4 on 2010-09-02
> **JackSkellington87 said:**
> I want to try out Ubuntu since a friend let me play around with the OS and I liked it, but when I searched the web about dual-booting, I saw that there could be a risk partitioning memory for Ubuntu. My friend says that I need at least 30 gigs to run Ubuntu, but when I put the installation disc, it said that my hard drive only has 10 gigs available, since the rest is taken up by Windows XP. I was wondering if someone could give me advice on partitioning the hard drive for Ubuntu. I also found what is called Wubi that is like a program that you can install and uninstall on XP. I was also wondering if this is a good idea as well? Thanks for helping out a Ubuntu newbie It takes about 4 to 5 gig for the complete OS with all packages installed to make a nice system. Any other would be for personal files. You do not want to fill your drive up with nothing left over. If you have less than 2 gigs of RAM you need to have a swap partition of 1 or 2 gig for memory. Awful tight with 10 gig left on drive.
 WUBI is a install that is a folder in C; drive in Windows that works fine for trying out Ubuntu and uses Windows boot manager. But again 10 gig would use the whole drive.
Maybe download ubuntu and burn a CD. Boot off of CD and choose try ubuntu not install and use package "startup disk creator and make a 4 gig USB flash drive to use to learn Ubuntu. If you like it get a USB external drive and install Ubuntu there. 
 If you decide to put on your XP drive in a partition defrag XP a couple of times first then install and on page 8 of install put grub or boot manager in sda not any other place. If WUBI just put in CD and choose WUBI install and follow instructions.

---

