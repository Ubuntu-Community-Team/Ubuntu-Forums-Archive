---
title: "Installing Xubuntu 14.04.1 over 16.04 keeping the Home Folder"
date: 2016-12-11
forum: Installation &amp; Upgrades
---

### Post by happydog500 on 2016-12-11
I installed Xubuntu 16.04 but it's to unstable and can't get the dual monitors and sound working. I have to go back to 14.04.1 to use fglrx. I remember a thread where someone installed an OS and kept his Home Folder intact. One person even switched distros (I think from Ubuntu to Mint) and kept his Home Folders with data. 

 On this computer, I have three partitions. /, /home and Swap. 
 
 During the install, I don't remember seeing a choice to not overwrite home. I realize I wasn't looking to do that at the time, but will I see a place to not do anything to the Home folder when installing Xubuntu 14.04.1? 

 Thank you,
 Chris.

---

### Post by ajgreeny on 2016-12-11
Choose "Something Else" when you get to the partitioning stage and you will see all your partitions listed.

You can then click on each of them and choose Change (I think that is the option, might be Edit).
For the /home partition choose to use it as ext4 (if that is what it was before), set mountpoint as /home but **make sure you deselect the Format tick box**.
For the root partition again choose to use as ext4, mountpoint this time will be / but **select the tick box** for Format
You can ignore swap at this stage as it will be found and reused automatically.

---

### Post by happydog500 on 2016-12-12
OMG!! This is so cool!!!!

 Everything is right there. Wish I would of known that a year a go. I've installed probably 20-30 times this year, losing everything. Really, really cool!!

 Thank you,
 Chris.

---

### Post by ajgreeny on 2016-12-12
No problem.  Glad I could help; it's how I have installed for many years now, even when I am not upgrading my OS version, as it give me total control of everything.

Please mark as SOLVED from the Thread Tools menu up-top if this is now solved to your satisfaction. It is a great help to users searching the forum.

---

### Post by happydog500 on 2016-12-12
Thank you. Only problem mow is 14.04.1 screen goes blank after about 10 minutes. Found it's a known problem and no easy fix, as the settings don't work. They fixed it in 15 (went away from x). 

Thank you for helping me through keeping the home folders. Kind of scary to think you can change the whole OS and keep home. If you have any mailware (It's not true "beginners mistake" Linux doesn't get them, no one looks) and change the OS, keeping home folders may keep the problem. 

 Chris.

---

