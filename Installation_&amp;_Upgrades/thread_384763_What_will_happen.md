---
title: "What will happen?"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by jas98235 on 2007-03-14
Hi everyone!  a couple months ago i orderd some ubuntu cds and i want to install it on my pc as a second os just so i can get the hang of it because i plan on getting a mac down the road!!! anyways i have 2 160gb ide hard drives in my pc i run windows x off of one and i want to install ubuntu off of the other, the 2nd one (the one i want to install ubuntu on) also has windows xp installd on it(i use to use it in my last pc) heres where i need help, when i go to install ubuntu i get options to eather overwrite(i for get what) or Partition and on one other option  for get what it was, i tryed the Partition option but i didnt know what i was doing and didnt want to ruin my hard drive! so my question is if i hit the overwrite option(or what ever it is)will it erace all the data on the hard drive (like reformat it?) and will i still be able to acess it from windows? because i have ALOT of stuff on it that i use in windows!! and i dont wanna lose it! thanks in advance to anyone who helps me!

---

### Post by Kateikyoushi on 2007-03-14
Free up at least 10GB on that disc so you can try out some programs after ubuntu is installed, also backup important data, while not often but things can go wrong with partitioning.
Run a checkdisk and defragment that drive a few times from windows.

Then start the installer and resize the windows partition to make free space for ubuntu. Make 2 partitions one for swap 1GB and a bigger one for the system with ext3 filesystem. Set mount points for them / for the big partition and swap for the small.
I recommend to read this dualboot installation guide. [LINK]("http://www.psychocats.net/ubuntu/installing")

---

