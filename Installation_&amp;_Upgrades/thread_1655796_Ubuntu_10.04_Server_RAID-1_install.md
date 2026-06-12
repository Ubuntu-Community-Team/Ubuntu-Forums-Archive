---
title: "Ubuntu 10.04 Server RAID-1 install"
date: 2010-12-30
forum: Installation &amp; Upgrades
---

### Post by jsalelle on 2010-12-30
Hello.

I'm trying to install a box with Ubuntu 10.04 LTS server with a typical LAMP system in order to replace my old Ubuntu 8.04 server I have at my school to have a "backup" system and also trying to replace NIS authentication with LDAP. Well I'm getting stuck on the first step: installation of base system.

I want to build a RAID-1 system with the two 320GB SATA HD's the machine has, I have a little experience in installing RAID because I installed my old 8.04 server with RAID-1 aswell.

I boot my box from an USB stick with Ubuntu 10.04 Server 64bit, the systems boots well, asks me about language, keyboard and so, finds the two NIC cards and the DHCP configuration of one of the card is done. Then it starts the partitioner.

One of the HD's already contains three partitions with an installation of a regional flavour of Ubuntu, the other HD only contains a partition for backups, I don't want to preserve all this stuff, so the first thing I do is to replace the partiton tables of both HD's with a new one. This is done without problems.

Then I go to the first disk, by example, and create a new partition, the partitioner ask me for the size, I write 0.5 GB (or 500 MB), then I select that it has to be a Primary partition at the beginning of the disk, all goes OK. Once created I go to the "Use as: " line, type Enter and select the option "Partition for RAID volume", when I hit Enter the error appears: the screen flickers in black for a second or two, then it shows a progress bar "Starting the partitioner..." THAT ALWAYS GET STUCK AT 47%!!!

Sometimes the partitioner allows me progress a little further (for ex. lets me activate the boot bit of the partition, or it allows me to make another partiton, even once the error didn't appeared until the first partiton of the second HD!!) but it always get stuck with the same progress bar at the 47%.

I've tried a lot of things: I downloaded again the ISO and rebuilt the USB, same result. Downloaded the ISO and rebuilt the USB from another computer, same result. Unplugged all the SATA and IDE drives except the two HD's, same result. Built a CD-ROM instead of an USB, same result. Downloaded the 10.10 server ISO (not an LTS), and the USB stick can't boot, is another error, but only to try.

When the error appears, I hit Ctrl+Alt+F2 and get into a root prompt, there I kill two processes: /bin/partman and /lib...don'tremember/init.d/35... and then when I return to the first console the progress bar has gone and the install process asks me at wich step I want to return, I hit "Partition disk" and then the progress bar reappears and STUCKS INMEDIATELY AT 47%!!!

I'm at the edge of give me up!!!! I've been with this problem for a week, I've searched and read a lot, but I haven't found anything useful. 

I'm begging you all for some advice. Is the Ubuntu 10.04 LTS server installer wrong?? Please help me!!

Thanks a lot!!

---

### Post by jsalelle on 2011-01-07
At least I've found the error!!!

I'm posting the solution here for hep people in case somebody has the same problem.

It was only the language I chose for the installer!! I chose my language (Catalan) for the installer and it seems that it is wrong. When I chose English as the language, the installer and the partitioner worked fine until the end!!
Now the sustem's language is also English, but it doesn't matter because the box will work as a LAMP server, without local users.

Thanks to all the people.

---

