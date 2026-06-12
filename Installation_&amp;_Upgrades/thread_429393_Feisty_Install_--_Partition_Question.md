---
title: "Feisty Install -- Partition Question"
date: 2007-05-01
forum: Installation &amp; Upgrades
---

### Post by melat0nin on 2007-05-01
Hi all

After a long run of work I've got some time off and my plan is to install Feisty and really start making use of linux properly.

Got some queries about partitioning, though.  Please bear with me cos I'm not too confident with partitioning.  Here is a screenshot of GParted with my current setup:

[IMG]http://img133.imageshack.us/img133/6087/gpartedib9.png[/IMG]

/dev/hda1 is my Windows installation, and /dev/hda5 is my documents partition.  I don't want either of these partitions to be touched in any way, for the moment.

The two 'unallocated' partitions are previous Edgy partitions - the 627mb one was swap and the other one was the Ubuntu install.  I deleted these in GParted to start fresh.

Now I'm wanting to create partitions using the Manual partitioning tool in the Feisty install.  I'd like a swap of, say, 1gig (I've got 1 gig of system RAM) and the rest of the remaining free space (~14 gigs) for the Ubuntu installation.  Trouble is, when creating the partitions, I'm not sure whether to make them primary or logical, and which option to select for 'Beginning' and 'End'.

Can anyone tell me what the best idea is?  I always thought it was a bit weird having the swap in the same logical (primary? extended? - confusing!) partition as my documents, and the actual Ubuntu installation seemingly in its own partition -- you can see how it was setup from the screenshot I posted above.  For cleanliness' sake I'd like the swap and Ubuntu installation partitions to be together, but on the other hand if that has no practical advantage then I'll do whatever is better.

Any help would be much appreciated and thanks in advance!!

-m

---

### Post by melat0nin on 2007-05-01
Anybody?  I'm really anxious to get started!

---

### Post by Topsiho on 2007-05-01
OK, here my two pennies for what it's worth :)

First thing is to extend the size of hda2 to occupy all the disk until the end, using all the unallocated space. If that's possible, I am not a professional.

Then you use the unallocated space that is left, which is about 13.52 GiB:

You make at least three *logical* partitions within the extended partition, which will probably be numbered hda6, 7 and 8:

1. you need a / partition, about 5 to 10 GiB, I would go for 8.
2. You need a swap, 1 or 2 GiB. Twice your RAM, but you have not so much space, and with one GiB RAM your swap is not used much.
3. The rest is for your /home partition, in which come the files of the users, and their configurations and so on. When installing another Ubuntu in the future you can leave this partition untouched and keep all your stuff: you do NOT format it then.

You will see that there is not much space left for your /home partition, so you should probably be somewhat more conservative than me, depending on what you really need for your personal stuff.

When installing Ubuntu you should be very careful that partitions hda1 and hda5 are NOT formatted. Please look twice and then yet another time before you go on and format the new partitions, and get on with the install. Better still: be sure you back up those data that you really don't want to loose.

Topsiho

---

### Post by DJMatty on 2007-05-01
Yeah, as I understand it, each physical disk can have up to 4 primary partitions, one of which (correct me if i'm wrong here) can be an extended partition.

The extended partition can then contain many logical partitions.

I ended up using primary partitions for my xp and vista installs, and another primary for a fat32 shared drive between ubuntu and the other o/s's, then the rest i made into an extended partition with the following logical partitions:

75MB boot
3gb swap
10gb (or the rest) for / (including /home, as everything that I want to keep hold of is elsewhere on my network)

HTH

Matt

---

