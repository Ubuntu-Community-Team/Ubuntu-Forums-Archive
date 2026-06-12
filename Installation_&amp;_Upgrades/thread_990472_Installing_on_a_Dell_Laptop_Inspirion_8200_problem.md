---
title: "Installing on a Dell Laptop Inspirion 8200 problems"
date: 2008-11-22
forum: Installation &amp; Upgrades
---

### Post by Jsunn on 2008-11-22
Hello All, 

I am brand new here and trying to install Ubuntu on my old Dell laptop Insirion 8200.  

I am running into some problems during the install.

I get through the steps 1-7 and the process begins, it tells me that it is installing the systems and it gets to about 50% complete and then I get an error?

The window tells me that the installer has run into a problem and that it cannot complete.  It recommends cleaning the DVD drive and also moving to a cooler area and maybe the HD is bad.  
It also suggests to burn the cd at a slower speed?

Upon I just purchased a new HD and installed it today and I am recieving the same message. 

I have burned the cd at 7x?

any suggestions?  

Since it is an older computer it doesn't boot from a USB drive, just the floppy, HD, and Cd drive.  

Thanks for your help!

-Jason
:confused:

---

### Post by redoscar3 on 2008-11-22
Have you tried checking the integrity of the CD using the initial Ubuntu menu item?  As a matter of policy, I always burn my Linux CDs with a burn speed of 4X, but 7X doesn't sound outrageous to me.  Was the CD burned on the same machine you are trying to install to?  It almost sounds like questionable CD media or a flakey CDRom drive.

---

### Post by Jsunn on 2008-11-22
> **redoscar3 said:**
> Have you tried checking the integrity of the CD using the initial Ubuntu menu item?  As a matter of policy, I always burn my Linux CDs with a burn speed of 4X, but 7X doesn't sound outrageous to me.  Was the CD burned on the same machine you are trying to install to?  It almost sounds like questionable CD media or a flakey CDRom drive.


I have checked the integrity of the CD via the tools that are available with the CD when it boots.  It didn't say that there was a problem.  I also ran a check of the hardware and everything checked out ok.  

Orgionally I thought it was a bad HD, so I purchased a new one.  I ended up getting the same error at about 50%.  I am going to try and burn another CD, I am also downloading the alternate installer as well hoping that I can get it installed.  

The error I get is:

"The Installer encountered an error copying files to the hard disk:

[Error 5]: input/output error
This is often due to a faulty cd/dvd disk or drive, or a faulty hard disk, it may help to clean the cd/dvd , to burn the cd/dvd at a lower speed, to clean the cd/dvd drive lens, to check whether the hard disk is old and need of replacement, or to move the system to a cooler environment."

-Jason

---

### Post by redoscar3 on 2008-11-23
Generally speaking, if the CD passes its integrity tests, then you have a good burn.  Now I also assumed you checked the md5sum of the .iso file before burning the CD and it passed.

So if we feel we have a good CD, the next possibility is a hardware problem.  Since the hard drive is new, I doubt this is your problem.  The installation will work both the CD/DVD drive and the CPU pretty hard.  Usually a bad CD/DVD drive will start to seek and reread if there are problems.  Often you can hear the laser control arm cycle to home and back to the target track.  Are you hearing any strange CD drive noises?

Also, is your CPU fan running at all?  The last error message suggests that the CPU could be overheating and giving you install errors.  Perhaps a cleaning of your CPU fan may be in order.  Or try to find a way to better cool your laptop.

By the way, what version of Ubuntu are you trying to install?  You might want to research any possible issues between your version and your model of laptop.  Personally, I have Hardy Heron 8.04 running on my Acer Apire 3003LCi laptop and have no significant problems.

Just make sure to check the md5sum on the .iso files before you burn any more CDs.  And let me know how things go.

Red

---

### Post by Jose Catre-Vandis on 2008-11-23
Yep, check your md5sum. Has happened a couple of times to me, especially when doing a split download. if you do not know how:

Go to [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
There you will find an entry for the md5sum for your iso
write down or save the number to a file, for Ibex Desktop (32 bit) it is 24ea1163ea6c9f5dae77de8c49ee7c03
If you already on linux, md5sum should already be installed so all you need to do is cd to your download directory, and in a terminal type:
```
md5sum ubuntu-8.10-desktop-i386.iso
```
This will return the md5sum hash numebr for you to compare

If you are on windows, you can download an open sooource windows exec [here]("http://www.nullriver.com/index/products/winmd5sum")
and do much the same as above.

If the hashes don't match, you will need to download again

	



Can you boot the Live CD to desktop?

Perhaps consider downloading the ALT CD which has lower memory requirements

---

### Post by Jsunn on 2008-12-06
I was able to get 8.10 installed!!

It was a bad CD drive.  I found on off e-bay for $10, installed the drive and tada!!

I am looking forward to using this new OS.  Thanks for your help!

-Jason

---

### Post by solitaire on 2008-12-06
> **Jsunn said:**
> I was able to get 8.10 installed!!

It was a bad CD drive.  I found on off e-bay for $10, installed the drive and tada!!

I am looking forward to using this new OS.  Thanks for your help!

-Jason

I've been running my old 8200 for nearly 18 months, only thing not working is compiz (due to crud video card!) :)

---

### Post by linux_tech on 2008-12-06
$10 wow thats a great deal, can't beat that!

---

