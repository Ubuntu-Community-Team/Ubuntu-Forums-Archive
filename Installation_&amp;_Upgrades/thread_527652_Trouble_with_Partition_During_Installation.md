---
title: "Trouble with Partition During Installation"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by Palerider07 on 2007-08-16
Well, I've been having wild urges to get Linux after i heard about Ubuntu. I've finally convinced to go through the works and install the thing.

My installation starts off fine. Everything goes through ok in the first steps: language, keyboard setting, time, and everything else. The problem comes with the partitioning.

When I start it off, i go for the first option and free up 22700 MB on my 80GB Hard Drive. I click next, and it tells me it needs to resize the partition. When I click next, it gives me an error saying it cannot resize, and takes me to manual settings.

From here on, I cannot figure out what to do, because no matter what I keep doing after, i cannot resize the partition. I'm trying to dualboot with windows, and I only have one hard drive.

Help would be appreciated.

---

### Post by merlinus on 2007-08-16
What version of windows?  

Before attempting ubuntu install, delete temp and other unneeded files, backup data, set virtual paging to zero (set it back after install), and defrag several times.

If using vista, use its disk manager to resize its partition.

-merlin

---

### Post by Palerider07 on 2007-08-16
I'm using Windows XP.

How do I change the memory to 0?

---

### Post by merlinus on 2007-08-16
Search Help for virtual paging.  It is probably in System Tools.

Then you will most likely need to restart.

-merlin

---

### Post by Palerider07 on 2007-08-16
But how do I create the partition so that ubuntu can use at least 15-20GB?

---

### Post by merlinus on 2007-08-16
After following my suggestions, boot from the live cd and see if the partitioner can now shrink the windows partition and make room for ubuntu.

Another option is to use gparted live cd to do this before attempting install:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

-merlin

---

### Post by Palerider07 on 2007-08-16
Just a quick question before I finish. It managed to resize. But I have a question. 

When the installation came to step 4, about the partition, i took the first option, guided, and moved the bar to 58.6GB. Does that mean Windows will have 58.6GB, or Ubuntu?

---

### Post by merlinus on 2007-08-16
If you chose to resize, then moving the bar to the left gives the new size.  So windows would have 58.6G, and ubuntu the rest.

Keep in mind that you will also need a swap partition of about 1.5G, which the partitioner will create.

-merlin

---

### Post by Palerider07 on 2007-08-16
I have a horrible problem. Linux is working. But instead of windows receiving 53.5 gB, Linux did. THAT'S BAD! 

Now, Windows doesn't even open up. When I try to boot it, I get an error. Is there any way for me to change it so that windows has 53.5 GB, and so that it starts up again? Please, I'm begging you.

---

### Post by merlinus on 2007-08-16
Use gparted live cd (link in previous post) to resize the windows partition.

Afterwards, go back and reset virtual paging to whatever it had been.

-merlin

---

### Post by Palerider07 on 2007-08-17
I can't get into windows. When I press enter on the Windows Os from the list of my OS's, I get a    Disk Write Error    problem. HELP!!!

---

### Post by merlinus on 2007-08-17
Boot from your xp cd (or dvd) and select Recovery Console (or something similar).  You can restore the windows bootloader to the mbr from there.

I believe the command is fixmbr.

If this gets you into windows, then you can reinstall grub in order to dual boot.

You did back up your data, as I advised?

-merlin

---

### Post by Palerider07 on 2007-08-17
I have evrything running. Both Oses are working. I have just one last question.

My hard drive now only says I have 53.5 GB. I know this is because of how I partitioned the computer. Is there anyway to revert the size of the hard drive to its original state? Is there any other sofware, because your previous one seemed to not have worked. Help.

---

### Post by merlinus on 2007-08-17
What software is saying your hdd has 53.5G?

Did you try booting from gparted live cd?  What does that show about partitions and sizes of same?

You can shrink your ubuntu partition from left to right, and then add the freed-up space to windows.

Can you post a screenshot?

From a terminal in ubuntu, post results of:

```

df -h

```-merlin

---

### Post by Palerider07 on 2007-08-17
Thank you for all of your help. I am finally done with the installation, and everything on the computer is working flawlessly. I don't know what I could have done without you. Again, thank you.

---

