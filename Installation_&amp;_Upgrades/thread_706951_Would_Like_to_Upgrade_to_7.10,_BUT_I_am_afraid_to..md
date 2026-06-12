---
title: "Would Like to Upgrade to 7.10, BUT I am afraid to."
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by Pepse3 on 2008-02-24
I would like to upgrade to KUBUNTU 7.10 Gutzy, but I am afraid to because I don't want to lose everthing on this box.  I mean with Mandriva it was easy and usually pretty safe.  Since I have only been with Kubuntu for almost a year I would like to keep up like I did with Mandrake/Mandriva but since it is an internet download and not an upgradeable CD or DVD like Mandriva I am a bit worried something will screw up between here and there (where ever there is). And since this is my main box I have a lot of stuff to worry about.  My win HDD is not as much a main part of what I do and save as my Linux boxes always have been for the last 7 years.  And yeah I've screwed up a few upgrades and I am just getting tired of losing everything and having to start over.  Yeah I do back up stuff to CD's but I usually don't waste the time to put the stuff back in except for bookmarks.  SO, I am asking if it safe, 4 months later, to upgrade to KUBUNTU 7.10 G/G.  AND if it is thought to be safe/stable should I use the UPGRADE button that shows up after downloading updates?  

  I do have high speed ineternet.

 REMEMBER THIS IS KUBUNTU, NOT ubuntu.  And don't whine about the caps.  TOO many people don't completely read what they're looking at.  I've been dealing with that almost as long as I've been on the 'net.

Later. Pepse.

---

### Post by pytheas22 on 2008-02-24
I had some problems trying to upgrade from 7.04 to 7.10 over the Internet--specifically, compiz got messed up.  Otherwise there was no serious damage to the system, and I probably could have fixed compiz if I'd tried hard enough, but I just ended up doing a fresh install because it seemed easier.  For most people, however, upgrading works fine.  So you should evaluate how much of a risk it is to you; you could also search the forums for some of the common problems in the latest upgrade to see if they're likely to affect your hardware and setup.

Another thing to keep in mind is that if you install your /home directory on a separate partition from the rest of the system, you can do a fresh install without losing any of your personal settings.  I've done this for a long time and it works great.  You still have to reconfigure the system as a whole after a reinstall, but all of your bookmarks, preferences, personal files and so on are not touched.  If you end up doing a new install, you might want to consider setting the system up in this way so that in the future it will not be as much of a problem.

Also, be aware that you'll get an error the first time you try to log in to KDE if you put /home on a separate partition, but you just need to run a couple of chown commands and it fixes the problem till the next reinstall.

---

### Post by shad0w_walker on 2008-02-24
I believe if you download the alternate install CD there is an option to upgrade your system using that.

---

### Post by Pepse3 on 2008-02-25
pytheas22,

 "  Another thing to keep in mind is that if you install your /home directory on a separate partition from the rest of the system, you can do a fresh install without losing any of your personal settings. I've done this for a long time and it works great. You still have to reconfigure the system as a whole after a reinstall, but all of your bookmarks, preferences, personal files and so on are not touched. If you end up doing a new install, you might want to consider setting the system up in this way so that in the future it will not be as much of a problem."

  Yeah, I wish Kubuntu would've had that setup of having a separate partition for /home like Mandriva.  Made things easier.

  shad0w_walker,
  
  I thought I had seen something about that CD on Ub's web but just dismissed it as what I downloaded last fall.  I guess I'll go back and look and see.  Is it similar to what pytheas22 is saying as it would give me 3 partitions instead of 2?

  The descript of your baby looks impressive.

Later. Pepse.

---

### Post by pytheas22 on 2008-02-25
The alternate CD is just a text-only installer meant for systems without enough memory to run the live CD.  It may also indeed have an option to upgrade your installation; I don't remember.

To get three partitions, you need to set up the partitions manually instead of letting the installer do it for you, and make sure that you create one with a mountpoint of /home and the other with a mountpoint at /

---

### Post by shad0w_walker on 2008-02-25
If memory serves there is an upgrade script included on the alternate disc to allow upgrading.

---

### Post by zvacet on 2008-02-25
> Yeah, I wish Kubuntu would've had that setup of having a separate partition for /home like Mandriva.

All ubuntu flavors have that option,but you didn´t use it when you partitioned.You can make separate home following [this.](http://www.psychocats.net/ubuntu/separatehome) Alternate Cd looks like better option,because you will allways have CD if something goes wrong.But that is just my opinion.

---

### Post by Pepse3 on 2008-02-25
Ah, what about swap-space? Don't I need a partition  for that?  Can I make a bootable CD or DVD of my Kubuntu, and just reload it if I screw up?  

Later. Pepse.

---

### Post by pytheas22 on 2008-02-25
Yes, you would want an additional swap partition.  To back up your system, see this thread [http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087) , which explains how to save everything as a tarball.  There are other options as well, like ghosting the image of your disk, but I'm not sure if that can be done with free software.

---

### Post by Pepse3 on 2008-02-26
I can't seem to find a link for the KUBUNTU alternate CD.  Or do I use the ubuntu alternate CD and hope it works for upgrading KUBUNTU?

Later. Pepse.

---

### Post by Chappy7777 on 2008-02-26
> **Pepse3 said:**
> I can't seem to find a link for the KUBUNTU alternate CD.  Or do I use the ubuntu alternate CD and hope it works for upgrading KUBUNTU?

Later. Pepse.
=================

I would have thought someone would have asked you this since it's the first thing that comes to mind. 

Try running 7.10 as Live CD. If you have no issues w/it, if everything works fine, the go ahead and install it. Or don't. Maybe there is much more to your question than my thought. 

I know I would never install Ubuntu on any system until I'd tried it as Live CD first. maybe a few times. One thing for sure, if it won't work as a Live CD, then I would NOT install it. I'd rather run a tried and true happy system like I have here now, than a newer version that is buggy, or doesn't like my soundcard, video, etc.

---

### Post by zvacet on 2008-02-26
[Here](http://releases.ubuntu.com/kubuntu/gutsy/)

---

### Post by pytheas22 on 2008-02-26
> Try running 7.10 as Live CD. If you have no issues w/it, if everything works fine, the go ahead and install it

this is of course a good way to make sure that 7.10 would work--but keep in mind that there could be weird issues caused by upgrading rather than doing a fresh install.  I think that this is a major part of the thread-starter's concern.

---

### Post by Pepse3 on 2008-02-27
First I will thank zvacet for the link.  I guess I wasn't lookin' deep enough. Again, my thanks.

  Now as for the other 2.  Pytheas22 says it right.  Yes, I have concerns about 7.10.  In hopes that 4 months later most of the bugs are worked out.  Especially since I just want to upgrade to 7.10 from 7.04.  I did download and run/install the live CD on a smaller HDD in Oct.  It ran out pretty good, but after coming here to the boards I see people freaking out over various bugs.  So, I decided to wait.  And now it seems to be worth it because now there is an upgrade (alternate) CD available.  Altho I probably could've ran 7.10 back then with very minimal probs because ever since day 1 with Linux I have "always" made sure that what I put in any of my computers is Linux compatible.  And even if it costs a little more I will go that route to save on headaches.  

  So, I will go and download that Kubuntu alternate CD and probably run it tomorrow.  Come to think of it I will get out a small HDD and put 7.04 on it and then go with the 7.10 upgrade for practice.  I will post as soon as I can on the progress.

Later. Pepse.

---

