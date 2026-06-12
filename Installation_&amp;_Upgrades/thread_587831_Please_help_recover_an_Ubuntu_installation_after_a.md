---
title: "Please help recover an Ubuntu installation after an upgrade attempt"
date: 2007-10-23
forum: Installation &amp; Upgrades
---

### Post by alexsokol on 2007-10-23
**How it happened**

I was upgrading my Ubuntu system from 7.04 to 7.10 online. In the middle of this process it just crashed and turned off all of a sudden. (Though online upgrade using update-manager is the recommended upgrade method!)


**What I have now**

Now the system is loaded up to the point where a blue screen with a mouse pointer appears. A complete desktop should be next, but it doesn't appear.


**What I tried to do**

***A) In the recovery mode (console)***

1) apt-get install..., apt-get update etc.

Error: dpkg was interrupted, you must run 'dpkg --configure -a'

When I run 'dpkg --configure -a' it shows a lot of dependency problems, tries to solve them, but is finally aborted:

Error: too many errors, stopping

2) 'do-release-upgrade'

Error: unable to get exclusive lock, some other package management program must be running. (???)
[B][I]
B) Using the alternate CD 7.10[/I][/B]

1) Tried to upgrade from the CD with 'sh /cdrom/cdromupgrade'

Error 32: gutsy not found

2) Chose the item 'Rescue a broken system' on the CD menu. There appeared a kind of console - and what now? Any utilities or commands to recover a broken system?


That's it. What can I do in this situation? I would be very grateful if some of more experienced guys out there gave me some advice.

---

### Post by ninjad on 2007-10-23
i'm in the same boat as you, any help would be great for me too.

---

### Post by Biswajit Bhuyan on 2007-10-23
Similar situation.
What I've done now is reinstalled Fiesty preserving my /home.
Back to good ol' things I'd grown comfortable with.

Will wait for a while before I try the dist-upgrade again!!

---

### Post by toecutter on 2007-10-23
> **Biswajit Bhuyan said:**
> Similar situation.
What I've done now is reinstalled Fiesty preserving my /home.
Back to good ol' things I'd grown comfortable with.

Will wait for a while before I try the dist-upgrade again!!

I think I might have to do this - I had a very similar problem:
[LIST]
[*] 2 different Live CDs with correct MD5 sums won't load properly and hang at loading install scripts
[*]when using Update Manager everything seemed to load okay (although the process couldn't restart xscreensaver & gnomescreensaver) but reboot hung up again at loading install scripts
[*]when loading into safe mode none of my partitions could be found[/LIST]

---

### Post by captaink on 2007-10-23
Hmm, I think the best and easiest solution is to start from scratch. 
Use the alternate cd to start a new installation. I suppose you have your data backed-up or placed to your home directory, which /home is on a different partition. If not, use **Puppy Linux** to back to copy your data to an external drive, like flash drive or CD/DVD, or an external hard disk.
If on a separate partition, choose to partition manually, and format ONLY the / that references to all the rest of the system. 
I repeat, ONLY "/" IF YOU HAVE "/home" TO A DIFFERENT PARTITION! IF ON THE SAME PARTITION, BACK UP FIRST using Puppy Linux.

Now, about saving the upgrade, I can't think of a best solution, except of going on recovery mode and use 

*sudo apt-get dist-upgrade.*

Please, refer to the apt-get manual or to an other forum on how to use this function.

Hope I've helped a bit both of you!

---

### Post by toecutter on 2007-10-23
Can I ask why using the alternate CD is the way to go for some people? Why not use the regular live CD?

edit: forget it, I found the answer - it's cuz the alternate install CD is for computers that aren't online so I'm guessing it includes all dependencies and files that could be needed

---

### Post by ninjad on 2007-10-23
How do we know if our "/home" is on another partition as "/"? I remember making partitions for the original install but i cant remember if home is different from /.

---

### Post by captaink on 2007-10-24
> **toecutter said:**
> Can I ask why using the alternate CD is the way to go for some people? Why not use the regular live CD?

edit: forget it, I found the answer - it's cuz the alternate install CD is for computers that aren't online so I'm guessing it includes all dependencies and files that could be needed

Sort of, but it's not only that!
Let's have an example. My old computer, an Athlon XP 2400+ with 1024MB RAM DDR and nVidia Graphics card. The first time I tried to load ubuntu live, ended with a black screen and the monitor trying to send a singal on display. Just that. 
The problem was that for some reason, the OSS driver "nv" wasn't compatible with my nVidia Graphics, when dual-booting!!! With a clean hard drive or a linux distro only, no problem.
So, how do you install ubuntu there?? That's where the alternate cd goes. I installed ubuntu, then from console I installed the nvidia driver, either from nvidia site, or from ubuntu repos using apt-get.

Furthermore, when reinstalling ubuntu, it's useful because you go straight to install, rather than loading the live OS first, thus you can save time!
And you can use the alternate cd for offline upgrade, as you mentioned.

Useful solution, don't you think?

---

### Post by captaink on 2007-10-24
> **ninjad said:**
> How do we know if our "/home" is on another partition as "/"? I remember making partitions for the original install but i cant remember if home is different from /.

You can install gparted from synaptic or using apt-get to see your partition table. There you 'll see if /home is on a separate partition.

I think if you type "mount" on a terminal, or opening /etc/fstab using gedit, you can see also if /home is mounted elsewhere. If you see a line with an ID refering to a /dev/<partition> and mount point /home, as well as another ID refering to /dev/<another_partition> with mount point /, then this might be your case.

REMEMBER: Whether your case is, back up your valuable data, just in case...

---

### Post by The Chef on 2007-10-26
In case this helps:  I traced the same symptoms to a flash memory card reader that was attached by USB.  With this device attached, even the live CD would not load.  Without it attached, everything's fine - upgrade manager installed Gutsy.

See [http://ubuntuforums.org/showthread.php?t=591135](http://ubuntuforums.org/showthread.php?t=591135) for details of a repair I had to make due to the first install crashing.

---

