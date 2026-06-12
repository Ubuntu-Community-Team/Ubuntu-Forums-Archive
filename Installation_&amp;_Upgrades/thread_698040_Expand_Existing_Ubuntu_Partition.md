---
title: "Expand Existing Ubuntu Partition"
date: 2008-02-15
forum: Installation &amp; Upgrades
---

### Post by Mark Bowers on 2008-02-15
Several days ago I installed ubuntu Gutsy (dual boot with Win XP), and did not give it a very large partition as I frankly expected problems. It's installed on an IBM T60p with ATI graphics and I thought I'd run into all kinds of problems - video, etc. HOWEVER, much to my surprise it's all working extremely well.

I'd like to give Ubuntu more of the HDD, and shrink the Windows XP partition. I can do this by reinstalling Ubuntu, but after all the work to get me to this point I'm wondering if there is an easy way to expand the Ubuntu partition, shrink the WinXP partition, and to keep both XinXP and Ubuntu working as is?

Thanks in advance for any help.

Mark B.

---

### Post by Partyboi2 on 2008-02-15
You can use the ubuntu live cd to resize your current partitions. Boot up the live cd and look under System>Admin for Partition Editor. Once that is open you will see a option to resize your partitions.

---

### Post by Mark Bowers on 2008-02-16
Partyboi2-

Thanks for the response! I'll try it sometime over the weekend and let everyone know how it worked.

I'm also thinking of developing a fairly detailed 'how to' for installing Gutsy on the IBM T60p with ATI graphics. I've been playing with this for about a year, mainly playing with suggestions from many different sources, and have found that it makes a big difference in the sequence of how the changes are made. At any rate, I have EVERYTHIING working including the 'eye candy'; however, I've had to use XGL/Compiz rather than Compiz Fusion.

Thanks again.

M. Bowers

---

### Post by torgrot on 2008-02-16
Please be sure to back your system up first.  Playing with partitions has been known to cause problems.  Don't particularly need to here a plaintive cry for help "Ubuntu has deleleted my Windows installation.

torgrot

---

### Post by SloYerRoll on 2008-03-04
I figure I'll post in here to help keep the insane amount of new threads down and I have the same exact question. Sorry if I tell you more than you need to know. I'd rather you read it then have to ask for it and wait.. 

I have tried to boot from both the live CD and a gparted boot CD I created. Gparted will let me shrink the volume, but not expand it. 

When I go into gparted. It shows all the drives and partitions (most of them are crap from the factory install), but doesn't let me expand the Ubuntu partition anymore. *The problem is I only set up a 10GB partition for Ubuntu, not realizing that I'd need ot install XP under VMware..

So what I ultimately want to do is remove all remnants of Microsoft and run 100% Ubuntu. But I need to figure out how to run VMware w/ my Adobe applications and set up dual monitors before I do this. 

I have two internal drives. One is for my data, the other for the OS's. 
The OS drive has 4 partitions. But one of them is just unallocated space. I can't do anything w/ that either. I'd love to just "merge" it w/ the Ubuntu volume if possible. 
So it has: 1. A main volume. 2. a factory install data backup (crap). 3. Ubuntu volume 4. unallocated space.
the second internal is just one big volume w/ tons of folders. 

Both Internals are 250GB. 

Screen grab below if it helps any..


[IMG]http://jbritt.smugmug.com/photos/261984011_eDs2t-XL.png[/IMG]

---

### Post by Partyboi2 on 2008-03-04
Before you can do any work on a partition it needs to be unmounted. When you have started up gparted on the live cd, highlight the partition you want to work on and right click and choose to unmount the partition. I would suggest changing your swap partition to just 1 (roughly about x2 the amount of your ram you are using)

---

### Post by SloYerRoll on 2008-03-04
First part makes perfect sense. Amazing how simple things can be when you step back (or are handed the answe:)r)

Could you please elaborate on the following? I have 4GB of RAM if it matters. 
> **Partyboi2 said:**
>  I would suggest changing your swap partition to just 1 (roughly about x2 the amount of your ram you are using)

Will doing this allow me to increase the Ubuntu OS partition? I want to paly around w/ it, but pigeon holed myself w/ not enough space.. Still breaking free of old Windows habits..

---

### Post by SloYerRoll on 2008-03-05
Not being impatient (this isn't critical, yet). But I did want to say what happened after I went into gparted and took your advise Pboi. 

I booted from the Gparted CD I created, and there were no options to unmount any of the volumes. I went in and tried reducing the size of my main partition (the one w/ Vista on it) and it shrunk the volume. Easy Peasy. But I still can't increase the size of my Ubuntu partition. I'd like to increase this partition by roughly 75GB so I can really put this OS to the test and make sure this is right for me. 

-Jon

---

### Post by cabbey on 2008-03-07
Jon, your ubuntu partitions are inside the extended partition (sda4), they won't be able to grow any larger than it is. Assuming you shrank sda3, you'll need to first grow the extended partition that contains your actual ubuntu partitions. I'm pretty sure gparted will let you do that, though I've not tried to resize an extended partition container.

As for the swap partitions, you currently have two seperate swap partitions, sda5 and sda7... you would be slightly better off with just one.


I would suggest the following order of operations in gparted:


[LIST=1]
[*]grow sda4 down into the space freed up from sda3
[*]delete sda5 (redundant swap partition)
[*]move sda6 (ubuntu root file system) down to the start of sda4
[*]grow sda7 (swap partition) to the size of the total swap you want (2x ram, or 8G would follow the "normal recommendation".)
[*]grow sda6 (ubuntu root file system) to fill remainder of sda4
[/LIST]

I believe you can queue all of those steps up in one sequence.... but if gparted complains, or if the results after each step "just don't look right", try doing them one step at a time.

Then get back to shooting, we've got to give Vandana a run for her money this year!! :)


ETA: this was supposed to be a reply to comment 8, but apparently I hit the wrong 'reply' button.

---

### Post by SloYerRoll on 2008-03-07
Thanks much for the reply cabbey!

I'm moving the Ubuntu OS onto a new drive and am killing this since I found out what you confirmed. That I can't expand the drive. 

I am going to do this for practice though. Since I think it's good to have a stong understanding of gparted in case I ever need it in a more critical situation. 

I'm actually going to shoot in LPS this time. I kind of got turned off by the cliques going on in there. But I'm mingling forums now.. Whoops:):lolflag:

---

