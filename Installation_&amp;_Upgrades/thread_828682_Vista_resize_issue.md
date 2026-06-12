---
title: "Vista resize issue"
date: 2008-06-14
forum: Installation &amp; Upgrades
---

### Post by -Outcast- on 2008-06-14
Hi guys,

I resized D the other day to prepare for dual boot with 8.04 and it made a new volume E 

Now I got C D E. Most people are recommending I resize C before instanlling Ubuntu. But if I do that I will get C D E F. Can I just use gparted to wip D and E to create a single D to install Ubuntu on for a dual boot?

---

### Post by PmDematagoda on 2008-06-14
If you are using Vista then you should resize the partition using Vista's own partition manager, and then delete the partitions to be changed in Gparted and create a new partition from the new unused space, that should create a new partition D.

---

### Post by llama320 on 2008-06-14
While I haven't personally had this problem, I've heard it's a bad idea to use gparted to repartition instead of the native vista partition app

So for me, I have a C drive and D drive that vista can see..ntfs and vfat respectively...then the rest (before I installed ubuntu) was just "unformatted" or something like that...it was empty space

Then when I got into the ubuntu installer, I just created my swap and ext3 in that empty space

The point that I'm trying to make (perhaps so far unsuccessfully) is that, in vista, you can just right click on the partition(s) you want to use for ubuntu and say "delete partition" and it will create this empty space for you..so in your case, you can resize vista, make that E drive, then just delete it and make it into the unformatted stuff

Sorry if that was a bit wordy..couldn't quite find the words

Good Luck

---

### Post by -Outcast- on 2008-06-19
Thanks for the reply, unfortunately my D: had a hidden boot loader from Sony. Couldn't delete it. So had to use Gparted to do everything. IT all worked out. Ubuntu used grub on C: with ubuntu on D: and everyone boots up together. Vista see's D: but can't touch it. So I guess all is good

---

### Post by housam on 2008-06-19
> **-Outcast- said:**
>  Vista see's D: but can't touch it. 

this [[COLOR="Red"]_driver_[/COLOR]]("http://www.fs-driver.org/") will allow you to access ubuntu partition through windows.

---

