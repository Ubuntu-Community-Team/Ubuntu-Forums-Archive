---
title: "Blank screen with cursor after grub"
date: 2014-06-29
forum: Installation &amp; Upgrades
---

### Post by jonathan-l-harrison on 2014-06-29
Having spent an age building my new PC and finally getting it working, suddenly after a reboot I get the blank screen after the GRUB menu.  I have tried to use GRUB rescue which normally resolves verything but to no availe.  All software and OS are up top date with latest versions.  Any helpers, please?

---

### Post by kc1di on 2014-06-29
A little more information about your system would be helpful. 
What video Card are you using?  What Driver?  Can you load recovery mode?
if so go to root terminal and type the following. one at a time and list the outputs here that would be start. 

```
 lspci 
lsmod 
```

---

### Post by jonathan-l-harrison on 2014-06-29
Sorry Kc1di
Until I had someone who can help I put down what I have.
[QUOTE=kc1di;13061177]A little more information about your system would be helpful. 
What video Card are you using?  What Driver?  Can you load recovery mode?
if so go to root terminal and type the following. one at a time and list the outputs here that would be start. 

I am using Ubuntu 14:04 and switch between lubuntu, xcfe, etc...  Processor is Intel i7 and 4 x 8Gb Kingston RAM. The graphics card is an old one, for now, do not recall the model, but it is nVidea.  And there is a SkyDVB card.

No can not load recovery.

Tried going in to GRUB menu and putting in nomodeset, acpi=off, but they do not work either.

I was using not using the nvidea drivers as they would not work so I was using the x-org (I think that is what it is called)

---

### Post by Bashing-om on 2014-06-29
jonathan-l-harrison; Hello ,

It might prove interesting to see what results when you boot (L)ubuntu to a text terminal from the grub boot menu. See what the terminal relates when a GUI is started . Start the trouble shooting from that perspective ?

[INDENT][INDENT]When in doubt
[INDENT][INDENT][INDENT]terminal time
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by jonathan-l-harrison on 2014-06-29
It's gone from bad to worse.  I tried GRUB repaire and that failed to make it work, so I used the GRUB purge in GrUB repaire, and now I can't get anything to work.  I have loaded the CDR with the image on.  It loads to the screen where I can choose a Distro (it has multi versions on it) It then fails part way through....  I have then tried deleting the install partition deciding to start from scratch and still nothing.  memt est is OK, and I have put in a Graphics card from another machine....

I am stumpped.

---

### Post by Bashing-om on 2014-06-29
jonathan-l-harrison; Hey !

 Panic not. Just proceed in a calm and orderly fashion. 
So presently what we require is a means to boot from, to look things over. Find out what it will take to boot a liveDVD of 'buntu.

What are you using now - to post back to the forum ?

Find out what we have to work from and with and take it from there.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by jonathan-l-harrison on 2014-06-29
Hiya Bashing-om
Could have done with you 2 hrs ago.  I have just made things vastly worse.  Can't believe I have spent 2 months getting this PC to where I wanted it and have now deleted the image and still can't boot.  I have a Ausu Rampage IV and it had warning lights, I noticed against the Graphocs card, so I tried the other one and that too was showing faulty, but if they are faulty how comes it did work at first and it did show the initial load from the DVD...????????

OK, so gettim calm and rational again how do i proceed?

---

### Post by kc1di on 2014-06-29
Hi Jonathan-l-harrison,
I would try your ubuntu dvd again.  this time hit the tab key as it just starts to boot.  select f6 and then selct acpi=off and nomodeset. 
see if the live disk will boot that way.

---

### Post by Bashing-om on 2014-06-29
jonathan-l-harrison: Hey ,

+1 to kc1di's methology //
see what results .. or maybe just boot to a terminal and see what the graphics situation is like.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by jonathan-l-harrison on 2014-06-29
It won't boot properly at all now.

I get
```
error: no such partition.
Entering rescue mode...
grub rescue>
```

---

### Post by Bashing-om on 2014-06-29
> **jonathan-l-harrison said:**
> It won't boot properly at all now.

I get
```
error: no such partition.
Entering rescue mode...
grub rescue>
```

