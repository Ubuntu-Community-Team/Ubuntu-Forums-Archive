---
title: "The disk drive for /home is not ready or not present"
date: 2013-11-26
forum: Installation &amp; Upgrades
---

### Post by Dáire Fagan on 2013-11-26
Hi

Until recently Ubuntu had been working fine, which I dual boot with working Windows 8 on the same HDD. I have not knowingly changed any of the partition settings unless Windows has somehow although Ubuntu has definitely worked for some time since I initially set up the dual boot.

I found previous threads on the same topic where the original poster was asked to paste the output of fdisk -l and /etc/fstab. Not knowing how to copy text from recovery I took pictures, please see them below and advise:

[IMG]http://s17.postimg.org/bhsv3zfbj/20131126_122410.jpg[/IMG]

[IMG]http://s21.postimg.org/ys4mts17r/20131126_123218.jpg[/IMG]

---

### Post by oldfred on 2013-11-26
You can just copy & paste terminal output. Best if longer to use code tags.
       Code tags
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

fdisk works for MBR but not gpt partitioned drives. 
You need to use parted or gdisk. Gdisk is the fdisk for gpt partitioned drives, but usually is not installed by default.
sudo apt-get install gdisk
      
 sudo parted -l

 sudo gdisk -l /dev/sda

 sudo gdisk -l /dev/sdb

With the 24GB drive is that a SSD and system is an Ultrabook with Intel SRT?
      
  Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)


 GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

---

### Post by Dáire Fagan on 2014-01-14
Firstly, sorry for the late reply.

> **oldfred said:**
> You can just copy & paste terminal output. Best if longer to use code tags.
       Code tags
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

I can use code tags, but I am not sure how to copy and paste when I am logged into a recovery console. I am unable to login normally, unless I log in as guest.

> **oldfred said:**
> fdisk works for MBR but not gpt partitioned drives. 
You need to use parted or gdisk. Gdisk is the fdisk for gpt partitioned drives, but usually is not installed by default.
sudo apt-get install gdisk
      
 sudo parted -l

[IMG]http://oi44.tinypic.com/35butth.jpg[/IMG]

 > **oldfred said:**
> sudo gdisk -l /dev/sda

 sudo gdisk -l /dev/sdb

It is not installed and I am not sure how to connect to the WLAN from the command line (if necessary?).

> **oldfred said:**
> With the 24GB drive is that a SSD and system is an Ultrabook with Intel SRT?

Yes it is, and before some months ago I had it all working dual booting Windows 8 with Ubuntu, the 24GB properly functioning for IRST (Intel Rapid Storage Technology) - confirmed functioning with expresscache. 
      
Something small has obviously changed, considering it was all working, any thoughts? Please advise on the way forward.

---

### Post by oldfred on 2014-01-14
I think I need lots of detail.Boot from live installer and install Boot-Repair and post link.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

I only see one ext4 partition, so mounting /home should not be an issue. But some of your screen shots showed sda7 as /home originally. And sda7 is now NTFS which cannot be /home as NTFS does not support Linux ownership & permissions.

---

### Post by Dáire Fagan on 2014-01-15
> **oldfred said:**
> I think I need lots of detail.Boot from live installer and install Boot-Repair and post link.

       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

I only see one ext4 partition, so mounting /home should not be an issue. But some of your screen shots showed sda7 as /home originally. And sda7 is now NTFS which cannot be /home as NTFS does not support Linux ownership & permissions.

Thanks for the quick reply, here's mine:
[URL="http://paste.ubuntu.com/6756731/"]
[http://paste.ubuntu.com/6756731/](http://paste.ubuntu.com/6756731/) [/URL]

---

### Post by oldfred on 2014-01-15
You reformatted your /home to NTFS.

Current partition sda7
 /dev/sda7        BECEB44ECEB3FD29                       ntfs     


# /home was on /dev/sda7 during installation
UUID=c3784ee9-b776-4afd-a954-e3804235e5c0 /home           ext4    defaults        0       2

You have no partition with the UUID of /home.

---

### Post by Dáire Fagan on 2014-01-15
> **oldfred said:**
> You reformatted your /home to NTFS.

Current partition sda7
 /dev/sda7        BECEB44ECEB3FD29                       ntfs     


# /home was on /dev/sda7 during installation
UUID=c3784ee9-b776-4afd-a954-e3804235e5c0 /home           ext4    defaults        0       2

You have no partition with the UUID of /home.

Ouch. The main docs I wanted from it before reinstalling are in the cloud, I just wanted to check if there were any others. Thanks for your help.

---

