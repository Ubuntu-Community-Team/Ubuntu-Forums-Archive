---
title: "Dell M1330 + Ubuntu 7.10 RC,can't recognize partition"
date: 2007-10-13
forum: Installation &amp; Upgrades
---

### Post by Garrett_Wu on 2007-10-13
I tried to install ubuntu 7.10 RC on my Dell M1330 yesterday , and I got a very strange problem.

At the step that I have to choose one partition to install , it just shows a full empty unalloated harddisk. But I have Vista and prepared partitions for Ubuntu, I can even access these partitions from Ubuntu's file manager.However I can't choose one of these from install process.

I tried set BIOS to ATA or ACHI (disable Flash cache), the problem is the same.

I took the screenshot , hope somebody can help me, thanks!

[http://farm3.static.flickr.com/2291/1558909564_84cb21d08c_o.png]("http://farm3.static.flickr.com/2291/1558909564_84cb21d08c_o.png")

---

### Post by vto80 on 2007-10-13
Exactly the same problem i just described in this post: [http://ubuntuforums.org/showthread.php?t=575038](http://ubuntuforums.org/showthread.php?t=575038)
So it's not a Dell issue. Maybe it's hardware dependent - i'm using an old asus a7n8x-x MBO, with an Athlon XP @ 7.5x200 and 1 GB ddr. And an ATI 9550 AGP. My first hunch was the FDD as it was accesed repeatedly by Gparted and it showed a non-existent disk just a few Kb big, when in fact the FDD was empty. So i disabled the FDD controller completely in bios, but still no success. Gparted continues to act weird.

vto.

---

### Post by vto80 on 2007-10-13
It turns out my problem was due to the partition table being utter nonsense, i'll have to fix it before installing anything. Maybe something similar happened to you too - maybe something to do with those 'hidden' vista rescue partitions...

vto.

---

### Post by Garrett_Wu on 2007-10-14
I've already deleted all hidden partitions on my M1330 ,including Vista rescue,media direct and the diagnose partition.

I tried alternative CD today , the problem still exist , ubuntu just can't recognize my partition correctly during install process no matter under GUI or Text mode.

Hope this is a bug of RC....

---

### Post by Garrett_Wu on 2007-10-14
I got problem fixed!

I used Disk Suite to make 2 partitions for ubuntu & swap in advance, it seems ubuntu can't accept these partition so show an empty harddisk. I delete those ext3 & swap partition ,and install process iworks fine now!

---

### Post by zarry on 2007-10-15
I had this problem also.

With a normal install you would be able to choose "Guided" but this didn't show and my partitions weren't recognized. 

```
sudo su
fdisk /dev/sda
m
```

When I did this my MBR was fixed and I was able to to what I was looking for.. Install where the hell I want it and not format the whole damn thing :)

Hope it works for you because I started searching 8 hours ago for the solution :D Peace

---

