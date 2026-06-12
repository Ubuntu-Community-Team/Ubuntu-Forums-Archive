---
title: "Expedited, customized install?"
date: 2007-07-05
forum: Installation &amp; Upgrades
---

### Post by davidsiegel on 2007-07-05
I've been a happy Ubuntu user for a while now, and I've been doing my duty to show off Ubuntu and explain the advantages of FOSS to all of my friends. At first I was delighted when my friends would ask me to help them install Ubuntu on their computers, but now that I have ten friends who want me to do this for them, at around 2 hours of installation and setup a piece, that's at least 20 hours of work. What I would really like to do is to create a custom copy of Ubuntu with all of the settings just right (extra packages, Gnome panel applets set up just right, fonts set up nicely, preferences tweaked here and there, etc.). Once I have this customized copy of Ubuntu, I want to either turn it into a live cd/dvd installer, or install it using a USB drive (the preferred method). This way, when my friend says "I want you to install Ubuntu on my computer," I can do everything I need to do to get my friend up and running in 15 minutes or so.

Any help on this issue would be greatly appreciated by me and my friends eager to try Ubuntu!

---

### Post by Medieval_Creations on 2007-07-05
Well I haven't had the time or been brave enough to dive into creating my onw personalized Ubuntu ISO, but I know it can be done.

I've taken a some-what easier path.  I use Apt-On CD.  It copies all the deb's that you have in apt-cache (basically everything you've ever apt-get) and just had it build an ISO of all the deb's.

Then after a clean install all you really need to apt-get is Apt-On CD.  Once installed you can then use it to copy all the deb's back into your apt-cache from the ISO.  Now when you do an apt-get for something you've already installed b-4 it doesn't have to download it, it will just install it.

I use this method to when doing a clean install of all my PC's & Servers.  I just have a script that I run that will apt-get all the appz.  Not having to download everything shaved off like 2-4 hours on install time depending on the build.

I know this isn't quite the route you were looking for, but it might be a good work around in the mean time.

---

### Post by davidsiegel on 2007-07-05
That's part of what I'd like to do, but apt-get is not a major hurdle - what I'm really trying to minimize is the time I spend tweaking preferences and configuring GNOME, etc.

---

### Post by Medieval_Creations on 2007-07-05
That one has me stumped currently too... I think editing / creating your own Ubuntu ISO is what your really looking for.

My buddie has Ubuntu Hacks, from Oriely, I know it has the steps in there as one of the hacks to create your own ISO.  I'll see if I can snag it for a couple days, type it up and post it.

---

### Post by xxdeusxx on 2007-08-28
you could install and tweak ubuntu on one pc...
then backup the partition with partimage and just copy this image to all of your friends computers...

---

