---
title: "[SOLVED] Updating Drivers and Booting issue"
date: 2008-10-06
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by WakkaOwnages on 2008-10-06
Hi, i'm trying to update drivers on Kubuntu 8.10 i click on Activate Window on version 177 (Screen 1) and it asks me to authenticate (Screen 2), i do and then i click activate again and it just freezes in there, what can i do? Is there any other option to install this driver?

Another issue is when kubuntu is booted (randomly) it gives me a lot of non-stopping beeps since "Waiting for boot file system" till it completely load or till it freezes, this just happens randomly, could it be hardware related? Or it could be a bug of the new 8.10 version? Note that this has never happened with any other version of Ubuntu/Kubuntu.

Thanks in advance

**Screen 1**

[img]http://ubuntuforums.org/attachment.php?attachmentid=87537&stc=1&d=1223334766[/img]

**Screen 2**

[img]http://ubuntuforums.org/attachment.php?attachmentid=87538&stc=1&d=1223334766[/img]

---

### Post by WakkaOwnages on 2008-10-07
Bump

---

### Post by jerome1232 on 2008-10-07
I had a similiar thing happen to me, I just updated the system, then it started working. (this was under Gnome not KDE) So my first suggestion is check the update manager make sure you've updated.

---

### Post by Sef on 2008-10-07
Moved to Ibex forum.

---

### Post by WakkaOwnages on 2008-10-07
> **jerome1232 said:**
> I had a similiar thing happen to me, I just updated the system, then it started working. (this was under Gnome not KDE) So my first suggestion is check the update manager make sure you've updated.

I updated all my system but it keeps happening randomly, but now i get another weird thing, when the system doesnt freeze (and doesnt start the non-stopping beep thing), before the login screen appears i get a green messed up screen and then after a few seconds i finnaly get the login manager.

About the driver issue it keeps unsolved i tried many different ways but until now i was unsucesseful.

i'll try to make a video of what keeps happening when booting and upload it on youtube, it may help. 

Regards

---

### Post by dabl on 2008-10-07
I gave up on the "Hardware Drivers" aka jockey-kde method, and installed the downloaded Nvidia driver 177.78 on mine.  It works fine that way. YMMV, of course.

---

### Post by WakkaOwnages on 2008-10-07
By the way my system info is:

**Asus M70Vseries** notebook

**VIDEO CARD:**

Manufacturer :		Nvidia Corp  (ASUSTeK Computer Inc) 

Model :	                NVIDIA GeForce 9600M GS  

Bus Type : 	        PCI-Express 

Total Memory :		512 MB 

Texture Memory : 	1779 MB 

Processor :		GeForce 9600M GS  Converter :		Integrated RAMDAC 

Refresh Rate (min/max) :59/59 Hz 

**CPU:** 

Type :			Intel Mobile Core 2 Duo 
Internal Specification :	Intel(R) Core(TM)2 Duo CPU     P8600  @ 2.40GHz 
Model Number :		P8600 
Codename :		Penryn 
Revision :		M0 
Technology :		0.045µ 
CPU ID :		6.7.6 
CPU IDEx :		6.17.6 
Microcode :		MU06760C 
Mobile :			Yes 

**MAINBOARD:**

Manufacturer :		ASUSTeK Computer Inc. 
Product :		M70Vm 
Version :		1.0 
Serial Number :		BSN12345678901234567 
Support MP :		Yes, 2 CPU(s) 
Version MPS :		1.4

---

### Post by WakkaOwnages on 2008-10-07
> **dabl said:**
> I gave up on the "Hardware Drivers" aka jockey-kde method, and installed the downloaded Nvidia driver 177.78 on mine.  It works fine that way. **YMMV**, of course.

Sorry, i'm still a bit noob on ubuntu what's YMMV?

And can you tell me what steps to follow so i can manage to install the driver properly?

Thanks in advance

---

### Post by Kevbert on 2008-10-07
It may just be that the nvidia download is a bit slow, please be patient.

---

### Post by WakkaOwnages on 2008-10-07
> **Kevbert said:**
> It may just be that the nvidia download is a bit slow, please be patient.

But wasnt supposed to appear something when i click on activate?

---

### Post by Kevbert on 2008-10-07
If you've not activated anything else and haven't yet been prompted for a password, that password prompt should appear almost immediately.  The download is very slow (probably due to many of us updating drivers for the latest kernel). It was the same at one stage for Hardy.  If you still get problems it may be worth checking [[COLOR="Red"]launchpad[/COLOR]]("https://launchpad.net") to see if a bug has been raised.

---

### Post by WakkaOwnages on 2008-10-07
> **Kevbert said:**
> If you've not activated anything else and haven't yet been prompted for a password, that password prompt should appear almost immediately.  The download is very slow (probably due to many of us updating drivers for the latest kernel). It was the same at one stage for Hardy.  If you still get problems it may be worth checking [[COLOR="Red"]launchpad[/COLOR]]("https://launchpad.net") to see if a bug has been raised.

I am prompted for a password to authenticate as i show on screen 2, after the authentication nothing else happens.

---

### Post by WakkaOwnages on 2008-10-07
Check out my video about the booting and leave an answer.

[http://www.youtube.com/watch?v=XHdR65Lti1g](http://www.youtube.com/watch?v=XHdR65Lti1g)

I hope it helps solving the problem. It only happens with this Ubuntu and Kubuntu including the live cd, the only exception is that with the live cd it ALWAYS happens.

I also found some reports that seems the same bug as mine, so i left a comment on launchpad.

[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/279187](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/279187)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/160509](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/160509)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255590](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/255590)

---

### Post by WakkaOwnages on 2008-10-11
Solved the driver update with the 2.6.27-6-generic, about the beeping i solved it by disabling the splash screen.

---

### Post by cjazz on 2008-10-11
> **WakkaOwnages said:**
> Sorry, i'm still a bit noob on ubuntu what's YMMV?


Your mileage may vary.

---

### Post by Efros on 2008-10-14
One of my machines beeps continuously during bootup only stopping when it gets to the first screen of the gui. The display seems to be a bit funny too on that machine, the monitor actually switches off for a while during bootup and then comes back on for the final stage onto the desktop. V weird.

---

