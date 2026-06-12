---
title: "Cannot get past &quot;unknown user id (0)&quot; during install from CD"
date: 2011-05-11
forum: Installation &amp; Upgrades
---

### Post by ubix on 2011-05-11
Due to the flaws in 11.04 (Natty) I decided to reinstall earlier 10.10 release. However, when reading the installation CD, I can not get past the following error message:

```
(process: ###) Glib Warming **: getpwuid_r(): failed due to unknown user id(0)
```

I tried about 10 times even by disabling hard drive in CMOS, in case my current Natty installation would be interfering with no luck.

I tried also two releases older Lucid (10.04) and I get the same behaviour.

I do not see any reason for this to start to happening now, after I was able to install my previous releases without problems. I upgraded to the problematic Natty release online.

Does anybody know how to solve this problem?

---

### Post by mörgæs on 2011-05-11
Try post 176 in this thread
[http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231)

---

### Post by ubix on 2011-05-11
The post you gave me above is interesting, however it does not make sense, with regards to my experiences. Namely, why would this *"regular ISO"* as you call it, have a problem now but not when I first installed it? I had been able to install Maverick (10.10) from the same CD as this time on the same hardware (I only then screwed up by updating to Natty over the Internet).

Also, I wish to avoid automatic installation because I wish to preserve my disk-partition layout and all the data outside /root, /boot, /usr, and /var i.e. in partitions I created manually. Besides I have no clue what will the code **"apt-get install ubuntu-desktop"** do. 

I want to install entire Maverick not just the desktop, since Natty has some very nasty bugs that nobody who matters seem to know about. Particularly I do not like the numerous screw-ups in notification mechanism that effect language and keyboard management, Skype, and even periodically block the mouse events. Also file management, trash and Evolution are all half broken! My Natty is practically unusable and I just want to get rid of it.

---

### Post by mörgæs on 2011-05-12
> **ubix said:**
> 
I want to install entire Maverick not just the desktop 

This is what **apt-get install ubuntu-desktop** does. 

I can not explain why your CD worked in the first attempt but not now.

You can reuse the old partition layout if you want to.

---

### Post by ubix on 2011-05-15
**mörgæs**, thank you for your help. You have helped me much more than you could so far reckoned from our conversation. In fact the following post **#31** and not so much your **#176** in the thread [http://ubuntuforums.org/showthread.php?t=1443231](http://ubuntuforums.org/showthread.php?t=1443231) you gave me solved my problem. 

In the past few days I was busy rolling back to previous Maverick release. This is not a small task when you are reinstalling entire OS. I recovered all my data except few e-mails from the week I had been running Natty. I just didn't want to risk contaminating Maverick with Natty's problems and restore its e-mail on the rollback.

What is more interesting is the CD screw-up. It surely looks like the screw up could be a sabotage! By tweaking the hardware, I was able to recover not with different but with the same hardware.   

**mörgæs**, thank you again very much for your hints :P :P :P

PS:

> **mörgæs said:**
> This is what **apt-get install ubuntu-desktop** does. 

I can not explain why your CD worked in the first attempt but not now.

You can reuse the old partition layout if you want to.

Forgive my my ignorance but there isn't any identification of the release in the following command: **"apt-get install ubuntu-desktop"** !??? Besides, I doubt that this would cleanup the mess introduced by the upgrade on the first place, unless it would allow to  format the /root, /boot, /usr, /home, and /var, ...

---

### Post by mörgæs on 2011-05-15
Good you got it solved.

The command is supposed to be run after a fresh install using the minimal ISO, which defines the release number.

---

