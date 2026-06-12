---
title: "Kubuntu - Issues with Network and LILO"
date: 2005-10-25
forum: Installation &amp; Upgrades
---

### Post by natstupid on 2005-10-25
I tried installing Kubuntu Linux today. Following are the issues I faced. 

Background : 
PC Config : AMD64 3000+, NForce3, 512MB DDR, Geforce6600 GT, A PPPoE connection to the Internet and a Pioneer DVD Writer. 

I already have two partitions with two copies of Windows on them, I use [XOSL]("http://www.ranish.com/part/xosl.htm") to switch between the  two installs. I decided I would use 5GB for the Linux, so I split it into 4.5 for / and .5 for the SWAP area. Was briefly considering a separate /boot partition, but gave up the idea. Anyway 4.5 for / and .5 for swap. 

1. On to the install. It did not detect my network settings. It said that either my network does not use DHCP or DHCP server might be slow. I was not sure about this. I knew that in WinXP I had to install TCPIP v6 for the network to get detected, and once it was detected, I would create a dialup connection with my username and password to connect to the net. However I could not enable this here. I thought I might be able to configure it once the install is over, however in the network all I can see is eth0 disabled. If I try to click administrator mode and give the password, then it accepts the password (it gives a warning if it is a wrong password) but still does not let me make any modifications. This same thing is repeated in the Storage & disks section. I can see the list of partitions all greyed out, and even if I give the administrator password I cannot edit anything over there. So how do I configure my internet connection ?

2. I could also not install LILO as the boot manager. It gave me an error about lilo.conf and said install could be continued, but no matter what I try I could not get it to install. I was not installing in the MBR as I already had a boot manager (XOSL) that I was using, I wanted it to be installed in my Kubuntu partition (/dev/sda9). I ended up using GRUB. But Lilo never worked. 
I also would like to know how to configure GRUB so that I can remove the reduntant Windows entries in the choice. 

3. I could not find a way to change the monitor refresh rates, it shows only as 60Hz. My Monitor supports much more and 60hz seems as if it flickers a lot. It is a 19" CRT Viewsonic. How do I change this. I installed a nvidia driver for Xorg, but still I do not get options for changing the refresh rate. 

4. I am not able to mount my windows partitions. All my music is on a NTFS partition, and I would like to access it, but I am unable to do so. In the disk & storage section all the options are grayed out. Even if I click administrator mode, I do not get the options. 

Can someone please help me with these issues ?

Thanks.

---

