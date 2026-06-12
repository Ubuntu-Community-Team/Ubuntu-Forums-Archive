---
title: "Grub Error 18 -- HELP!!!"
date: 2007-02-19
forum: Installation &amp; Upgrades
---

### Post by milesdavis222 on 2007-02-19
Hello everyone --

Today I installed a 500 GB Seagate barracuda EIDE hard drive in my old Dell B667r. I booted up with the ubuntu 6.10 livecd and the installation went perfectly --- until I rebooted. Grub began loading, and then in stage 1.5 threw "Error 18" :confused: -- I flashed the newest BIOS prior to that as well. I am somewhat new to linux (mac user), so please, in your response be down to earth.

Thank you so much to all who help!!! It is much appreciated!

---

### Post by milesdavis222 on 2007-02-19
Let me clarify - 

I installed ubuntu in the following way after googling and after i got the Grub Error 18 message -- i made a 9 GB EXt3 partition in the beginning of the HDD and set the flag to boot, then had a 1 gb swat partition and the rest of the hard drive space was also formatted to ext3 and was at the center of the drive (between the other 2 partitions). Thanks again -- if you need further clarification, please tell me.

I spent an entire day with this --PLEASE HELP!!!

---

### Post by milesdavis222 on 2007-02-19
BTW - I called up Dell about the problem and their solution was installing Windows Vista :) :D

This is the problem  - please help:

I have installed Ubuntu 6.10 on a Dell B667r with bios version A08 on a new 500 GB Seagate EIDE hard drive. I installed with the first partition as ext3 and set the flag to "boot." The next partition contains approximately 490 GB of space and is also set to ext3. I then set the last partition as my swap at around 1 gb. I reboot the computer, and the Grub begins loading but this occurs:
Stage 1.5 : **Error 18** and then the system stops. What is the solution to this problem :confused:  ?

---

### Post by confused57 on 2007-02-19
Here's a description & possible solutions:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)

The first & easiest thing would be to check LBA settings in bios, enable or disable, as described in the above link.
If that doesn't work, then maybe a separate /boot partition.

You already have the latest bios.

---

### Post by milesdavis222 on 2007-02-19
Confused57 -

Thanks so much! I went to that website, and did two things. I am not sure which one is the one that made this work. I initially did have a /boot partition of 100 MB after i heard about the large hard drive issue with old computers, but it didnt work. So I reformatted this partition a second time, but this time using the Ubuntu "alternate" install CD -- IE, minus the GUI interface. I then changed the type of partition of my large 450 gb partition to "logical" as per the webpage you sent me. That probably did the trick -- my ubuntu is installed and booted as we speak, recognizing the entire partition :D.

What is the difference between a logical and primary partition? Will it affect drive speed at all? Will it have a large affect on drive speed if the drive is primarily for UATA/100 and my motherboard is meant for ATA/66?

Thanks again and take care. Haha, and dell wanted me to install Vista :D -- and then they said that it is impossible for it to recognize any more than 80 gb :D

---

### Post by confused57 on 2007-02-19
Glad you were able to get everything working...each hard drive can have only 4 primary partitions, but one of them can be an extended partition, which can contain many logical partitions...it shouldn't make any difference speedwise(or otherwise), whether primary or logical...
Goes to show, you'll get better support here in the forums than you'd probably get from MS or Dell...their Linux knowledge is rather limited.

---

