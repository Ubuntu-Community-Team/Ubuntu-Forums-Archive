---
title: "HELP! Install ubuntu(linux)"
date: 2009-12-18
forum: Installation &amp; Upgrades
---

### Post by brainiacary on 2009-12-18
This is my first time with Linux/ubuntu :( I had never installed it on any PCs b4.so plz help me to solve my problem :) and make me at least a good linux user :D. 
I had run live several times and i had dared to try to install it few  times but i never installed it(cancelled after steps 5 out of 7 :lolflag:.) I'm very frightened that i might lose my data and my windows xp.
[SIZE=2]**1. I have 4 primary partitions on my 80gb HD**[/SIZE](Sata):
[SIZE=2][B]windows show them like this:
C = primary partition = 30 gb
D = [/B][/SIZE][SIZE=2][B]primary partition = 9.5 gb
E = [/B][/SIZE][SIZE=2][B]primary partition = 17 gb
F = [/B][/SIZE][SIZE=2][B]primary partition = 18 gb

2. I have WindowsXPSP3 installed on my C (i.e. 30 gb partition).

3. I dont want to mess up the C drive(windows xp) nor E and F. The only drive I want to use is D drive(i.e 9.5 gb).So i am ready to format D drive ( 9.5gb primary partition).

4.  So help me,[/B]**geniuses of ubuntu linux :wink:, to successfully install ubuntu 9.10 on my PC on the so called D drive(9.5 GB second Primary partition) by formating it(maybe with ntfs if possible) and keeping everything intact**[/SIZE][SIZE=2][B] other than this partition :guitar:.
Im Waiting eagerly for Ur helpful replies and suggestions :-D
Thanks in advance :popcorn:


[SIZE=3]ps : I have 512 mb Ram [/SIZE]

 [/B][/SIZE]

---

### Post by darkod on 2009-12-18
OK.
First: back up any important data. You never know what can go wrong, just in case.
Second: From XP delete the D: partition (if that's where you want ubuntu installed).
Third: Boot with ubuntu cd, select Install Ubuntu option, and in step 4 tell it to Use Largest Continuous Free space. That would mean the 9.5GB unallocated space you created by deleting D:.
It should work out fine. Although 9.5GB is slightly tight for ubuntu, but if that's all you have to use it will have to do for start.

---

### Post by brainiacary on 2009-12-18
Thank u very much for instant reply, I'll do everything u said and reply later :D

---

### Post by darkod on 2009-12-18
> **brainiacary said:**
> Thank u very much for instant reply, I'll do everything u said and reply later :D
BTW did u mean to delete d drive or format it

Delete. From windows you can only format it as ntfs and linux doesn't run on ntfs. You would have to delete it during install anyway. It's best to delete it now, that will create unallocated, unpartitioned free space that linux can use, then just select the guided install and it should be fine.

---

### Post by brainiacary on 2009-12-18
Here I go sir,I'll give it a try,thanks indeed. Seems this is a very good forum,i think i'll like it ;)

---

### Post by brainiacary on 2009-12-18
**:cry: Brother I messed everything up,I had forgot to mention that i had installed vista on d drive after windows xp.I did everything u have told i.e deleted the d partition,Now the problem is much more serious, computer bios hangs during booting it shows the intel logo and stops there. I can get to bios setup only if i detache sata hard disk.plz help me i dont want to lose anything :( I am accessing this forum with the same computer by detaching sata disk and running live puppy linux :(**

---

### Post by brainiacary on 2009-12-18
its really frustrating,plz help me , should i plug the cable of sata hd after bios boot up and run windows xp cd ?

---

### Post by mybodymyself on 2009-12-18
[FONT=Trebuchet MS]Found the live disc images with from their site didn't work at all.  Even after downloading and installing it.  Gave up on that and requested a free live disc from them and which they granted.  Got it, yesterday.  Its working much better now.  At the same time have mention everything that I mention here in the threads that I started on here.
[/FONT]

---

