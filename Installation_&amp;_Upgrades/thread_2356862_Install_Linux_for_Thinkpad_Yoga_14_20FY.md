---
title: "Install Linux for Thinkpad Yoga 14 20FY"
date: 2017-03-27
forum: Installation &amp; Upgrades
---

### Post by sunjh831 on 2017-03-27
Hi, guys. I am looking for help to get Linux installed. My laptop is Thinkpad Yoga 14 20FY (i5 6200U, 8G RAM ,256G SSD , NV940M)
 
I tried 3 distro , ubuntu( 17.04, 16.10,16.04) Fedora 25, Mint 18.1.

I am Ok to load the grub and choose installation or try out. There is problem when it load the linux into memory to prepare installation  
 
Fedora 25, it stuck in 
Error message mmc0: Unknown controller version (3). You may experience problems.
 
For Both ubuntu and Mint, initramfs says &#8220;unable to find a medium containing a live file system&#8221;.
looks like it fails to mount the thumb drive(/dev/sdb) which contains image to /cdrom
 
I tried kernel parameters like monodetest, apci=off, modprobe.blacklist=hid_senor_hub. They do not give me any help
 
When I tried nolapci, the system even crashed in boot the installation thread.
 
I am so exhausted , Some one could give me a hand? Thank you veeery much.

---

