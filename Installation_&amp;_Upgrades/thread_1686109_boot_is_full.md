---
title: "/boot is full"
date: 2011-02-11
forum: Installation &amp; Upgrades
---

### Post by Gildarrious on 2011-02-11
Hello all, I have been running ubuntu for around 3 years, picked up some commands here and there, just using it as a side project server/desktop editions. I seem to have trouble updating Ubuntu 1.04 LTS '2.6.32-25' at all, I keep getting the error that /boot is full. When I installed this system I gave it 100MB as it was only used for kernals which are very small files. I have removed the old kernals that I am no longer using apt-get remove... and seem to have freed 0mb of space even upon removing all but the one I am currently using. df-h gives me this: 
/dev/sda1              92M   79M  7.8M  92% /boot

however while looking in the file structure itself of /boot I get this: 

194 items, totalling 17.8 MB
(some contents unreadable)

Would those "unreadable" contents add up to that many MB of space?
If so how can I remove these contents that I can neither see or access as Superuser.

---

### Post by oldfred on 2011-02-12
Did you empty trash? 

Since it is a separate partition does it have its own (hidden) trash folder?

---

### Post by Gildarrious on 2011-02-12
I believe I have, temp is empty within the directory, and I have run various "cleaners". Is there a specific command that would let me see those hidden files if they are trash?

---

### Post by oldfred on 2011-02-12
I have this in my notes for root. I do not know if then a separate /boot has it in root or boot?

/root/.local/share/Trash System Trash (hardy and later)

---

### Post by Gresley on 2011-03-15
I have the exact same problem, but got into the mess in a slightly different way. Having realised /boot was full I used a live cd to boot the machine, mounted /boot and used sudo nautilus to browse and delete the unwanted kernel files. Though I know I've deleted 75mb of unused files out of a 100mb partition it still shows up as 100% full. 

Upgrade manager now refuses to work, telling me I must free up space on /boot. I'm totally stuck, having tried everything I can see on the forum to no avail to free up the space.

any help gratefully received.

---

### Post by Gresley on 2011-03-18
OK, solved it now. I looked at hidden files in /boot, and although the trash folder claimed to be empty I deleted it. This magically freed up 65mb of space. 

To really sort this issue why cant the upgrader get rid of old copies of the Kernel from boot? when this problem struck I had 4 different kernels in /boot. I cant for the life of me think why I'd ever want more than 2. The current one and the possibility to boot from the previous one in case of issues.

An OS that needs this kind of tweaking if /boot is in its own partition (and I have very good reason for putting it there, its the only way I can force the bios on my laptop to boot from my external drive) will never have any hope of being mainstream.

---

