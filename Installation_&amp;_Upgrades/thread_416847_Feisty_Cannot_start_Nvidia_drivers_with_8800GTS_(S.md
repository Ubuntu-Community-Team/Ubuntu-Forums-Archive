---
title: "Feisty: Cannot start Nvidia drivers with 8800GTS (SLI)"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by Shinobi326 on 2007-04-21
First off I'm a Linux newbie but I feel like at least half-way competent when it comes to configuring PCs.

I installed a fresh Feisty I386 on my main PC as a dual boot between 2 harddrives.  I have read through numerous posts here in the forums to try to help my problem but I'm now at an impass when it comes to getting the full latest Nvidia drivers to work.

Here are the things I've tried to no avail:
Latest Envy script for Feisty
Restricted Modules
sudo dpkg-reconfigure xserver-xorg


The only thing that appears to at least let me use the Vesa drivers was "sudo dpkg-reconfigure xserver-xorg" with the following settings from a post I read:

Video card driver: Vesa
Framebuffer on
Select proper resolution and 16-bit color
startx

I've looked at some of the documentation on the Nvidia website and it seems to assume you've done certain things to your environment before you can do some of the root commands which I can't follow.

I thought I was getting the closest with the Envy script but at the end when it tries to start the x server I get the same old blue screen failed to initialize window that I got when I installed fresh.

If someone would be so kind to give me a step by step "Barney Style" approach to getting this video driver set to run correctly I'll forever be in your debt.  Again, I've read through scattered posts throughout this forum and while some appeared to get me close nothing got me all the way there.  I've read through the main documentation on the Ubuntu site and it says for Geforce 6 and 7 series only which doesn't help me.

My system:
AMD64 3200
Nforce4 SLI x16
Dual Raptor drives
Dell 30inch LCD
Dual Nvidia Geforce 8800GTS SLI

Thanks in advance!

---

### Post by mid_night gypsy on 2007-04-21
Welcome,Shinobi326
 I post a small how-to on a theard. I prefer using the Nvidia drivers straight from there web site, To me I have better luck with them. Here's the link it's half way down.Hope this helps,gypsy

     [http://ubuntuforums.org/showthread.php?t=412133&highlight=gypsy](http://ubuntuforums.org/showthread.php?t=412133&highlight=gypsy)

---

### Post by Teamgeist on 2007-04-21
Have yout tried the restricted-drivers-manager?
Just click System--> Administration--> Restricted-drivers-manager (Or something like that. My system is in German thats why I dont know the exact name of it).

If that does not do any good try
```
sudo apt-get install nvidia-glx-new
``` and when it's done downloading and installing type ```
sudo nvidia-glx-config enable
```

This should actually do the trick.
Good Luck. :)

---

### Post by Mongoose on 2007-04-21
There is a new driver out today too it seems as others in this forum have pointed out.

[http://www.nvidia.com/object/linux_display_amd64_100.14.03.html](http://www.nvidia.com/object/linux_display_amd64_100.14.03.html)

---

### Post by Shinobi326 on 2007-04-21
Thanks guys!

I actually took the initial advice because for some reason the Kernel wasn't matching and I needed something to recompile the Kernel so the video drivers will work.

Just for anyone else searching the forums to find out what made it work for me I did the following steps.

1.  Downloaded "NVIDIA-Linux-x86-1.0-9755-pkg1.run" directly from the Nvidia website to my Desktop

2.  Rebooted and used the Ubuntu recovery mode
3.  ```
CD Desktop
```
4. Typed in ```
sh NVIDIA-Linux-x86-1.0-9755-pkg1.run
```
5. I answered all of the questions in a logical way including allowing it to recompile and save.
6. Typed in ```
startx
```

I know this is a regurgitation from the recommendation from above but I wanted to repost the concise steps I took to finally get the drivers to work.

Note: The restricted drivers enabling did not work for me which led me to simply use the steps I did above.

Again, thanks to everyone that helped!

---

### Post by superr on 2007-05-09
Hi, i make all the steps and work but when i restart/shutdown i lose everything... why?

I need to do this every time... :S

Can anyone help me?

When i try to startx without the steps i have this error: 
no screens found
XIO: faltal IO error 104 on X server ":0.0" after 0 requests with 0 events remaining

---

### Post by Shinobi326 on 2007-05-10
Well I'm not too sure about your problem there because I'm also a newb.

I'm not at my Ubuntu box right now but once I do I'll try to see if I was missing something somewhere.

I do remember that once you get it to work I would go into the Nvidia Video Driver GUI and reset my resolution to 2560x1600.  From there if I wanted to keep that setting I had to change the resolution in the xconf file.  I think I remember I also had to add something to the Sessions menu too, I don't totally remember off the top of my head.

I'll try to repost later if I have more info.  In the meantime I'm hoping a real Ubuntu guru could help out here because I kinda feel like the blind leading the blind :) :confused:

---

### Post by fuzz500 on 2007-05-27
Hey guys, 
I saw that dell 30 incher that will run at 2560x1600 ... I want it!
Does anybody know if you can run AIGLX/Compiz/Beryl with
SLI enabled?

regards,
Fuzz

---

### Post by Shinobi326 on 2007-05-28
Yes, the Dell 30 incher rocks... I have it and it's quite nice to run 2560x1600.

I'm also curious about the whole SLI world when it comes to Linux.  I've asked before and nobody can give me an answer yet as to whether or not you can run SLI at all in Linux let alone your desktop manager.

Anyone?

---

### Post by fuzz500 on 2007-05-29
I read this thread, but let me get this straight: you don't have SLI working in ubuntu? I have been doing research on the web and from what I can tell, you should definitely be able to run SLI under ubuntu ... and linux in general, provided of course, that all your hardware is compatible with each other. Do you have SLI setup on a windows gaming rig?

I have compiled a non-exhaustive list of links that may be of help. Also, I just met a guy who's super techy, and I'm going to ask him about SLI setups and report back. These may help in the meantime.

_general reading:_
[http://en.wikipedia.org/wiki/Scalable_Link_Interface](http://en.wikipedia.org/wiki/Scalable_Link_Interface)
[http://www.phoronix.com/scan.php?page=article&item=326&num=1](http://www.phoronix.com/scan.php?page=article&item=326&num=1)
[http://www.phoronix.com/scan.php?page=article&item=730&num=1](http://www.phoronix.com/scan.php?page=article&item=730&num=1)
[http://www.phoronix.com/scan.php?page=article&item=338&num=1](http://www.phoronix.com/scan.php?page=article&item=338&num=1)
[http://www.bit-tech.net/hardware/2005/05/17/nvidia_sli_pt2/1](http://www.bit-tech.net/hardware/2005/05/17/nvidia_sli_pt2/1)

_hardware:_
[http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-w.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-w.html)
[http://accessories.us.dell.com/sna/productdetail.aspx?c=ca&l=en&s=dhs&cs=cadhs1&sku=222-7315](http://accessories.us.dell.com/sna/productdetail.aspx?c=ca&l=en&s=dhs&cs=cadhs1&sku=222-7315)
[http://accessories.us.dell.com/sna/productdetail.aspx?c=ca&l=en&s=dhs&cs=cadhs1&sku=222-7175](http://accessories.us.dell.com/sna/productdetail.aspx?c=ca&l=en&s=dhs&cs=cadhs1&sku=222-7175)

_nvidia drivers:_
[http://www.nvidia.com/object/linux_display_ia32_1.0-8174.html](http://www.nvidia.com/object/linux_display_ia32_1.0-8174.html)
[http://www.nvidia.com/object/linux_display_amd64_100.14.03.html](http://www.nvidia.com/object/linux_display_amd64_100.14.03.html)

_forums:_
[http://www.slizone.com/page/home.html](http://www.slizone.com/page/home.html)
[http://forums.slizone.com/index.php?showtopic=2953&hl=](http://forums.slizone.com/index.php?showtopic=2953&hl=)



incase you don't have an account a the slizone.com, this last posting in slizone.com forums says  

one guy asks:

Does SLI mode work in Linux?
I am running Ubuntu 6.10 Gnome desktop.
I have the nVidia 3D Linux drivers installed, but there is not "control panel" of any sort. I have a couple games that I run In Linux and just if Sli is working or not?

and the reply:

Yes,
[http://www.phoronix.com/scan.php?page=arti...m=338&num=1](http://www.phoronix.com/scan.php?page=arti...m=338&num=1)
Drivers:
[http://www.nvidia.com/object/linux_display...2_1.0-8174.html](http://www.nvidia.com/object/linux_display...2_1.0-8174.html)
Read this README to enable, SLI is down the bottom..
[http://http.download.nvidia.com/XFree86/Li...html/index.html](http://http.download.nvidia.com/XFree86/Li...html/index.html)



That's all for now! Cheers.



UPDATE
Just talked to my techie friend, and learned that I don't even need SLI to drive 2560x1600... nvidia 8500 will do it for 150 bux. Hope those links help you... signing off. F500.

---

