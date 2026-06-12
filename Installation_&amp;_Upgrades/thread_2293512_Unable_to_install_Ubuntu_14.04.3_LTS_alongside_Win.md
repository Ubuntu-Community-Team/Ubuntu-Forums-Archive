---
title: "Unable to install Ubuntu 14.04.3 LTS alongside Windows Ultimate"
date: 2015-09-05
forum: Installation &amp; Upgrades
---

### Post by BhuvneshKapoor on 2015-09-05
Hi,

I am new to Ubuntu and wish to work on it so I am installing it for the first time. 
I am trying to install Ubuntu 14.04.3 LTS with USB drive, and i have kept aside 20GB (NTFS type) partition for it. Now when I reboot my system and select install ubuntu option after going through some steps (until configuration of wifi settings ), 'installation type' window follows there as per the instructions on the website i should see the option 'Install Ubuntu alongwith Windows' (and other options...), but i see install Ubuntu options and below it a warning is displayed which says that if i select this option then all my data and other OS will be erased. Through 'something else' option also I could not install Ubuntu on the seperate partition!

Can you please give the instructions that how can I install Ubuntu 14.04.3 LTS alongside Windows Ultimate, on a seperate partition of 20GB?

Warm Regards,
Bhuvnesh Kapoor

---

### Post by yancek on 2015-09-05
> I am trying to install Ubuntu 14.04.3 LTS with USB drive, and i have kept aside 20GB (NTFS type) partition for it. 

That's your problem.  That is a proprietary windows filesystem which only works for windows operating systems.  When the Ubuntu installer looks at the drives/partitions, it sees only windows partitions so the only option you will get is to Erase disk and install over windows.  Doing the opposite, trying to install a windows system on a partition with a Linux filesystem will have the same result.  Delete the partition you created for Ubuntu while you are booted into windows.  If you do this, you should see the Install Alongside option although you will actually be better selecting the manual (Something Else) option.  More control.

One other thing you neglected to mention is which windows.  Is it windows 8 or later?  That will make a difference as it will then probably be using UEFI to boot.

---

### Post by BhuvneshKapoor on 2015-09-06
Hi yancek,

Thanks for the reply.

I am using Windows 7 ultimate.
I tried with removing the partition and then installing Ubuntu again, but still I face the same problem. I have attached some screen shots.
Please let me know if i am not following the correct way of installing it or is their some other solution to this problem?

Thanks,
Bhuvnesh

---

### Post by yancek on 2015-09-06
If you select the 'free space' from the Installation Type window, you need to click on the + sign to the left/below the window to add it.  You will be given several options such as filesystem type (ext4) and Mount point which should be /, the forward slash being the symbol for the root of the filesystem.  Use the Something Else option.  If you still have problems, reading a tutorial such as the one below would help.  If you scroll down the page it has a step by step on dual-booting.

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

