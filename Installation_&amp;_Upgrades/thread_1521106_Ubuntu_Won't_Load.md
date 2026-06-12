---
title: "Ubuntu Won't Load"
date: 2010-06-30
forum: Installation &amp; Upgrades
---

### Post by sb2146 on 2010-06-30
Hi,
 
I installed the recent 10.04 upgrades this morning, was prompted to restart, and now I can't get back into Ubuntu. When turning on my computer I have the option to select Windows or Ubuntu (like normal), I select Ubuntu, it goes to the short Ubuntu command prompt (I don't remember the string) and then immediately takes me back to the screen where I select Windows or Ubuntu again. I don't even get to the screen where I can open Ubuntu in an earlier version.
 
Help! Is there something I can try to type super fast when that Ubuntu string comes up that will try to restore Ubuntu?
 
Thank you in advance!
 
Stephanie

---

### Post by zkriesse on 2010-06-30
It might be the fact that you updated. Are you trying to do a dual boot?

---

### Post by sb2146 on 2010-06-30
Nope, I've never tried to do a dual boot - I always select either Windows or Ubuntu, and every time I select to boot up Ubuntu now it kicks me back to the same Windows or Ubuntu screen over and over again . . . I've never had this happen.  I have always had the Ubuntu version screen come up so that I could default to an older version.
 
Thanks!

---

### Post by sb2146 on 2010-06-30
Further clarification - I select to boot Ubuntu, and am taken to the try (hd0,0) NTFSS:  prompt, then the screen immediately goes black, and takes me back to the screen where I select Windows or Ubuntu.  Lather.  Rinse.  Repeat.  
 
Thanks!

---

### Post by Rubi1200 on 2010-06-30
Do you have the installation CD for Ubuntu?

If yes, you can boot the computer with it and choose to try rather than install.

Once you get in click on the link at the bottom of my post and follow the instructions there before posting back here.

---

### Post by sb2146 on 2010-06-30
I don't have an installation CD for Ubuntu . . . it was installed by my brother from somehing he found online.  It has been working fine since October, then the updates this morning caused me to not be able to get in.

---

### Post by Rubi1200 on 2010-06-30
It sounds to me like an update from the previous version 9.10 to 10.04 or could this be a Wubi install?

Can you still get into Windows?

Finally, are you able to download and burn an .ISO image?

I can walk you through it if needs be.

---

### Post by sb2146 on 2010-06-30
I upgraded from 9.10 to 10.04 a month ago and updated the system patches that were prompted this morning - I'm not sure if Wubi is the original way that we installed Ubuntu.
 
I can still get into Windows.  I'm not sure how to download and burn an .ISO image - thanks for the help!!

---

### Post by bcbc on 2010-06-30
Have you replaced your wubildr yet?
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

---

### Post by mocoloco on 2010-06-30
Sounds like you might have installed via Wubi, so your Ubuntu install is inside your Windows partition.  To verify this, boot in to Windows and open "Add/Remove Programs".  If you see Ubuntu in the list then it's a Wubi install.  If you don't have any important data in your Ubuntu setup you can uninstall it from there and re-install the latest version by going to [http://wubi-installer.org/]("http://wubi-installer.org/")

Reply back and specify if it's Wubi or not, and if you need data from your Ubuntu install or not.

---

### Post by sb2146 on 2010-06-30
No, I hadn't replaced it yet - just did it, and am going to restart and try to get into Ubuntu again!

---

### Post by Rubi1200 on 2010-06-30
@ bcbc > **sb2146 said:**
> I upgraded from 9.10 to 10.04 a month ago and updated the system patches that were prompted this morning - **I'm not sure if Wubi is the original way that we installed Ubuntu**.

I think to play on the safe side it would be best to run a LiveCD and check what is going on.

Ok, first download the latest Ubuntu image here:

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Then, in Windows since you can get in there you need to burn the image to CD at the lowest possible speed. If you don't have software to do this may I suggest this:

[http://portableapps.com/apps/utilities/infrarecorder_portable](http://portableapps.com/apps/utilities/infrarecorder_portable)

It is portable, meaning no settings written anywhere, no registry entries etc.

Once you have the image burnt you need to restart the computer and set BIOS to boot from the CD. Computers differ but it is often F2, F8, or F12. In BIOS you look for boot options and simply move boot from CD to first option.

Then, once that is done run the Ubuntu CD and choose to try NOT install.

If you are successfully in (meaning at the desktop) click on the link at the bottom of my post and follow the instructions there.

Let me know if you need more help or if anything wasn't clear.

**If above works (regarding wubildr file)**** then disregard this post**

---

### Post by bcbc on 2010-06-30
@rubi I know OP isn't sure, but from what she's described it is wubi (first menu is the windows boot menu). Also, if she has a wubildr file, that's a giveaway.

But I agree she should have a live CD and might still need it now.

---

### Post by Rubi1200 on 2010-06-30
> **bcbc said:**
> @rubi I know OP isn't sure, but from what she's described it is wubi (first menu is the windows boot menu). Also, if she has a wubildr file, that's a giveaway.

But I agree she should have a live CD _and might still need it now_.

Agreed  :-)

It is ALWAYS handy to have one available, no matter what type of setup one has.

---

