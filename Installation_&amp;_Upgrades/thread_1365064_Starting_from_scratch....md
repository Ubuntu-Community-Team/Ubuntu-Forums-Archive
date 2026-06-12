---
title: "Starting from scratch..."
date: 2009-12-26
forum: Installation &amp; Upgrades
---

### Post by Yith on 2009-12-26
Hi everyone, well... I just wiped out my old laptop's hd and installed Vista from the hidden recovery partition.

Now since I'm a total noob I was wondering on what was the best way to install kubuntu on the now clean hd. My goal is to create a new partition (lets say... 50% of the space) and install kubuntu there, also, will the files on the vista partition be available on the other one? 

Please someone tell me how to do it :p

---

### Post by oldfred on 2009-12-26
I have not used Kbuntu but I am sure the installer is the same.

Dual Boot Win7 & Ubuntu
[http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Karmic#Dual-Booting_Windows_and_Ubuntu)
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)
[http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting](http://lifehacker.com/348858/use-a-single-data-store-when-dual-booting)


Ubuntu will read & write NTFS partitions but windows will not read ext4 partitions and there is discussion on whether the program to read ext3 paritions from windows is reliable. I like to create a separate NTFS data partition for shared data between windows and Ubuntu. I put photos and my profiles for Firefox and thunderbird in the shared partition.

---

