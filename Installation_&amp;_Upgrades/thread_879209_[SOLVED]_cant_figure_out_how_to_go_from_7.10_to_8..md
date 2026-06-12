---
title: "[SOLVED] cant figure out how to go from 7.10 to 8.04"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by luckymoonboy1 on 2008-08-03
i am having a problem upgrading from 7.10 to 8.04. i do not want to  do a fresh install so i am trying to upgrade from the CD that i got in the mail. i put the disk in and it asks if i want to manage the the packages from the package manager, i say yes and try to install the packages but nothing will.  i think i am doing this wrong i don't really understand the upgrade instructions. also this is not 8.04.1 it is just plain 8.04, and the computer i am trying to upgrade doesn't have internet. i would greatly appreciate the help.:confused:

---

### Post by kahlil88 on 2008-08-03
Unfortunately, the CD that comes in the mail doesn't do upgrades - you need to download what is called an "alternate" CD. I discovered this the hard way, but because I'm clever I found a way around it:
[LIST=1]
[*]From the install disc, rename the **/home** directory to something odd, perhaps "ziggy" (sudo mv /home /ziggy)
[*]Perform a regular install WITHOUT FORMATTING - this will overwrite all the system folders, but not "ziggy", because it has an unusual name
[*]Once the install is finished, move your old home folder in /ziggy to /home
[/LIST]
This will result in a fresh install of 8.04, without any of the programs that you installed when you were running 7.10, but if you have a high-speed connection (unlike me) you might not care so much.

---

### Post by luckymoonboy1 on 2008-08-03
ahh, ok, is there a way for me to keep my installed programs?

---

### Post by kahlil88 on 2008-08-03
Using my tricky method involves a clean install, so if you want to keep your programs, you'll have to use the 8.04 alternate CD. You could also backup the packages in your **/var/cache/apt/archives** directory and then re-install them later (you'll probably run into a few dependency conflicts though).

---

### Post by luckymoonboy1 on 2008-08-03
i think I'll just download the alt CD it'll make upgrading my other computers much easier. thanks for the help, i had no idea what i was doing. :KS

---

