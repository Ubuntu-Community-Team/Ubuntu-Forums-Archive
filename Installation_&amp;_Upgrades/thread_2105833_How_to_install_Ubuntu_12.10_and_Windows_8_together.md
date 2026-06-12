---
title: "How to install Ubuntu 12.10 and Windows 8 together"
date: 2013-01-17
forum: Installation &amp; Upgrades
---

### Post by redthule on 2013-01-17
Hi everyone!
 
I've got problems with the installation!
 
At moment I have a new laptop, and windows 8 already installed.
I'd like to install Ubuntu but I want Windows as well because it is the original version.
 
The problem is that I have only one partition that is the root for windows8,
Can I get some space from the HDD ie 100GB where to install Ubuntu?
Do you know some software that I could use to do this?
 
It seems that on Italian Ubuntu website nobody knows how to tackle with this problem, I think it is very important, because a lots of people that buy a new computer with windows won't use Ubuntu for this reason, I'v already tried to use a virtual machine like virtualbox but it is too too slow... 
 
 
Please help me or help us!
 
Thanks!

---

### Post by Warren Hill on 2013-01-17
Take a look here
[http://askubuntu.com/questions/227817/installing-ubuntu-with-windows-8](http://askubuntu.com/questions/227817/installing-ubuntu-with-windows-8)

Ubuntu will happily install alongside Windows.  The only concern is secure boot.  Make sure you know how to disable it.  It should not be necessary with 12.10 but I have not tried it.  It is necessary for 12.04 and earlier.

If you read all of the install screens carefully it gives you the option to repartition your drive so you can have both.

---

### Post by redthule on 2013-01-17
I've read, but that is the normal procedure, the problem is that if I have one partition I cannot split it into two parts, If I create a new partition table I will lose all my partitions, if I try to reduce my primary partition by using windows it tells me that is not possible. 
If I do this during the installation the wizard tells me that I will lose all previous partition... it is very strange... 
Anyway I can try to do this again ... I'll restart and try to install again...

---

### Post by grahammechanical on 2013-01-17
There are many posts here on this forum that deal with Windows 8, secure boot, UEFI and installing Ubuntu.

It would be wise to read through them as there is advice from knowledgeable members of this forum.

From my reading of these threads I see that you must

1) Defragment Windows from Windows
2) Create space using Windows utilities
3) Make sure that Windows is booting correctly. May be defrag Windows several times and boot Windows several times.
4) Switch off Fast boot.

Do things like this first before trying to install Ubuntu.

I wonder if you have dynamic disks. This is a Microsoft method for allowing more than one partition but it cannot be read by Linux utilities.

[https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI")

[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1077565]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1077565")

If i was going to do this I would use Ubuntu Secure Remix - make sure it is the 12.10 version. In this way you will have some tools that will be useful for fixing things if it goes wrong. At the moment, 12.10 is the only Ubuntu version that has a kernel signed by a Microsoft approved key. This will make it possible for Ubuntu to install on a secure boot enabled machine.

[https://help.ubuntu.com/community/UbuntuSecureRemix]("https://help.ubuntu.com/community/UbuntuSecureRemix")

[http://sourceforge.net/projects/ubuntu-secured/]("http://sourceforge.net/projects/ubuntu-secured/")

Regards.

---

### Post by oldfred on 2013-01-17
If you have Windows 8 pre-installed it will be secure boot and gpt partitioning. With gpt there is no limit like MBR on the number of primary partitions. Only if Windows converted to dynamic would you have issues.

Post this from Ubuntu liveCD/DVD/Flash.

       sudo parted /dev/sda unit s print
    
If you paste & then highlight like copy again, and click on # in edit panel above message, it will add code tags which preserves formatting.

---

