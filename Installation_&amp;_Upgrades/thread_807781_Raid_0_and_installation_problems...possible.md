---
title: "Raid 0 and installation problems...possible?"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by jim256 on 2008-05-26
Hey all,
Ok, so I had Ubuntu on my previous box about a year or so back, and was playing around with 7.04/7.10 and really liked it.

My problem was that I then upgraded to a slightly higher performance pc, one that I configured as Raid0. I read back then, and have done some reading now, but must say that I feel more than slightly overwhelmed/lost.

My question that I just want to get is...With my current setup, A WinXP Pro SP3 PC, with two 80gb HDD's configured as Raid0 and partitioned as a few different sizes/drives...Can I install Ubuntu with Raid 0 or no?

If not, can I install it at all, such as using the method of a live cd (did this a few times before).

Thanks a lot!,
Jim.

p.s. im sorry if this answer is obvious. I am pretty used to the forum system and am a very active member of a couple boards, but just haven't been able to find the straight answer im looking for just yet.

---

### Post by jim256 on 2008-05-26
alright well i loaded up the live cd, installed dmraid, and that definitely helped.  my ubuntu system can now recognize the raid partitions but...when attempting to install, after hitting all the "ok"'s and "forward"'s, I get this error...

"The ext3 file system creation in partition #4 of Serial ATA RAID pdc_jgabeiii (stripe) failed."

any ideas anyone?  would be much appreciated.

Thanks!...sorry for my noobishness...

EDIT: ok well i thought i may as well give ext2 a shot and...it got farther, but still got this error not too long after :S 
"The attempt to mount a file system with type ext2 in Serial ATA RAID pdc_jgabeiii (stripe) at / failed.

You may resume partitioning from the partitioning menu."

thanks!

i would love most to just go ahead and use ntfs but...my only mount options there are \dos and \windows?...? 
thx.

EDIT2: reiserfs gave me this: "The attempt to mount a file system with type reiserfs in Serial ATA RAID pdc_jgabeiii (stripe) at / failed.

You may resume partitioning from the partitioning menu"  

and xfs and jfs gave me the same error that i got very first. im not sure if any of this is really relavant/matters/helps but..thought i might as well throw it out there.

---

### Post by twright on 2008-05-26
the wubi installer (run within windows) should work

---

### Post by jim256 on 2008-05-26
> **twright said:**
> the wubi installer (run within windows) should work

well I posted this problem over in the wubi forum and got the response that "...it is likely NOT to work..."
I was also looking at the ubuntu/wubi documentation and it was actingc like it would work...should I still give it a go?

my raid controller is a fasttrak promise tx2.

thx a lot.

---

### Post by htnusa on 2008-06-28
Hi All.....
Same problem here.... I used the Wubi download link but default won't work a little help please,,,Heres the problem.

My windoze XP pro is running on the following MOBO:
ASUS A7V266-E with an AMD 2000 XP CPU
(2) 80gb hard drives 2 + 0 promise raid
Fasttrak 100 lite      biosversion Promise technology

I downloaded Wubi + Ubuntu
And rebooted my machine and chose Ubuntu for startup……
And the error messages started as follows…..

[xxxx.xxxxxx] Buffer I/O error on device sdd, logical Block 0
[xxxx.xxxxxx] Buffer I/O error on device sdd, logical Block 1
[xxxx.xxxxxx] Buffer I/O error on device sdd, logical Block 2
[xxxx.xxxxxx] Buffer I/O error on device sdd, logical Block 3

and the numbers in the brackets [xxxx.xxxxxx] keep changing but eventually they repeat until I crash the system and restart in windows.
Can I pass along an argument to the kernel from wubi (like GRUB)???

Something like "Root No verify???"

I'm confused a step by step would be very helpful....
htnusa:confused:

---

### Post by jim256 on 2008-06-29
and i'll jump in and say if anyone out there is still willing to help me out a bit i'd appreciate it! have sort of just given up on ubuntu (and linux) for the time being but would sure love to have it if possible...thx!

good luck man

---

### Post by htnusa on 2008-06-29
Hi Jim,
I'm hoping somebody can help us both out....Don't give up on linux though it's way cool!! I have a seperate box running fedora 7 and will be adding Ubuntu to it as well at some point. The Wubi-Ubuntu / windows interface is what I really want to get going on my primary box though. The fact that The promise drivers are controlling the raid seems to be what causes the problem  and not the raid itself. Somebody knows the answer....It's just a matter of that person reading your post... I'm hoping that happens soon for both of us...regards, Htnusa

---

### Post by jim256 on 2008-06-29
> **htnusa said:**
> Hi Jim,
I'm hoping somebody can help us both out....Don't give up on linux though it's way cool!! I have a seperate box running fedora 7 and will be adding Ubuntu to it as well at some point. The Wubi-Ubuntu / windows interface is what I really want to get going on my primary box though. The fact that The promise drivers are controlling the raid seems to be what causes the problem  and not the raid itself. Somebody knows the answer....It's just a matter of that person reading your post... I'm hoping that happens soon for both of us...regards, Htnusa

hmmm ya agreed.  i definitely believe that someone out there has the right answer...but hey if i find out ill let you know, and vice versa deal? also...have you run ubuntu recently? if so, do you prefer it or fedora more?

---

