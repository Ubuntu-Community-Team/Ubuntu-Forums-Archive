---
title: "Does 8.04 have better hardware support?"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by Jordanwb on 2008-04-10
I currently have 7.10 on my Thinkpad T21. However about 1 in 3 boots it stalls after the loading screen (I have posted a support thread: [Linky]("http://ubuntuforums.org/showthread.php?t=744535"), but I haven't gotten a reply). So my question would 8.04 possibly sove this problem? I don't want to go back to Windows because it's slow and takes up a lot of space.

---

### Post by oilchangeguy on 2008-04-10
> **Jordanwb said:**
> I currently have 7.10 on my Thinkpad T21. However about 1 in 3 boots it stalls after the loading screen (I have posted a support thread: [Linky]("http://ubuntuforums.org/showthread.php?t=744535"), but I haven't gotten a reply). So my question would 8.04 possibly sove this problem? I don't want to go back to Windows because it's slow and takes up a lot of space.

it may, or may not solve your problem. the only way to know for sure is to burn it cd, and run the computer from the live cd. and see how your computer responds.

---

### Post by Pumalite on 2008-04-10
Why don't you take 8.04 Beta for a spin?

---

### Post by Jordanwb on 2008-04-10
I'm downloading Alternate right now due to the fact that my Laptop isn't very new:

Pentium 3 @ 800 Mhz
256 MB Ram

According to Utorrent the download will be done in about 8 minutes. Is there a way to format the drive? I read that Ubuntu does a quick format.

---

### Post by Pumalite on 2008-04-10
With that RAM, I'd go for Xubuntu Alternate CD.

---

### Post by Jordanwb on 2008-04-10
It actually handles Ubuntu very well. I don't multitask a whole lot. Got any suggestions to format the hard drive? I don't have a floppy drive, I do have a flash drive but my laptop won't boot off of it. I only have one blank cd left.

---

### Post by Pumalite on 2008-04-10
10 GB for '/'
/swap=RAM
The rest for /home.

---

### Post by thisiam on 2008-04-11
> **Jordanwb said:**
> It actually handles Ubuntu very well. I don't multitask a whole lot. Got any suggestions to format the hard drive? I don't have a floppy drive, I do have a flash drive but my laptop won't boot off of it. I only have one blank cd left.

1 cd left.good thing they are cheap this days. check this out [http://gparted.sourceforge.net/liveusb.php](http://gparted.sourceforge.net/liveusb.php)

EDIT: ha ha just saw that your computer wont boot of USB. still a good read though.

---

### Post by Jordanwb on 2008-04-11
> **Pumalite said:**
> 10 GB for '/'
/swap=RAM
The rest for /home.

I don't know how or where to do that.

---

### Post by Pumalite on 2008-04-11
You do it on the space allocated for Ubuntu: either the whole drive or a partition. Be careful, you can have only 4 primary partitions on a drive. You can use the partitioner (gparted) Install Ubuntu, go 'Manual' and then make the partitions I indicated.

---

### Post by Jordanwb on 2008-04-11
Ok yeah but I want to completly erase (full format) the hard drive before I make the partitions.

---

### Post by Pumalite on 2008-04-11
Then use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it.

---

### Post by Jordanwb on 2008-04-11
Perhaps you could also explain to me what each of the four partitions do. I understand what Swap is for.

[Edit] Wow I downloaded the LiveCd in 1 minute and 6 seconds.

---

### Post by Pumalite on 2008-04-11
'/' is for the filesystem
/home is for your settings and anything else you want to keep there.

---

### Post by Jordanwb on 2008-04-11
I burned GParted to a Cd but 1 minute is too short for a full format, even for a 20GB drive. Oh well, I'm starting the 8.04 installation right now on my laptop.

---

