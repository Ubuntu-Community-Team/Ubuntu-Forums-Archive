---
title: "Apt-get Broken!!??"
date: 2007-08-31
forum: Installation &amp; Upgrades
---

### Post by Talako on 2007-08-31
For a few days, I have been having trouble updating, it stopped almost immediately, and gave me an error about /var/lib/available. I wasn't too worried, and was going to take care of it tonight, but when it forced an fcsk (?sp), it came back with an error saying that apt-get wasn't installed, wtf? I know it is installed, and I haven't messed with any files or anything, before when I tried to fix /var/lib/available, it opened in gedit, and nothing was there, it said "loading" for about 5 mins before I just closed gedit, has anyone ever had a problem like this, I don't have a printout of the code, what is the command to print the code from the past command? The fsck returns that it can't boot because apt-get isn't installed, so it gives me a root terminal and tells me to fix it then ctrl-d reboot. I am in my dual-boot windows partition now, so I have a backup, but I **REALLY** don't want to have to reinstall, but i can if absolutely necessary. I know just enough to get by in the terminal. Thanks you guys.

---

### Post by PaulFr on 2007-08-31
1. **fsck** only checks file systems for consistency - I doubt that has anything to do with apt-get. Perhaps your file system has become corrupt. If typing ```
**fsck**
```at the root prompt does not work, please post the exact message. Of course, fsck may prompt you to fix things, and usually you can accept its changes.

2. I cannot find a /var/lib/available file or directory. There is however a **/var/lib/dpkg/available** file that contains a list of all available packages. On my machine, /var/lib/dpkg/available is about 1974 KB (47000 lines). This can be updated using ```
dpkg --update-avail
``` or ```
dselect update
```. 

However, you need to fix your fsck problem first, then reboot, then come back to fixing apt-get.

N.B. To see recent operating system messages, you can use the command ```
dmesg
```Older messages can usually be found in the files in **/var/log**( look for all filenames starting with **messages**).

---

### Post by Talako on 2007-09-10
Sorry I haven't responded in a while, I did boot again, if I had read more carefully I just had to run fsck on unmounted volumes, so I got back in. Then I had to do a dpkg --clear-avail to finally get things back to normal, the original error was something about a parse error, and not having a colon after some things in /var/lib/dpkg/available.
Thanks for your help!
Talako

---

