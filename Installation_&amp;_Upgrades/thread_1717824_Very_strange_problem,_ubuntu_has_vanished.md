---
title: "Very strange problem, ubuntu has vanished"
date: 2011-03-30
forum: Installation &amp; Upgrades
---

### Post by bobeyuno on 2011-03-30
I got Ubuntu 10.10 about a week ago my first time using and am dual booting it with vista. Today i restarted the system and got an error that Kernal could not be found. In other fourms i saw i could update it by rebooting it from USB/Disk. I started all that but before hand went to look for the ubuntu files and they have gone and their is only windows vista on the boot menu.
My main concern is it safe to reinstall ubuntu from scratch in this situation?

---

### Post by Rubi1200 on 2011-03-30
Hi and welcome to the forums :-)

I suggest the following so we can see the current state of your setup:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by bobeyuno on 2011-03-30
I reinstalled using wubi as it didn't go onto my USB properly and got corrupted along the lines.
It's all working correctlly but lost all my settings and applications. 
The command that you gave me did not run correctlly
```
jack@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
[sudo] password for jack: 
bash: /home/jack/Desktop/boot_info_script*.sh: No such file or directory
jack@ubuntu:~$ 

```
but other than it seems fine.

---

### Post by coffeecat on 2011-03-30
> **bobeyuno said:**
> The command that you gave me did not run correctlly
```
jack@ubuntu:~$ sudo bash ~/Desktop/boot_info_script*.sh
[sudo] password for jack: 
bash: /home/jack/Desktop/boot_info_script*.sh: No such file or directory
jack@ubuntu:~$ 

```

That is because you forgot to do this:

> **Rubi1200 said:**
> 2. Once downloaded, move the boot info script to the desktop.

Was the original installation a wubi one, or on its own partition? Because if it was not a wubi one, you're likely still to have a Linux partition taking up space on your hard drive. In which case the output of the boot script might be useful.

---

### Post by bobeyuno on 2011-03-30
> **coffeecat said:**
> 


Was the original installation a wubi one, or on its own partition? Because if it was not a wubi one, you're likely still to have a Linux partition taking up space on your hard drive. In which case the output of the boot script might be useful.

nope the first one was also wubi, i wasn't happy to make a new partition on my system. Ive just done all the updates and all is running. :)

---

### Post by Rubi1200 on 2011-03-30
If this is a fresh install, make sure you lock the grub-* packages as explained in the main post of the Wubi Megathread:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by bobeyuno on 2011-03-30
Fantastic! Thanks guys for your help

---

### Post by Rubi1200 on 2011-03-30
No problem, you are more than welcome :-)

You might want to consider marking this thread Solved (assuming all issues have been resolved).

---

### Post by bobeyuno on 2011-03-30
Was just about to but got distracted by playing around with ubuntu again, and to think i was stuck with vista for about 2 years.

---

