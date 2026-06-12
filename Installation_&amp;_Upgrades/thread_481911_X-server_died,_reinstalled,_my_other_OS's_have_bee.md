---
title: "X-server died, reinstalled, my other OS's have been wiped?"
date: 2007-06-23
forum: Installation &amp; Upgrades
---

### Post by Tikitiki on 2007-06-23
I recently ran into some trouble with xserver-xorg not working - I tried tumultuous things after searching for several hours to try and fix the problem - even an IT professional who uses Linux daily couldn't figure out the problem with xserver. People kept telling me to just reinstall as it'll be easier, but I was reluctant to do so. Finally after 3 days of searching around trying various things I gave up. I went for the reinstall - using my Live CD to boot into Safe Graphics mode I ran the partition manager. My current installation was on an external HDD so it wouldn't prevent me from accessing my main OS in case Ubuntu screwed up. I was using Ubuntu/KDE on my HDD for sandbox testing / messing around with as I learned how the system worked. My other OS was windows Vista which was mounted into my internal harddrive on my computer - not the HDD.

So back to opening the Partition Manager, there were two listing 1) The Swap for linux on my external HDD and the rest of the space which was roughly 120 GBS on my external HDD. I knew neither were my internal hard drive because it was only 80 GBs. I unallocated both of them, connected to my network, fetched updates, and ran the install. I go to play halo 2 on xbox for a hour or so and then I come back. Ubuntu says that it has finished installing and asks weather I should stay on the live CD or restart into the real Ubuntu. Fair enough, I restart. First signs of trouble: 1) GRUB didn't list my Vista OS (loader) to boot from - it went straight to the Ubuntu loader. Second sign: Checked my media devices: 1) My external HDD and my Internal Disk 2) Both had Ubuntu files on them. 

What had Ubuntu done? I fear I have lost all my years of precious data because Ubuntu didn't prompt for any sort of specifications during the installation, assumed that my internal hard drive was the one to install and overwrote it? I hope this is not the case.

Although I'm very sad/angry about loosing data, I feel this might be good if I reinstalled Vista - One problem, it's an upgrade version. So how about it folks? Can you suggest any ways I can get my data back or at least be able to re install vista? I don't care if it takes calling Microsoft up them selves and explaining the situation to them, but I'm not a happy camper. I paid a lot of money for Vista and I won't be pleased if Ubuntu wound up rendering it useless.

And if I knew Ubuntu would blatantly override my hard drive I *would have* backed up my data, but I thought the installation or the people who programmed it would have been smarter to take more precautions or at least WARN the user before tampering with such *sensitive* data without my explicit knowledge first.

Ryan

---

### Post by apjone on 2007-06-23
Ubuntu did not do anything to you vista install, you controlled the partitioning and if you over wrote your vista that is a user error not  software.

Now If you didnt over write your vista then all you have to do is manually add it in to /boot/grub/menu.lst .

Also if you installed Windows over the top now, it would replace grub and you would be unable to access your ubuntu o/s unless you re-installed grub.

Also you should take backups of important data on a regular basis. This will prevent data loss from virus/hardware failure as well as user error

---

### Post by apjone on 2007-06-23
> **Tikitiki said:**
> 
And if I knew Ubuntu would blatantly override my hard drive I *would have* backed up my data, but I thought the installation or the people who programmed it would have been smarter to take more precautions or at least WARN the user before tampering with such *sensitive* data without my explicit knowledge first.
Ryan

On the Ready to install screen before disk changes are committed the following text is displayed 

> 
 Language: English
 Keyboard layout: United Kingdom
 Name: apjone
 Login name: apjone
 Location: Europe/London
 Migration Assistant:



If you continue, the changes listed below will be written to the disks.
Otherwise, you will be able to make further changes manually.

[B]WARNING: This will destroy all data on any partitions you have removed as
well as on the partitions that are going to be formatted.[/B]

The partition tables of the following devices are changed:
 SCSI1 (0,0,0) (sda)

The following partitions are going to be formatted:
 partition #1 of SCSI1 (0,0,0) (sda) as ext3
 partition #5 of SCSI1 (0,0,0) (sda) as swap


So you are warned that you will lose data on the disks/partitions you have selected

---

### Post by Tikitiki on 2007-06-23
As for adding vista to the list, how would I do that? I see how it works in the menu.lst file but I don't know what I should set for the specific options.

> **apjone said:**
> On the Ready to install screen before disk changes are committed the following text is displayed 



So you are warned that you will lose data on the disks/partitions you have selected

apjone, I don't remember seeing anything like that.

---

### Post by apjone on 2007-06-24
try this
[http://www.helpero.com/Questions-and-answers/Computers/Linux/How-to-add-Windows-entry-into-GRUB-menu_1508.html](http://www.helpero.com/Questions-and-answers/Computers/Linux/How-to-add-Windows-entry-into-GRUB-menu_1508.html)

---

