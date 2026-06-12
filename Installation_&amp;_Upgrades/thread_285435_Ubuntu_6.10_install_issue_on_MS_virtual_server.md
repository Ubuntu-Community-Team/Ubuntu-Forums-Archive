---
title: "Ubuntu 6.10 install issue on MS virtual server"
date: 2006-10-26
forum: Installation &amp; Upgrades
---

### Post by TwoSeven on 2006-10-26
This seems to be an issue related to one of the changes to the graphics display manager in ubuntu 6.10 as it does not occur in 6.06.

In 6.06 to install and run in Microsoft Virtual Server, one had to choose "safe graphics mode" and also choose a 16 bit font (although not sure that last bit was required).  If the safe graphics mode option was not chosen, the display would become corrupted with incorrect video refresh settings.

In 6.10, this installation hack no longer works resulting in a messed up screen (like someone hasnt gotten the horizontal refresh rate correct) occuring all the time - there are some colors on the left of the display (random block pixels) and the rest of the display is blank.  I can just make out what looks to be part of the login field, but display graphics too badly corrupted.

I suspect whatever this issue is, is also the same one for another install issue posted in this forum.

Can someone tell me what the 6.06 'Safe mode settings' were, and how to force 6.10 to use the same settings (ie. by using the F6 command line option).

Note:  When I remove the quiet option from the command line, I can see that it loads the gnome desktop manager, the screen font changes, then goes blank (I suspect a desktop manager may be loaded) to load the login screen - thats when the display goes haywire.

Cheers
Two Seven.

---

### Post by TwoSeven on 2006-10-28
bump.


[Years ago when I used to do commercial s/w development, programmers who worked on a product would man the phones when it went live.  Not only did it reduce the amount of defects they created in the long term, but their familiarity with the way users interacted with their system also increased resulting in better software design.  Funnily enough, it also resulted in happy users who had their support queries answered.  Shame that practice seems to be no longer performed]

---

### Post by AnonymusKitten on 2006-10-28
This is actually a long-standing well-known problem with X.Org, that the X developers for unknown reasons refuse to fix, or are just not interested in fixing for the people who are running Virtual PC/Virtual Server.

You can either blame MS for not supporting 24bit in their virtual S3 Trio 64 graphics card, or blame X.Org for not probing the ROM for what modes are actually supported.

I blame X.Org as they are making a known to be incorrect assumption about S3 Trio 64 specifically.

FYI, not only Ubuntu have this problem. Fedora 6 have it as well.

[http://blogs.msdn.com/virtual_pc_guy/archive/2005/05/09/415814.aspx](http://blogs.msdn.com/virtual_pc_guy/archive/2005/05/09/415814.aspx)

---

### Post by waynep on 2006-10-28
I have the same problem as you. What I did was download the Alternate install disk and install in text mode. I then booted the rescue/recovery kernel option and edited the default depth setting in /etc/X11/xorg.conf. Thigns work fine now.

I agree, it's a pain. I just downloaded the Trial version of Parallels. Installing 6.10 right now using safe graphics mode and it's working fine. Performance during the install is drastically better. I'll let you know how things run after the install is done. I may spend the bucks on parallels if things are that much better. Just starting up the live cd portion was remarkably faster than VPC. 

wayne

---

### Post by TwoSeven on 2006-10-28
errg.
Thanks for the reply folks, info is useful.

Once was a time when I was a young geeky type that I would sit down and solve the issue by working out all the little fiddly command line options.  Now in my old age I find it tiresome mainly because it frustrates me for having to use important time to do things I should really at the end of the day be having to do (after 20 years or so of putting up with this I'm learning to say no).

Thing is, the product I am trying to use is called Ubuntu. Its these folks that are responsible for testing out the issues and getting them resolved (even if it does mean working with third parties).

Me having to go to the x.org folks to complain about something is like me having to go to to the farmer because my hamburger is cold.  The people responsible behind the scenes should be transparent to the end user.

Anyhow, until I see a fix posted, ubuntu goes in the junk bin and another distro shall be used. :)

---

### Post by JoseStefan on 2006-12-07
Another solution, while still using the desktop CD:

1- On the boot menu, select the 1st option and press **F6** (Other Options) to edit the command.
2- Go near the end of the line and remove **splash**, then press **Enter**.
3- After it boots, the display will "still" be corrupted. But now there will be slight difference. If you go to a terminal screen (Ctrl+Alt+F1) It won't be corrupted.
4- Once in the terminal screen, you might need to press **Enter** to get a prompt. Then run:
*sudo dpkg-reconfigure xserver-xorg*
You'll want to stick to defaults but change the color depth from **24-bit** to **16-bit**.
5- Go back the GUI (Ctrl+Alt+F7) and restart X (Ctrl+Alt+Backspace)

---

### Post by The Deadite on 2006-12-26
Ok, I'm having trouble using 6.06 with virtual pc. I have tried safe graphics mode and it wouldn't go past the splash screen. This is my first post btw. I came across this thread through google.

---

