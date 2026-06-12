---
title: "Partitioning Help - 7.10 Installer"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by TheSe7enthProphet on 2007-10-21
*See my second post. the question in this one has been answered!*

I'm attempting to install Ubuntu 7.10 on a secondary hard drive. I want to dual-boot it with Windows.

I have two hard drives in my computer, one that will be Windows-only and one that I want to Partition to give 30 GB to Ubuntu and 50 GB to Windows. Windows is on IDE:1 and I want Ubuntu on IDE:2.

There are files, such as my music and programs on the drive I want to put Ubuntu on that I do not want to lose. 

The installer for 7.10 does not have an option to autosize the partition, which is what I was told to use by support in the IRC channel. My options are to use the whole drive, use the largest continuous free space, or to do it manually. I get an error trying to use the largest continuous free space and cannot figure out how to use the manual partitioner.

My question:

Can I partition my secondary hard drive, saving the files that are on it already, into two sections so that I can install and dual-boot Ubuntu on it?

---

### Post by chewearn on 2007-10-21
Here is my suggestion (i.e. if I'm in the same situation, this is what I would do):

1. back-up, back-up
Back-up your data that you absolutely cannot loose.  Maybe 99% of the time, it will  go smoothly, but it's the 1% that will cause regret.
Also, back-up your Windows, if you think it's important.  E.g. if you have a laptop that is a big big hassle to restore Windows on, or you have a pre-installed Windows, but don't have an installation disc.

2. Defrag
In Windows, defrag your second HDD, moving all your data to the beginning of the disk.  You might need to repeat defrag a few times, to make sure all data moved to below 50GB of your disc.

3. Partition
Use a partition tool to resize your data partition on the second HDD to 50GB, leave the rest of the disk unpartitioned.  You can use a commercial partition tool (e.g. Partition Magic) if you have one.  My favorite is the free GParted LiveCD.

4. Install ubuntu
Choose the option: largest continuous free space.  Double check that the unpartition space of the second HDD is selected before confirming the installation to go ahead.

That's all. :)

---

### Post by TheSe7enthProphet on 2007-10-21
Thank you very much. That allowed me to install Ubutnu. However, I've ran into another, rather serious, kink.

I'm currently booting from the Ubuntu Live CD. I'm getting an error from GRUB. It is error 21. I've figured out that means that it cannot find the drive to boot from... But, all the guides I've found require a bit more know-how of the GRUB system. I really need an idiot's guide to GRUB to fix this. Would you, or anyone, know where I can find this? 

I don't get any other information. It says:

> GRUB Loading, please wait....
Error 21

---

### Post by TheSe7enthProphet on 2007-10-21
I apologize for the double-post.

Problem solved! I went out on a whim and changed a few system settings (based on the guide I found... or at leas the word "auto-detect") and got it to work.

Thanks again for the help, AstalaVista!

---

### Post by mikeescott on 2007-10-31
> **TheSe7enthProphet said:**
> I apologize for the double-post.

Problem solved! I went out on a whim and changed a few system settings (based on the guide I found... or at leas the word "auto-detect") and got it to work.

Thanks again for the help, AstalaVista!



What did you use to get this fixed?

---

