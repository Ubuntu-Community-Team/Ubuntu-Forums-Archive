---
title: "drive dilemma and partition questions"
date: 2010-02-21
forum: Installation &amp; Upgrades
---

### Post by SeePU on 2010-02-21
Okay, this might be a silly question, I don't know.

I have always dual booted the typical way:  install Windows first, then install Linux and let Grub handle the booting.   

I use large, 1Tb+ drives for storage.  Yet, here I am, I ran out of space in both Windows and Linux!!! LOL!

I might start over but not before I copy my data (much of it is on 1TB storage drives) over.

My OS drive is a 320GB drive.  

I thought maybe buy a 500GB HDD and then boot Windows on one and Linux distros on the other.  Is this method more complicated and troublesome?

Or should I just manage my partitions better and write/copy my data to my 'storage' drives?   Is 500GB or 1TB too large for OS drives?   Shouldn't a 320GB be enough for an OS drive or maybe it's completely normal to run out of room after a while? :)

I know, I know, I should get a SSD but imho, they are still too expensive and low capacity.  I guess if I was only going to use Ubuntu and write any data to a storage drive immediately???? :D

Any advice or recommendations?

---

### Post by darkod on 2010-02-21
I'm dual booting win7 and karmic and I only have single 250GB drive. Now I feel miserable... :(

I think you do need to reorganize rather than buying bigger drive for OSs. You might consider buying another storage drive. The 320GB is plenty to dual boot both OSs as long as you keep most of the large data on separate drives which it seems you do.

I mean, win7 ult is approx 10GB (not counting the swap file) and karmic is 2.7GB default install. You can load all the software you can find and still the 320GB should be plenty. As we already said, all your large data is on separate drives.

If it helps you, consider LVM for ubuntu. It sort of beats the purpose when you have windows on the same drive, but it's still helpful. In short, you assign the whole partition you want to dedicate to ubuntu as physical volume for LVM and create partitions on it (logical volumes) which you can resize on the go. So if your root needs more space, no problem. Tomorrow if your /home need more space, no problem again (if it's separate partition). Until you hit the max space which is the size of the partition you dedicated as physical volume.
Even then, install another drive, assign it to the LVM and off you go using it's space too.

Bottom line, I really think the 320GB is enough.

---

### Post by SeePU on 2010-02-21
thanks for your insight, darko!

Should I re-install everything, then?  My experience with trying to clear space is that it's more trouble than it's worth.  Especially with Windows.   So many programs want to read or install into 'C'.....ugh...   In Linux, it's somewhat of a different story but again, I am not sure what to delete half the time.  

I had a storage drive fill up so I ultimately had most of the data (talking about Linux now) kept in /home.   I typically have one partition per distro since I haven't installed just one.   Should I alter this strategy next time?   Or just invest in storage drives so it doesn't happen again?

If I install many of the popular Linux apps, how much disk space should that take up?  

You're probably right, I only need the storage drives but maybe I should re-think how many distos I install?  Or is 20 to 25 GB enough per OS?  I guess it's mostly data that ultimately fills up the partition?

---

### Post by darkod on 2010-02-21
Especially in linux, it's mostly the "large" data as videos, music, large docs, that would take space. And all that would be kept on your storage drive(s). I don't know which of the popular apps are you talking about, but just the fact that the default karmic install takes around 2.7GB says it all. You would need to put loads, and I mean loads of apps to even get to 10-15GB. Even keeping home as a folder on / (not as separate partition), still / partition of 25-30GB sounds enough.
For windows it's a different story. Apps are space hungry and they don't go away. But I have 65GB system partition for win7 ult and it's barely 50% full. But I don't play games though, they can takes gigs and gigs...
As far as system drive goes, the 320GB is good for both of them to fit onto nicely.
For the storage drives, only you can answer that question, about how much space you need. :)

Reinstalling windows definitely cleans it up. For linux, if you move large data out of it (if you used it because the data drives got full), no need to really reinstall. You'll just need to restore grub to the MBR once windows deletes it.

If it helps, here is my setup and have in mind most space is taken by the data partition shared between the two because I don't have separate drives for that.

65GB ntfs primary win7 system
141GB ntfs primary data
15GB ext4 primary /
extended
2GB swap logical
10GB ext4 logical /home

And ubuntu still has plenty of space in both partitions, C: partition also 50% free.

PS. You might consider clean install of ubuntu in April when 10.04 LTS comes out. For now remove any large data onto a data drive, and it will go smooth until April.

---

