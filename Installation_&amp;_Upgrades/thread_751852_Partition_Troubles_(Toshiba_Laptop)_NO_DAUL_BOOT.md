---
title: "Partition Troubles (Toshiba Laptop) NO DAUL BOOT"
date: 2008-04-10
forum: Installation &amp; Upgrades
---

### Post by aries_green_monkey on 2008-04-10
Recently my Windows XP Home Crashed, my CP was runniong poorly because of it anyway (made for 98).

Anyway, i want to put on Ubuntu 7, but whenever i am installing, it says:

> The Creation of Swap Space in Partition #5 of IDE1 Master (hda) Failed.

I will admit i am a COMPLETE n00b to OS installation. I do not want to dual boot, i understand the concept of partitioning and everything, just not the specifics. I've searched all around the internet (Yahoo, Google, My Other Forum, Youtube, Random Computer Sites) But have not had any luck, so i thought i would come straight to the source... :)

ANY help at all would be greatly appreciated. Maybe a link to, or a tutorial, because i need to know what exactly to do to get this baby running!! :)

Also: This version of Ubuntu is perfect, I've run it off the live CD for like a week now and am sure it is perfect for laptop performance-wise. It is a Toshiba Sattelite A20 with a ~40 GB hard-drive. 

Once again, thanks so much for any help.

---

### Post by cmykflutterby on 2008-04-10
i'm actually using the exact same lappy running 7.10-
it has installed fine for me.
what partitoin setup is on the drive
and what partition options are you choosing during install?

---

### Post by aries_green_monkey on 2008-04-10
Well right now i'm following the tutorial here [http://www.funnestra.org/ubuntu/gutsy/#install](http://www.funnestra.org/ubuntu/gutsy/#install) so i have:

ext3 / root directory @ ~10 MB
ext3 /home documents directory @ ~30 MB
swap @ ~2GB 

Also, the number in my boot partition error changes each time i try.
I dunno, i wish it would work though....

^^ How i got to that is from the install button on the desktop, then since the automatic partitioner doesn't work, i just hit manual to set up that... anybody know whats wrong.

---

### Post by cmykflutterby on 2008-04-11
well i would suggest to use gparted to manually setup your partitoins before running the installer- off the live cd it should be:
system->administration->partition editor
on a 40 gb drive i setup a 2gb swap, a 10gb root, and a 18gb /home
(i have my root and home using only one partition out of laziness, and my swap is in an extended partition- i run dual boot)
see if that helps- if you can get gparted to redo your HD right
then i'd rerun the installer using what you've made

---

### Post by cmykflutterby on 2008-04-11
also, remember to delete any unused partitions that are taking up space- a windows partition will just eat up space

---

### Post by aries_green_monkey on 2008-04-13
I tried to do all of that... but i always get the same message,

Theirfore, i just tried to do it without the swap space and i get this:

[http://img151.imageshack.us/img151/5736/screenshotye2.png](http://img151.imageshack.us/img151/5736/screenshotye2.png)

Why am i getting these errors?

---

