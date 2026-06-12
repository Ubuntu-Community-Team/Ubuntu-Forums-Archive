---
title: "Best way to upgrade ubuntu 16.04 to kubuntu 18.04"
date: 2018-05-16
forum: Installation &amp; Upgrades
---

### Post by ricardosilva on 2018-05-16
Hi!
I apologise if this question is repeated, but I was not able to find it.
I have a laptop running Ubuntu 16.04 LTS (Unity as by default), and I would like to try Kubuntu 18.04 LTS.
Should I first upgrade to 18.04 and then switch desktop to Kubuntu, or is it better to switch to Kubuntu 16.04 and afterwards do the upgrade?
The machine is my second laptop, so if I screw up it is not the end of the world, but still, I would like to do it the proper way. 
I never really tried any of the flavour distros: the only previous experience I had testing other DEs was when I first discovered I could install other DEs. I was naive and had 5 installed just to check them out before I messed up my system. After that I painfully tried to remove everything else and stick to gnome, and never played with DEs again. But that was on my main laptop, the machine I am trying to upgrade has Unity by default, and I have never messed it up.
Thank you for your help.

---

### Post by wildmanne39 on 2018-05-16
My recommendation is to back up your important files since you want to go from ubuntu to kubuntu then do a fresh install of kubuntu, you will have a much cleaner system that way and the install process will be a lot quicker then upgrading.

---

### Post by Autodave on 2018-05-16
+1 with wildmanne39.

---

### Post by oldfred on 2018-05-16
+1 on wildmanne39's suggestion.

I also believe in clean installs. Also does, in effect, a major houseclean.
Many seem to like VM, but I use multiple installs and have all data in a shared data partition. 
If a newer user using a /home partition is easier as it creates mount point, adds entry to fstab, and gives you correct ownership & permissions. 
And then a separate partition lets you install a new system but reuse settings & data in /home, if you use Something Else install option.
But if switching gui, then the separate /mnt/data partition may make more sense as then each install can have separate /home with its own user settings, but little or no data in /home.

I have 16.04, 18.04 and am working on getting 18.04 configured the way I want. But have 16.04 as main working install. And all data is in both installs, so I do not have to switch back to 16.04 if in 18.04 to find something.

---

### Post by ricardosilva on 2018-05-17
Thank you, I will do a clean install, then!
Since it is my second laptop, I don't really have to worry about losing important files: all my important stuff are on my principal laptop.
That way I will learn. Actually, it was a friend of mine that did the Linux installation for me in the past, but in the meanwhile I have learned how to use GParted.

@oldfred: where can I find more detailed information on doing multiple installs?
For the moment, I am using dual-boots (Windows and Ubuntu), with a partition for each OS, and a shared partition for data.
Is there anything special about having dual-boot for different linux distros instead of one Windows and one Linux? This would be something I would be willing to try during my summer holidays.
I don't think I am ready to use a single /home for 2 installs yet...

---

### Post by oldfred on 2018-05-17
I do not recommend sharing /home. You may have conflicts between your user settings in one system and then in the other system. If upgrading then a separate /home may make sense.
But if dual booting two Linux, better to use a shared data partition. I have mine at /mnt/data ext4. But then I have to set my own ownership & permissions to allow me to use it.
One one Linux install will control booting, but you can boot all installs from that one grub. Last install will be the one in MBR or UEFI's ESP for booting. But you can reset to use any one as main working install.

       Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /mnt/data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /mnt/data and just configure / for install. 
   [https://askubuntu.com/questions/1013677/storing-data-on-second-hdd-mounting](https://askubuntu.com/questions/1013677/storing-data-on-second-hdd-mounting) 
   [http://ubuntuforums.org/showthread.php?t=2315714](http://ubuntuforums.org/showthread.php?t=2315714)
Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)

---

### Post by ricardosilva on 2018-05-18
Thank you!

---

