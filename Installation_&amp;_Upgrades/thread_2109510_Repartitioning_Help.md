---
title: "Repartitioning Help"
date: 2013-01-27
forum: Installation &amp; Upgrades
---

### Post by ntzrmtthihu777 on 2013-01-27
Hello all.

I have been using a dual-boot set-up on my HP dv6, with the following partitions

```
Logical
sda1 (32gb) Root for Precise x64 

Extended sda2 containing
sda5 (32gb) Intended Root for arch, project abandoned after scragging my /home partition :(
sda6 (32gb) Root for Backtrack5r3
sda7 (100gb) /home for Precise x64 on sda1
110gb of unallocated space
sda8 (8gb) Swap space


```After my abortive attempt to install arch I have decide to play with it in a vm until I get a better feel for it, and as sda1 is approaching its max (room to spare, but I would like a bit more wiggle room) I would like to "merge" (my understanding is you don't actually merge partitions, just delete and resize) sda1 and sda5 for a total of 64gb for root, but I am not sure how to proceed, I can't figure out how to do it and do not want to scrag my install (I got it set pretty nice, don't want to have to redo it)

I am comfortable with GUI and CLI programs, I just don' wanna mess up.

---

### Post by Bucky Ball on 2013-01-27
You have a problem as sda5 is in an extended partition which sda1 is not a part of.

My solution would be to delete sda1, expand the extended partition into the free space created then expand sda5 inside the extended partition. Should work.

One question: Why do you want it so large? I have never used anything larger than 15Gb for an install partition (/). I do keep all personal data on a /home partition, though, and not in the /home directory inside /.

---

### Post by ntzrmtthihu777 on 2013-01-27
> **Bucky Ball said:**
> You have a problem as sda5 is in an extended partition which sda1 is not a part of.

My solution would be to delete sda1, expand the extended partition into  the free space created then expand sda5 inside the extended partition.  Should work.

One question: Why do you want it so large? I have never used anything  larger than 15Gb for an install partition (/). I do keep all personal  data on a /home partition, though, and not in the /home directory inside  /.
Sounds doable, but it seems you missed a point -- I should like to avoid having to re-do everything I have done (heavy tweaking has occurred, lol)

I just like having room, seems to be a holdover from my win$ days.

---

### Post by Bucky Ball on 2013-01-27
Well, as sda5 is in an extended partition and sda1 is not, never the twain shall meet. ;)

PS: Also not sure why you have an 8Gb /swap. Do you hibernate often? If not, 2Gb is fine.

---

### Post by ntzrmtthihu777 on 2013-01-27
> **Bucky Ball said:**
> Well, as sda5 is in an extended partition and sda1 is not, never the twain shall meet. ;)

PS: Also not sure why you have an 8Gb /swap. Do you hibernate often? If not, 2Gb is fine.

Dang, I was afraid of that. :sigh:

8 gigs cuz I can, lol. I never hib, but I am a chronic multi-tasker, and it's my understanding that swap takes over if you start to "run out of" ram (correct me if I am wrong here).

---

### Post by Bucky Ball on 2013-01-27
Multitask your hardest and while doing so check out the system monitor and see if you are even using the /swap.

---

### Post by ntzrmtthihu777 on 2013-01-27
> **Bucky Ball said:**
> Multitask your hardest and while doing so check out the system monitor and see if you are even using the /swap.
I have never seen swap go into use on my system, but I am a bit of a doomsday preparationist, in real life and in the wired. "Better safe than sorry" is my motto :D What is 6 more gigs out of 320, yah feel me? It would be overkill on a tiny hard drive, but I got room to spare (142gb to be "precise" yuk yuk)

---

### Post by Bucky Ball on 2013-01-27
> **ntzrmtthihu777 said:**
> I have never seen swap go into use on my system, but I am a bit of a doomsday preparationist, in real life and in the wired. "Better safe than sorry" is my motto :D What is 6 more gigs out of 320, yah feel me? It would be overkill on a tiny hard drive, but I got room to spare (142gb to be "precise" yuk yuk)

Fair enough. ;)

---

### Post by ntzrmtthihu777 on 2013-01-27
Hmm, your sig link on building a linux computer is interesting, will read at another time. Ok, another question:

You mentioned deleting sda1 and growing sda5 into the free space, why can not the opposite be done, delete sda5, shrink sda2 by the appropriate amount (in essense moving the new 32 gigs of free space out of the extended partition) and then expanding sda1 into the resultant free space?

---

