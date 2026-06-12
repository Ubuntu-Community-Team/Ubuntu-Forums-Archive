---
title: "Problem Installing Ubuntu 6.10"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by vm89 on 2007-02-26
I have downloaded the i386.iso file from the ubuntu.com
and i used nero to burn it
when i bootup the ubuntu 5 option with other F1-F6 Keys
So after i select the first option it says "[COLOR="Red"]Loading[/COLOR]" 
and then it freezes and no repose what so ever.
I have tried several times several computer but same thing
What should I do now ?
I am downloading the file again and will try to burn it one more time but 
i think it is not the issue.
Thanks you for your help and support

---

### Post by ImmortalGrey on 2007-02-26
> **vm89 said:**
> I have downloaded the i386.iso file from the ubuntu.com
and i used nero to burn it
when i bootup the ubuntu 5 option with other F1-F6 Keys
So after i select the first option it says "[COLOR="Red"]Loading[/COLOR]" 
and then it freezes and no repose what so ever.
I have tried several times several computer but same thing
What should I do now ?
I am downloading the file again and will try to burn it one more time but 
i think it is not the issue.
Thanks you for your help and support

It sounds like your CD might have an error in it.  When you get the download finished again, make sure you run MD5 to ensure the checksums match up, that way you know things are in order.  

[Instructions on using MD5.](https://help.ubuntu.com/community/HowToMD5SUM)

And by first option you meant the "Start/Install Ubuntu", correct?

EDIT:  Also, I read in another thread that NERO caused a problem with the installation CD, you might want to try an [alternate method.](https://help.ubuntu.com/community/BurningIsoHowto)  =)

---

### Post by .alpeffers. on 2007-02-26
one thing i found, was that any and all of my old CD-Rs were just unfriendly to linux ISOs... I changed no software settings, or programs, etc.  just discs and it worked no issues.


old discs were Ritek(if thats any help) and i'm now using Memorex or Fujifilm... ones my CDs the others DVDs ;)

---

### Post by vm89 on 2007-02-26
Burning Sure did SOLVED the problem.
Thanks ALL
I recommend every new Linux user to use the Infra Recorder than Nero
Trust me Nero does not work (no at the first time)

After starting up I got few errors
wondering what to do now.
Here it is:
17139703.572000 buffer i/o error on device hdc, logical block 293702  TO  293729 
17139703.572000 buffer i/o error on device hdc, logical block 293747  TO  293750
vfs: brelse: trying to free buffer
squashfs:sb_bread failed reading block 0X8e7a3
squashfs:unable to read page, block 239e1b8c, size 7356
And then it did nothing or froze

What should i DO!!!

---

