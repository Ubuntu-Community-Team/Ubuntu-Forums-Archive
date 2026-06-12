---
title: "Weird Problem"
date: 2011-07-12
forum: Installation &amp; Upgrades
---

### Post by wickedwill on 2011-07-12
Ok i had an installation of windows 7 which was originally vista.  w7 was just an upgrade.

i installed wubi and everything worked great.. i also think i installed ubuntu to another partition. 

PROBLEM. i goofed up and had to do a clean install of windows vista then w7. 

now i seem to have lost wubi and or a partition that i believe ubuntu was on.. in disk management it says i have 232gb hard drive when in fact it is 250 and i know that when i installed wubi i chose 17gb.

i thought wubi installed as a windows ap and would not need a partition.. 

anyways is there a way to get that 17 gb back.. not a major problem.. just annoying

any help would be greatly appreciated.

---

### Post by Bucky Ball on 2011-07-12
Normal for the drive to show as less than it is. Wubi does install as a Windows app (basically) and does not need a partition so not sure what went wrong there.

I'd install Windows on whatever space it needs, leave the rest as free space, and install Ubuntu from an ISO install CD (not Wubi) into the free space.

Wubi is to try Ubuntu for awhile and see if you like it, not intended to be a permanent solution or a production OS. You've tried it. Did you like it? If so, do a clean install from a CD.

---

### Post by Quackers on 2011-07-12
If you have recovered your Windows system with a recovery dvd it is likely that the whole disc was used. This over-writes everything you had on there originally, so wubi and any other partitions are now gone.

A 250GB drive should show about 232GB after use.

And welcome to the forum :-)

---

### Post by coffeecat on 2011-07-12
> **wickedwill said:**
> anyways is there a way to get that 17 gb back..

It never went anywhere! :wink: 250 and 232 are the same. No, I haven't gone mad. Your drive is a 250GB (gigabyte) drive, which is the same as 232.83GiB (gibibytes).

1 Gigabyte = 1000 x 1000 x 1000 bytes
1 Gibibyte = 1024 x 1024 x 1024 (=1073741824) bytes.

That's when the prefix giga is used in the strict metric sense, such as the way manufacturers describe the capacity of their drives. Unfortunately, and confusingly, gigabyte (GB) is sometimes used to describe 1073741824 bytes, which it sounds as though Windows Disk Management is doing. In Ubuntu, you'll see GiB used when GiB is meant, except when GB is used to mean GiB.

Clear? :p

Do you have an Ubuntu live CD? If so, boot up with it, choose "try Ubuntu" and when you get to the desktop open Gparted (System > Administration if the desktop is the old classic gnome). Post a screenshot of the Gparted window, which will show your partition layout more clearly and more accurately than Disk Management in Windows. And it shows sizes in GiB too!

---

### Post by wickedwill on 2011-07-12
ok i am going to try to do the live cd gparted thing.. i am sorry about a few things as i am very comfy with windows and not so comfy with ubuntu.. but i can manage to get to gparted.. ill try to get screen shot if done the same way.. will post back..

---

### Post by wickedwill on 2011-07-12
ok i got two images

first one is from gparted showing 232 gb

second one is from the file system thing showing 250gb disk

---

### Post by Quackers on 2011-07-12
There is only Windows on the disc now. Linux is no more :-(
It will be necessary to either install via wubi again or shrink the C: partition in Windows Disk Management screen and create some free space for Ubuntu to install into. If you go down this route you should defragment Windows before shrinking the C: drive - defragmenting twice is better.

---

### Post by halibaitor on 2011-07-12
yeah, what coffeecat said...

You are showing the normal results for a 250 gig drive...

---

### Post by coffeecat on 2011-07-12
> **wickedwill said:**
> 
first one is from gparted showing 232 gb

Nope. Have a closer look. It's showing 232 GiB.

---

### Post by wickedwill on 2011-07-12
thank you i did not understand the difference between GB and Gib..

never ran across this.. and after doing the math seems correct..

will now be installing ubuntu again


thank you all so much was bothering me i thought i lost 17 GB and i even did a clean install of windows with format too..

anyways seems problem solved... is there a way to force windows to report GB in GB?

---

### Post by Bucky Ball on 2011-07-12
I'd advise the defragging Win drive, shrinking (in Windows with Disk Management, NOT Gparted) then a clean install. 10.04 LTS most stable and longest support and good place for a newcomer to start. ;)

Wubi installs can be notoriously buggy.

* Incidentally, this does a much better job than Win defragger:

[http://www.softpedia.com/get/System/Hard-Disk-Utils/Power-Defragmenter.shtml](http://www.softpedia.com/get/System/Hard-Disk-Utils/Power-Defragmenter.shtml)

It will even defrag Tivo files! Run that a couple of times.

---

