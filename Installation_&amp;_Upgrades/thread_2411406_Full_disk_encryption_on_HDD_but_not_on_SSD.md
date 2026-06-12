---
title: "Full disk encryption on HDD but not on SSD"
date: 2019-01-30
forum: Installation &amp; Upgrades
---

### Post by SBTlauien on 2019-01-30
I have a laptop that has Windows installed on the SSD.  I'd like to install Ubuntu on the HDD that I put in the laptop but I'd like it fully encrypted.

When installing, I have the option to encrypt the drive but it doesn't ask me what drive I'd like to install it onto and I don't want to erase Windows on the SSD.  When I choose the "Something else" option, I do not get the option to fully encrypt the drive.

Will I have to physically detach the SSD, install with encryption, and then reattach the SSD?

---

### Post by kashioz on 2019-01-30
Please note that I do not have expirience with this. Few things which I know I just read from searching about it.


As I understand, some disk encryptions are vulnerable because, for example, it can be still accessed by cold boot attack. Thats just one method which I read about while searching. Who knows how much more of them is there.


So, is there any encription that protects against all of that possible attacks? From ANYONE, not just mid-ranged hacker or my girlfriend trying to break to desktop :D , but even expert with forensic knoweledge and equipment.


That would require strong encryption method, and absence of vulnerabilities like that one mentioned above, and similar.


If there is not ideal solution, that just suggest me the best one out there (which would make attacker's life as harder as possible).


Also, is there one with, or is there a way to implement it, feature like some lockdown, to erase all or make disk unusable permanetly, after some failed password attempts. To protect against brute force attack.


tnx!

---

### Post by oldfred on 2019-01-30
You should be able to turn off drive in UEFI, so you do not have to physically disconnect.

I do not use LVM and full drive encryption. And do not recommend LVM unless somewhat knowledgeable on Linux or must have encryption. But you are jumping into the deep end of the pool, so best to know how to swim.

       Full-system encryption with manual control and dual-booting Paddy Landau
[URL="https://ubuntuforums.org/showthread.php?t=2357627"]https://ubuntuforums.org/showthread.php?t=2357627
      [/URL]
 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)
[https://www.howtoforge.com/linux_lvm](https://www.howtoforge.com/linux_lvm)
[https://linuxconfig.org/linux-lvm-logical-volume-manager](https://linuxconfig.org/linux-lvm-logical-volume-manager) 
    [URL="https://ubuntuforums.org/showthread.php?t=2357627"]
[/URL]

---

