---
title: "installation problem v7.04"
date: 2007-09-21
forum: Installation &amp; Upgrades
---

### Post by 92sho16 on 2007-09-21
Ive read a bunch of different threads about install problems but none of which seem to have the same problem i am having. I boot from the live cd and I have selected both the safe boot and the regular boot function and it gets to the screen where is say ubuntu and has the loading bar the bar bounce back one time and then freezes and nothing happens. Ive tried the alternate cd and it froze too. Anybody know whats going on here? 



Specs of system:
700mhz celeron
384 mb ram
10 gig hd

---

### Post by Pumalite on 2007-09-21
Too little memory. You can boot Live CD making 1 GB swap partition ahead of time.

---

### Post by 92sho16 on 2007-09-21
so if i wipe the hard drive clean and leave it open just for ubuntu it shouldnt have a problem?

---

### Post by Pumalite on 2007-09-21
Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) and make 1 GB swap partition, then install.

---

### Post by 92sho16 on 2007-09-21
> **Pumalite said:**
> Use Gparted: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php) and make 1 GB swap partition, then install.

The same thing happens with this software as well, it starts loading then hangs up before it gets into gparted.

---

### Post by Pumalite on 2007-09-21
Do md5sum on your isos, burn at 4x, check CD for corruption after burn and before install, clean lens of your burner  or change if necessary.

---

### Post by Jackel15 on 2007-09-21
I am having the same problem with a HP Pavilion N5310. It is 750mhz with 128mb of ram and a 10gb hd. I booted ubuntu from the 7.04 live disk that i burnt at 4x. then i pressed f6 for boot options and took away the quiet splash so i could see the commands and it gets stuck at the line right after it identifies my CD drive.

[   36.976404]  Squashhfs: version 3.2-r2 (2007/01/15) Phillip Lougher

then my screen flashes once and comes back to the same thing.
I am able to enter text but it doesnt do anything.

This is my first time dealing with linux and i would like to make it the only thing on my laptop. 
My HD is not formated but i would like linux to be the only thing installed. i believe it is ntfs with one partition.

Is there a way to format once i get to the desktop.

I also downloaded the thing that was mentioned above but i have no clue what to do with it.


Thank you Very much for any help.

---

### Post by Pumalite on 2007-09-21
Your problem is different. With that amount of RAM you are better off sticking to a smaller distro: Zenwalk, DSL, Puppy.

---

### Post by Jackel15 on 2007-09-21
Which one would you recommend for a beginner?

I know nothing about linux, i just want to get my feet wet so i can have some bearings inside this os.

What are the differences between Ubuntu and the others that you mentioned.

Thank you for your fast respond time, i thought i would be waiting for a few days.

---

### Post by Pumalite on 2007-09-21
I'm a Zenwalk user.

---

### Post by Skidpad on 2007-09-21
DSL (Damn Small Linux), Puppy & Zenwalk are all distro's ("distributions") that are designed for older computers, or are designed to be bootable from usb stick, thus, all three require far less system resources.

They are fully functional of course, but do not come loaded with all of the programs, etc that Ubuntu does.  Ubuntu has greater system requirements.

---

### Post by 92sho16 on 2007-09-23
well it looks like the cd drive on the laptop cd drive works intermittently  or selectively and there were some clearance laptops at the local best buy so i picked one up and had no problem loading lol

---

### Post by Pumalite on 2007-09-23
Glad you fixed your problem1

---

