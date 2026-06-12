---
title: "Installation- Ubuntu 7.10"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by blastizard on 2007-11-26
Hello All,

I have been using 95/XP since i can remember using a computer.  I want to try something new and thought i'd pick up a copy of Ubuntu.  My copy is in the mail and will be arriving today or tomorrow.  First I want to list my specs of the computer its getting installed on.


Intel® Core™ 2 Q6600 Quad-Core (8MB L2 cache,2.4GHz,1066FSB) 
2GB Dual Channel DDR2 SDRAM at 667MHz- 2DIMMs
128MB nVidia GeForce 8300 GS 
80GB Serial ATA Hard Drive (7200RPM) w/DataBurst Cache™ 
Genuine Windows® XP Home Edition 

It's nothing special, i have another computer in which I want to also install Ubuntu on assuming it works accordingly and i will also list those specs later.  Now i use this computer for basic needs... checking e-mail, chatting with friends, playing some games, ect.  My upmost challenge is I need World of Warcraft to run and run smoothly.  But i also still want all that eye candy i've been reading about- cube, 3d, effects, customization.  If possibly, i wouldnt mind being able to dual boot Windows (which is allready installed) and Ubuntu.  My question is this,  Will my computer specs be able to give me the dependability i want for average computer (i am a die hard WoW player, i cant go one day without it) use if i opt not to dual boot.

Alot in 1 thread but user imput would be great.

Thanks in advance and feel free to link me to helpful guides.:)

---

### Post by dabl on 2007-11-26
Nice rig!  :)

Here's the view from 100,000 feet:

1. Make yourself a GParted Live CD, from the ISO here: [http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

2. In XP, run "disk cleanup", and then run "disk defragmenter" about 4 times, then shut it down and boot your GParted Live CD.

3. Using GParted, shrink the Win XP partition down to whatever you think it needs -- 20 or 30 GB maybe.

4. For *buntu, make 3 more primary partitions in the "unallocated space" that you freed up:

0.5GB -- the future "Linux swap"
6GB - -the future "/"
the rest of it -- the future "/home"

5. Using your *buntu CD, follow the instructions on the CD to do a "manual installation" and mount the filesystem as indicated above on the partitions you made.
 
6. Expect video issues.  This might help: [http://kubuntuforums.net/forums/index.php?topic=3085112.0](http://kubuntuforums.net/forums/index.php?topic=3085112.0)

7. Plan to install it 3 or 4 times -- call the first ones "practice".

:lolflag:

---

