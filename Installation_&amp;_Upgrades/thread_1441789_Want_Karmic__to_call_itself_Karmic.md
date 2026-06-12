---
title: "Want Karmic  to call itself Karmic"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by Randymanme on 2010-03-29
With PCLinuxOS, you install as root, but use the os as a different user.  That way, whatever you (as different user) screw up or break has no effect on the rest of the system.  "Different user's" system can be totally disabled, while root's system is as pristine as a fresh install.
 

 For some reason (I"m not sure what), I thought it was like that with all Linux systems, namely Ubuntu. Well, I've discovered the hard way that that's not true.
 

 At the social club where I volunteer, I login in to the computers there as a "different user."  While I do have administrative privileges, it's understood by consensus (our formal decision making process) that we (a non-hierarchical, egalitarian collective) only use Ubuntu on our shop computers. Well I installed (and used) some Linux Mint tools on "my" desktop (but not as root), but it has had the effect of upgrading the entire system to Helena.  What to do, now?
 

 Linux Mint does not recognize an Ubuntu system upgraded to LM as ". . . genuine Linux Mint package."  And Karmic's terminal output says ". . . can not downgrade Helena to Karmic . . ."
 

 I've read in one of the Linux Mint/Ubuntu comparison reviews, that when installing the two systems as a dual boot, the latter install gives the option to import files and settings from the former to the latter.  Does anyone know this to be practical fact?  
 

 As things stand, no one (other than me) is bent out of shape about it and I don't want to make the situation worse.  
 

 Any help or advice will be much appreciated.

---

### Post by dstew on 2010-03-29
I am not sure what happened. How did you install Linux Mint tools on Ubuntu? If you use the Software Center, or Synaptic, it should not upgrade to Helena. But, you usually need root privleges to install software, so it is possible to create problems. Perhaps you installed a package that required a more recent kernel?

---

