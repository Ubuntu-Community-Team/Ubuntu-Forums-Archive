---
title: "Best way to do clean install but preserve existing environment?"
date: 2005-11-01
forum: Installation &amp; Upgrades
---

### Post by buzst on 2005-11-01
A year ago I took my first step into linux with ubuntu warty and am now addicted. As I learned about linux, I made many changes to the system, added and deleted applications, upgraded to hoary, and now have an environment I like. It’s time to upgrade to breezy. I would like to do a clean install, to fix some things I did wrong on the initial install. 

Here’s what I would like to do:

Expand swap partition
Create new partition for home
Reinstall all the applications I am currently using (though I never recorded what I installed and am sure I won’t remember them all) 

So this is my plan for the upgrade any comments and suggestions would be appreciated.

While still in the hoary environment:

Expand swap using gparted
Create new partition for home using gparted
Do a dist upgrade to breezy

Then in the new breezy environment

Copy home to a temp directory in the new partition
Copy etc to the same temp directory in the new partition

Then do a clean install of breezy from disk

Copy the home files from the temp directory to the new home
Copy samba config back to its directory
I’m sure there will be other config files I’ll need from the temp etc dir ?
I’m hoping synaptic will now reinstall my old applications, as its history file is in the new home directory?

Please comment (be nice I’m still new at this), is this the best way? What am I missing.

Thanks in advance for the help.

---

### Post by 23meg on 2005-11-01
You have an option to copy files from another partition during install. I'd just preserve the existing home partition, wipe everything else with the install partitioner, create a new home partition, copy data to it from the old one, and then remove the old one with gparted later on.

I've never done this myself though, so I wouldn't like to be misguiding you; can anyone verify this is going to work?

---

### Post by SickTwist on 2005-11-01
Buzst,

If you do the above suggestion, be aware that the "copy files from another partition" feature does not work with ReiserFS. (I just tried doing it two days ago). I'm not sure if any other filesystems are supported (EXT3 perhaps?).

---

### Post by buzst on 2005-11-02
23meg,
thanks for the reply. I thought of  that, but I currently only have one partition, so I think that solution will copy the entire system into the new partition (maybe thats not bad just have to make the partition larger)?

---

