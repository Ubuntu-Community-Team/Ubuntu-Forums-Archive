---
title: "Looking forward to Jaunty upgrade"
date: 2009-02-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by Messyhair42 on 2009-02-05
So I'm looking forward to the release of Ubuntu 9.04 but i've got a set of concerns. it will be my first upgrade since swtiching to Ubuntu and talking with other people who have been with it longer got me thinking into some things i could do better. I have two hard drives a 1 TB drive containing windows and all my photos and music, and a 160 GB drive containing Ubuntu and my other media. when i installed ubuntu i let the installer do everything automatically so my /home and / are the same partition. I've done a fair amount of playing around customizing things and have a number of unique programs. What i'd like to do when Jaunty comes out is switch the hard drive's my OS's are on, so Ubuntu gets the big drive. I'm not worried about my media b/c i have backups or can get an external HD for storage and portability.
my concerns are everything becoming a complete disaster with new installs. i can gradually put programs and apps back on after a new install but the process itself scares me a little, such as how do i clean both drives so i can get a fresh install, how do i make /home its own partition so for future upgrades i dont have to overwrite it, how many other partitions and mount points should i make unique and things like that? my aim is to make things easier to work around and upgrade rather than leaving everything static. Thanks in advance, Messyhair42

---

### Post by Messyhair42 on 2009-02-07
bumping with an add on

if /home is it's own partition it doesn't have to be overwritten for each upgrade right?

---

### Post by beyboo on 2009-02-07
You are correct. AFAIK - since Hardy Ubuntu offers to preserve existing /home partition. 

However you are warned, this is not auto-detected. 

During install just  select the option that lets you manually set up the partitions, instead of the guided option. This will let you choose what partition gets mounted where on your new install. Also, there will be check boxes that let you choose which partitions get formated... 

Make sure your /home isn't one of them!

---

### Post by Messyhair42 on 2009-02-08
I was moreover looking for advice as to how to reinstall both OS, as far as formatting goes. can i just boot to a liveCD to install JJ on my big drive or do i have to wipe everything off both first? and if so what's the best way to wipe them?

---

### Post by cariboo on 2009-02-08
If you setup a separate /home partition you will have to select the manual partition option when you get to the partitioning step. 

I have a separate /home partion, because I always start using the next version as soon as the repositories are open, and at times there is nothing you can do to repair several problems, without reinstalling.

Jim

---

