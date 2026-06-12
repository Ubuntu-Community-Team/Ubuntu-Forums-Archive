---
title: "Help me install . . . please."
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by mrhirsh on 2007-08-16
I have a new laptop (AMD 64 x2 processor, ATI Radeon X1200 graphics, 160gb HD, Vista).

Here's what I've done:

1.  I partitioned the HD using the utility in Vista, creating about 73 GB for Ubuntu;
2.  I first attempted to install 7.04 for 64 bit processor, saving it to CD as an image file;
3.  On attempting to do the install got the error message concerning my graphics driver;
4.  Spent the day finding a driver for said card, couldn't get that to install (got a "job not open" message).
5.  Went through same process with version 6.06 and could actually use it as long as I was doing it from the CD.
6.  When I attempted install, all seemed to be well until I got to "Step 5 of 6" where it asked me about partioning, etc..
7.  The computer looks like it's "looking" at the HD, but it will show me the little rotating icon for hours (if I let it).  Eventually I hit cancel and it takes me out of the install.
8.  In browsing around this forum, there seem to be some suggestions, but those are geared to those more accomplished than myself.  So if typing code is involved in the fix, tell me where I am supposed to type in the process.

Thanks,

---

### Post by dabl on 2007-08-16
Here's how I would try it:

1. Download and burn the AMD-64 Alternate Install CD (ISO image).
2. On that 73GB partition, I would use my Live Gparted CD (from [[COLOR="Magenta"]**here**[/COLOR]](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828) ) and make a 7GB partition for "/", a 0.5GB partition for swap, and the rest of it for "/home".
3. Using my Alternate Install CD, follow the step-by-step, and choose the appropriate mount points for the partitions.
4. Upon reboot, understand that you're probably going to get the black screen.  At that point, follow the instructions [[COLOR="Magenta"]**here**[/COLOR]](http://kubuntuforums.net/forums/index.php?topic=3085112.0) to make a VESA display, in which to operate.
5. Become a student of drivers for ATI cards ....

:popcorn:

---

### Post by mrhirsh on 2007-08-16
I don't see an "AMD-64 Alternate Install" option.  Is this the 7.04 or the 6.06 or another version?

Thanks,

Michael
770-924-0153

---

### Post by dabl on 2007-08-16
Meh -- shame on me for working from memory. On this page:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

it's the one called "64bit AMD and Intel computers".  I recommend Feisty (7.04), and check the "Alternate Desktop CD" box under the "Download Here" link.


EDIT: Since Vista takes 2 partitions, and I recommended 3 more for your Ubuntu Linux, and you're limited to 4 primary partitions per hard drive, I assume you understand that you need to make a third primary partition, and then put an "extended" partition in it, and then make your 3 "logical" partitions inside of that.  Or you could make 2 more primary partitions if you want to get fancy, and put an extended partition with 2 logical partitions inside of it, and leave the fourth as a primary partition.  Your choice(s) ....  ;-)

---

### Post by mrhirsh on 2007-08-16
I need some help going through the use of the live Gparted CD.  It's scrolling at 100 mph and I don't know what to type where.  I am attempting to follow the process outlined at [http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php) but I am not getting as far as that in installing the program.  Based on the message, it is another video graphics driver problem . . . I am getting to a prompt to run a forcevideo script, but I don't know what that is or how to do it.

This is preceded by a warning about never to mount anything on /mnt!

thanks,

---

### Post by merlinus on 2007-08-16
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)

-merlin

---

### Post by mrhirsh on 2007-08-16
I have been attempting to use the link given above.  WHen I do the auto configuration option, it goes through a lot of gyrations, then prompts me that:

"The graphical environment configuration should have been done automatically.  Unfortunately, it did not, since you are back to the bash.  So please run Forcevideo script [i don't know what that is or how to do it], and you will be asked for the video driver, and resolution."

---

