---
title: "Unable to access internet Ubuntu 10.04 LTS after motherboard upgrade"
date: 2013-04-06
forum: Installation &amp; Upgrades
---

### Post by wbool63 on 2013-04-06
Hi, I am not a dedicated or experienced Ubuntu  user. For some years I have had a split system with  xp, win 7 and ubuntu 10.04 lts.  I have recently upgraded my motherboard and cpu and now find that I cannot get on the internet with Ubuntu 10.04. Because I have spare drives and because I eventually will be a linux user for 80 % , I have also installed Fedora 18 on a spare disk to look at fedora as another linux option. I can get on the internet with all partitions and live disks except for ubuntu 10.04 ( my present ubuntu 10.04 disk partition and my old ubuntu live 10.04 live cd will not allow internet access). My new motherboard is an Asrock Z77 Fatal1ty Performance  with a Lan chip (broadcom BCM57781) 
As I have had no problems in the past with my ubuntu 10.04 connecting to the internet with my previous Gigabyte motherboard and my present win 7, win XP, Fedora 18 partition, and live ubuntu cds 11.10 and 10 can all connect to the internet, I assume that there is a incompatibility problem with this broadcom driver/chip and ubuntu 10.04. I have spent 3 days trying to sort this out but cannot find an answer. There is probably a simple solution somewhere but I failed to see or find it.

My question is , is there a convenient/ simple  way to save my personal files and preferences to dump into Ubuntu 12.04.2 LTS when I install that over my 10.04 LTS partition? Taking into account that this partition (10.04 LTS) cannot connect to the internet.

Cheers Wbool63

---

### Post by Doug S on 2013-04-06
It is possible that your 10.04 is still trying to use the old network interface. You could try to delete the file /etc/udev/rules.d/70-persistent-net.rules, and then re-boot. The file will automatically be re-created, but for whatever NICs you have now. (and by "delete" I really mean save it under some different name, for possibly restore later, in case something does not work as expected.)

I do not know the answer to the question you actually asked (I only use ubuntu server).

---

### Post by wbool63 on 2013-04-06
> **Doug S said:**
> It is possible that your 10.04 is still trying to use the old network interface. You could try to delete the file /etc/udev/rules.d/70-persistent-net.rules, and then re-boot. The file will automatically be re-created, but for whatever NICs you have now. (and by "delete" I really mean save it under some different name, for possibly restore later, in case something does not work as expected.)

I do not know the answer to the question you actually asked (I only use ubuntu server).

Doug, Thank You for your reply. I have not looked at that possibility. I did not see that in my searches. I will have to try that out.

---

### Post by wbool63 on 2013-04-07
Ok I give up, I got 12.04 to install over 10.04 but found that it would not recognise my nvidia 9800gt card so I could not get a usable screen above 1024X768 . I looked at many answers but none worked, I installed  11.10 which recognised my screen and was able to see all possible screen modes. Unfortunately it would not see my see second monitor. 
I had a nice working setup until I put in an  other motherboard and cpu. Everything worked , win7, Xp, ubuntu 10,04 and fedora 18 on different partititions.
I decide to upgrade ubuntu because I thought there appeared to be  a compatibility problem with my motherboard  (asrock Z77 Fatal1ty Performance). 
What really irks me is that the live CD's work perfectly but the installs do not. 
I have preferred Ubuntu over over distros for a few years before making a definite switch , but I am extremely disappointed with my recent ubuntu experience. 
Installing 12.04 LTS should be a piece of cake , but for some (me) it turns to a nightmare. 
My XP, Fedora18, win7 and all live cds (including live CD for12.04 lts)  recognise my nvidia  card and allow/configure  dual screen configurations.

---

### Post by oldfred on 2013-04-07
I have nVidia 9600GT and ever since 10.04, I have had to boot liveCD and first boot after install with nomodeset. Once I install nVidia driver, everything just works.

 Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for current version if 12.10 or 12.04.2:
sudo apt-get install linux-headers-generic
# only reason to purge is there are several versions, if you know you have different nVidia use that:
#To see available  versions:
dpkg -l | grep -i nvidia*
apt-cache search nvidia-sett*
# Houseclean out all old versions to avoid issues
sudo apt-get remove --purge < nvidiadriverpackagename>
 # [ using the correct names] for each driver, before running: 
sudo apt-get purge nvidia*
# I used nvidia-current-updates & nvidia-settings-updates, example below is just nvidia-current, use version you prefer
sudo apt-get install nvidia-current
sudo apt-get install nvidia-settings
sudo dpkg-reconfigure nvidia-current
sudo nvidia-xconfig
sudo reboot
May want nvidia-current, nvidia-current-updates or nvidia-current-experimental-XXX for most recent testing version.
apt-cache search nvidia-sett*

---

### Post by wbool63 on 2013-04-10
I could not get Ubuntu to work for me (even though the live CDs worked faultlessly). I installed Linux Mint, everything worked out of the box. Very impressed with LM Nadia.
Thank you for your advice. 
Cheers Wbool63

---

