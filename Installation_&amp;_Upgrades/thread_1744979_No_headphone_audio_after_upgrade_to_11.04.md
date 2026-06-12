---
title: "No headphone audio after upgrade to 11.04"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by DestroiTe on 2011-04-30
Hi guys!

After upgrade to 11.04, my headphones won't work when connected to the front audio jack.

I checked alsamixer and they aren't muted. Switching to "analog headphones" on the volume icon didn't did anything. I can only get audio from the rear port.

---

### Post by mörgæs on 2011-05-01
How does the machine work in a live boot?

---

### Post by DestroiTe on 2011-05-01
I haven't tried that, I upgraded from 10.10 so I don't have a live CD.

---

### Post by mörgæs on 2011-05-01
Yes, I expect that is the problem.

It is good to have a CD around for troubleshooting. You can download it in no time from a torrent.

---

### Post by DestroiTe on 2011-05-01
Ok, I downloaded it. Should I do a clean install or is there an easier way to fix this?

---

### Post by DestroiTe on 2011-05-22
I've downloaded the CD and made a clean install, but I still can't get no sound from my front audio jack.

---

### Post by mörgæs on 2011-05-22
Since the problem is also in a fresh install, it is a bug and should be handled in Launchpad (the Ubuntu developers do not follow the debate here). 

If you google **headphone site:[https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)** , you will find the present bug reports. If one of them is similar to your problem, it would be good if you could confirm it.

---

### Post by Loganiii on 2011-05-23
I've got the same issue running an 11.04 upgrade from 10.10 on a Toshiba Satellite 655D.  

Found it's been reported at Launchpad, and is being worked on now.  [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/779307]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/779307")

---

