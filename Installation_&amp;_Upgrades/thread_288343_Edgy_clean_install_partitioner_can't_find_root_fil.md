---
title: "Edgy clean install: partitioner can't find root file system"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by Luke771 on 2006-10-29
The short version:

I couldn't install Edgy because the partitioner kept saying that no partition was set to be mounted as "/".
*why*?

The long version:

As I said in [www.ubuntuforums.org/showthread.php?t=282336 ](www.ubuntuforums.org/showthread.php?t=282336 ) I was back on Ubuntu and happy with it, so what happened?
Well, to begin with, a couple of days after I installed Dapper, Edgy was released, so I tried to upgrade and had some problems with the nVidia drivers  as reported in [www.ubuntuforums.org/showthread.php?t=285529 ](www.ubuntuforums.org/showthread.php?t=285529 ) 

So I did what I thought would be the easyest thing: I got myself an Edgy CD and started a clean install. My partitions were already set up in a way that had worked with Breezy, Dapper, Debian Sarge, Debian Etch, Slack 10.2 and Slack 11 without any problems.
I start the live CD, click install, go thru the first steps, and once at the partitioner, as I always do, I chose "Manually edit partition table"

I had a small partition for /boot, a big partition for /home and a medium-sized partition for /, (/ and swap were marked to be formatted) all of them ext2 (yes, ext2, no journaling) , a swap space and a couple of windows partitions that I wasn't going to set up in /etc/fstab anyways. 

Well, that's basically how far I got.
Once all my partition were set up, **including** the root file system, a primary ext2 partition on hda2, I click "next", I choose not to go back and assign a mount point to my NTFS partitions, I hit Next... And get an error message about "no root file system".
According to that message, no partition had "/" as mount point.

I'm pretty sure I did assign a partition to /

I double checked, retried: nothing.
I rebooted and restarted the whole install from scratch: nothing.
I also tried to find a boot option to start the installation in text mode, but I couldn't find anything like that, so I gave up and re-installed Slackware.
Now I'm thinking what I didn't think then: I had that upgrade install because I had installed the proprietary nVidia driver: if I installed Dapper again, and then upgraded right away, that may work. By the way, annother thing that may help diagnose the problem is that the first two times I installed Dapper, I got a graphical interface on a live CD, like Edgy, but the last two or three times I did that, I only got a regular Debian-like installer, though I can't remember changing anything ib the meantime.

---

### Post by Luke771 on 2006-10-29
I tried again: I installed Dapper and upgraded right away.
Btw, any idea about why my Dapper CD runs a Breezy-like text install though it did run an Edgy-like live-cd install before?
Anyways, that didn't work. I got that nVidia driver problem again; then I tried once again using the install/live Edgy CD.
It's copying files right now.

I don't know yet, maybe I'll get the same problem again after rebooting, but at least, I got the "no root file system" problem fixed.

Instead of reformatting my old partition that I wanted to use as /boot and /, this time I deleted and recreated them.
That did the trick.
The biggest of the two got the mount point "/" by default (with mandatory reformatting), the smaller one got a place in the /media directory and I changed that to /boot, then I set my biggest partition to be mounted as /home, and everything went fine.
So far.  

We'll see what will happen after the reboot.
Will I get thet nVidia problem again?

---

### Post by jpreszler on 2006-10-29
Just wanted to post that this problem is not unique. I was trying to install 
Edgy on my laptop today that previously had Slackware 10.2. I didn't want to
change the partition scheme I had because I didn't want to reformat my /home
partition. My only difference was that all of my file systems were reiserfs,
but the partitioner still couldn't detect "/". 

I tried installing Drapper and everything worked fine, so this is a problem
with the new release.

jpreszler

---

### Post by Luke771 on 2006-10-29
Rebooted and working.
So we know the trick now: in case the partitioner  gives you a "no root file system" error during install, all you have to do is delete and re-create the partition you want to use as "/".
That worked for me.

---

### Post by Ubnuut on 2006-10-29
I had the same problem, and deleting and recreating the partition resolved the problem for me too. 

I was a bit baffled first when I encountered the problem, cause with Edgy Beta version I installed on the same partition and didn't encounter this problem then. So this bug must have crept in after the Beta version.

---

### Post by Lamar on 2006-11-01
It appears that deleting and reformatting the root partition doesn't work if it's set up as a logical, rather than primary, partition. Lame.

---

### Post by rjr1049 on 2006-11-01
This is a known bug reported on launchpad (bug #67082).  And it did show up after the beta.  The release candidate had this bug but not the beta.

---

### Post by andresv on 2006-11-04
Same problem here :( - quite a bad bug. I will try tomorrow deleting the (logical) partition I want to define as / and will post the result.

---

### Post by rsambuca on 2006-11-05
There is definitely a bug in the Edgy installer not recognizing certain gParted partitions.  I found a workaround and posted it here:

[http://ubuntuforums.org/showpost.php?p=1700787&postcount=29]("http://ubuntuforums.org/showpost.php?p=1700787&postcount=29")

---

### Post by chikebum on 2006-11-05
try here

[http://ubuntuforums.org/showpost.php?p=1715851&postcount=36](http://ubuntuforums.org/showpost.php?p=1715851&postcount=36)

---

