---
title: "Lubuntu Graphics Issue : Live CD : Question"
date: 2014-04-07
forum: Installation &amp; Upgrades
---

### Post by Al_Szymanski on 2014-04-07
Good day. Have already installed Ubuntu (too big) on my test system because when I booted from Lubuntu Live CD I have a display issue. I believe that I want Lubuntu as I am resource limited.
Running the Live CD version 13.10 , I find that the graphics are somewhat messed up and before I commit to installation, I'd like to see if it's a surmountable problem. 
The issue is that what I suspect is supposed to be a very pretty desktop .jpg image is painted poorly and there is corruption of the GUI in the menus, and task ( lower edge of screen) bars. I have attached a few small images to show the problem. If I make the desktop just black, it looks fine, but the GUI are still messed up. Looks to me like a sync issue with image size and display size.

Bottom line : Will this problem be correctable once I'm not running on the Live CD? Or will this just be an issue because of the display/graphics card/drivers inter-relation? Thanks to all. Hope I posted this in the correct spot. 

My system specs:
2005 Mac Mini PowerMac 10,2 ,  1.33GHz, Dual booting with yaboot, 512Meg RAM ( soon to be 1Gig ), ATI Radeon 9200
Naxa LED monitor ( fixed at 1360x768 @60Hz and both Ubuntu and Lubuntu recognize it as such, as does the Mac).

[https://www.dropbox.com/s/8kclpbuiivavuca/DSC_3405.JPG](https://www.dropbox.com/s/8kclpbuiivavuca/DSC_3405.JPG)  Whole screen image showing corrupt desktop image
[https://www.dropbox.com/s/me4t9y6pqif62mn/DSC_3406.JPG](https://www.dropbox.com/s/me4t9y6pqif62mn/DSC_3406.JPG) Bottom left corner showing pixelation of task bar
[https://www.dropbox.com/s/mhh2dit5z3s0wq9/DSC_3407.JPG](https://www.dropbox.com/s/mhh2dit5z3s0wq9/DSC_3407.JPG) Bottom right corner showing pixelation of task bar
[https://www.dropbox.com/s/ihee5ftadt9z5b1/DSC_3408.JPG](https://www.dropbox.com/s/ihee5ftadt9z5b1/DSC_3408.JPG) Gparted window showing corrupted tool bar images

---

### Post by Rex Bouwense on 2014-04-07
Wow.  Nasty.  When you downloaded the image did you do an MD5Sum?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
Did you burn the image to the CD at the lowest possible speed?
Those are the first two questions I always ask, but it looks like your video card.

I just realized that I didn't answer the question.  The image that you see using the live CD will not be significantly different from the installed one.  At least that has been my experience.

---

### Post by Al_Szymanski on 2014-04-07
Thanks Rex. Yes, I did an MD5 both before and after. I burned the DVD at the only speed available to the Mini - I suspect nothing amiss there. I will re-burn it and see what happens. Is there a tool to actually check the hash of the finished DVD / CD ? Nothing I know about.
Al

---

### Post by Al_Szymanski on 2014-04-07
Well, just to muddy the waters.. I downloaded Lubuntu 12.04 PPC , checked the MD5 sums and validated the package and it displays perfectly with no changes to the system.

I will re-download the 13.10 version and recheck the sums, and try that package again. 

It's a mystery to me why an older version of the install will work perfectly with the old box and the newer version has issues.

Al

In all likelihood, I will just install 12.04 and call the project a start.

---

### Post by Rex Bouwense on 2014-04-07
You know in 10 days the new version of Lubuntu (14.04) will be released.  While the Lubuntu version that apparently works on your mini (12.04) has technically reached End Of Life, the Ubuntu portion is still valid and is a Long Term Supported version.  If it works, use it.  Then you can upgrade from it to 14.04 when you are ready.  It too is a LTS version and you can upgrade directly from one LTS to the next without bothering with the versions in between which are almost all no longer supported anyway.  While it may not be the correct answer, I was always of the opinion that if it works do it.  Let us know how it turns out and if you have any other problems.

---

### Post by Al_Szymanski on 2014-04-08
Good day. As I stated, I re-downloaded the Lubuntu 13.10 desktop ppc iso, checked the md5 and got a validation. Then burned at slowest speed. Then booted from the LiveCD - end result... no change at all. Exactly the same display corruption as with the previous attempt. 
So, in summary, 12.04 ppc works great, perfect display both from livecd and from install, 13.10 installs, but has corrupted display as initially described. I don't think this is a problem with my video card, as two different version of ubuntu work fine as does the core Mac OS X.
I am going to stick with my 12.04 install for now - test the 14.xx when it's out, and report.

---

### Post by IvantheDugtrio on 2014-04-19
I've been having the same issue with a variety of lubuntu versions (13.10, 12.04) on my PowerMac G5. It has an ATI X800 GPU and it does the video corruption thing when I attempt an install with the default settings. 
The closest I've gotten to a working install was with Debian Wheezy using the "video=ofonly" setting at the yaboot prompt. The desktop environment would never load up though so I only got as far as using it in command line. 
There has to be some yaboot option to get the install working but I don't know of any yet.

---

