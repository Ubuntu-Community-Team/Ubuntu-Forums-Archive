---
title: "Help me please"
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by meatsheets on 2008-01-01
Hey,

my friends parents gave me their laptop because they couldnt get it to work and they got a new one.
The problems that they told me were, it was throwing kurnel errors.

I figured if i zeroed the hard drive out, which i did, and try to install ubuntu it would be fine.

But when i tried to run the first disk it would tell me a bunch of errors, and then would go to the live root command
I burned a second disk, and when it got to where the screen was tan and then it would just freeze.
My brother told me that he would try to fix it (he works at a computer store) and told me he got kubuntu working on it.
But when i tried to boot it up, it would give me the same errors that the ubuntu live disk was giving me and would go to root comand

I was wondering if there is something else i could try.
Or would buying a new hard drvie fix this problem

Thanks alot

---

### Post by taurus on 2008-01-01
You could list the spec of that laptop.

---

### Post by meatsheets on 2008-01-01
im not positive on the specs
but i am pretty sure they are

1.05 ghz procesessor
384 RAM
and i dont know how mny gigs
i think its 40

im not sure because they gave me the computer with the problems and ive never been able to check the specs on it

---

### Post by PmDematagoda on 2008-01-01
I would recommend that you use [Xubuntu]("http://www.xubuntu.org/get") since Kubuntu may not work that well on 384Mb of RAM. 

But about the errors, could you please tell us what they are? What are they saying? If we do not really know what errors you are getting then we cannot help you much.

---

### Post by taurus on 2008-01-01
Or try the alternate CD and burn it at a slow speed like 4x.  Some old laptops don't take fast burning CDs too well.

---

### Post by meatsheets on 2008-01-01
you know when you are booting the computer up, and ubuntu gives you that loading bar?
well half way threw that it stops and and then it goes to liek cammand mode, where it is telling you what it is doing.
And it says "checking file systems"

and then it says like [ 155.704362} Buffer I/0 error on device sda3, logical block 1643

and it says this and a bucnh of other things under file systems (i can only type so fast..
and then it says file system check     [fail]


but like sometimes it does boot up...
like i just restarted it to get some more of the errors but it worked this time...

---

### Post by meatsheets on 2008-01-01
and i dont think its that old of a laptop...
i think its only like 2 or 3 years old

---

### Post by meatsheets on 2008-01-01
when it did start up it said 
"could not start kstartupconfig. Check your installation."

---

### Post by xeth_delta on 2008-01-01
Messages apearing on the screen, instead of the bar, do not necessarily indicate a problem. By the other hand, "it says file system check [fail]" as you mentioned, seems to show a file system/hard-disk problem.

I wonder if performing a file system check from the live CD would help.

Xeth

---

### Post by xeth_delta on 2008-01-01
Might be a silly question, but how much space do you have on the "/" partition?

---

### Post by meatsheets on 2008-01-01
i set it up so the entire hard drive was used for the install

and it is a 40 gig hard drive

---

### Post by oldsoundguy on 2008-01-01
If you were getting kernel errors on WinDOZE, there is a slight chance that you may have hard drive issues with some bad sectors.  You need to run a scandisk or chckdisk program (usually from a floppy disk you have set up) and have it fix or repair the sectors or MARK THEM if that can not be done.  Then, when you load the program, it will not attempt to load to a bad sector.

---

### Post by xeth_delta on 2008-01-01
> **oldsoundguy said:**
> If you were getting kernel errors on WinDOZE, there is a slight chance that you may have hard drive issues with some bad sectors.  You need to run a scandisk or chckdisk program (usually from a floppy disk you have set up) and have it fix or repair the sectors or MARK THEM if that can not be done.  Then, when you load the program, it will not attempt to load to a bad sector.

I am afraid that he won't be able to use chkdck or scandisk, but fsck. From what I understand the entire hard-disk is used for Linux, and most likely ext3 is being used.

Xeth

---

### Post by meatsheets on 2008-01-01
windows was on the computer before i put linux on
but the entire hard drive is now ext3

would it be easier to just buy a new hard drive?

---

### Post by xeth_delta on 2008-01-01
> **meatsheets said:**
> windows was on the computer before i put linux on
but the entire hard drive is now ext3

would it be easier to just buy a new hard drive?

First make sure the hdd has any real damage. Boot from the live CD and perform a file system check with fsck. If you need any help with that, let us know.

Xeth

---

### Post by meatsheets on 2008-01-01
i am running fschck now

---

### Post by oldsoundguy on 2008-01-01
xeth, thanks for the correction!
meatsheets .. easer, not cheaper!

---

### Post by xeth_delta on 2008-01-01
> **oldsoundguy said:**
> xeth, thanks for the correction!
meatsheets .. easer, not cheaper!

No problem, I have also mistakenly skipped lines when reading posts before. :)

---

### Post by meatsheets on 2008-01-01
when it says
"Error reading block 1033 (attempt to read block from filesystem resulted in short read) while getting next inode from scan."
should i ignore error or no

---

### Post by meatsheets on 2008-01-01
never mind i figured it out

---

