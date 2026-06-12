---
title: "Breezy &gt; Hoary ?? Should I attempt the upgrade?"
date: 2005-10-16
forum: Installation &amp; Upgrades
---

### Post by linkunderscore on 2005-10-16
I LOVE my Hoary install. I feel like I finally have everything just the way I want it. 

I have installed Breezy on my desktop and I love some of the new features. It seems like everything is working flawlessly. I had some issues with my network card (but I think it was hardware, not software). 

Here are my questions and concerns: I have everything set up exactly the way I want it. I really would like to upgrade because I do like the new features breezy offers, but I don't want to re-install the applications I already have installed. 

Would I have to either remove/reinstall/reconfigure the applications I already have installed? 

I know I will have to re-install the nvidia drivers, but there are other things that I have installed and tweaked such as ndiswrapper (my wifi card)...would these things be affected? I have been reading through these forums and it seems like breezy is having some upgrade difficulties. 

Should I wait until all of the kinks are worked out? Should I go for it? I really love Ubuntu and I feel awkward not using the "newest" version of it.

---

### Post by dtfinch on 2005-10-16
For the most part upgrading doesn't replace config files that have been modified, or it asks first. Config files under your home directory are very unlikely to be affected. I haven't tried an an in place upgrade from Hoary to Breezy though, but I have upgraded from Warty to Hoary without trouble. I installed Breezy from scratch because some things were already a little messed up on my Hoary. From there I was able to recover a lot of my settings from a backup.

I don't have wifi or an nvidia card though. If there's nothing specific you need from Breezy, there's really no rush to upgrade until you're sure it'll all go well.

---

### Post by ender on 2005-10-16
I just upgraded yesterday and I'm loving Breezy even more than I loved Hoary. It's just like a Christmas present (and yeah, I do know it's october). ;) 

Unlike other people I didn't really have any issues with the upgrade. Synaptic did the job quite nicely (not a single glitch in over 1200 upgraded packages and nothing seems to have been left behind :D). I was surprised that it actually worked because my power went out towards the end of the installation part and I was left with a barely bootable system. But dpkg managed to pick up the installation where it had been interrupted and finish the job. :o  :cool: 
When it was done I had absolutely no problems with GNOME and my NVidia drivers have been upgraded automatically (no ideea why it didn't work for other people, I really didn't do anything special to get them :confused: ).

Anyway, if the stability of your system and the safety of your data are what matters most to you than I guess you should wait for a while (or do a backup before you begin ;) ). Problems are bound to appear, at least on some configurations, when doing such a major upgrade.

---

### Post by GrammatonCleric on 2005-10-16
Personally?  Knowing the time and effort it take setting up your system just the way you want....I'd say wait since your system is running the way you want.  Like the old saying "If it's not broke....don't fix it!"  

With that said if you want to throw caution to the wind and taste death to truly live life... jump on in the pool and upgrade.  Just make sure that you've made a good complete system backup before you do.

I've lucked out and my workstation and laptop upgrades went very smoothly.

GC

---

### Post by linkunderscore on 2005-10-16
What is the best way to create a full system back up?

---

### Post by GrammatonCleric on 2005-10-16
Take a look at this thread....

[http://www.ubuntuforums.org/showthread.php?t=35087](http://www.ubuntuforums.org/showthread.php?t=35087)

I'd also add a --exclude=/media to the list Heliode has listed.  Well that is unless you want to backup any mounted volumes you have in /media.  Here's a shell script I use to backup my systems to a shared network drive.

```


###################################

# Backup Script

# Objectives to backup data and configs.

###################################



# set date variable



tdy=`date +%m%d%Y`



# create tar backup file

tar cvpjf /media/backups/ares_backup_$tdy.tar.bz2 / --exclude=/proc --exclude=/lost+found  --exclude=/mnt  --exclude=/media --exclude=/sys --exclude=/sys


```

GC

---

### Post by linkunderscore on 2005-10-16
thanks I will try that script when I get a chance.

---

### Post by Mitt3ns on 2005-10-16
My upgrade has been fine! No flaws what-so-ever! Even when i went to GRUB to load it and selected the new kernel, i just thought about the chance of all my files being gone, but there werent! Everything just the way i wanted it and with a new kernel and updated distro :D . Definately worth the try, and, if you mess up, why not just format and try again?

---

