---
title: "XP can't see my whole drive"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by KARaidl on 2007-12-29
This might not be completely on topic, but my problems started when I installed Kubuntu so I'm gonna give this forum a try.

I ordered a new computer and it came with Vista on it. I don't want Vista, I want XP. But what I really wanted to do was set up a triple boot between XP, Vista, and Kubuntu. So I started by downloading the torrent for Kubuntu, created a DVD, and installed, but after a little while of using KDE, I decided to go back to Gnome, which I've used before, after which I preceded to just nuke the partition Kubuntu was on.  I later found out from Linux savvy friend that that was very bad idea. Sure enough, I got a Grub error #22.

From there I tried to install XP on the whole drive, but the funny thing is that the bootable CD was only seeing 132 gigs (Which is what I partitioned for Vista) out of my 465 gig hard drive. I just went with it and decided to use the Gparted Live CD to extend the partition to the whole drive, but that caused a boot error. So then I tried wiping the whole drive with KillDisk, but to no avail - XP still only saw 132 gigs.

Now, Kubuntu sees the whole drive, and Vista sees the whole drive. What's it gonna take to get XP to see the whole thing too?

Once I get this done, my plan is to install Ubuntu instead.

---

### Post by ghsfr33d0m on 2007-12-29
search for disk management in xp, when u open that up u should see the partitions u currently have and some "unallocated space" this is your missing drive space. though disk management u can eather add that space to one of your other partitions or create another partition with it.

---

### Post by KARaidl on 2007-12-30
No you can't. Disk management only allows you to see all of the partitions, but nothing more. A pre-installed way to edit them didn't come until Vista.

Regardless, I've managed to track down what my issue was. Apparently before SP1 came out for XP, it didn't have support for 48 bit logical block addressing. I had no idea what LBA was only a few hours ago. So I updated all the way past SP2 and THEN edited my partitions with the GParted Live CD.

Could've avoided this whole mess if I hadn't been so impatient and just updated my OS. I just couldn't get over why Kubuntu and Vista could see my whole drive, but XP couldn't.

---

