---
title: "Login, then, blank screen w cursor"
date: 2008-03-18
forum: Installation &amp; Upgrades
---

### Post by smandoli on 2008-03-18
I am such a total newbie that I have reinstalled Ubuntu 7.04 Feisty only eight times.  You may say, "If that's all your reinstalls, you have NO business using Linux!"  Maybe so, but here is my issue anyway.  

When I boot, the system shows a login prompt which I am able to complete.  Then the system goes to a screen that does have a background color (it's brown!) and has a controllable cursor arrow. Besides moving the cursor around, I can Ctr-Alt-F2 to command-line.  That has let me poke around, but my trouble shooting skills run out pretty quick.  

My general experience is that when I fresh install things work well, but at some point while installing applications I have some kind of failure.  (I try to handle the installations incrementally but haven't been able to identify problem spots.)  After that I can boot up off my CD of course, but can't resolve the issues.  Oh, and I did try Gutsy but failures discouraged me there.  

I am running 
[INDENT][FONT="Courier New"]  Chip       :  AMD Athelon 1200 MHz, 1.5Gig RAM
  Board      :  ASUS KK266 plus
  Vid Card   :  Nvidia MX400 64MB 
  Monitor    :  NEC AccuSync[/FONT]

      I am running Dansguardian - I know it 
      enters early in the boot routine.  [/INDENT]

I had 3D video enabled during "round 1," the first of my two installs that seemed to get anywhere.  (I did not use Envy for that.  Trial-n-Err got me to nvidia-glx.)  But have put off attempting that during round 2.   

I have edited xorg.conf -- for "depth 24" I deleted some higher res levels.  This made my screen sequence happen in a better res, but no difference otherwise.  I also specified H/V synch.  

The monitor is working so I think video settings are okay.  Seems more like gnome is failing to launch, or a sys logon issue.    

QUESTION, what about a log file where I can see what I installed (using Synaptic) on my last install round?  Where is that, and would it lead to a method tome roll back?

---

