---
title: "Partitioning under v.5.1 [I want to keep my old files]"
date: 2006-12-20
forum: Installation &amp; Upgrades
---

### Post by freedom1378 on 2006-12-20
Hi, I was introduced to Ubuntu a week ago when my computer's OS went haywire and wouldn't boot up normally [Windows XP].  Since I haven't backed up my drive in 5 months, I needed to find a way to get them out and my friend wondered if it could.  He gave me his old copy of Ubuntu 5.1 [I ordered 6.6 but it won't be here for a while] and read on the CD sleeve that to keep my old files I would have to follow the special instructions. I went through and got to the partitioning part when I got very confused.

I looked around the forums and didn't really find anything that would help me.  Google didn't help much either.  So I'm asking all of you directly.

[If few people remember the interface of 5.1's installer, it's the text-based one.]

I would really like my files back :)

Ubuntu looks like a very stylish OS btw, and when I get my files out and get the 6.6 installer CD, I will definitely use that as my primary OS.

---

### Post by K.Mandla on 2006-12-20
Probably the best way to salvage your files is to download a live CD of Ubuntu (or better yet, a live CD of Xubuntu, which is lighter and faster).

Then boot to that CD, open a terminal window and try this command:

```
sudo fdisk -l
```
See if you can match the size of your hard drive to the results it shows. What you're after is a name and number like this: /dev/hda1 ... in fact, chances are that's the one.

Now try these commands:

```
mkdir ~/drive
sudo mount -t ntfs /dev/hda1 ~/drive
```
Hopefully that will attach your hard drive to a folder in the computer's memory. 

From there you should be able to plug in a USB drive and copy things from that folder, using a file manager (in Xubuntu, it's Thunar). 

These are kind of sketchy directions, but this is a little bit of an advanced maneuver, so you might need some help walking through it.

---

