---
title: "Upgrading form Karmic Alpha 6 to Beta"
date: 2009-09-29
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by ErikEhlert on 2009-09-29
Hi, I just got a new computer in my room up and going, and I don't know if I should install a stable of Kubuntu 9.04, just like my laptop, or install Karmic Alpha 6, since it will go into Beta TOMORROW.

If I install Karmic A6 then I can upgrade to Beta without doing a full re-install right? As in I won't lose my other various files?

Edit: Oh, if I go from Alpha to Beta I still keep all my other files, it just installs some additional packages, gah I am such a noob XP

---

### Post by danns on 2009-09-29
That is completely up to you.  You can install Jaunty and upgrade to Karmic from there or just go straight to Karmic.  

If you install the alpha when you do an upgrade you'll get the updated packages that are released in the beta.

---

### Post by darco on 2009-09-29
> **ErikEhlert said:**
> Hi, I just got a new computer in my room up and going, and I don't know if I should install a stable of Kubuntu 9.04, just like my laptop, or install Karmic Alpha 6, since it will go into Beta TOMORROW.

If I install Karmic A6 then I can upgrade to Beta without doing a full re-install right? As in I won't lose my other various files?

Well actually the first it comes out....

darco

---

### Post by ErikEhlert on 2009-09-29
Oh, I see, well, I didn't know if Alpha and Beta upgraded through downloading some packages or in the sense of installing, then keeping other various files (i.e. files in my Home folder), or if it just totally cleared everything and re-installed from scratch. 

I wanted to really know if I should download other important files for my computer before I upgraded to Beta, which I see now I can do if I went to Alpha for today.

Thanks, Q Has been A'd :D

---

### Post by ErikEhlert on 2009-09-29
> **darco said:**
> Well actually the first it comes out....

darco

Ack, my computers calendar

Well, two days, yeah. Still, its fairly close.

---

### Post by louieb on 2009-09-29
lol - do you feel lucky? Upgrades go smooth most of the time. Just be prepared to get a lot of updates daily.  Last minute updates to multiple packages have happened in the past. Don't see any reason this time would be different.

Anyway notices you will want to see are posted in the Karmic Development Section of th forum. Including if you can / should upgrade from Alpha to Beta.

---

### Post by Sef on 2009-09-29
Moved to Koala Testing.

---

### Post by novafluxx on 2009-09-29
I'm going to do a clean install of the Beta, then just do normal update from there, until alpha 3 or beta 1 of Lynx :-D

---

### Post by ErikEhlert on 2009-09-30
> **novafluxx said:**
> I'm going to do a clean install of the Beta, then just do normal update from there, until alpha 3 or beta 1 of Lynx :-D

Yeah, I also found out I don't have a blank CD, so I will probably go buy one or burn a DVD at my moms by the time beta of Karmic releases.

---

### Post by VMC on 2009-09-30
> **ErikEhlert said:**
> Yeah, I also found out I don't have a blank CD, so I will probably go buy one or burn a DVD at my moms by the time beta of Karmic releases.

Why not use DVD/RW's. that way you can re-use them multiple times. I only use write once cd/dvd/s for finals or something I plan on keeping for a long time.

---

### Post by dadedo123 on 2009-09-30
I'm not getting much updates the couple of days. They're are all less than 1 mb in size. lol

---

### Post by &#1057;&#1090;&#1088;&#1072;&#1085;&#1085;&#1080;&#1082; on 2009-09-30
Did you tried
$ sudo apt-get dist-upgrade ?
 
btw I like flash drivers for installing gnu/linux. it's at least 10 times faster than cd seek time

---

### Post by MonsterTrimble on 2009-09-30
Actually, I think you should go to 9.04 and wait.

1) You're new to this and if something breaks you're toast
2) You're on a laptop and those things break stuff left right and straight

I'm running Kubuntu Karmic Alpha 6 on my desktop at home (AMD Sempron 1.6 Ghz/1 GB RAM) and I have found it to be not so stable even now. It does a lot of bizarre restart crashes and things just aren't together like they should be. Frankly, the only reason I upgraded from Jaunty was because I couldn't get the facebook plugin for Kopete to work otherwise. Now that is generally does I'll stick to the 'stable' stuff.

My $0.02, YMMV

---

### Post by ranch hand on 2009-09-30
> **MonsterTrimble said:**
> Actually, I think you should go to 9.04 and wait.

1) You're new to this and if something breaks you're toast
2) You're on a laptop and those things break stuff left right and straight

I'm running Kubuntu Karmic Alpha 6 on my desktop at home (AMD Sempron 1.6 Ghz/1 GB RAM) and I have found it to be not so stable even now. It does a lot of bizarre restart crashes and things just aren't together like they should be. Frankly, the only reason I upgraded from Jaunty was because I couldn't get the facebook plugin for Kopete to work otherwise. Now that is generally does I'll stick to the 'stable' stuff.

My $0.02, YMMV
+1

I am quite excited about 9.10 and think it is going to be great.  There is an awful lot of stuff not ready yet.  I think that there is quite a bit of breakage still ahead.

Jaunty is nice and stable.  Install Jaunty on 2 partitions (/ and /home). Wait for Karmic to release.  Upgrade.

---

### Post by archiesteel on 2009-09-30
> **ErikEhlert said:**
> I wanted to really know if I should download other important files for my computer before I upgraded to Beta, which I see now I can do if I went to Alpha for today.

Karmic has been running very well for me so far, but you should *always* back up files before doing a major upgrade, just in case...

Side note: with USB hard drives being so cheap these days, a complete system backup is just a command away (provided you boot from CD-ROM or a USB key):

```
$ sudo -s
# dd if=/dev/sda of=/media/YOURDISKSNAME/sda_backup.img conv=sync,noerror bs=64K 
```

(Note, if your primary HD is /dev/hda, change command accordingly...also, YOURDISKSNAME should be replaced by the name that appears when you plug the external HD in.)

---

### Post by GARoss on 2009-09-30
> **&#1057 said:**
> Did you tried
$ sudo apt-get dist-upgrade ?


Is this (*sudo apt-get dist-upgrade*) what I type in the terminal if I want to upgrade from Ubuntu 9.04 AMD64 to Ubuntu Karmic Beta 9.10 AMD64, rather than a clean install?

---

### Post by archiesteel on 2009-09-30
> **GARoss said:**
> Is this (*sudo apt-get dist-upgrade*) what I type in the terminal if I want to upgrade from Ubuntu 9.04 AMD64 to Ubuntu Karmic Beta 9.10 AMD64, rather than a clean install?

Here's my preferred method to upgrade from 9.04 to 9.10. First, make sure the repository is updated. From your Ubuntu desktop, open a terminal window and type the following command:

```
$ sudo apt-get update
```

Then, make sure Update Manager is up-to-date:

```
$ sudo apt-get install update-manager
```

Finally, run the Update Manager with the '-d' option (to update to the latest development release):

```
$ sudo update-manager -d
```

You should see a note in the top portion of the window that says "New distribution release '9.10' is available". Click the Upgrade button and follow the instructions.

---

### Post by rburkartjo on 2009-09-30
arch tks for the info

---

### Post by tjeremiah on 2009-09-30
Alpha > Beta > Final is what im doing. Dont feel like starting the lengthy install process again.

---

### Post by rburkartjo on 2009-09-30
tj that is what i am also doing hopefully no more crashes like the x problem with a4-a5

---