### Post by Bucky Ball on 2013-01-27
Yep, perfectly achievable.

---

### Post by ntzrmtthihu777 on 2013-01-27
> **Bucky Ball said:**
> Yep, perfectly achievable.
-rubs hands manically- alrighty then!
Question is, I tried doing this with my (admittedly limited) knowledge of partition manipulation, and could not figure it out. I was using Gparted from a USB install of 12.04 I use for troubleshooting other pc's and as a general toolkit.

---

### Post by Bucky Ball on 2013-01-27
Yep, that is the way to do it (running from a LiveUSB or LiveCD) as you can unmount all partitions (they need to be unmounted to resize; impossible if you are running Ubuntu from a partition you want to resize).

If resizing Windows partition though use the Win software to do that, not Gparted. It can cause problems with newer versions of Win.

---

### Post by ntzrmtthihu777 on 2013-01-27
> **Bucky Ball said:**
> Yep, that is the way to do it (running from a LiveUSB or LiveCD) as you can unmount all partitions (they need to be unmounted to resize; impossible if you are running Ubuntu from a partition you want to resize).

If resizing Windows partition though use the Win software to do that, not Gparted. It can cause problems with newer versions of Win.
...win$ partitions?! Mah 'top is pure linux buddy :D ...
Ok I fibbed, I do have a winXP VM to run some software there is no good linux alternative to... yet... and simply do not work under wine.

---

### Post by Bucky Ball on 2013-01-27
All good then. ;)

---

### Post by ntzrmtthihu777 on 2013-01-27
Again though, I need help here. I simply could not figure out how to do it myself, and I am deathly terrified of scragging up again -shudder- my whole /home partition was destroyed when I tried my hand at arch, and I consider myself fortuneate I had most of my personal data backed up via Dropbox, although I now have 2 useless gpg keys that I can't get rid of now.

Personal advice and/or a instructive link would be appreciated.

---

### Post by Bucky Ball on 2013-01-27
Well, boot from a liveusb or disk, once at the desktop launch Gparted, right click on partitions to make sure they are unmounted, delete sda5, shrink sda2. This should leave the free space now *outside* of the extended partition (sda2) right next to sda1 and you simply expand sda1 into it and up to the beginning of sda2.

Hope that helps.

---

### Post by ntzrmtthihu777 on 2013-01-27
Hrm, coulda sworn that's what I did, oh well :shrug: will give it a shot. Off topic, but being staff as you are perhaps you could explain something to me:

In my details it refuses to show the location I put, it reads &#12470;&#12540;&#12527;&#65286; but should be &#12470;&#12540;&#12527;&#12452;&#12516;&#12540;&#12489; (Za Waiyaado - kana for The Wired, little geek anime reference), is there something I am missing here?

---

### Post by Bucky Ball on 2013-01-27
Sounds like you have all valuable data backed up already but if not, make sure you have before attempting this rejig. 

Hmm. Not sure about that second question. I would post that in ***Forum  Feedback & Help*** sub-forum and get one of the Admins to have a look. Maybe it is having problems with some of the characters but as you can post them here I'm not sure why that would be. It also doesn't appear to be too long ...

---

### Post by ntzrmtthihu777 on 2013-01-27
-heaves a huge sigh of relief-
It worked. Apparently the crucial step I was missing was to swapoff. I deleted sda5, shrank sda2 away from sda1, and grew sda1 into the resultant free space, thereby achieving my goal.

I have noticed that gparted and the ubuntu installer system must use a different definition of a gigabyte, the latter reported my 32gb root partition as such, but gparted (and conky, now that I look at it) reports it as somewhere in the region of 29.8 gb... strange but not crippling.

Puzzling, mostly. I rather wish everything in my box would agree on what is what (nautilus reports my new root as being 64, but conky and gparted show 58.7 and 59.61 respectively)

Marking thread as solved.

---

### Post by Bucky Ball on 2013-01-27
Great news and glad it all worked. You can mark as 'Solved' from Thread Tools at top right of this page. 

As for the size discrepancies, one sees the total size of the drive and the other would show the available size of the drive excluding the space used by essential system files I would think. All good. ;)

---

### Post by ntzrmtthihu777 on 2013-01-28
Hmm, any way you know of to change this behaviour? I should rather like conky and nautilus to agree at the very least, as I interact with them most. Gparted would be a plus, but that's poking into very technical things that I am not quite yet comfortable with.

---

### Post by Bucky Ball on 2013-01-28
Not that I know of.

---

