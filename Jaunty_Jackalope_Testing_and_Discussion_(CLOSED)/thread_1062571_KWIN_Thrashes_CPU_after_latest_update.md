---
title: "KWIN Thrashes CPU after latest update"
date: 2009-02-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by RIchard James13 on 2009-02-07
After the last lot of upgrades, KDE loads but then crashes after playing the opening sound. Going into the console and running top reveals that KWin is using up 50% of CPU and the rest by Xorg.

Does anyone know how to fix?

Gnome is working as a fallback.

---

### Post by inportb on 2009-02-07
Interesting... when was this update? I think I've been keeping up to date but I haven't experienced any slowness.

---

### Post by RIchard James13 on 2009-02-07
It was last night roughly in the morning in the USA. 

And it is not a slowness. The entire desktop is locking up. If you kill KWin then you kill KDE. Nothing is responding you have to go to a console which is why I am back using Gnome until I work out how to fix it. hopefully it is a minor regression and another update will fix it.

*Note:* I added the date in the subject line.

---

### Post by BackwardsDown on 2009-02-07
Yeah, KDE has stopped working for me also. Too bad, bugreport anyone?

---

### Post by gmclachl on 2009-02-07
Yeah, kde is dying for me as well. Hopefully an update will cure things

George

---

### Post by bruno666 on 2009-02-07
Kwin is working again after disabling desktop effects (kill kwin and launch system settings)

---

### Post by RIchard James13 on 2009-02-07
I can confirm that disabling "Desktop Effects" works. The program to disable it is called systemsettings. I ran it from a console in gnome.

---

### Post by minisori on 2009-02-07
It's related to this thread.

[http://ubuntuforums.org/showthread.php?t=1061919](http://ubuntuforums.org/showthread.php?t=1061919)

---

### Post by inportb on 2009-02-07
Hm... interesting. Might be a video-related problem? because my desktop has been working just fine. No slowness *and* no crashes.

---

### Post by minisori on 2009-02-07
It was the update of this package.

> xserver-xorg-core

---

### Post by BackwardsDown on 2009-02-07
How can I disable the desktop effects without having to install gnome? Can I find an option in a configfile somewhere?

edit: Found it, its in ~/.kde/share/config/kwinrc

---

### Post by Kevbert on 2009-02-09
> **BackwardsDown said:**
> Yeah, KDE has stopped working for me also. Too bad, bugreport anyone?

I've recently raised a [[COLOR="Red"]bug report[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/326559") on this. Please confirm and add comments as required.

---

### Post by minisori on 2009-02-09
> **BackwardsDown said:**
> How can I disable the desktop effects without having to install gnome? Can I find an option in a configfile somewhere

Someone said this, maybe works for you:

[http://ubuntuforums.org/showpost.php?p=6692881&postcount=23](http://ubuntuforums.org/showpost.php?p=6692881&postcount=23)

Kevbert:

The bug is already reported, if you read the post i told you.

---

### Post by Kevbert on 2009-02-09
> **minisori said:**
> Someone said this, maybe works for you:

[http://ubuntuforums.org/showpost.php?p=6692881&postcount=23](http://ubuntuforums.org/showpost.php?p=6692881&postcount=23)

Kevbert:

The bug is already reported, if you read the post i told you.

Just to clarify. I have not enabled compiz on Kubuntu and it is not running in the background. It's kwin and xorg that are the problem. So if I run
```
ps ax | grep compiz.real
```
I get no reply. 
If I do the same in Ubuntu Jaunty I get the problem with compiz.real and have to turn it off to continue starting a new session, hence a new bug report. It may be the same, bug or inter-related as the symptoms are similar but not the same. It may still be due to driver interaction.  Edit: I've found that all these bugs are duplicates of LP [[COLOR="Red"]326344[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/326344"). This bug details the problem in both Kubuntu and Ubuntu, and my bug report is a duplicate of this.
Cheers
Kevin.

---

### Post by minisori on 2009-02-09
Noone said it's compiz, it's a xorg error when using direct rendering. So that bug affects to compiz, kwin and whatever compositor using direct rendering.

Sorry if i made you missunderstand it in the previous posts.

---

### Post by gmclachl on 2009-02-09
I just pulled down some updates and normal service seems to have been restored. I now have desktop effects back

---

### Post by caryb on 2009-02-09
I'm connected to the "main" server but my effects are still pooched:confused:

Cary

---

### Post by Kevbert on 2009-02-10
> **caryb said:**
> I'm connected to the "main" server but my effects are still pooched:confused:

Cary
Are you sure you&#8217;re actually running xorg-server - 2:1.5.99.902-0ubuntu5? 
To check, run 
```
grep ^xorg-server /var/log/Xorg.0.log
```
(Thanks to Ander Kaseorg for this info).

---

