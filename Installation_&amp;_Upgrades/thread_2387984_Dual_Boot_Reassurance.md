---
title: "Dual Boot Reassurance"
date: 2018-03-26
forum: Installation &amp; Upgrades
---

### Post by hudsonrecords on 2018-03-26
Hello, all.

I bought a new 1 TB laptop with Windows 10 and attempted to install Red Hat Linux (RHEL) on a 200 GB partition. Although I chose to partition manually,the install recommended sizes for each partition (/, /home, /boot, swap). Everything seemed to go well until I rebooted.  Windows was not included in the grub menu.  It's been a while since I had to look at a grub.conf file (now it's grub2.conf, I think) because my last couple of installs I let Linux have the entire hard drive.  At one point, I held the power button down for several seconds, to turn the computer off.  The screen went dark but the power button stayed on.  I press it several times but it wouldn't come back on.  I returned the laptop to Walmart and got another one (Lenovo IdeaPad 320).

I don't want to install any Linux distro unless I know for a fact that I'll be able to boot into either OS.  At this stage, I shouldn't even have to say this -- the Linux install should be smart enough to know that it's installing alongside Windows.  I have tried 3 more distros (Linux Mint, Kubuntu and Ubuntu) and I am not confident that I will have a dual boot laptop when I'm done with any of them.  I had high hopes for Ubuntu (I prefer Kubuntu because of KDE) because I saw a screenshot saying that it could be installed alongside another OS.  But then when I ran the install, at the disk setup screen, it said that no other operating system was detected.  If not, then it doesn't seem likely that it will produce a proper dual boot .conf file.  If anything, a preview of the .conf file or some other assurance that the PC will be dual boot would be great.

Is there something that needs to be done in order for the Ubuntu (or Kubuntu) install to be able to detect Windows 10?

Given the following sizes, what are the correct settings?: /boot 1024, swap 4096, / 51200 and /home whatever was left from the 200 GB.  I guess I'm most concerned about the boot partition.

Any help would be truly appreciated.

Steve

---

### Post by oldfred on 2018-03-26
There are several potential Windows issues that prevent the Linux NTFS driver from mounting & then seeing the NTFS partitions.
The most common with Windows 10 is fast start up.
       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

For general UEFI install steps see link in my signature below. Do not skip any steps. 

Redhat uses LVM which is a full drive erase & convert to volumes. Did you erase Windows when you installed.
If new user do not use LVM with Ubuntu as it also erases entire drive.
I do prefer to partition in advance, but you need to understand partitioning.
 
Some of the older Ideapads were difficult to install as they used 32 bit UEFI on 64 bit system.
Not sure if these are similar or not.

 Lenovo Y700 Ideapad Windows 10 & Ubuntu SSD & HDD
[http://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html](http://www.everydaylinuxuser.com/2016/05/how-to-dual-boot-ubuntu-and-windows-10.html)
Lenovo Legion Y520-15I  Installer does not detect SSD and HDD: Ubuntu 16.04 LTS
[https://ubuntuforums.org/showthread.php?t=2359208](https://ubuntuforums.org/showthread.php?t=2359208)
Lenovo 110s  Experience Installing and Using Linux on my Lenovo 110s UEFI settings better support than 100
[https://ubuntuforums.org/showthread.php?t=2350394](https://ubuntuforums.org/showthread.php?t=2350394)

---

### Post by kansasnoob on 2018-03-27
It looks like the Lenovo IdeaPad 320 comes with a wide variety of specs, but if it has at least a 2.4 GHz CPU and 8GB RAM I'd be inclined to recommend a virtual machine rather than a dual-boot. It would just be safer all the way around.

---

