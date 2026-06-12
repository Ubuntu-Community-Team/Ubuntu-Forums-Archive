---
title: "What to backup before re-install"
date: 2011-06-18
forum: Installation &amp; Upgrades
---

### Post by smcrossman on 2011-06-18
I'm preparing to reformat & repartition my HD and do a clean install of Natty.  I know I either need to copy or backup my Home file (of course) but is there anything else I should copy / backup?  Is there a difference in the files if I backup vs. copy? (I'm still trying to figure out how to get the blasted mounting to work for backup...don't ask....long story)

I did a quick search but what i pulled up was old...2008, so I wanted to make sure the information was still valid.  It said that home folder was all that would be needed.

BTW this PC is currently the stand alone server for Samba (not that I've got that working yet either!)  will those current settings be included in the Home folder somewhere?

Thanks for the information & assistance!

---

### Post by amauk on 2011-06-18
2 points
Any reason why an upgrade won't do?
and for servers, it's best to stick to LTS releases (supported for 5 years)

---

### Post by vanadium on 2011-06-18
Your safest bet to have a good working system is a fresh install. An upgrade usually will do, but is less fool proof than a fresh install.

The only things that you need to backup (on a very regular basis) are the things that are unique on this world: this is: your own data, documents, pictures.

Once you have these backed up, there is nothing bad that can happen anymore. Operating systems come for free and change every now and then. There is no reason to backup these.

---

### Post by amauk on 2011-06-18
> **vanadium said:**
> Your safest bet to have a good working system is a fresh install. An upgrade usually will do, but is less fool proof than a fresh install.Don't agree

As for backing up for a fresh install, it depends on your config to a certain extent, but the usual suspects are:
/home
/root
/etc
/var
/opt

---

### Post by smcrossman on 2011-06-18
Okay...

first....I did an upgrade ? I did an install last 2 weeks ago of upgrade 11.04 to 11.04.  First one the installer crashed so I redid it.  Works better than the original install was, BUT my goal was to eventually do away with Windows and dual boot on this machine AND I have a strange Install RELEASE icon now. Add to that, that this is going to be the "host" for my external HD holding my Samba shares...well clean fresh install seems best idea all around.

On the LTS version....I'm still kind of considering there. But I want to be as consistent across the "network" as I can, and I really do like Unity for the most part. I also agree that OS come & go and none are sound-proof. One of the things I'm really enjoying about Ubuntu is that I can look up issues, ask others, and play around to fix the things that come up or that I don't like.  So frequent updates and/or version releases aren't a hardship for me right now.

Also after 18-20 months of reformatting and reinstalling factory specs on this machine with Windows  every 7-10 days I don't have a lot of fear about systems crashing, AS LONG AS I have alternative internet access (with 2 more pcs and an iPhone that should be covered).

Now basically when I did the "ugrade" I did not back anything up (I've only be on Ubuntu for a month or so...) and a lot of this past week (or 2) has been tweaking wireless internet connections and samba setups and looking at and trying some different software applications.

So other than my home (to keep files, organization setup, etc) I'd like to try to keep the drivers for wireless, and the samba files.  Currently Deja Dup is still unable to do a backup....I think it's a mounting problem since that is what is my problem in Samba as well, so either I'm opting for a USB stick or will have to do it manually.

Will those 5 directories give me those things? A whole lot more? Not?

Where can I find a start on the coding/commands to use to back up?  I am guessing that just copying the directories (well home directory anyway) over to a USB stick and then moving it back to the new install isn't going to work as well as an actual backup. (My experience with backing up in Windows is that it is useless...so pardon the seemingly nonesensical questions) I also know that copying file system directories is a lot more difficult than backing up probably is.

---