That on the install or trying to boot the liveDVD ?

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by jonathan-l-harrison on 2014-06-29
Live CD won't work at all.. Managed to get the GRUB Recovery CD to work - yipee... God knows how many attempts.  F6 to acpi=off and it boots in to the recovery.  Taking a look at Gparted and the Hard disk is broken...  I.e. it is a 1Tb disk and shows only 500Mg and that is "unallocated" and un-usable.

I suspect it is faulty and I will need toi buy another one.  Whatever, I will need to start from scratch.

I shall look in to a new (hopefully under guarantee) HD and get back, unless you guys have anything else to add.

PS:  The HD looked fine when all this started.  So not convinced it was the cause.

---

### Post by Bashing-om on 2014-06-29
jonathan-l-harrison; Welp. Not Good.

As you suggest there may be hardware failure. Boot up the ubuntu liveDVD -> disk utility and run the full SMART test on the drive overnight, as 1TB may take a while.

If it is under warranty, well if it tests bad, yeah replace it. 
Else, if it shows bad and you want to try and salvage it .. we can sic 'dd' on it and see if it is then usable.

[INDENT][INDENT]gotta have the hardware
[/INDENT][/INDENT]

---

### Post by kc1di on 2014-06-30
Did you try the DVD?

---

### Post by Jonners59 on 2014-07-06
Ended up stripping down the machine and rebuilding and then removing the BIOS battery and went back to absolute basics....  Rebuilt and bar an issue with the SKYDBV (another thread) card all is sorted.

---

### Post by Bashing-om on 2014-07-06
Jonners59; aka jonathan-l-harrison (??);; Hey ,

Glad ya got it sorted out, and all is good in the end. I bet you endured a "learning experience" .

Please mark this thread solved; aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.

It is all a process
[INDENT][INDENT]and that process starts in bios
[/INDENT][/INDENT]

---

### Post by Jonners59 on 2014-07-06
> **Bashing-om said:**
> Jonners59; aka jonathan-l-harrison (??);; 

Long story :) all sorted now.

> **Bashing-om said:**
> Hey ,

Glad ya got it sorted out, and all is good in the end. I bet you endured a "learning experience" .

Please mark this thread solved; aides others seeking the solution,
helps keep the forum clean and
precludes others miss-directing efforts to aid.

It is all a process[INDENT][INDENT]and that process starts in bios
[/INDENT]
[/INDENT]


I always do Bashing-om...  though I can't find the "SOLVED" tab anymore!!!!!  Where is it now???  Used to be in the tools

PS  couldn't help me with anotherr thread.  Not the subject matter, it is more about understanding the linux commands.  I have instructions but one line I do not understand how to interpret.  [http://ubuntuforums.org/showthread.php?t=2233138](http://ubuntuforums.org/showthread.php?t=2233138)

---

### Post by Bashing-om on 2014-07-06
Jonners59; Sure !

Solved -> top of the posting right side -> thread tools.

Will look at the other thread, see how much I do not know, and what we can finger out.

open source
[INDENT][INDENT]all of 1 and one for all
[/INDENT][/INDENT]

---

### Post by Jonners59 on 2014-07-06
Cheers Basin-om
I don't have it listed.  Probably due to the naming issue now sorted.  Have asked that the thread be deleted as it did not fix the problem..  thanks for taking a look at the other thread

---

### Post by Bashing-om on 2014-07-06
Jonners59; Hey,

Only you - or having to bother a forum moderator - can mark your own post as solved .. 
As you scroll this thread up to the top- in normal viewing mode, not editing it, look to the right side for 3 tools, the middle one is "thread tools" click on it and choose "solved".

[INDENT][INDENT]simple as falling out of bed
[INDENT][INDENT][INDENT]wide awake, once you know how
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Iowan on 2014-07-06
> **Jonners59 said:**
>  though I can't find the "SOLVED" tab anymore!!!!!  
Probably more help than you need, but...
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Jonners59 on 2014-07-07
[SIZE=2][FONT=arial][/FONT][/SIZE]I think I know how to mark a thread as solved. But as this was created under a different profile I do not have the option.  It has to be marked solved, deleted or some other behind the scenes action by a moderator or just left, as I do not have a "SOLVED" option for this thread.

---

