---
title: "New Pulseaudio volume control applet"
date: 2009-02-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rockin_goliath on 2009-02-28
Does anyone know of a way to get the Pulseaudio mixer that was in the alpha versions a while ago back? Even if it's not going to be in the final release, I'd still like to use it.

---

### Post by lean on 2009-02-28
It is not built in at the moment, but hardcoded to the old mixer. Too bad.
If you want to use the new mixer, you have to compile your own gnome packages.

---

### Post by avb on 2009-02-28
> **rockin_goliath said:**
> Does anyone know of a way to get the Pulseaudio mixer that was in the alpha versions a while ago back? Even if it's not going to be in the final release, I'd still like to use it.


sudo apt-get install pavucontrol

thats it

---

### Post by plun on 2009-02-28
You probably mean Gnomes volume control which Ubuntu changed back to old fashion style. 

pavucontrol works.

gnome-media from svn also works, download, compile and install.

---

### Post by rockin_goliath on 2009-02-28
Thanks guys. I've been using pavucontrol, but I was really looking forward to a more native and "fewer clicks" gui. I'll think about getting gnome-media from svn.

---

### Post by hanzomon4 on 2009-03-01
Anybody got a pic of the new mixer that was dropped from jaunty?

---

### Post by rockin_goliath on 2009-03-01
This page has a few.
[https://fedoraproject.org/wiki/Features/VolumeControl]("https://fedoraproject.org/wiki/Features/VolumeControl")

---

### Post by Kosimo on 2009-03-01
anybody knows why the decision was rolled back?

---

### Post by autocrosser on 2009-03-01
Read my old post about it:  [http://ubuntuforums.org/showthread.php?t=1062561](http://ubuntuforums.org/showthread.php?t=1062561)

And the rest of the sad news here: [https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/326607](https://bugs.launchpad.net/ubuntu/+source/gnome-media/+bug/326607)

I really liked the new panel--We'll get to see it again during Karmic testing in about 2 months from now.......

---

### Post by plun on 2009-03-02
Picture from the application tab

[[img]http://ubuntu-pics.de/thumb/10390/snapshot16_J8nq0j.png[/img]](http://ubuntu-pics.de/bild/10390/snapshot16_J8nq0j.png)

Maybe the challenge is that Gnome devs must talk to Pulseudio and Alsa devs...:-k

---

### Post by bash on 2009-03-02
Btw if you want a different applet, I found this the other day:

[http://code.google.com/p/gnome-pulse-applet/](http://code.google.com/p/gnome-pulse-applet/)

Looks really sweet. I think even better than the new upstream volume control. 

Screenshots (taken from their website):

[img]http://gnome-pulse-applet.googlecode.com/files/pulse-applet-devel-9.png[/img][img]http://gnome-pulse-applet.googlecode.com/files/pulse-applet-devel-10-fixed.png[/img]

---

### Post by plun on 2009-03-02
> **bash said:**
> 
[http://code.google.com/p/gnome-pulse-applet/](http://code.google.com/p/gnome-pulse-applet/)

Looks really sweet. I think even better than the new upstream volume control. 



Yup.. I compiled latest SVN and its a good one, thumbs up !

[IMG]http://ubuntu-pics.de/bild/10396/snapshot17_8ynpUR.png[/IMG]

---

### Post by chrisccoulson on 2009-03-18
For those of you who preferred the newer gnome-volume-control-applet - it is now built again and is shipped in a new binary package:
```
sudo apt-get install gnome-volume-control-pulse
```

---

### Post by biasquez on 2009-03-18
> **chrisccoulson said:**
> For those of you who preferred the newer gnome-volume-control-applet - it is now built again and is shipped in a new binary package:
```
sudo apt-get install gnome-volume-control-pulse
```

i don't have this package on my distro

---

### Post by rudenko_ruslan on 2009-03-18
> **biasquez said:**
> i don't have this package on my distro
I don't have it too. Maybe it's located in someone's PPA? :-k

---

### Post by chrisccoulson on 2009-03-18
No, it's defaintely there. Perhaps it hasn't reached your mirror yet, or your package list is out of date

---

### Post by rudenko_ruslan on 2009-03-18
> **chrisccoulson said:**
> No, it's defaintely there. Perhaps it hasn't reached your mirror yet, or your package list is out of date
Huh, I'm using "Main Server". Updated my package list now, and still can't see this package.

:(

---

### Post by chrisccoulson on 2009-03-18
Ok, maybe I got a little bit ahead of myself then. The package has been uploaded, it just hasn't reached the archive yet ;)

[https://edge.launchpad.net/ubuntu/+source/gnome-media]("https://edge.launchpad.net/ubuntu/+source/gnome-media")

---

### Post by pferraro on 2009-03-18
> **chrisccoulson said:**
> Ok, maybe I got a little bit ahead of myself then. The package has been uploaded, it just hasn't reached the archive yet ;)

[https://edge.launchpad.net/ubuntu/+source/gnome-media]("https://edge.launchpad.net/ubuntu/+source/gnome-media")

FYI - the gnome-media 2.26 packages are built but are sitting in the acceptance queue:
[https://launchpad.net/ubuntu/jaunty/+queue?queue_state=0&queue_text=gnome-media](https://launchpad.net/ubuntu/jaunty/+queue?queue_state=0&queue_text=gnome-media)

---

### Post by rockin_goliath on 2009-03-18
As I felt myself sinking into the lava pit of 6 more months of difficult to configure audio, a developer swooped down on the wings of angels and rescued me.

Thank you devs!

---

### Post by rudenko_ruslan on 2009-03-19
**chrisccoulson**, I installed "gnome-volume-control-pulse", but how can I add [that applet]("http://code.google.com/p/gnome-pulse-applet/wiki/Screenshots") to my GNOME panel? I still have only old one :(

---

### Post by Mr. Picklesworth on 2009-03-19
Just restart your session and it will be on the notification area. (Or run gnome-volume-control-applet).

---

### Post by rudenko_ruslan on 2009-03-19
> **Mr. Picklesworth said:**
> Just restart your session and it will be on the notification area. (Or run gnome-volume-control-applet).
Thanks. I just disabled my notification area, that's why I couldn't see it ):P

---

### Post by chrisccoulson on 2009-03-19
Also, jsut to clarify - this is not the gnome-pulse-applet shown in the screenshots in this thread. This is the gnome-volume-control-applet that ships with gnome-media, and was the one that was enabled earlier in the Jaunty cycle.

---

### Post by olskar on 2009-03-19
> **chrisccoulson said:**
> Also, jsut to clarify - this is not the gnome-pulse-applet shown in the screenshots in this thread. This is the gnome-volume-control-applet that ships with gnome-media, and was the one that was enabled earlier in the Jaunty cycle.

Yes, the one we miss with all of our hearts :(

---

