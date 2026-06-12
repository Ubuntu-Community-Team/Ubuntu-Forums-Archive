---
title: "Grub error"
date: 2010-01-26
forum: Installation &amp; Upgrades
---

### Post by frostymm on 2010-01-26
Okay well this is what I've done so far:
-Have windows xp installed
-Tried to install Kubuntu (Failed 4 times)
-Attempted to load dual boot
-Gotten error 
Booting from local disk....
Grub loading.
Error: no such disk
Grub rescue>
-Looked online for several hours finding many useless threads that I don't understand
Ex: [http://ubuntuforums.org/showthread.php?t=1306900](http://ubuntuforums.org/showthread.php?t=1306900)
      [http://ubuntuforums.org/showthread.php?t=1341757](http://ubuntuforums.org/showthread.php?t=1341757)
-Tried everything it said that I could understand to no avail
-Raged.... A lot....

I've tried ubuntu before and I always have problems with it. I don't see how ANYONE can say it's so much better than windows with all these issues but then again I don't know much about it except how to get issues....  I need an easy and very specific guide on how to either fix this or remove Kubuntu from my computer entirely. Can anyone please help me? I just want my computer back to normal.... Or even completely formatted so I can load something else would be nice.

---

### Post by gnack on 2010-01-26
Those two threads you reference seem relevant and fairly clear.  Are you installing using Wubi or with an install CD?  Are we talking about kubuntu 9.10 here?

There's something wrong with the bootloader (grub) that isn't allowing your system to boot.

---

### Post by gnack on 2010-01-26
Oh, and when you say, "Failed 4 times", what do you mean - how did it fail?

---

### Post by frostymm on 2010-01-26
Install CD, Yes.
The first time it said I got a bunch of errors and my disk was Read-only but it's not.
The second and third time it just froze.
The fourth time it just got stuck on 47%.

Oh and it installed twice apparently... One of the installations has all the files while the other is short a bunch. I guess the one that's short was from the first try. Ubuntu is horrible in that it doesn't give you the option of reinstalling over the same place.


Also, while I was trying to do the first thread in my examples I got an error saying cannot guess the root device and can't open /dev/sda while checking disk size.

---

### Post by oldfred on 2010-01-26
If the partitions are set up, then you use manual install. All you have to do then is choose / (root) and swap. If you created /home you can choose that also. Manual install is not difficult for those who know about partitions but it is not for users who haven't a clue what a partition is. That is why the installer tries to make it easy for new users.

---

### Post by frostymm on 2010-01-26
No idea what you're talking about, I didn't see an option for swapping. Nor do I know what the root would be considered.

---

### Post by presence1960 on 2010-01-27
I need to see your setup & boot process. Without seeing these it is a waste of time trying to guess what the problem may be.

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by sahabcse on 2010-01-27
Please follow below url for fixing the grub issue

[http://ubuntulinux.co.in/fixing-grub.php](http://ubuntulinux.co.in/fixing-grub.php)

---

### Post by presence1960 on 2010-01-27
> **sahabcse said:**
> Please follow below url for fixing the grub issue

[http://ubuntulinux.co.in/fixing-grub.php](http://ubuntulinux.co.in/fixing-grub.php)

That will only work for legacy GRUB 0.97. If the OP has karmic and GRUB2 the process is totally different. it would be in the OP's best interest to run the boot info script as requested so we can see his/her entire setup & boot process. let's not blindly give commands to run without knowing exactly what he/she has on the machine. That only serves to make problems worse if the suggestions are not fit for the problem.

---

