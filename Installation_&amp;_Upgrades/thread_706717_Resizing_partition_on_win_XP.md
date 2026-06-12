---
title: "Resizing partition on win XP"
date: 2008-02-24
forum: Installation &amp; Upgrades
---

### Post by rominho on 2008-02-24
Hi guys I hope I can get some help,

I need to get to make my C: partition a little bigger, I've got less than 6gb at me moment and I want to get it to be around 10gb.

I tried using the Gparted software to make my D: partition (which I use for data) about 4gb smaller, so that I could use those 4gb to add to the C: partition, so I did it, and those 4gb are now listed as "unallocated Space". However I couldn't find the way to "grow" the C partition, I wouldn't give that option and I couldn't do anything with the 4gb that is now "unallocated Space".

Can anyone guide me up on how to use those 4gb to add to my C: partition? :confused:
I don't really care if a have to format the drive C and reinstall Windows as my data is safe on the drive D.

Thanks in advance.

---

### Post by Pumalite on 2008-02-24
Use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
Burn to disk and boot from it. Post a screenshot.

---

### Post by rominho on 2008-02-24
> **Pumalite said:**
> Use Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
Burn to disk and boot from it. Post a screenshot.

[[IMG]http://img84.imageshack.us/img84/6549/overviewiq0.th.jpg[/IMG]](http://img84.imageshack.us/my.php?image=overviewiq0.jpg)

---

### Post by rominho on 2008-02-24
When I try "resize or move" the C partition this comes up:

[IMG][[IMG]http://img84.imageshack.us/img84/5869/cpartitionuy5.th.jpg[/IMG]](http://img84.imageshack.us/my.php?image=cpartitionuy5.jpg)[/IMG]

---

### Post by Pumalite on 2008-02-24
Sorry, bad shot; couldn't see anything, but look at the documentation for Gparted and you'll know what to do.

---

### Post by rominho on 2008-02-24
> **Pumalite said:**
> Sorry, bad shot; couldn't see anything, but look at the documentation for Gparted and you'll know what to do.

Try clicking on the thumbnail image.

---

### Post by Pumalite on 2008-02-24
For what I can see, there seem to be no space left.

---

### Post by rominho on 2008-02-24
> **Pumalite said:**
> For what I can see, there seem to be no space left.

That's my point!

I used Gparted to make my Data Partition 6gb smaller. Those 6gb (5.98gb precisely) are now "unallocated space". So what I want is add this freed space to the C partition (which doesn't have space at this moment).
Isn't it possible?

---

### Post by Pumalite on 2008-02-24
Maybe the screenshot is bad, but I didn't see any unallocated space.

---

### Post by rominho on 2008-02-24
> **Pumalite said:**
> Maybe the screenshot is bad, but I didn't see any unallocated space.

If you look at the first screenshot it's right below the 64.47GB Data partition

---

### Post by Pumalite on 2008-02-24
You arer right. That would mean expanding hda5 to the left. Post:
sudo fdisk -lu

---

### Post by rominho on 2008-02-24
> **Pumalite said:**
> You arer right. [B]That would mean expanding hda5 to the left. Post:
sudo fdisk -lu[/B]

wow... I have no clue what you meant there!! :confused:

---

### Post by Pumalite on 2008-02-24
I hope you have an Ubuntu Live CD and that you can boot it. From the Terminal, copy and paste the command and do the same with the output here.

---

### Post by wireddad on 2008-02-24
Can you not merge the free space to C:?

---

