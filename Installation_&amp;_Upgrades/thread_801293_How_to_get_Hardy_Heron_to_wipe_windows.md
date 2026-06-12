---
title: "How to get Hardy Heron to wipe windows?"
date: 2008-05-20
forum: Installation &amp; Upgrades
---

### Post by beezum88@gmail.com on 2008-05-20
Hi.  I'm installing Hardy Heron on an old Windows 98 and Suse 9.2 dual boot machine.  When I booted to the install disk, I saw no way to completely wipe both partitions from the drive and do a clean install of Hardy.  Is there an easy way to do this from the install disk, or should I just use a third-party solution to wipe the disk and then run the installation?

Thanks,
--Beezum

---

### Post by bigken on 2008-05-20
you could use the partittion editor or download and burn gparted live CD

---

### Post by MaindotC on 2008-05-20
If you do a clean install of Hardy, the partition editor will allow you to write over the entire hard drive.  I know this isn't the same as wiping the disk, but it will definitely remove any references to windoze.  I don't know of any tools included on the Live CD that have a wiping functionality, but the one we use at our campus help desk is [DBAN]("http://www.google.com/url?sa=t&ct=res&cd=1&url=http%3A%2F%2Fdban.sourceforge.net%2F&ei=mhozSKzkHJiQ8wSB77ngAQ&usg=AFQjCNEINLrxBE39ypaBEHkRApIW3N0RXg&sig2=0PqJFeSwqbFFeyR556phag")

---

### Post by housam on 2008-05-20
Use the [[COLOR="Red"]_Gparted live CD_[/COLOR]]("http://gparted.sourceforge.net/livecd.php") to do reformat the partitions you want.

---

### Post by MaindotC on 2008-05-20
Guys I don't think he's talking about partitioning or formatting - I think he wants all information completely removed from the drive.  If you don't do this, you can easily retrieve the data using a tool such as [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk").

---

### Post by markbuntu on 2008-05-20
In the patrition manager choose manual and you will get a new screen where you can remove all your existing partitions one at a time and edit them to make new ones and format them, etc. If you want dual boot with another hard drive be sure to check advanced and choose it further along in the process. look for the advanced checkbox.
I don't remember where it is but it shows up somewhere along there.

If you want to completely wipe the drive for security reasons there are a few programs to do that but you need to have your Ubuntu installed and running on a different drive to do that.

---

### Post by beezum88@gmail.com on 2008-05-20
I tried the manual mode on the repartitioning but had no idea what i was doing.  It seems like DBAN ought to do the trick, though, from what I read on their website.  Thanks!

---

### Post by MaindotC on 2008-05-20
Yeah I get a star for that :-p  Does anyone know of disk-wiping utilities in the Ubuntu Live CD?

---

### Post by wpshooter on 2008-05-20
> **beezum88@gmail.com said:**
> I tried the manual mode on the repartitioning but had no idea what i was doing.  It seems like DBAN ought to do the trick, though, from what I read on their website.  Thanks!

Get and use [www.killdisk.com](www.killdisk.com) to completely WIPE that hard drive and then install Hardy.

Good luck.

---

### Post by Slim Odds on 2008-05-20
dd if=/dev/random of=/dev/hda (or /dev/whateveryourdriveis)

do it multiple times for good measure.

---

