---
title: "so annoyed with my hdd"
date: 2006-10-18
forum: Installation &amp; Upgrades
---

### Post by abba on 2006-10-18
Hey all
 ubuntu newb here but have some experience with other linux os's. I am having an issue with one of my partitions after installing ubuntu. been searching but cant seem to find anything like this. 
 installed ubuntu onto hda which was windows. np there. hdb is screwey right now but not worried about that one. hdc1 is my concern. i cant gain write access to this partition. ive edited the etc/fstab. ive managed to mount it. i am able to read it only if i sudo nautilus. but i can not write to it or change permisions or ownership of it. 
 I did create an identicle partition on the same drive (had extra room) and it works properly. 

Any help would be appreciated. 

oh btw its an ntfs partition that i was using under xp

---

### Post by orb9220 on 2006-10-19
You cannot write to an nfts partition. This is not supprted by default  unless you try  HOWTO: NTFS with read/write support using ntfs-3g (easy method) [http://www.ubuntuforums.org/showthread.php?t=217009&highlight=3g](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=3g)

In my case I had a 120 with all my music,vids,pics ect... and lucked out by defragging the drive and convert it to fat32 with partition mageic 8 in xp and now my xp and ubuntu can read and write to it.

---

### Post by abba on 2006-10-19
Hey orb9220

 thanx for getting back so quick. alright i gave that ntfs-3g a try. everything went well on install howeve it made things worse. after doing that i was no longer able to mount my drives. so i undid the changes to the fstab. now the partition hdc1 (the one i need) is accessible by all users which is an improvement but i still cant write.

And I'm Unable to mount the 2nd ntfs partion hdc2 which before I was able to write to. I have been reading that you cant write to ntfs in linux but that doesn't make sense as I was writing to an ntfs partition before i tried the ntfs-3g. which make me wonder, is there a difference between linux created and windows created ntfs partitions or are ppl wrong and u can write to ntfs? 

Oh and is there a linux partition tool? i could deffinately try the conversion over to fat32 if its possible.

---

