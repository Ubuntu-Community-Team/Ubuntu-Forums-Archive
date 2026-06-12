---
title: "Install lubuntu with no USB boot nor CD reader"
date: 2012-02-03
forum: Installation &amp; Upgrades
---

### Post by darrask on 2012-02-03
Hello all,
I did an inconclusive search that did not come up with helpful threads.

I have an old Latitude C400 where I want to install Lubuntu (CPU 1.2Ghz, RAM 1 Gb, integrated Intel graphics card). It is NOT capable of booting from USB nor do I have a CD reader that can be connected to it.

So I installed Lubuntu from a flash drive connected to a another, USB boot capable computer, which contained the hard drive I intended to use on the Dell C400. Note that I had no Internet during installation.

Problem is, or maybe it is not: During Lubuntu installation, I can see that the installer detects hardware and configures it appropriately. **Does it mean my Lubuntu install will be wrongly adapted on my target computer and that I will have mismatches between the Lubuntu configuration and the hardware of my C400?**

After installation I put the hard drive with the fresh Lubuntu install inside the C400 and could use the system, however I don't know whether the screen flashes, some sluggishness, etc. are due to the fact that Lubuntu was installed from a different computer than the one it is running in now.

Any way to fix that or is nothing wrong? Is there a utility that can configure my system so that it is adapted to the present hardware?

thanks in advance

---

### Post by oldfred on 2012-02-05
Generally Ubuntu/Lubuntu adapts to booting most systems. The main issue is often proprietary drivers for video cards. If you did not install those and can boot, you should be ok.

With 1GB of memory system should not be all that slow. If you use terminal and use top to see what is running, does it show some tasks consuming all the resources?

If you type free, does it show swap being used, as that will be a lot slower. I have Ubuntu with 1.5GB and rarely use swap, but try not to load many programs at once.

```
fred@fred-LT-A105:~$ free
             total       used       free     shared    buffers     cached
Mem:       1528932    1484608      44324          0     263212     575768
-/+ buffers/cache:     645628     883304
Swap:      3068376          0    3068376
fred@fred-LT-A105:~$ 

```

---

### Post by darrask on 2012-02-05
Thank you for your answer!

I'll have a CD-reader in a few weeks. Would you recommend to reinstall from the CD drive directly to the Dell latitude C400 or leave it like that?

Detail: I originally installed Lubuntu on the hard drive inside a Latitude D420.

---

### Post by oldfred on 2012-02-05
I doubt a reinstall will change much, but do not know for sure. Generally if it is working it has updated itself to what ever you need.

---

### Post by BC59 on 2012-02-05
Another good solution instead of Lubuntu, in such an old machine, is the Ubuntu minimal installation:
[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

And another thing. When I have problems like this, I extract the hard drive and I put it in a box as external drive. Then it's easy to install the system and later reinsert it to the original computer.

---

### Post by darrask on 2012-03-06
Thanks for your answers! Sorry I did not properly read the first one!

The "top" command shows no particular process being greedy on resources, BUT Xorg is always the first one, and I think that has to do with graphics...

It uses only 2.6% CPU and 1% RAM if I don't do anything and nothing is open.

[B]BUT as soon as I start moving my mouse wildly, it fires up to 16% CPU!

[/B]It's quite funny to watch and it always works, just my moving my mouse in circles. I managed to get it to 50% CPU by switching between desktops rapidly too. RAM unchanged, swap use 0 with nothing open.

The problem with my C400 is that it does not have enough power from USB to power my external HDD so that I could install it that way...

Do you think that is a proper behavior for the Xorg process? Could it be that I don't have the right driver or configuration for my graphics card?

---

### Post by darrask on 2012-03-07
As I have webcam problems too with skype ([http://ubuntuforums.org/showthread.php?t=1936169](http://ubuntuforums.org/showthread.php?t=1936169)), I read instructions here:
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)
where it says:
>  Graphics Cards XV Skype and gstfakevideo

 There are a couple of issues that create problems getting webcams working with skype. The gstfakevideo driver will probably get things working provided you have a suitable graphics card driver set up in xorg.conf 
There is a highly significant thing called xv this is easily overlooked in the rush to get video working. 
you need to install the gstreamer packages and try this out. 
gstreamer-properties 
go to the video tab and test your camera with the default settings if it doesn't work with the plugin 'autodetect' in 'Default output' change it to 'X Window System (No Xv)' then try again 
if that works and 'X Window System (X11/XShm/Xv)' doesn't work then you are using an incompatible graphics driver. 

So on my computer, that is the case, output to 'X Window System (No Xv)' works but not 'X Window System (X11/XShm/Xv)'. Do I have an incompatible graphics driver? Where can I download it?
"lshw -c video" says that I'm using the i915 driver

---

