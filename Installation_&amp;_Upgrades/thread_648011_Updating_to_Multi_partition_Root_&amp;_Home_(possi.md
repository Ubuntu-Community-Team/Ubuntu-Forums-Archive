---
title: "Updating to Multi partition Root &amp; Home (possible?) (Unique Problem)"
date: 2007-12-23
forum: Installation &amp; Upgrades
---

### Post by rsangole on 2007-12-23
Hello,

This is the first time I'm posting here, although this forum has helped me setup my Kubuntu so successfully on my Dell 6400.

I have a problem that I'd like to share. I'm pretty sure there's an answer out there.

[U]Situation
[/U]
Here is the current setup of my filesystem.

Filesystem           1K-blocks      Used Available Use% Mounted on
[B]/dev/sda6             12468096  10342648   1492088  88% /
[/B]varrun                  517292       112    517180   1% /var/run
varlock                 517292         0    517292   0% /var/lock
procbususb              517292       136    517156   1% /proc/bus/usb
udev                    517292       136    517156   1% /dev
devshm                  517292         0    517292   0% /dev/shm
lrm                     517292     33788    483504   7% /lib/modules/2.6.20-16-generic/volatile
[B]*/dev/sda1             31455236   1334540  30120696   5% /media/sda1*
/dev/sda5             71584832  39907968  31676864  56% /media/sda5
[/B]

/dev/sda6 is my root. As you can see its 88% full. My home likes in here too (Takes around 3gb at the moment.

/dev/sda5 (56% usage) is a FAT32 where I keep all my documents, music, pictures, vids etc. Its a common space for my stuff between linux and winxp.

/dev/sda1 (5% usage) is a FAT32 where I *used* windows xp. It crashed on me and I dont want it anymore.

_Here are my questions:_
Without reinstallation of my system,

1. Can I move my /home/rsangole to /dev/sda5 or /dev/sda1 ?

2. I'm out of space in my root (/dev/sda6) I can't even upgrade to gusty. Can I use a portion of my /dev/sda1 for root?

Thanks for any inputs. I really appreciate your help,

Cheers!
Rahul

---

### Post by Craigus on 2007-12-23
[http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/")

[http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome")

You should be able to use Gparted to just resize your root partition, stealing some space from the others.

[http://gparted-livecd.tuxfamily.org/]("http://gparted-livecd.tuxfamily.org/")

---

### Post by nzadLithium on 2007-12-23
should be easy enough to do.


you should probably wipe the partition? that your going to move that home directory too.
as craigus suggested gparted is good for wiping / resizing etc.

once thats done 

open /etc/fstab

i think its kdsu kate /etc/fstab for kubuntu users?

add or modify the line for your sda5 as follows
/dev/sda5 /home/rsangole auto defaults,errors=remount-ro
or to use sda1 instead do 
/dev/sda1 /home/rsangole auto defaults,errors=remount-ro

(i think that would do it for your home directory then just copy and paste your home directory there)
(someone check that line for me plz dont want not being able to login coz files arent found)

once you move ur home directory from the root partition it should be all good for space on your root partition hopefully.

:D

if none bothers to verify that line then just try it
if it doesnt work then post back

---

### Post by nzadLithium on 2007-12-23
ah i just remembered i was gona do this same thing when i had a new hard disk so i had a page on these forums bookmarked bout how to do it :D

here:
[http://ubuntuforums.org/showthread.php?t=46866](http://ubuntuforums.org/showthread.php?t=46866)

---

