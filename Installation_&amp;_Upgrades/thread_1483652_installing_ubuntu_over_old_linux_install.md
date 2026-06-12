---
title: "installing ubuntu over old linux install"
date: 2010-05-14
forum: Installation &amp; Upgrades
---

### Post by 5dolla on 2010-05-14
currently my partitions are as thus: / is linux mint /home is a separate partion 
and I have a 12gb swap. How does one go about installing another linux over the old one with my setup. Do i just format /  and leave /home  or what sorry im a newb.

---

### Post by BoneKracker on 2010-05-14
The installer gives the opportunity to create new partitions, or you could use the existing ones.

If you are really new to linux, then it's probably best just to tell the installer to erase whatever partitions are there and use the space to set up ubuntu the way it wants to.

If there's nothing else on the disk (no Windows you want to keep or anything), you can just tell it to use the whole disk and erase whatever's there.

It will ask you when you get to that part.

(Oh, and 12 GB swap is a big waste of space.  Let the installer figure out how much swap you need.  If you must decide for yourself, a good rule of thumb is twice as much as the amount of RAM you have, but not more than 2 GB or so.  Unless your requirements are unusual, your system would rarely use more than a few hundred megabytes of swap, so that's plenty.)

I like to use the mantra "Default is Good" (i.e., more often than not, I find out months or years later that the default was the proper choice anyway).

---

### Post by 5dolla on 2010-05-15
ya i understand this but what im asking is if I format my root partition and install 
Ubuntu over it can i keep my home partition intact to save my files and configs?

---

### Post by pete_m on 2010-05-15
As far as i understand things that should be fine.  . just don't let the install do anything to that partition( for instance DON'T tell the installer to mount your partition to /home ) - 
I'm pretty sure that anyway you can only do that from within the advanced partitioning settings . .

make sure you've used fdisk -l to know what's what on your present system.

if it's feasible you could physically disconnect any drives not to be used in the install.

I successfully made a clean install of karmic over an existing 8.04 - & was happily surprised how smoothly it all went  - and when i mounted my old home partition it picked up the configuration stuff 

I doubt that much/any or your config stuff will be useful - not sure how Mint fits into the linux eco-system .. .bashrc and other basics at least should be fine .. 

I'm an EEE PC user planning an imminent move to Ubuntu from Karmic to Lucid  .  .
in the hope of performance improvements and the benefit of tying in to a fresh LTS release.

i've put some work into my existing Ubuntu install based on 9.10 karmic nbr2 and am very happy with the results - full credit and thanks to all . .

i'm hoping to be able to upgrade my machine rather than do a fresh install. .& i've been following some threads about this process and possible pitfalls

First screenshots - more soon - of my work in progress at

[http://www.youtube.com/watch?v=YoI4wRVVjBs](http://www.youtube.com/watch?v=YoI4wRVVjBs)

---

### Post by BoneKracker on 2010-05-15
> **5dolla said:**
> ya i understand this but what im asking is if I format my root partition and install 
Ubuntu over it can i keep my home partition intact to save my files and configs?

Yes, I suppose you could.  However, the installer is going to make a home directory for you one way or the other.  If your current home directory is on the root filesystem (not a separate partition), it will get nuked when the installer creates the new root filesystem.

So what you probably want to do back is up your home directory somewhere, run the installer and then copy your old /home directory from the backup, replacing the new /home directory which the installer created for you.

Alternatively, if your /home directory is on its own partition, you could pretend during the installation that you don't want to have a separate partition for home (and that you want to leave that partition intact but not use it).  Then, after the install, just go in and delete everything in the new /home directory which the installer created.  Then mount your existing /home partition to the empty /home directory (and add the appropriate entry in your /etc/fstab file so it will be automatically mounted at boot).  I'm assuming you're the primary user and that you'll therefore have the same UID; if not you'll need to change ownership recursively on all the files in your home directory after you mount it the first time ('chown -r myusername: /home/myusername').

(Be careful, if you tell the installer to use your old /home partition for /home, I believe it will erase it and create a new filesystem and /home directory there.  So if you intend to reuse it, tell the installer to ignore your old home partition.)

---

### Post by ToFue on 2010-12-04
I know im a necromancer, but I thought I should relate my own experience:

5dolla, though you probably have your answer by now, I've been upgrading that way scince 7.10, without incident to my home (except once with ubu studio).. The thing to keep an eye on with the custom partition/mount part of installation is that when you 'change' the home partition for FS setup, keep it the same, i.e. if was ext2, keep mount as ext2, etc., set the moint point as /home, and *don't* enable Format for the partition.  After sys install you may have to re-permission your user folder if your UID or GID is different, i.e. old install was 1002, and new install is 1001.  type 'id' at terminal to find out, before and after, or you can cat /etc/group...

Cheers


PS: if the dead can yeild answers, then let the dead talk! (to necromancy phobia ;)

---

### Post by gordintoronto on 2010-12-04
> **BoneKracker said:**
> 
(Be careful, if you tell the installer to use your old /home partition for /home, I believe it will erase it and create a new filesystem and /home directory there.  So if you intend to reuse it, tell the installer to ignore your old home partition.)

I'm sorry, BoneKracker, but all you have to do is make sure the installer is *not* told to format /home. You can tell it to use the same partition for /home, and all your data will be preserved.

Mind you, it's always prudent to have complete backup: hard drives fail at the most inconvenient time.

---

### Post by BoneKracker on 2010-12-05
> **gordintoronto said:**
> I'm sorry, BoneKracker, but all you have to do is make sure the installer is *not* told to format /home. You can tell it to use the same partition for /home, and all your data will be preserved.

Mind you, it's always prudent to have complete backup: hard drives fail at the most inconvenient time.
You're right.  I had forgotten that.

---

