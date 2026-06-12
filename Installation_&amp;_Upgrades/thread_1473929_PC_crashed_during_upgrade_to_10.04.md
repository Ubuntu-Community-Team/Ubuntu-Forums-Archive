---
title: "PC crashed during upgrade to 10.04"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by kylekobe on 2010-05-05
Hi all,

So I was upgrading to 10.04 through the update manager and my pc froze during the install, and I mean dead stop. It's happened a few times since I've come home from college for the summer, but I thought it was just the game I was playing or something so I wasn't concerned.

Now when I try to boot it gives me errors mounting /media/1 and /media/2 and various other others regarding NTFS (yet linux doesnt use NTFS so I'm confused...). When I hit any button that's not a letter (Esc, Delete, Backspace, etc.) it flashes over to a screen that says 10.04 with 4 dots underneath. Similar to what the loading screen should be, yet obviously not the loading screen. 

Is there anyway I can install/upgrade this system through a LiveCD or something similar? I can't boot to Linux at all now, but I can boot to the Windows partition on the same hdd. Please let me know what you need from me to help fix this. I'm fairly new to Linux, so any help would be greatly appreciated.

-Kyle Kobetitsch

---

### Post by kylekobe on 2010-05-05
Could I just go on the machine using a LiveCD and save the /home directory and then reformat the whole partition using the 10.04 disk? Is that feasible? Or is there an easier way to go about this?

---

### Post by theantidj on 2010-05-05
I don't know about your specific freezing issue, but I also experienced issues in doing the upgrade. 

I did as you suggest.  I downloaded a live cd on one of my other computers, used it to get into my messed up machine, and transferred all of the files I wanted to save onto a USB drive.

I then did a clean install from the live CD.   

It might be your best bet, as that way, you're starting off with a clean slate, so there are fewer variables that could create problems.

---

### Post by kylekobe on 2010-05-05
I think that's the route I may take then. I'm not really concerned about the freezing issue.. I'm pretty sure it was a beta game causing probems, so an upgrade should fix it. Clean install seems like my best bet though.

---

### Post by kylekobe on 2010-05-05
So I'm realizing that I can't access /home/kyle. Permission denied on everything I try to do, even in root. I realize this is a "security" feature, but since I'm new I don't know how to get around it. What can I do? I've noticed I can use mv to rename it, yet I can't copy it. Can I just move it to an external without any problems? I'm afraid of moving something I shouldnt be moving, but then again, I'm just going to be formatting the whole system anyway.

---

### Post by kylekobe on 2010-05-06
Alright...  So after doing a little searching I accessed my user directory, but it appears to be encrypted using Ecryptfs. I didn't set this up, and it seems that the only way to decrypt my data is to use a mount passphrase that I wouldn't know? I'm kinda stuck now...

Trying ecryptfs-mount-private gives me the error:
```
ERROR: Encrypted private directory is not setup properly
```

---

