---
title: "Install Help"
date: 2005-09-21
forum: Installation &amp; Upgrades
---

### Post by green708 on 2005-09-21
I am trying to install Hoary on my HP laptop (AMD64) for the first time and am having limited success.  The installation completes without any major hitches, but after I type in my user name and password the system freezes.  Additionally, while booting I get an error saying that the hardware clock can not be accessed by any means.  I believe the source of my troubles originates from one of two places.  

First, during installation the network configuration fails.  I'm not on any permanent network and don't even know what DHCP is.  The only way I get on the internet is at the local coffee shop (free wireless).  At this stage of the installation I select "Do not configure network at this time".

Second, I am not confident that I partitioned the hard disk properly.  I have a 40Gb hard drive.  The first 10Gb is selected as "primary", formatted as ntfs, and is currently running windows without any problems.  The second 10Gb is selected as "primary", formated as ext3, bootable and is where I am attempting to load ubuntu.  The third is 18Gb, "logical", ext3, and is the home directory.  The remaining 2Gb are swap. 

I appreciate any help/tips, anyone can give me.

Thanks in advance.

---

### Post by John.Michael.Kane on 2005-09-21
You could try to reinstall,and let the ubuntu install partintion the space automaticly for you. also you can try the 32bit standard version of the iso and not the 64bit one. if your using the 32bit version then you may want to look into the 64bit verison. which ever one you use let it part the space for you. also you really dont need to make a seprate home dir.. 

Hope that helps

---

### Post by grimmson on 2005-09-24
This probably won't help a bit but I don't think Configure network later is the problem. I'm a n00b to so my advice is flimsy. The only thing I saw durring install access the net was open office download a dictionary. After installation I downloaded several updates not incuded in the install cd. I have heard laptop flatscreen drivers can be a pain. Some things you might think about, did you download 5.04 or 5.10 (5.10 is a beta and probably not recomended for newb's.) I feel bad asking this next one. You did get the 64 bit cd NOT ppc or 386? Past that I can't really helpbut I can answer your question "what is dhcp?" Dynamic host client protocal. You'r the client, the wireless coffee shop router is the host. When you boot your computer your opperating system checks to see if there's a network it can join. Your wireless card anounces itself, the router registers your mac address and issues you an IP Address,subnet mask,gateway and dns servers. Now with your ip address registered to your mac address your internet stuff shouldn't end up on someone elses computer. 
TIP: If you do this at the coffee shop you may want to turn off file sharing.

---

