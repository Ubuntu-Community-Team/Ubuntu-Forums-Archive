---
title: "Re-install but keep the home folders"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by shiznatix on 2007-04-24
I upgraded to Fiesty from Edgy with a lot of problems. Beryl messes up a lot and videos won't play if I started beryl during that session. I was kinda able to get my built in wireless working but it does not work anymore and the wireless USB that I was using in Edgy won't work anymore either. These are the big issues as they are essential to me, having a cool looking desktop that can play movies and can get wireless.

So what I want to do is just do a fresh install of Ubuntu but I certainly don't want to lose all of my awesome data. Everything that I want is in my home folder so I figure I should just get that backed up. Here are the problems / concerns / questions:

-All of my media is about 40 or so gigs. I don't have that much backup space anywhere and I don't have enough blank DVDs. Is there any way at all for me to remove everything but my home folder and re-install ubuntu without touching my home folder? This would be the best thing in the world if it was possible.

-Will obsolete or incompatible settings follow over to the new installation if I copy everything in my home folder? I don't want crappy settings following me over but I need some programs settings (like my incomplete torrents in azerus and whatnot). What is the best course of action here?

Please let me know what my options are so I can get my computer working again. Sadly for me every time I upgrade to a new version of ubuntu on any laptop I own I encounter problems. I love Ubuntu and will never go back but I just need a way to format without loosing my awesome gigabytes.

---

### Post by elcasey on 2007-04-24
The only way (that I know of) to preserve your home directory like this is by putting it on a separate partition, which I gather you did not. I used to have multiple Ubuntu partitions, but I have a second 320GB drive that I use for data storage and, you guessed it, backing up my homedir every time I reinstall (which is often, because Ubuntu hates me and my hardware).

Your best bet is to back up your critical data to DVD-Rs and take a hard look at what you absolutely cannot live without. You may think all those DVD backups or AVIs of Aqua Teen Hunger Force are irreplaceable and you could never live without them -- but you can.

Backing up 40GB of data will only take 9 DVD-Rs, and you can usually buy 50 of them for less than $20 at your local CompUSA, Best Buy, whatever. It's important to back up your critical data, whether to different partitions or HDDs or to removable media to avoid exactly this situation.

---

### Post by Big Ed on 2007-04-24
You can certainly reinstall and keep your home folder.  Boot from the cd into a live session, mount the partition that is normally /home and clean out everything that you don't want to keep.  That will get rid of old configuration files, etc.  Make sure you are looking for hidden directories/files also.

Start the install.  When you get to the partition section, choose manual and pick what partitions you want and where to mount them.  (/, /boot, /usr, etc.)  For each one, select format (or make a new filesystem, or whatever it says) but not for /home.  Just pick that partition as /home but tell it to use the existing filesystem.  It will reinstall and you will still have your data.

If you use Thunderbird and you want to keep your old e-mail, then don't delete that directory and when you are done installing, move the directories and files over.  The directory will have a bunch of strange letters.  Note the one you have now so you can identify it later.

It's actually a fairly painless process.  I haven't had to do it for Feisty, but I did it for Edgy, Dapper and (I think) Hoary also.

HTH,
Ed

---

### Post by shiznatix on 2007-04-24
> **elcasey said:**
> You may think all those DVD backups or AVIs of Aqua Teen Hunger Force are irreplaceable and you could never live without them -- but you can.

wow, I can't even begin to tell you how wrong you are :) 

Seriously though you have a point. My biggest concern is the torrents I am downloading now that are not finished. If I just copy what I have now back to the new installation and open my torrent program will it just work? I hope so...

---

### Post by shiznatix on 2007-04-24
> **Big Ed said:**
> You can certainly reinstall and keep your home folder.  Boot from the cd into a live session, mount the partition that is normally /home and clean out everything that you don't want to keep.  That will get rid of old configuration files, etc.  Make sure you are looking for hidden directories/files also.

Can I do this if the home folder is not on it's own partition? And if I am able to give it it's own partition somehow, how much space should I give it? I have a 70 gig HD so what do you think would make sense for the home folder and whatnot?

---

### Post by Big Ed on 2007-04-24
> **shiznatix said:**
> Can I do this if the home folder is not on it's own partition? And if I am able to give it it's own partition somehow, how much space should I give it? I have a 70 gig HD so what do you think would make sense for the home folder and whatnot?

Hmm, this is why /home should always be on it's own partition.

The answer to your question depends on whether you have multiple partitions or if you have everything (except /swap) on one partition.  Use "du" to find how much space is being used by your current directory structure.  That will give you an idea of how much space you need.  

[http://linux.about.com/library/cmd/blcmdl1_du.htm](http://linux.about.com/library/cmd/blcmdl1_du.htm)

Leave some extra space for packages, etc.  I normally use partitions for /boot, /home and /usr with everything else in /.  Some people like to have /var by itself also.

If you have just one large partition, I think you should be able to use parted or gparted to resize it.  I haven't tried this myself.  Do it from the live cd so your partitions are not mounted.

[http://www.die.net/doc/linux/man/man8/parted.8.html](http://www.die.net/doc/linux/man/man8/parted.8.html)

If you do have multiple partitions, then you can eliminate and remake/resize/reformat whatever ones you don't have /home on.  Just remember to not format that partition. 

Ed

---

