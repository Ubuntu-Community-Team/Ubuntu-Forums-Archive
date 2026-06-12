---
title: "GRUB Hands on Install"
date: 2005-06-24
forum: Installation &amp; Upgrades
---

### Post by programgeek on 2005-06-24
Hi - I am one of those people in need of a helping hand, yet aren't going "HELP!!!!!" because people who do that give me a headache.  But those are humans.  I'll shut up now.

[http://ubuntuforums.org/showthread.php?p=227810#post227810](http://ubuntuforums.org/showthread.php?p=227810#post227810)
This thread was never solved, or at least I haven't seen it solved.  This is on 5.04 fo r me, so I posted here. O:)

Does anyone here know a link to an Ubuntu FAQ on this?  Or is there another post that solved this?

I have the symptom of my grub doing
"Loading stage 1.5

Loading Please Wait..."

And then it just stalling.  :grin:  What mistake could I be making here?  I could go up and bring my HD geometry, but I'm a human being, my name is just a cover. ;)

Also, the person who finds the answer to my problem gets a cookie.  :razz:   Thanks!

---

### Post by Dave_is_sexy on 2005-06-24
Oh bootloader fun  :smile: 

Using my advanced knowledge of partitions and filesystems i deduce that... *uses mind powers*....

did you install ubuntu on a new partition further in your harddrive? Often there are issues with installing the bootloader past the 1028th cylinder. To you and me that's "physically after windows"

The work around is to hve a seperate /boot partition where boot-type stuff goes on. This has to be at the start of your harddrive and it has to be on a native linux filesystem - so you can't just put the files on C;` unfortunately.

You ned to make a tiny partition before windows. about 70mb maybe. you don't need that much but some programs have that as a minimum (eg partition magic).

Now, you can't move the windows partition without partition magic (or geek qualifications). so time to boot windows. CD in. > repair existing instalation > C;` > then type fixmbr

That's windows up. get partition magic through some legal channel (trial version?) and RESIZE windows partition to be create 70mb or so space before it. don't fill that in with a patition, do that later in ubuntu - using manual partitioning if you know how to do that.

---

### Post by Dave_is_sexy on 2005-06-24
..continues. once you've done that and ubuntu is saying "what kind of manual partitioning?" you should say 

"one here. 70mb. mount point = /boot" (before windows)
"one here. 2000mb. mount point = /" (after windows). That size is the size you want your instalation to be

set the filesystems to be ex3

before you write to disk make sure that the only smiley faces are on the partitions you just made.

Then proceed. All should be fine - assuming that's the problem

---

### Post by programgeek on 2005-06-24
Honestly, what was I thinking?  Putting windows BEFORE ubuntu on my hard disk?

... That is EVIL thinking.  *gives you cookie*

Ugh - Just a wierd situation I got myself tangled up into.  Sorry. :) Enjoy though, it's chocolate chip! :D

---

### Post by mohaham on 2005-06-24
GRUB uses LBA by default, so it can't be the 1024-cylinder limit thingy..
is GRUB installed on MBR
what partition is Ubuntu installed on
can u post ur /boot/grub/menu.lst file

---

### Post by electrosoccertux on 2005-06-24
do you have LBA/Large mode enabled on your mobo's BIOS? I had mine on Manula -> LBA and I had to put it to Auto -> LBA for my grub to not have problems. Go figure. Maybe this will help?

---

