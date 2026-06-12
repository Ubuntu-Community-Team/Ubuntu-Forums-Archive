---
title: "Space Needed?"
date: 2005-04-25
forum: Installation &amp; Upgrades
---

### Post by DavidF on 2005-04-25
I'm just wondering how much disk space an average Hoary installation takes... trying to figure out if I can fit it on my current drive with all the XP stuff already on it.

---

### Post by john_c on 2005-04-25
David:

I have a pretty basic hoary installation and use a "/" and "/home" partition setup.  The "/" is now right on 2.0 GB and the "/home" partition is at about 2.6 GB with three users.  I have a bunch of small data files on it and some photos but not much music and no video.  I've made the "/" partition 3.0 GB in case I need the room for other applications or installing them.

Hope this is some help.

John.

---

### Post by bored2k on 2005-04-25
[QUOTE=DavidF]I'm just wondering how much disk space an average Hoary installation takes... trying to figure out if I can fit it on my current drive with all the XP stuff already on it.[/QUOTE]
 About 1.5-1.8gb. After you install it you can just remove OpenOffice and other apps to release about 500mb.

---

### Post by DavidF on 2005-04-26
[QUOTE=bored2k]About 1.5-1.8gb. After you install it you can just remove OpenOffice and other apps to release about 500mb.[/QUOTE]
 I've got about 8 gb free right now, and if I run OpenOffice I can probably ditch MS Word and Works to free up even more space.

So, it sounds like I have plenty. :)

---

### Post by bored2k on 2005-04-26
[QUOTE=DavidF]I've got about 8 gb free right now, and if I run OpenOffice I can probably ditch MS Word and Works to free up even more space.

So, it sounds like I have plenty. :)[/QUOTE]
 Don't think you'll ditch Works. And by the way, If you deal with a lot of MS Office files, don't uninstall it, just in case one of these decides not to display itself the way it should on OO.o.

---

### Post by DavidF on 2005-04-26
Now I can't wait till my CDs arrive! I want to play with it from a Live CD before doing the install and dual-boot thing. :)

---

### Post by fordfan753 on 2005-04-26
[QUOTE=DavidF]I've got about 8 gb free right now, and if I run OpenOffice I can probably ditch MS Word and Works to free up even more space.

So, it sounds like I have plenty. :)[/QUOTE]


I would never choose OO over MS Office, I don't care if it's MS...if it works better then use it. Personally, I kept my MS Office, uninstalled OO, and components to free up all that space, and installed abiword. Sure, it's only the Word Processing bit of OO...but really, if you have MS Office on another partition how often would you use all the extra unnecessary stuff in OO?

---

### Post by DavidF on 2005-04-26
[QUOTE=fordfan753]I would never choose OO over MS Office, I don't care if it's MS...if it works better then use it. [/QUOTE]
Well, that's part of the reason for trying Ubuntu... to see if I like it and its applications better than the MS stuff. :)

---

### Post by bored2k on 2005-04-26
[QUOTE=DavidF]Well, that's part of the reason for trying Ubuntu... to see if I like it and its applications better than the MS stuff. :)[/QUOTE]
 I have encountered some problems in OO.o that keep me away from it. I get sent a lot of MS Word written .docs, and some of them aren't displayed the way they should [also .pps presentations], so I basically stick with Abiword, then open it in MS Word for the final touches [I'm not a big Open Source only advocate].

---

### Post by DavidF on 2005-04-26
[QUOTE=bored2k][I'm not a big Open Source only advocate].[/QUOTE]
Personally, I am an advocate of "whatever works." I guess that makes me a pragmatist. If Linux can do a job better, I'll use it. If Windows can do a job better, I'll use that.

---

### Post by bored2k on 2005-04-26
[QUOTE=DavidF]Personally, I am an advocate of "whatever works." I guess that makes me a pragmatist. If Linux can do a job better, I'll use it. If Windows can do a job better, I'll use that.[/QUOTE]
 Personally, I don't have a problem with using a non-free as long as it works [example: I doubt I'd ever find a Sony Vegas+Architect DVD Authoring substitute -- retails at +$600]. I also don't like being "one more of the pack", so I challenge myself everyonce in a while [my main reason leaving Windows as a main system was the fact I haven't learn anything good in like, ever].

---

### Post by DavidF on 2005-04-26
By the way, another big reason for starting to play with Linux is that I want to get into networking, and I understand that many servers use Unix/Linux. :)

---

### Post by Nano on 2005-04-26
By uninstalling *-dev packages you might save some space.

---

### Post by az on 2005-04-26
By passing the archive-copier/copy=fase argument to the installer, you avoid having about 300 megs worth of packages sit uninstalled on your harddrive.  You need to pop in the cd everytime you install one, though....

---

### Post by nad on 2005-04-26
Or just get it online.

By the way, why isn't the apt cache autocleaned? I had one machine with over 800M there.

---

### Post by fordfan753 on 2005-04-27
[QUOTE=nad]Or just get it online.

By the way, why isn't the apt cache autocleaned? I had one machine with over 800M there.[/QUOTE]
 I've found that happening too...My HardDrive was basically full, then I tried and apt-get clean, and now it's half empty. (Not half full...and no, I do not believe in the optimist/pesimist thing :-P

---

