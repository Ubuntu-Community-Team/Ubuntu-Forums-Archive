---
title: "Can't boot LiveCD, Permission Denied"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by OPineault on 2008-02-15
This is my Setup:

2 SATA Drives, 
First HDD has 1 NTFS Partition with WIndows XP installed
Second HDD has 1 NTFS Partition, and 1extf/1swap with OpenSUSE installed.

When I try to boot from the Ubuntu live CD, I get to the Ubuntu menu, and select the first option to startup and install Ubuntu.

Iget the Ubuntu logo, the bar goes fully across, and on the next screen I get:

Loading, please wait...

Permission denied

Permission denied (10 lines of Permission denied)

And it just stays stuck there

I tried Ubuntu 7.10, Kubuntu, and Ubuntu 6.06 same thing on each.

I can boot my OpenSUSE CD fine..

My goal is to replace my SUSE with Kubuntu but I figured I'd ask advice here before starting random formats/repartitioning

I'm a Linux newb of course... haha

Thanks in advance!

---

### Post by louieb on 2008-02-15
Just wondering did you run the media check option on the CD. 
Just a shot in the dark. But a few twisted bits in the wrong place will give some odd errors. 

Just seems strange you get the same error on two different CD.

---

### Post by OPineault on 2008-02-16
Well, I just ran the option to check the CD for errors, and all 3 CDs came back with errors found in 4 files.

I burnt them each with the application K3B from my SUSE system, unfortunately I don't have a different brand of CD available to try on at the moment.

Would you have a different software to recommend for burning the images?
Something I'd be able to find through Yast? :)

And thank you for the reply!

---

### Post by rulerofogame on 2008-02-24
I have the exact same problem, although I have ordered(for free) multiple cd's from shipit, and they all have four errors. So that's not the problem.

---

### Post by Hilko on 2008-02-29
I tried to install Gutsy, I also get the same problem. > When I try to boot from the Ubuntu live CD, I get to the Ubuntu menu, and select the first option to startup and install Ubuntu.

I get the Ubuntu logo, the bar goes fully across, and on the next screen I get:

Loading, please wait...

Permission denied

Permission denied (10 lines of Permission denied)

And it just stays stuck there

The CD is good, I verified md5 sums before and after burning, all ok. The CD also works on other machines, just not this one.
I have tried the 7.04 normal and alternate CDs, these didn't work either.

I really really want to install Ubuntu. If anyone knows what is the cause of this problem or the solution or can point me in a direction where to look. Please let me know.

---

### Post by dstew on 2008-02-29
> Well, I just ran the option to check the CD for errors, and all 3 CDs came back with errors found in 4 files.It is important to burn the CDs very slowly, 4x at most. And, a CD that works in one machine might not work in another because the CD reading lens might be a bit dirty, or the CD-ROM drive has other problems. It can happen that a disk has some marginally visible bits on it, and one drive can see them, but another cannot, due to the weak signal, and to varying ability of CD-ROMs to read bits. It is an optical system, and just like your glasses, it can get dirty.

---

### Post by xen-uno on 2008-02-29
I couldn't get Live to work on this machine at all, tho I did get further than you did. Using the alternate iso worked for me ... along with Supergrub.

---

