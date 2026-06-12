---
title: "Feisty won't let me get to partitioning"
date: 2007-05-14
forum: Installation &amp; Upgrades
---

### Post by ken_38 on 2007-05-14
I've tried installing Feisty from the Live Cd as my first ever non-Windows OS. The first few choices are fine - then it comes to the partitioning part. I select manual as I want to create a /home partition as well as root and swap. The progress bar goes through the examine partitions bit and I am then put on to the next screen with no partitions listed, everything grayed out and no explanation.

I seem to remember someone having a similar problem in this forum when I was looking through it at the sort of problems I might face, but I can't find the relevant post [perhaps my search parameters aren't right].

Anyway, is there anyone who can help a beginner to get off the blocks? Or do I step back to an earlier distro like Edgy?:confused:

---

### Post by ken_38 on 2007-05-15
Just to follow up in case the problem isn't clear enough.
I've currently got XP installed on a 200GB HD in two partitions, the first for the OS and applications, the second [which I need to maintain at present size] for my files, records etc.
When I'm trying to install Feisty, the screen which should show my HD partitions is blank and all the point and click instructions are grey. I can't do anything on any part of the screen and so can't move forwards.
I need to keep XP because of the work I produce for other people, but even if I wanted only Ubuntu, I couldn't do anything about repartitioning.
I can see I've had a number of viewings; that at least stops me feeling in limbo! But if there is anyone out there from the community with an idea as how to progress, please share it.

---

### Post by ken_38 on 2007-05-24
Without any replies since posted, so I suppose no-one knows how to advise me on the problem.

So, I've downloaded a copy of Edgy and had no trouble in installing it, partitions and all. Pity, though, about Feisty.

I suppose when the next issue comes it will be all right to save my data and do a clean install without having to go through Feisty, which I can't seem to get on to the computer anyway!!:confused:

---

### Post by stchman on 2007-05-24
> **ken_38 said:**
> I've tried installing Feisty from the Live Cd as my first ever non-Windows OS. The first few choices are fine - then it comes to the partitioning part. I select manual as I want to create a /home partition as well as root and swap. The progress bar goes through the examine partitions bit and I am then put on to the next screen with no partitions listed, everything grayed out and no explanation.

I seem to remember someone having a similar problem in this forum when I was looking through it at the sort of problems I might face, but I can't find the relevant post [perhaps my search parameters aren't right].

Anyway, is there anyone who can help a beginner to get off the blocks? Or do I step back to an earlier distro like Edgy?:confused:

You are trying to repartition a hdd that has XP (NTFS)?  Correct?

If so then you are probably getting errors and gparted is telling you it cannot perform the operation.

You need to defrag your XP install (all drives) and run chkdsk /f on all drives.  Running chkdsk /f on the C: drive will run it next boot.

Once that is done you should be able to create partitions off the ntfs drive.

---

### Post by ken_38 on 2007-05-25
Thanks stchman - sorry to take so long to get back to you.

That's the first ray of light I've had. Didn't run chdsk /f though I did defrag my two partitions a couple of times.  I suppose I'll have to do that some more and then run chdsk.

I'll let you know how I get on, though it may be a little while. Off on holiday!:D

---

