---
title: "Failed 12.04 upgrade, recovery mode unavailable with whiptail error"
date: 2012-07-06
forum: Installation &amp; Upgrades
---

### Post by juanbuntu on 2012-07-06
CPU: AMD FX-6100 Zambezi 3.3GHz Socket AM3+ 95W Six-Core 
MOBO: ASUS M5A97 AM3+ with Bios Version = 1208, which is the most updated as of 2012.05.25 
Video Card: EVGA 01G-P3-1556-KR GeForce GTX 550 Ti

In May I installed Ubuntu 10.10. in Early June I upgraded to 11.04, in mid-June upgraded to 11.10. Last night I tried to upgrade from 11.10 to 12.04. The upgrade process had numerous errors. Now I am at a point that even when I try to recreate the install/update sequence from 10.10, my system can't go beyond 11.04, i.e., after the update for 11.04 is done, the boot fails.

Is there a compatibility problem caused by having an nVidia GeForce graphics card with an AMD CPU?

I am lost. Any help is greatly appreciated. Thanks.

---

### Post by juanbuntu on 2012-07-14
I got zero replies, but I fixed the problem, sadly by re installing from scratch from the Ubuntu-10.10-AMD6 DVD.

This time I set up partitions manually to something like this:

/boot    primary     ext4     512MB  
/               primary     ext4    150GB
swap                         ext4     100GB
/home   logical      ext4     remaining GBs

Immediately after the install the system warned me that 10.10 was no longer supported and asked me to *update* and then to *upgrade* to 11.04. 

After the updates I rebooted the system, then issued the command

sudo apt-get install nvidia-new

rebooted, and then upgraded to 11.04 . When the upgrade to 11.04 ended, I rebooted, went to system settings/Additional Drivers, where I saw that the nVidia accelerated graphics was activated &#8220;but not in use&#8221;.  I played to make the dual-monitor system work. 

Then I upgraded to 11.10, rebooted, did the updates, re installed tools I was using. 

I am *NOT TOUCHING* 12.04 until I have evidence that the AMD FX-6100 MOBO works with the nVidia GeForce 550 Ti card works 

So I am posting this response hoping to save for other people the countless hours I wasted.

Juanbuntu

---

### Post by jmfal on 2012-07-14
Welcome to Ubuntu

There are reports of problems with the nvidia driver from the proprietary drivers and your card,  might have to add ppa for driver from here

[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates/]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates/")

OR here
[http://www.unixmen.com/bleeding-edge-script-is-available-for-ubuntu-12-04/](http://www.unixmen.com/bleeding-edge-script-is-available-for-ubuntu-12-04/)

The second one looks like you have to compile a driver, do some research on both

Burn a 12.04 iso and make sure it works before you install, maybe burn a Gparted and boot-repair disc while your in a burning mood.

[]("https://launchpad.net/%7Eubuntu-x-swat/+archive/x-updates")

---

### Post by juanbuntu on 2012-07-16
Jimfal: thank you for your response. I am not that versed in Ubuntu. Do you mind telling me what PPA stands for?

Thanks

---

### Post by jmfal on 2012-07-16
Your Welcome

I'll let you read this ,, it explains it  better than I can:

[http://www.makeuseof.com/tag/ubuntu-ppa-technology-explained/](http://www.makeuseof.com/tag/ubuntu-ppa-technology-explained/)

You can do some research here in the forum, use the "search this forum"  link and enter your video card number and read the posts, and see what is best for you.

I use the driver  from the x-swat for my gt240 and haven't had any problems , but their drivers may not work for your card.

---

