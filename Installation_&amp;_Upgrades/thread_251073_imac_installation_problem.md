---
title: "imac installation problem"
date: 2006-09-04
forum: Installation &amp; Upgrades
---

### Post by oysternan on 2006-09-04
I downloaded ubuntu and tried to install it on my old imac. I made sure to download the ppc version. I started my imac holding down the "c" key and ubuntu installation screen started but it asked for no input from me. I read the installation instructions and I was expecting to be asked whether to use the live install option or to install the operating system to disk but I was not offered that option. The splash screen showed me that about 30 or so checks were performed successfully then a flashing cursor appeared in the upper left hand corner of the monitor. After a few seconds, the cursor disappeared and the cd drive continued to spin. After a couple of hours, the cd drive stopped spinning and the computer is on with a blank screen and no drive activity. Where do I proceed from here? Any help would be greatly appreciated.

---

### Post by chicken101 on 2006-09-05
What version of ubuntu did you try?  From 6.06 onward, the install cd and the live cd are one in the same.  You boot into the live cd, and then there is a graphical installer on the desktop.

---

### Post by linear on 2006-09-05
By "old iMac" I assume you mean iMac G3.

The LiveCD does not write the correct display settings for the iMac G3 into xorg.conf. You will need to fix manually:

(If you're not familiar with the command prompt, be aware that commands are case-sensitive. Type carefully!)

After booting is complete,
1. **ctrl-option-F1** (should give you a command prompt, may take a couple of tries)
2. type: **sudo nano /etc/X11/xorg.conf** (return)
3. make your edits (see below)
4. **ctrl-O** (return) to write edited file
5. **ctrl-X** to exit nano back to command line
6. type: **sudo killall -HUP gdm** (return) to restart Gnome (normally sudo /etc/init.d/gdm restart would work, but not with the Dapper LiveCD)

Modify "HorizSync" to 60-60 and "VertRefresh" to 75-117. Both are in the monitors section.

Disable DRI (in the modules section, put a hash mark (#) at the beginning of the line containing "load dri").
         [IMG]http://www.ubuntuforums.org/images/misc/progress.gif[/IMG]                                                                                                                            [[IMG]http://www.ubuntuforums.org/images/buttons/edit.gif[/IMG]]("http://www.ubuntuforums.org/editpost.php?do=editpost&p=1427045")

---

### Post by markd1216 on 2006-09-05
I have a similar problem in that the boot never completes to a desk top screen.  I tried the live disk 6.06 onto an iMac 600 MHz with 640 MB RAM and 80 GB HD.  I went through the many checks and ended with a black screen that for a moment had a blinking white cursor.  I believe I even heard a background boot up sound.  I am at work at the moment, but I am assuming that even with a black screen going through the key combinations will bring up a typable area. I did read a post that suggested one download the "alternate" ppc version.  I did this and the process did not lead first to a desktop with an install icon, but started off doing all the settings required -- and did get to the desk top.  However, everything is deathly slow so as to be unusable. This Mac hummed along with OS X.  I haven't checked for posts regarding the slowness and if need be will start a new thread. Any help on either matter is appreciated. I am only 1 1/2 days into my Ubuntu adventure but would like to see what's beyond the starting gate and am anxious to see if the manual edit works.    Thanks ... Mark D

---

### Post by markd1216 on 2006-09-05
Now that I'm home, I followed linear's instructions.  In deed, when the live cd came to the black screen I followed his/her directions and a command line screen did appear.  Using arrows to scroll to the lines to edit was a bit cumbersome and I had to hunt around a bit, but linear's instructions worked fine.  Since I wanted to jump right in I started the install with a complete HD erase.  I rebooted, logged in, and checked out a few of the apps.  They launched within a very reasonable time.  I believe I'm on my way.  Thank you linear.  I hope this post is seen by the moderators -- this fix should be posted to a Mac FAQ.  If I see other similar issues I'll try to pass it on with attribution. While I remain a pleased OS X 10.4.7 user on my other Macs it is fun to check out the Linux world as a very viable altenative to windoze. 

Mark D

---

### Post by jamesr316 on 2006-09-06
Is there a way to install without the graphical installer? I have an old iMac and followed the directions above, however, when starting gnome i get a lot of errors and it either exits back to the prompt, or loads up with NO desktop-just a top bar.

---

### Post by Dreyco on 2006-09-14
Yea you can download the alternate CD from the ubuntu web page should be the third group down. Then it will just install ubuntu (no live CD)

---

