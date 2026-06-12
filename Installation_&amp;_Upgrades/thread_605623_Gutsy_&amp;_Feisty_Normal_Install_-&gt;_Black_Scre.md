---
title: "Gutsy &amp; Feisty Normal Install -&gt; Black Screen, Gutsy Alternate -&gt; No GRUB"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by mtdewulf on 2007-11-07
So I built a new computer a few weeks ago and installed vista before Gutsy was out.  Everything is currently working fine (with Vista).  The important specs are of my system are:

AMD X2 4400+
2GB Ram 
nVidia GeForce 8600 

I went to install gutsy on this machine and I ran into the black screen problem.  I read around on the forums here and it was suggested to change the boot options on the live cd to "nosplash".  I tried that and a few other suggestions, but no luck - X would not start and I still had a black screen. 

Final suggestion was to download the alternate CD and try that since it does not use X.  I tried that last night, and everything seemed to work fine.  Install said it completed and told me to eject the disk.  However, when I restarted the computer, *nothing* would boot (No vista, no ubuntu, no grub).  It looked like GRUB had failed.  I tried installing again to make sure this wasn't a fluke, but got the same result.

Finally, I decided to just install Fawn and then to the upgrade from synaptic.  However, when loading the feisty install, I got... another black screen!  At this point, I gave up and repaired the mbr to boot back to Vista.  

I would really like to install Gutsy, but don't know how it is possible?  Has anyone had a similar experience to this and solved it?  

thanks,
mike

---

### Post by tettayes on 2007-11-07
yeah when i upgraded to gutsy from feisty, i could not start the latest version, it said like grub could not be mounted on unknown block or something... but i still could run feisty by choosing that option at the start up.
however, i did not like the way it ran, so i basically formatted my whole disk to start over with feisty, and now it runs fine, too afraid to upgrade to gutsy again, so i am sticking with feisty!

---

### Post by mtdewulf on 2007-11-07
This is a bump / addition.

I imagine that the various problems I listed above are not all related.  Has anyone solved any of them?  I just need to fix one to get my ubuntu working.

---

### Post by TihSon on 2007-11-07
I have a new Thinkpad I was planning to install Kubuntu 7.10 onto that is now instead running Mandriva 2008, all because of this bug. I also tried Fiesty, and I also failed to get anything usable. I know this isn't much help to you, but so far I have found nothing in the forums that worked, and the devs are not talking yet. I hope it gets fixed soon, as I plan on this laptop being my main system, and I wanted Kubuntu on it. If I am forced to keep this current OS on it, I will have to commit to it December 1st. (I am moving and will need to migrate daily stuff somewhere.)

---

### Post by mtdewulf on 2007-11-07
So I fixed the black screen problem by following the instructions of this post:

[http://ubuntuforums.org/showthread.php?t=606076](http://ubuntuforums.org/showthread.php?t=606076)

Using the "envy" script worked well.  I had edit /etc/apt/sources.lst to include all repos.  Then run apt-get update.  Use gdebi to install the envy script.

---

### Post by dave61430 on 2007-11-07
See problem #16895 here
[https://answers.launchpad.net/ubuntu/+questions?start=300&batch=75](https://answers.launchpad.net/ubuntu/+questions?start=300&batch=75)

Dave Cohen

---

### Post by mtdewulf on 2007-11-07
[http://ubuntuforums.org/showthread.php?p=3728185#post3728185](http://ubuntuforums.org/showthread.php?p=3728185#post3728185)

So this thread talks about the boot issue I was having with feisty. Turns out I had it with gutsy when I got it up.  Fixed by adjusting the boot settings on my foxconn motherboard.

---

