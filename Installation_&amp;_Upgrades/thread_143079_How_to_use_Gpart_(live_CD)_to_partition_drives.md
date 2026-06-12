---
title: "How to use Gpart (live CD) to partition drives?"
date: 2006-03-11
forum: Installation &amp; Upgrades
---

### Post by totallylost on 2006-03-11
Im trying to partition my 200gb (186gb formatted) into a 145gb windows xp home partition and a 41gb kubuntu linux partition.  I was told that gpart (on a live cd) would be able to partition the drives the way i wanted.  Can anyone tell me how to use gpart to do this? im kind of cautious because this is my first linux anything and i dont want to mess up big time.

sorry for sounding like an idiot

---

### Post by aysiu on 2006-03-11
Is Windows already installed?
What Live CD do you have at your disposal?

Did you know you don't have to resize beforehand? You can actually resize during installation, following this tutorial:
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone)

---

### Post by totallylost on 2006-03-11
windows xp is already installed yes.
i dl gpart from this site:  [http://gparted.sourceforge.net/livecd.php]("http://gparted.sourceforge.net/livecd.php") 

i saved it to cd and booted off of it.

it did its thing and now its showing my drive at 186gb capacity which is correct.

what i need to know is can i from this screen repartition that 186gb space into 145gb windows xp home (already installed to my computer) and 41gb kubuntu linux (needs to be installed still)

if it is possible to partition it and have it permanently stay that way then i wish to know how to do that with out mucking up the works.

also i need to know once that is done (if it works) how i would go about using the kubuntu harddrive manager and how to utilize that 41gb free space for kubuntu linux and its swap file (which i hear is a necessity?)

thank you

---

### Post by totallylost on 2006-03-11
ok ive got the size of the partitions to 145gb windows xp and 41gb kubuntu linux (however that is NOT installed yet. the 41gb is currently marked unallocated space in gparted)  do i need to do anything further with gparted or can i just reboot and install kubuntu linux on the 41gb of unallocated space using FAT32 filing system? please help i have no idea what im doing

---

### Post by hotpurple on 2006-03-12
Why do you want to use fat32? A better choice is reiserfs or Ext3 as long as you don't need windows to read it.

Chris

---

### Post by Irony on 2006-03-12
You can just install kubuntu to the unallocated space - it will be seen as free space by the kubuntu installer.

However I would advise that you shrink the windows partition down to about 10G (or however much data it has in it) and divide up the rest of the space (from windows computer management) in to 10G blocks.

That way you can play around with different distros - you can always merge the partitions later if you want.

I say this because ever since I've installed ubuntu I find that I have divided up the partitions into smaller spaces, this is a pain when they are big in the first place.

The smaller partitions can be used as storage, for example if you run out of windows space you can format one of the small partitions to ntfs and use that.

---

### Post by Irony on 2006-03-12
Also make sure you defrag windows again prior to shrinking it again.

---

### Post by Sutekh on 2006-03-12
Yes, ext3 should be the format you use for Kubuntu, not FAT32.  That would be a very bad idea (if Kubuntu even let you install it on FAT32 at all)

Again I think you should check the link aysiu posted earlier (shows how to resize partitions during the installation process)
[http://users.bigpond.net.au/hermanzone](http://users.bigpond.net.au/hermanzone) for the guide to installing Ubuntu with Windows (NTFS)

---

