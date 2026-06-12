---
title: "Xubuntu install partition problem"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by V-600 on 2007-11-13
Hi everyone,

I am trying to install xubuntu 7.10 on a laptop (will be dual booting with windows). The problem seems to be with the partitioner (both gparted and the installer. I assume its the same underlying program) which gets stuck scanning the disk. The installer gets to step 4, the the progress bar stops at 46%.

I have been looking through the forums for help and this post seems most relevant, however I am looking for a different solution.

[http://ubuntuforums.org/showthread.php?t=593641](http://ubuntuforums.org/showthread.php?t=593641)

Unfortunately I have a monthly limit on my broadband connection and would rather not download the alternate install cd (also being a sucker for punishment I would rather struggle through this problem, rather than try something else). The cd checks out as a good burn, and the live cd environment works fine (with the exception of the partitioner). I did have some problems mounting the windows partition after hibernating windows, though after a complete shutdown (of windows) the partition mounted succesfully. I have tried unmounting everything (including running "swapoff -a") but the partitioner(s) still hang.

Any ideas how to get round this would be appreciated.

Also is it possible to do a text based install from the live cd version?

many thanks

---

### Post by Sef on 2007-11-13
Are you dual booting with XP or Vista?   If Vista, then use it's partitioner to shrink the partition.

---

### Post by V-600 on 2007-11-13
I am using xp. In an effort to keep the previous post short, I omitted a few facts. The hard disk is currently formatted (as best I can remember) hda1 is approx 30GB ntfs, hda2 is 8GB ext3, hda3 is 0.5GB swap

Edit: I used a knoppix live cd to everything except the windows partition. The computer now has 9 gigs of empty space at the end of the hard disk but still no luck with either the partitioner or the install.

Edit: This just an aside. Booting an older version of ubuntu (6.10) I noticed it uses the GNOME partition editor, while the xubuntu 7.10 uses GParted. Could this make a difference or are they both front ends for the same program?

---

### Post by V-600 on 2007-11-14
Bump

---

### Post by PaganHippie on 2007-11-14
> **V-600 said:**
> Edit: This just an aside. Booting an older version of ubuntu (6.10) I noticed it uses the GNOME partition editor, while the xubuntu 7.10 uses GParted. Could this make a difference or are they both front ends for the same program?

FWIW, AFAIK they are the same program.

---

### Post by confused57 on 2007-11-14
You might try running this in a terminal to determine your partitions:
```
sudo fdisk -l
```
-l is a small "L"

If you indeed have a swap partition on /dev/hda3(or /dev/sda3)...you might try mounting the partition as swap before you try installing...I'm not sure, but I think all you need is:
```
sudo swapon /dev/hda3
```

I'm just throwing out a possiblity you may want to explore further.

---

### Post by V-600 on 2007-11-14
Thanks. "fdisk -l" shows the partitions on the disk. Now I know the computer is seeing the disk, and can read the partition information.

What now remains is to work out why GParted and the installer can not.

Back to google me thinks, though as always I welcome any further ideas.

---

### Post by V-600 on 2007-11-15
Ok. I feel stupid now. I was playing about trying to get the installer working, left it and got a cuppa. As i forgot about it, I came back a few hours later and all was working.

Its just a bit slower than 7.04 was, so here's my advice. If it doesn't seem to work, leave it and get a drink. It probably is working but takes its time.

---

