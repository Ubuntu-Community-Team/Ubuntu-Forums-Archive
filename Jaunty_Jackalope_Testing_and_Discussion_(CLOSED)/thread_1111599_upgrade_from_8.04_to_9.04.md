---
title: "upgrade from 8.04 to 9.04"
date: 2009-03-30
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by exil3d on 2009-03-30
hi there. i have ubuntu 8.04 installed on my laptop. i would like to install jaunty by it's launch.

is it possible to upgrade from 8.04 to 9.04 by dist-upgrade?

best regards

---

### Post by SunnyRabbiera on 2009-03-30
I dont think so, personally I would stick to Hardy, Jaunty offers nothing in security or anything, plus not all .04 releases are LTS.

---

### Post by Therion on 2009-03-30
> **exil3d said:**
> hi there. i have ubuntu 8.04 installed on my laptop. i would like to install jaunty by it's launch.

is it possible to upgrade from 8.04 to 9.04 by dist-upgrade?

best regards
In short, no.  You would have to upgrade from 8.04 to 8.10 and then again from 8.10 to 9.04 before you were done.  

I'm not saying you CAN'T do it that way, but it's not a process I recommend.  

If you decide you want to upgrade I would suggest a clean install.

---

### Post by graysky on 2009-03-30
Yeah, just tar up your /home and your /etc, nuke the partition and reinstall.

---

### Post by exil3d on 2009-03-31
thanks. i'lll consider that opinion and make a clean install :p.

thanks a lot.

---

### Post by wkulecz on 2009-03-31
A strong vote for "if it ain't broke, don't fix it!".  Especially on a laptop.  

Unless all you want to do is play, then the learning is worth it and I'd give dist-upgrade a try first before a nuke and clean install if necessary.

Personally, any system I need to do useful stuff with is restricted to LTS releases.  6.06 is still going strong doing what needs to be done with little effort maintaining it, I suspect it'll stay this way until LTS ends in 2011.  8.04 has improvements I'm taking advantage of, along with some new headaches, but they are just not worth the effort of updating the 6.06 systems which continue to "just work".

--wally.

---

### Post by karhulitos on 2009-04-01
I'm already planning to do upgrade from 8.04 to 9.04 (it looked and worked great on usb test install).

Now, I know I need to go via 8.10 on the way but what I do not know is what I actually need to do?

When 9.04 is published, will my upgrade manager advertise 8.10 or 9.04? Both? Help a dummy please..

---

### Post by graysky on 2009-04-01
...why not just tar-up the important stuff (/home /etc /boot /root for example), make a list of your packages (something you should do as you install things you like) and simply wipe out the drive, install Jaunty, restore the backups, download your packages?

Here is my backup script that I use for this purpose:
```
#!/bin/bash

#remove thumbnails
rm /home/user1/.thumbnails/fail/gnome-thumbnail-factory/*.png
rm /home/user1/.thumbnails/large/*.png
rm /home/user1/.thumbnails/normal/*.png

cd /home/backup
tar zcvfp backup-system-ubuntu.tar.gz /etc /boot /root
tar zcvfp backup-user1.tar.gz /home/user1
tar zcvfp backup-user2.tar.gz /home/user2
tar zcvfp backup-user3.tar.gz /home/user3

cp *.tar.gz '/media/D/New_CD/Backups'
```

---

### Post by Stason on 2009-04-01
> **graysky said:**
> Yeah, just tar up your /home and your /etc, nuke the partition and reinstall.

Really? But what would that preserve and what should be reinstalled?

1) Would that keep my 3DCude desktop and all its settings, wallpapers etc? 
2) Programs installed like kino, smplayer, cairo-dock and their settings? 
3)Nvidia drivers? 
4) Tweaks to the system like alsa settings?
5) Fake Raid setup?

I am on Gutsy right now.

thanks

---

### Post by graysky on 2009-04-02
> **Stason said:**
> Really? But what would that preserve and what should be reinstalled?

