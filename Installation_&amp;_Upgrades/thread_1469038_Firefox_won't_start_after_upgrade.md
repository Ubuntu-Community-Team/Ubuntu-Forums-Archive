---
title: "Firefox won't start after upgrade"
date: 2010-05-01
forum: Installation &amp; Upgrades
---

### Post by Devinish on 2010-05-01
Just upgraded to 10.04 and Firefox will no longer start.  I get the tab that says starting firefox, and then the tab disappears, and I never get a window.


When I try to start via terminal it says (something along the lines of):

Attempting to load libmoonloaderxpi
Segmentation Fault

I tried logging out and back in, no dice; restarted, no dice; uninstalled and reinstalled firefox, no dice.

Running x64, if that matters, on a pretty decent laptop.  I would describe my technical knowledge of Linux as moderate.

Thanks in advance for your time.

---

### Post by Devinish on 2010-05-02
Bumping because I dislike Window$...

---

### Post by dashingdon on 2010-05-02
same here .... Firefox keeps disappearing :confused:

Update : use synaptic to locate libmoon and "Mark for Removal"

Reference : [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9204148](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9204148)

Issue resolved for me

---

### Post by rcarlton on 2010-05-02
Firefox does not appear.   I looked to see if libmoon is on my machine, it isn't so removing it is not a solution for me as it has been for some others with a Firefox problem.

I am using Chrome fairly successfully, but it has occasionally frozen the mouse when requesting a new page, requiring me to reboot.

Any more ideas of what causes this?

---

### Post by evoisard on 2010-05-02
Same here, the only message I get when I run FF from a terminal is "Bus error"...

Since I had to force X to start in "vesa" mode (during installation I've got the blackscreen/freeze because of my i855 GPU), I'm wondering if it's not related and if Ubuntu's FF is not expecting some H/W acceleration or so...

Eric

---

### Post by dashingdon on 2010-05-02
> **rcarlton said:**
> 

***I am using Chrome fairly successfully, but it has occasionally frozen the mouse when requesting a new page, requiring me to reboot.***



I am having similar behavior with Firefox ..

---

### Post by Devinish on 2010-05-02
> **dashingdon said:**
> same here .... Firefox keeps disappearing :confused:

Update : use synaptic to locate libmoon and "Mark for Removal"

Reference : [http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9204148](http://ubuntu-ky.ubuntuforums.org/showthread.php?p=9204148)

Issue resolved for me

This did not solve my problem.  libmoon was not installed on my system.  Still searching for answers...

---

### Post by Scari on 2010-05-02
so bottom line is I'm staying on 2010 version for now, my first attempt to upgrade failed half way through. So after finally getting this version back up I'm sticking with it until the bugs are fixed, not sure what happened here but think the team dropped the ball a bit which is disappointing since this OS has such a good track record.

---

### Post by rcarlton on 2010-05-03
I got Firefox to launch by disabling the Add-Ons (from a Terminal type Firefox -safe-mode).  

Both Chrome and Firefox will display pages fine for awhile and then suddenly the mouse freezes and everything stops.

I suspect the problem is a lower level OS function that both Chrome and Firefox use.

---

### Post by Arizon_Dread on 2010-07-07
> **rcarlton said:**
> I got Firefox to launch by disabling the Add-Ons (from a Terminal type Firefox -safe-mode).  

Both Chrome and Firefox will display pages fine for awhile and then suddenly the mouse freezes and everything stops.

I suspect the problem is a lower level OS function that both Chrome and Firefox use.

Got the same issue as stated (no libmoon installed), however, this is not after an upgrade. I installed 10.04 two days ago on a formatted hdd. I tried safe mode for firefox but to no avail. chrome works but I need firefox for plugins that're really crucial to my work and which I can't get to run on chrome. 

Any suggestions?

---

### Post by Arizon_Dread on 2010-07-07
I solved my issue.

[http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html](http://firefox-tutorials.blogspot.com/2010/05/general-troubleshooting-steps.html)

I ran 
```
firefox -P
```
and created a new profile and it worked. It remains to be seen if the problem reappears or not.
:popcorn:

Edit: The problem persists, It crashes from time to time and then I have to remove the profile for it to start again, which means that my bookmarks and add-ons disappears.. I'm quite unhappy with this.

Edit2: SOLVED, I made a new symbolic link and it worked! 
```
sudo rm /usr/bin/firefox && ln -s /usr/lib/firefox-3.6.6/firefox.sh /usr/bin/firefox
```

I tried first by changing the "command" part of the firefox short cut to point directly to /usr/lib/firefox-3.6.6/firefox.sh and that worked, so I recreated the symbolic link of /usr/bin/firefox

---

### Post by Arizon_Dread on 2010-07-14
bump, solved, see above if you have this issue.

---

### Post by gshockxc on 2010-12-07
I tried your suggestion, and I got: 

```

ln: creating symbolic link `/usr/bin/firefox': Permission denied

```

Any thoughts?

Thanks,

---

### Post by Arizon_Dread on 2010-12-08
put 
> sudo
in front of the command.

I also found that if I remove the file called secmod.db, starting firefox works without deleting the profile.

the file is located here:
> ~/.mozilla/firefox/<somethingRandom>.Default\ User/secmod.db

---

### Post by countrylane on 2011-01-28
Try freeing up disk space. I emptied my trash can (Gnome Trash Applet), then ran Bleachbit to get rid of other unnecessary files. You may or may not have the Gnome Trash applet and there are other ways to clean up your hard drive besides Bleachbit, but the point is the same: free up hard drive space if you are running low.

Prior to freeing up space Firefox wouldn't start, even in -safe-mode. I kept getting segmentation fault errors. My hard drive is very full, so I know it's an issue for several reasons besides Firefox.  I don't know if the act of freeing up hard drive space fixed the problem, or if there was some file somewhere that was corrupted that was causing the issue, but give it a try. At worst, you regain some space.

---

### Post by glendeni on 2011-01-29
I had the same problem immediately after an install (and package updating) of 10.04LTS, i.e. running "/usr/bin/firefox" in terminal gave "Bus error" and Firefox failure/exit.  Solution was removal of old profile in ~/.mozilla (which I was hoping to be able to use so I would not have to recreate all my old firefox usage settings).  Much thanks to Arizon_Dread for this solution!

---

