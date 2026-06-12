---
title: "Error 8: Kernel must be loaded before booting"
date: 2013-01-05
forum: Installation &amp; Upgrades
---

### Post by highrun on 2013-01-05
So I dual booted Ubuntu 12.04.1 LTS x64 with my Windows 7 laptop. I have  it burned to a dvd, so I booted the CD, selected to try Ubuntu, then  installed inside the "trial" environment. I installed the boot partition  as sda6 as /boot, then my root partition was sda7 as /, I made another  partition for my home on sda8 as /home. I then made a 4gb swap  partition. I did NOT allow it to update, but even when I did allow it to  update, the same issue occured. I have another NTFS partition as use as  my media partition which is why my boot partition does not start as  sda5.
Any suggestions, ideas, comments? I'm practically ignorant of Linux, so  y'all will have to greatly simplify any suggestions. Thanks in advance!

I should also say how I got to this screen. I went to the windows  side and set up the boot screen to "see" the Ubuntu boot partition using  easyBCD.
I then tried to boot to the partition which came up to a command prompt  like screen with grub. I typed "boot" and this error message is what  occurred.

---

### Post by oldfred on 2013-01-05
I do not know about EasyBCD and that complicates it. EasyBCD uses grub4dos as the boot loader, since Windows does not multi-boot other systems.

A few have reported EasyBCD does work, but you may have to fix grub on major updates as it forces grub into a partition which grub does not like.
       [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

    
Or you can use Boot-Repair to install grub2's boot loader to the MBR. Since you have a separate /boot be sure to check that box also. You can run from your liveCD or download a full repair ISO.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by highrun on 2013-01-05
I'll try the boot repair using the live CD. I tried to reinstall under the suggestion to allow Ubuntu to do the partitioning using the "install alongside windows 7" option. It just made two partitions. The Linux partition and the swap. Same problem and I used the same easyBCD process.

---

### Post by highrun on 2013-01-05
Success! I am now able to boot into Ubuntu. Instead of the Windows boot loader thought, the Ubuntu boot loader comes first. I'm not altogether against that. It is greatly more aesthetically pleasing; however, I have heard that sometimes a windows antivirus program will try to write to the boot partition and that can mess grub up. Is that true? If so, what can I do to stop that or fix it if it does?

Here is the link it generated while repairing: [http://paste.ubuntu.com/1500562/](http://paste.ubuntu.com/1500562/)

Thanks you so Much!

---

### Post by oldfred on 2013-01-05
Most of the issues with DRM or over agressive virus checkers have been worked around. But it pays to have  a live CD/DVD/Flash for the current version of every operating system installed including a Windows repairCD.

And knowing how to run Boot-Repair often simplifies repairs or creates the BootInfo report so we can suggest fixes.

---

### Post by highrun on 2013-01-06
Okay Thanks :)! I'll keep those discs handy. Appreciate all the help :)

---

