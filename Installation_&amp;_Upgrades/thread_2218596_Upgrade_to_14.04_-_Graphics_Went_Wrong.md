---
title: "Upgrade to 14.04 - Graphics Went Wrong"
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by echotech2 on 2014-04-21
Note:  I'm typing this in Midoro from SystemRescueCD. This disc boots and displays just fine
            Graphics card is a GTX650Ti using propietary nVidia driver nvidia-current-updates v319.xx 

  What I did: Online update 13.10 to 14.04.  This computer does NOT support boot from DVD or USB.  Install went well with no (obvious) errors.

  On Boot: On reboot after install completed everything went well, selected Ubuntu from GRUB, my DESKTOP opened mostly to my normal DESKTOP colours (blue>black gradient), launcher displayed OK with correct colour and icons but the top panel had a black (was blue) background with the icons displayed.

  What Happens: Using Firefox as an example but this happens with all programs with a couple of exceptions. Clicking the Firefox icon in the Launcher, the desktop area turns black (except for the Launcher and top Panel).  In the top Panel "Firefox Web Browser" text and Date/Time fonts change to an outline font of some kind.

  Stellarium (star chart) launches and works just fine, the only program that does.
  
  The Terminal also acts a little differently, opening it first after a reboot while I'm on correct Desktop I have the borders of it showing but the center is black.
 
  Clicking on the Dash icon the the application icons all display OK, albeit with a black background.  Selecting an application I'm back to the black Desktop.  
 
  If I open an application (e.g. Firefox) I get the two > < indicators in the Launcher (but the desktop is black), so I opened the Workplace Switcher.  I get the four Workplaces, but the unused Workplaces have a black background colour.  The Workplace where Firefox is has the correct gradient colour and Firefox displays in miniature as it should.  Selecting that Workplace I just get the black background again.

  If I click on a top Panel item, Network Manager, System Settings, etc. right after the Desktop loads and is looking OK, the drop-down menus are just a black box where the menu items should be. Choosing another top Panel icon and I now have two black boxes.

  
  There are a couple more anomalies but they are probably related to above, and they skip my mind right now.  They were probably stored in one of the 10,000 brain cells that die every day.

  So I guess the question is - How do (or can) I fix it?

  And a second question -  How do I navigate to my hard drives using emelfm, the file manager on the SystemRescueCD?

  Feel free to ask any questions, but I will be in and out all day so there may be some delay before I get back to see all the enlightening answers.......

-- Thanks, Dave.

---

### Post by i0ls on 2014-04-21
I just upgraded and have this exact issue. I have done a little searching around and I think it has something to do with Nvidia drivers. 
Do you have an nvidia video card? 
I have tried purging the drivers and adding different ppa's (edgers and xswat) with the same results. I recall saucy had an issue and you could purge bumblebee from nvidia drivers and the issue was resolved. Trying to purge bumblebee from trusty and the package is not found. 
If I find anything I'll post it up here, though I do recall seeing a bug about Nvidia drivers not working in trusty and if that's the case we could be sol. Why are nvidia drivers such a huge pita with ubuntu?

---

### Post by echotech2 on 2014-04-22
Video card is a GeForce GTX650Ti  using Nvidia proprietary driver nvidia-current-updates v319.xx.

---

### Post by vincentmichaud on 2014-04-22
Hello, I have a problem too with a nvidia gtx560ti. A friend of me have the same problem with a notebook. I post here [http://ubuntuforums.org/showthread.php?t=2218805&highlight=nvidia](http://ubuntuforums.org/showthread.php?t=2218805&highlight=nvidia)

---

### Post by echotech2 on 2014-04-22
Ok, I tried to boot in Recovery Mode - FailSafe Graphics.  It may be safe but it failed, just like above.

---

### Post by echotech2 on 2014-04-24
Just a gentle bump.......

---

### Post by echotech2 on 2014-04-30
Not really solved.  I gave up and re-installed.

---

