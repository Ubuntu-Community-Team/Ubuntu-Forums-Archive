---
title: "Fiesty upgrade success?"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by rillip on 2007-04-20
I'm seeing so many threads on issues with upgrading to Fiesty that I'm affraid everyone will think it is difficult/bugged.  Maybe it is, I don't know (I'm running Dapper and don't plan to update), but I thought we should have a thread for success stories too, to keep up heart for those having issues.

So if you've had a success, let us know about it!

---

### Post by elmerfud on 2007-04-20
If you are a newbie or you are running nvidia or wireless, I'd wait a bit until people have experience sorting things out.

I updated, it wasn't trivial to get things going again.  I'm quite experienced.

---

### Post by darrenm on 2007-04-20
Its the day after release day. The forums are going to be full of people with problems. They people who don't have problems have nothing to report and are enjoying their experience :)

---

### Post by Zewbie on 2007-04-20
No comment...  which means I have not been able to update.  when I goto update manager it says '7.04 available' I click the Upgrade button a new window pops up that says welcome to Feisty Fawn.  So I click that Upgrade button.  Another window pops upand starts downloading the "UPDATE" but has yet to finish to download the whole thing,  just when it seems to be almost done I get a error in yet another pop up 'Failed to fetch [http://ubuntusoftware.info/dists/edgy/all/binary-i386/Packages.gz](http://ubuntusoftware.info/dists/edgy/all/binary-i386/Packages.gz) 302 Moved Temporarily'.  Untill the find it a new home...

---

### Post by frodon on 2007-04-20
Remember that only persons with problems post on the forum so you don't see those who haven't had any.

Look at the sticky poll in this section and you will see that for 50% no problem at all, for 25% few problems which got fixed easily and for the rest many problems (which some have solutions).

---

### Post by hackman on 2007-04-20
This happened while trying to upgrade from 6.10:

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)

so what should i do?

---

### Post by omega13a on 2007-04-20
> **hackman said:**
> This happened while trying to upgrade from 6.10:

Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz) Sub-process gzip returned an error code (1)

so what should i do?

I'm having the exact same problem. :mad: I went to go view that file in my webrowser and its there but it appears to be a text file.  Is it supposed to be a text file or a gzip archive? :confused:

**Edit:**  I'm guessing its supposed to be a gzip archive because the copy of it on the US mirror is.

---

### Post by hackman on 2007-04-20
Someone please help us!!!!

---

### Post by FastZ on 2007-04-20
Well, I have a semi-success story to share.  I downloaded the ISO and burnt it, did a fresh install on my Dell Inspiron 9300 (with ATI video) and wow, everything seems to work perfectly.  Wireless worked immediately, Desktop Effects works pretty decent (get some sketchy stuff when I hover over the menu items and the drop down menus pop up), auto-adjusted to my 1440x900 screen resolution, looks great!
 
Now, when Edgy came out, I was running Dapper on my desktop and decided to just do a dist-upgrade via Synaptic and that went fine, this time, i rdiff'd the files I wanted to keep from my desktop to my server (running edgy at the time) and then decided to do a clean install of Fiesty on there to start over (I had made so many changes to that Edgy install I was tired of it and didnt know how to get it back to normal).  The desktop has an nVidia MX440 video card and when ran the LiveCD of Fiesty, and was going to test out the Desktop Effects from the the disc, it downloaded the NVidia-glx driver or something and then told me to restart...but I didnt because I didnt think it would matter if I just went from there and proceeded with the full installation, which I did.  It installed fine, perfectly actually, but when I restarted and tried to boot into Fiesty, I get an XOrg Server BSoD and that sucks.  So I went and found my working Xorg.conf file on my server that I had previously rdiff'd over there and was looking through it and comparing it to the one that was created during the Fiesty install on the desktop.  The only thing I could see that was different between the two was the last section.  The old, working Xorg.conf had "composite" "enabled" and the new one, didnt have that at all, it had "DRI" 0666 or something like that (I dont remember exactly).  With Edgy, I had been running Beryl-SVN religiously since late last year and it worked fine.

---

### Post by hanzomon4 on 2007-04-20
My upgrade went smooth, I only had to remove and reinstall python-mutagen and exaile.

As to that problem I had it when I upgraded to edgy not sure how I fixed it...

---

### Post by hanzomon4 on 2007-04-20
[quote=jsilve1
]I had this same (very frustrating) problem. To fix it, I did this (from a Terminal (Accessories->Terminal):

apt-get clean

and then ran

apt-get update

This seemed to do the trick.

I think the problem was a result of a borked sources list download, which doesn't get updated properly on subsequent apt-get updates. Cleaning and re-updating fixed it for me.

Later...[/quote]

I found this post from 3 months back, report if it works.

---

### Post by Toadmund on 2007-04-20
What I do, and it works good for me, 
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
then after all that I go to:
[http://www.ubuntu-nl.org/source-o-matic/]("http://www.ubuntu-nl.org/source-o-matic/")
and get the basic list (quicker, get other stuff later) for the version you want to upgrade to, replace the old list in 'sources.list' making sure the previous list is completely gone (or it will conflict):
```
gksudo gedit /etc/apt/souces.list
```
then
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

And after waiting for awhile, you should be updated to the next version :)

---

