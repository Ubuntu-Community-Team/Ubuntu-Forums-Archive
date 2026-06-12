---
title: "Re-install, save personal data only?"
date: 2010-09-16
forum: Installation &amp; Upgrades
---

### Post by Moozillaaa on 2010-09-16
I backed up my 'stuff', so I'm now wondering if I can re-install Hardy over Hardy and save my stuff in it's identical places?

I do NOT want configurations and settings preserved - I have made lots of boo-boos  :oops:

---

### Post by uRock on 2010-09-16
Do you have the /home partition or all-in-one partition?

---

### Post by kaldor on 2010-09-16
Simple way to do this is to just copy your entire ~/ (home) directory including the hidden files. Then, when you reinstall, put it back in. That's what I do if I ever need to do a reinstall (I prefer fresh installs every now and then).

---

### Post by kaldor on 2010-09-16
Edit button won't work!

Didn't notice you said you did not want configurations and such. If that's the case, only copy back the files you need. Don't bring directories such as ".mozilla" back, for example. All your personal settings are within subfolders in /home/user. Use Ctrl+H to view hidden directories.

---

### Post by Bucky Ball on 2010-09-16
Always pays to have a separate /home partition. It avoids this dilemma as on reinstall, during manual partitioning, you just don't reformat the partitions you want to keep.

---

### Post by kaldor on 2010-09-16
I agree with that. Although, I never use it. I'm too paranoid about losing my ~/ in an accidental gparted-related incident.

---

### Post by uRock on 2010-09-16
The problem with having the /home is that the OP wants all of the settings files removed.
A /data partition would probably be better in a situation like this. My next install will have one, as I love to thrash my settings on a regular basis.

---

### Post by Moozillaaa on 2010-09-16
> **uRock said:**
> Do you have the /home partition or all-in-one partition?

Home + Root combo...

I never do it the easy way (sometimes you learn more this way, sometimes you don't).

Can all settings and configurations be wiped to default, WITHOUT re-installing?
(never mind that; I'd prefer to 're-thread' that question...)

---

### Post by uRock on 2010-09-16
I have seen someone recently recommend using a LiveCD to wipe out all of the settings, then restart and the OS will create new ones, but I have never done this, so I can't say much about it.

---

### Post by David Andersson on 2010-09-17
> **Moozillaaa said:**
> 
I do NOT want configurations and settings preserved - I have made lots of boo-boos  :oops:

There are two kinds of "settings". *Personal* settings, things in System>Preferences, stored in hidden files in **/home**. *System* settings, things in System>Administration, stored in **/etc**. (A little bit of an over-simplification, but it will do.)

What category are your boo-boos?

---

### Post by Moozillaaa on 2010-09-18
> **David Andersson said:**
> There are two kinds of "settings". *Personal* settings, things in System>Preferences, stored in hidden files in **/home**. *System* settings, things in System>Administration, stored in **/etc**. (A little bit of an over-simplification, but it will do.)

What category are your boo-boos?

It would take less server space on Ubuntuforums, to say what categories I HAVEN'T botched. Mostly the problem is graphics configuration / and X-configuration.

Anyway, I re-installed and chose to **NOT** import data and settings (same partition; data backed up elsewhere). **IT IMPORTED BOTH**. :confused:

**I created another partition, on another disk, attempted a TOTAL clean install, and it did an instant replay - IMPORTED DATA AND SETTINGS, [SIZE=3]EVEN THO' I DID NOT SELECT TO DO SO. [/SIZE]UGH.**

So I installed Karmic, and all seems well so far (cross fingers, cross legs, cross toes, eyes, teeth, cross hair, cross EVERYTHING) :-\" [-o<

---

