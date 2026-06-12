---
title: "upgrading from 12.10 to 14.04 and adding SSD"
date: 2014-12-31
forum: Installation &amp; Upgrades
---

### Post by fiestaMojo on 2014-12-31
I have an old Gateway with a Core Duo 2 that i am running Ubuntu 12.10 on. My hard drive is showing signs of old age, and I want to replace it before it dies; I figure this is a good time to move up to 14.04. I also have a 120 Gb SSD I want to install - I'd like to configure the system so that the operating system (kernel?) is on the SSD, and data is on the hard drive. Is this possible? If so, what is the best way to do this? I'm not really a newbie when it comes to PCs, I have been adding to the PC a bit, but I'm a novice when it comes to Linux. . . any help/advice will be greatly appreciated. . .

---

### Post by oldfred on 2014-12-31
Will it be Ubuntu only, or will you also have Windows?

I did exactly that with my 2006 build with a Core2 Duo and a hard drive and newer video card in 2009. In 2012 I added small 64GB SSD. I made it have 2 / (root) partitions and had 12.04 on one, and another Ubuntu on the other for testing. But I had all data on my hard drive, so I could have smaller / partitions.

Will you be keeping a hard drive for data or just the SSD?

I find with data on hard drive a 25GB / partition is all I need, and I only use about 11GB of that. I then have a larger data partition on hard drive and link the standard folders like Documents, Music, Videos etc back to /home. 

That is a bit more advanced and a simpler solution is just to install / on SSD and /home on hard drive.
I might leave some room on SSD and backup some of your most critical data from hard drive to SSD and copy system configuration data from SSD to hard drive. But I do not consider that your only backup as you should have data copied to external drives, DVDs, flash drives etc. I use all of them for at least some data. :)

If not installing Windows, I suggest gpt partitioning, but it is not required. No issues of primary nor logical partitions. Other mostly minor advantages.
       GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

With two drives you do have to plan your partitions, and use Something Else. I prefer to partition in advance with gparted as I think it is a bit easier, but you still have to use Something Else.

      
 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)


 Any install with Something Else which is required with  external drives or any second drive or any install with separate /home
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, if external drive, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-optiond)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)

---

### Post by Dennis N on 2014-12-31
Yes, before or during installation, create your root partition on the SSD, and a separate home partition on the HDD. If you dual boot, you can also make a separate data parttion for storing and accessing your data files for use by all the OSes (such as your music files), avoiding duplication. 

Another option would be to just install the OS to the SSD (including home partition) and then make a separate data partition on the HDD.

---

### Post by fiestaMojo on 2014-12-31
Thanks for the replies. . . I will only be installing Ubuntu 14.04. . . the SSD and new hard drive (1 Tb) will be unformatted (?) when i install them - will I have problems installing Ubuntu onto the SSD? thanks again. . .

---

### Post by oldfred on 2015-01-02
Should not have issues, but some hardware has unique issues.

I prefer formatting in advance as I like to plan partitions on both drives. But if you follow examples posted above it should just install.

---

### Post by fiestaMojo on 2015-01-26
i installed the SSD and HD this weekend (had to repair clothes dryer first - happy wife, happy life!). hardware install went well. booted into Live session, used gpted to create \ and bios boot partitions on sda (SSD) and \home and swap partitions on sdb; attempted to install 14.04.1 - installation seemed to have gone OK, but when i restarted after being prompted to remove the installation disk, it wouldn't boot - got message that Intel boot agent (v 1.2.42) PXE no boot device found? (i'm at work right now trying to recall the exact wording) help!

---

### Post by tokyobadger on 2015-01-26
check boot priority in BIOS - HDD/SSD don't seem to be detected and so the system is skipping to a network boot scenario

---

### Post by oldfred on 2015-01-26
We can confirm boot loader is installed correctly:
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Or as tokyobadger points out the network boot or PXE is first or next default in BIOS.

---

### Post by fiestaMojo on 2015-01-27
i attempted to perform the boot-info test, but i got the message "cannot add PPA: 'ppa:yannubuntu/boot-repair'. Please check that the PPA name or format is correct." after i enter the first command on the Boot-Info wiki page. .  . maybe the iso image for the Live disk is corrupted? thanks for the help. . .

---

### Post by oldfred on 2015-01-27
If you are trying to run Boot-Repair from anything that is not a current version of Ubuntu, it will not work. Or you cannot run it from your 12.10, but need to then use the 14.04 live installer.

---

### Post by fiestaMojo on 2015-02-07
I am attempting to get Boot-Info running from the 14.04 Live installation cd. . . I went into the BIOS while booting - the boot order seems right, CD/DVD -> HDD -> floppy -> USB -> network, it seems the does not see the boot loader on the SSD. . .

---

### Post by oldfred on 2015-02-07
Is Ubuntu on a DVD or will system boot from a flash drive?

---

### Post by fiestaMojo on 2015-02-08
Dvd

---

### Post by oldfred on 2015-02-08
What tools did you use to create DVD, you cannot just copy ISO or extract ISO yourself to DVD, but must use an installer to have it be a bootable DVD.

       Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Most find a flash drive to be easier & faster booting. It also then is reusable. I used to burn a lot of coasters (bad burns so only use was as a coaster).

---

### Post by fiestaMojo on 2015-02-08
I downloaded the installation file from the Ubuntu site onto a laptop running Windows 7, then burned the DVD. . . I used it to install, and it ran fine - the installation completed. . .

---

### Post by oldfred on 2015-02-08
If it installed fine, then it should boot. But something is not correct if it does not boot.
And we really need the Summary report from Boot-Repair to see what the issue may be.

You should be able to use the 14.04 live installer to add Boot-Repair and run Summary report. Boot-Repair did not work on 12.10 or any version that is not current.

---

### Post by fiestaMojo on 2015-02-08
not sure what this means, I booted into Ubuntu with the Live disk (Try Ubuntu) and once it loaded, i opened gParted & looked at the ssd  (/dev/sda) - /dev/sda1, which i made / during installation, showed as an ext4 partition, but /dev/sda2, which i set the bios_grub flag during installation, showed as unknown with a warning exclamation point to the left. . . thanks for the continued help

---

### Post by oldfred on 2015-02-09
Bios_grub & Windows system reserved are unformatted partitions, so both will show error flags in gparted or other tools. 

Since they are flagged & correct gparted should really not be showing an error.

---

### Post by fiestaMojo on 2015-02-15
after some experimentation i have 14.04 installed, albeit not as planned. . .  i disconnected the HDD and installed 14.04 on the SSD, then once i confirmed things seemed to be working, i re-connected the HDD - it"s working. . . is there a way at this point i can make the partitions on the HDD /home folders? as always, thanks for helping all. . .

---

### Post by oldfred on 2015-02-15
You can move /home.
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

But I prefer to have a /mnt/data partition for all the data folders like Documents, Music, Videos etc as folders in my data partition and link those folders back into /home. Then system sees them in "normal" locations, but they really are in another partition. A bit more advances as you have to manually set ownership & permissions and add a permanent mount into fstab.

      
 Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

---

### Post by fiestaMojo on 2015-02-21
thanks oldfred for all the help, guess this puts me in the next chapter of my Ubuntu learning - time to mark this thred solved, and begin exploring. . .

---