1) Would that keep my 3DCude desktop and all its settings, wallpapers etc? 
2) Programs installed like kino, smplayer, cairo-dock and their settings? 
3)Nvidia drivers? 
4) Tweaks to the system like alsa settings?
5) Fake Raid setup?

I am on Gutsy right now.

thanks

1) Is that compiz-fusion?  If so your compiz settings are saved, you only need to reinstall the compiz-fusion package under the new version.  As to wallapapers, that depends on where you're storing them.  I keep mine in ~/reinstall/wallpapers and point gnome to them from there since I never nuke my /home

2) Those programs are packages you have installed.  I keep a simple text file in ~/reinstall/packages whenever I aptitude install a package that I like, I add it to a list in that file.  That way, I can do a reinstall and simply do a '$ sudo aptitude install package-a package-b package-c ... package-x' and get them all back.  Since I backed-up my /home/user1 dir all the settings are there.

3) You'll have to either use the nvidia driver that come w/ the new install, or simply d/l them from nvidia.com and install yourself

4) System tweaks are not kept in this fashion.  They are indirectly because you're tarring up the /etc but NEVER untar that onto your live file system.  Always do it to a temp dir and manually copy over a file or better yet edit the new file with the old one  as a guide.

5) Dunno about fake RAID since I never used it.

---

### Post by karhulitos on 2009-04-03
> **graysky said:**
> ...why not just tar-up the important stuff (/home /etc /boot /root for example)

I did this once, actually copied only /home/user and result was bad. Gnome whined about something, all little things appeared not to work and basically result was to nuke .app directores from home to get them running again.
I might have done something wrong back then but afterwards I've always done an upgrade and things have been smooth enough for transition to next version to another.
This is why I ask about Hardy --> Jaunty instructions, does anybody know?

---

### Post by taavikko on 2009-04-03
> **karhulitos said:**
> 
This is why I ask about Hardy --> Jaunty instructions, does anybody know?

This should be feasible by just pointing sources to jaunty.
and dist-upgrade
this might lead to serious b0rkage!

However, I still would recommend using hardy->intrepid->jaunty
or even fresh install.

---

### Post by ghindo on 2009-04-03
I upgraded from 8.04 -> 8.10 -> 9.04, and haven't experience any problems.

---

### Post by karhulitos on 2009-04-05
> **ghindo said:**
> I upgraded from 8.04 -> 8.10 -> 9.04, and haven't experience any problems.
This is my expectation as well. Let me ask the other way as it seems I'm misunderstood.

Let's assume Jaunty has been already published.
Now I am on hardy, and if I hit *update-manager --dist-upgrade* will I only be offered upgrade to Intrepid?

And then on Intrepid will *update-manager --dist-upgrade* offer me Jaunty?

Perhaps this is so stupid question that people fail to understand what I mean?

---

### Post by taavikko on 2009-04-05
> **karhulitos said:**
> This is my expectation as well. Let me ask the other way as it seems I'm misunderstood.

Let's assume Jaunty has been already published.
Now I am on hardy, and if I hit *update-manager --dist-upgrade* will I only be offered upgrade to Intrepid?

And then on Intrepid will *update-manager --dist-upgrade* offer me Jaunty?

Perhaps this is so stupid question that people fail to understand what I mean?

-d stands for "development" and searches for +1 devel version,
and this was intrepid on hardy. after release, you'll  use "update-manager -c"
that searches for current release. (if prompt is set to normal)

Long story short. you cannot upgrade with update-manager 8.04 -> 9.04
(Only 8.04LTS -> 10.04LTS is doable)

---

### Post by cybergalvez on 2009-04-05
ok what if I down load the Jaunty ISO and burn the disk.  when I insert it into my 8.04 machine will it do the upgrade? Thats how I upgraded my current machine when I went from 8.04 to 8.10. Or will I still have to go from 8.04 -> 8.10 -> 9.04? I still have a couple of 8.04 machines around that I want to upgrade once Jaunty comes out

---

### Post by markbuntu on 2009-04-05
There was just some updates in Hardy to smooth upgrade to Jaunty so I am thinking a direct upgrade path will be offered. Testers welcome,lol!

---

