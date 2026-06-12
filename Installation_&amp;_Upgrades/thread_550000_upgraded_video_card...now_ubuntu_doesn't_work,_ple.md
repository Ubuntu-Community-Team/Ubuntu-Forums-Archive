---
title: "upgraded video card...now ubuntu doesn't work, please help! :("
date: 2007-09-13
forum: Installation &amp; Upgrades
---

### Post by harlock74 on 2007-09-13
Hello, this is my first post here.  I installed Ubuntu about 2 months ago, been playing around with it and liking it tons.  Now, yesterday I bought a new video card (PNY Nvidia Geforce 7600 GS) to replace my geforce 4.  I installed the new card, try to boot Ubuntu, but now I get an error saying the X server couldn't start.  This is the full errror:

Using config file: "/etc/X11/xorg.conf"
****INVALID MEM ALLOCATION**** b: 0xd0000000 e: 0xd0000000 correcting
Fatal: Error inserting nvidia (/lib/modules/2.6.20-16-generic/nvidia/nvidia.ko): No such device
NVIDIA(0): Failed to load the NVIDIA kernel module!
NVIDIA(0): *** Aborting ***
Screen(s) found, but none have a usable configuration

Fatal server error:
No screens found

Now, I've been looking around the net, and have found old posts similar to mine... I tried running:
sudo dpkg-reconfigure xserver-xorg

and with "nv" it starts Xserver, but my display is not right... it looks like a big blur, I can see the mouse move ( a big white square) and the ubuntu logo smeared with like 8-bit colors.

I don't know what to do.  I tried running envy from command line, and after that, I get the same problem....failed to load nvidia kernel.....  does anyone have any idea of what I need to do to get my system running again?  Thank you so much for your time. 

NOTE:  I also tried running Ubuntu from CD  both install and safe mode....they both come up scrambled display.  Reminds me when in windows you set the monitor to the wrong refresh rate.

---

### Post by Pumalite on 2007-09-13
Try 'vesa' as your driver so you can get IN the system. Once in, re-install your nvidia driver.

---

### Post by harlock74 on 2007-09-13
Ok, tried VESA...no luck... error:  

Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

Here's what it looks like with VESA in  depth of 16 and depth of 24

flickr.com/photos/javitico


Any idea?  thanks.

---

### Post by Pumalite on 2007-09-13
Do you do this:
sudo /etc/init.d/gdm stop
Before configuring xserver?

---

### Post by harlock74 on 2007-09-13
Yeah.  I'm having to start via the recovery console, and yes, dgm is stopped.  Just tried it again to make sure...same issue with the display and that GLX extension error.

---

### Post by numb3r5ev3n on 2007-09-13
> **harlock74 said:**
> Yeah.  I'm having to start via the recovery console, and yes, dgm is stopped.  Just tried it again to make sure...same issue with the display and that GLX extension error.

This happened to me last night...I ended up just reinstalling the system. :(

---

### Post by harlock74 on 2007-09-13
update...still not working, but ....  I put back my old video card, rebooted...and loads up GUI...no problems...?!?!?!?!?  it's using nvidia-glx.....how come it loads fine with my old card, but not the new one?

---

### Post by Sunflower1970 on 2007-09-13
I have the nVidia 7600GT AGP card. Recently, when there was an upgrade to the kernel (from something like 2.6.20-16.29 to 2.6.20-16.31) my 3D stopped working, then problems with X. Couldn't log in unless I used the nv driver instead of nvidia. Tried everything I found here at the fourms, even tried Envy (which looked like it wanted to install nvidia-glx-new--and this didn't work either). In the end, I ended up reinstalling Feisty, and am now using kernel 2.6.20-15 which works well.

So if you haven't removed the -15 kernel, try using that one instead of the -16 kernel. It might work. If not, just reinstall with the new cardand use the older kernel instead of the -16 one.

My 7600GT with the -15 kernel uses the nvidia-glx driver not nvidia-glx-new. (Too afraid to boot into the -16 kernel to see what will happen with the new install now...)

---

### Post by harlock74 on 2007-09-13
Ok...this is crazy now.... I boot from the Ubuntu CD, tried to do a new install.....I can't!!!  The display is messed up, just like it looks when I was trying to get VESA to work:

[www.flickr.com/javitico](www.flickr.com/javitico)

so, now I'm stuck...I can't even do a new install...any ideas, anyone? :(  this sucks.

---

### Post by Pumalite on 2007-09-13
If you are not dual booting (I forgot to look at the start of the thread) you can use DBan: [http://dban.sourceforge.net/](http://dban.sourceforge.net/), then use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php), and start from zero again.

---

### Post by moonhk on 2007-09-15
I am using below command. All items .last than 10 min to complete
sudo dpkg-reconfigure -a

You need backup your ubuntu before testing above command

---

### Post by harlock74 on 2007-09-15
It's working!!!!  :guitar:

Ok, so after trying many many different things, following advice from many people, pages, postings, etc....it all came down to this:

1. Used Envy to install NVDIA driver (which I had been trying anyway)
2. Saw an warning in dmesg saying that maybe my bios had misconfigured my video card....
3. Went into bios...found that the AGP aperture was set to my 128...switch it to 512 and rebooted
4. I was greeted with Ubuntu....finally!!!!

Thanks everyone for all the help.

---

