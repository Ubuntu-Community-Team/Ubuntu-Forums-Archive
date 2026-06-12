---
title: "upgrade from 10.10 t0 11.04"
date: 2011-08-13
forum: Installation &amp; Upgrades
---

### Post by Argon99 on 2011-08-13
Hello All
  I am the sysadmin for my wifes computer.  I put Ubuntu on it for her in the hope that she would learn linux and Ubuntu.  Well so far she has only started to learn Linux.

I did an upgrade to 10.10 from the sysadmin> upgrademamager but all I got was up to 10.10.  I would like to go all the way to 11.4.  This system has been running 10.x for a long time.  But when I try and use the 
"How can I upgrade to the latest version of Ubuntu?" help page all I can get to is 10.10.  But I would like 11.4

Is there a way to have apt do that for me or do I have to use a CD?  I am currently downloading the CD and will do that if I have to.  I am backing up the windows stuff as well as all the home dirs to an external hard drive.  That should be done in a couple more hours.  So when I wake up it should be ready for the update.

Can I edit the sources file and have it upgrade from that?  Or would it be best to use the CD?  I noticed that I could also use a USB stick.  For those that read this here is a good tidbit of info.  I have a bunch of usb thumb drive.  Most are slow.  But I have a couple, they are more expensive then most, that are as fast as a hard drive.  They are made by Patriot.  I have a 4 and 8 gig version.  I put a version of linux on the 4 gig and can't tell the dif from a hard drive system.  So if anybody is looking for a super fast USB drive get Patriot.  You won't regret it.  I love mine.

So what is the best way to update from 10.10 to 11.4???

TIA
Argon

---

### Post by drpjkurian on 2011-08-13
Hi
You can upgrade to from 10.10 to 11.04 through Update manager.

---

### Post by garvinrick4 on 2011-08-13
Here is software sources look at bottom where it says "any new version" or "normal releases". Do believe
you have to have that setting to get the next version thru update manager. In update manager hit settings will get you to software sources.

---

### Post by garvinrick4 on 2011-08-13
> Can I edit the sources file and have it upgrade from that?There are many methods of updating sources.list and doing a dist-upgrade but
Ubuntu says preferable way is through update manager.

## For me it is just so much cleaner to do a fresh install instead of dist-upgrading. Right now 11.04 is a real
nice image and very, very stable. Takes more time to dist-upgrade a 1000 packages as it does to
install fresh and update and install ubuntu-restricted-extras and your choice of apps and ppa's.
Make a backup of firefox bookmarks also and import them into fresh install. Matter of fact have not used
a dist-upgrade for quite awhile, now that I think of it.

---

### Post by drpjkurian on 2011-08-13
Bt seeing the image I feel you are already running on 11.10 (Oneric ocelot)

---

### Post by Argon99 on 2011-08-14
Just in case anybody actually reads this I have tried using the update manager that I found on line that say update manager, using the -d switch, will show that 11.04 is available does nor work. I have looked for the proper way to do it.  I did try apt-get upgrade, apt-get update, apt-get dist-upgrade.  I have tried to use everything I have found online but nothing has gotten me to 11.04.  So how do I use the Ubuntu tools to upgrade to 11.4

And to recap so we don't go over well warn path.  The online tutorials don't get me there.  I don't understand why.  I can use the disk that I downloaded but I don't wipe out data that I want to keep.  But with that said I have backed up most of the disk to a usb drive.

So does anybody have any ideas I can try to upgrade to 11.4 with out using the disk.  I did download the 11.04 disk but I have some reservation about doing an upgrade from a disk.

---

### Post by Argon99 on 2011-08-14
> **drpjkurian said:**
> Hi
You can upgrade to from 10.10 to 11.04 through Update manager.
I tried that didn't show 11.04 as possible.  It said I was up to date at 10.10

---

### Post by Argon99 on 2011-08-14
> **drpjkurian said:**
> Bt seeing the image I feel you are already running on 11.10 (Oneric ocelot)


Update manager says I am at 10.10/

---

### Post by garvinrick4 on 2011-08-14
Here is code just to be sure "I stated Ubuntu says the best way is through there update manager" have no idea why yours is not working in proper fashion it is a fine package, most likely a setting wrong.
This way is basically obsolete:
```
sudo apt-get update && sudo apt-get upgrade
``````
sudo sed -i 's/maverick/natty/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade 

```

---

