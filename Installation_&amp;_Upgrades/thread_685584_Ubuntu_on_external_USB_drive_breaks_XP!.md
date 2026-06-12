---
title: "Ubuntu on external USB drive breaks XP!"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by chichilatte on 2008-02-02
Ah brilliant. I was curious about Ubuntu, so I installed it on an empty external USB hard drive. I thought "Let's try it! It won't break my windows XP because it's not even on my laptop, it's on the external drive".

It broke my XP. Now I can only run XP if the external drive is connected, otherwise on boot i get "Grub error 21" message, white text on black  :(

I looked into  it, and Ubuntu seems to have wiped something called the Master Boot Record on my laptop drive. Thanks for warning me Ubuntu!!

It's proving difficult to fix because I don't have the original Windows CDs (like many laptops these days, instead of CDs there's a hidden partition on the drive which can recover the original Windows).

I'm going to try burning some kind of recovery DOS disk and run something like "fdisk \mbr"

God knows if that will work. And if it doesn't, maybe the pute won't be able to boot at all.

brilliant.

Does anyone have any advice? Sorry for sounding pissed off, but what a stinker Ubuntu has pulled on me! (and plenty of other curious folk too)

---

### Post by naknak987 on 2008-02-02
Well at least you learned your lesson. :lolflag:
Any way, What I would do if I were you is get a xp install cd. This can be done in many different ways... Just get one then reinstall. Be sure to back up your data tho, wouldn't want to lose any .mp3's right. 
Then if you still want to try ubuntu. There is a way to put it on a flash drive and use it that way without affecting windows. I'll post a link later for ya. Good luck and PM me if you have any questions pertaining to obtaining the xp install cd.

---

### Post by JamesDS on 2008-02-02
Yes, this has happened to me before.  I, similar to you, dedicated 10 GB of my external hard drive to an Ubuntu installation.  Just like you, I was rather annoyed (and momentarily frightened) when XP couldn't boot.  I was able, after a little work, to run either fixmbr or fdisk /mbr, both of which I think do the same thing.  I'm not sure if I booted into XP to do this, or booted from a flash drive with XP boot up files.  Either way I recovered my previous MBR.

This also happened a few days ago when I decided to do a fresh install of the latest Ubuntu, 7.10.  I actually tried a "non-destructive" recovery - let it go for 15 seconds, and immediately hard booted.  It was too late, it had deleted my Windows registry, and all system files, leaving my data intact and programs there but unable to run due to lost sys files and registry keys :( - so much for non-destructive.  I couldn't boot up either, so backing up my data in Ubuntu (just in case) I went through the non destructive recovery fully.  In the end, I did a fresh install of Windows.  Definitely not the way it should have been, and I feel a little stupid now :(.

Anyway, don't let that scare you, just warn you.  If I were you, I'd find a boot disk with fdisk on it, and put it onto a flash drive.  If it can boot you into a command prompt, so you can use fdisk /mbr, then you should be sorted.  Best of luck for finding such a boot disk though, and if you do find one that works, I'd appreciate it if you could post a link here :).

---

### Post by Mze on 2008-02-02
Download Super Grub Disk....

If you have to install Grub again, make sure you install it on your internal hard drive.

Also run a search on "Installing Ubuntu on external hard drive" on the forum.

---

### Post by chichilatte on 2008-02-03
Thanks everyone for your advice, much appreciated.
-------------------------------
...
yeh naknak987 i totally learned my lesson. what the lesson was i don't know. maybe "don't piss around with ubuntu you noob, you'll always be a noob"

I looked at the Super Grub Disk site, and it looked sickeningly complicated. I don't think i have the stamina to root out every nook and cranny where grub has dropped its pigeon guano. 

god.

So my laptop didn't come with CDs, but it did come with a disk-to-disk recovery partition. I just now booted into that from grub and reinstalled windows with it, a totally fresh version, but the MBR is still the same grub-21 guy :(

I'll do like JamesDS says: get a boot disk with fdisk or fixmbr on it and blast away at this grubby MBR till it's a cloud of atomised iron filings.


I was wondering if the Ubuntu installer actually saves a backup of the original MBR before it wantonly destroys it? I've found a windows program(HDHacker) which can read and write files to the MBR, so that would really fix it. I'll try and find out.

thanks again

---

### Post by chichilatte on 2008-02-03
Oh and i see the linux commands...

```
sudo dd if=/dev/sda of=MBR.dat bs=446 count=1
```
and
```
sudo dd if=MBR.dat of=/dev/sda bs=446 count=1
```

will backup and restore my MBR,
so if i do ever find the original windows MBR, there won't be a problem restoring it.

_____________________________
Also, i see there's a linux version of fdisk...
[http://www.arsgeek.com/?p=3340](http://www.arsgeek.com/?p=3340)
but it looks scary. If it screws up the MBR restore, my pyoot will be LiveCD only, if at all.

ach what a business!

---

