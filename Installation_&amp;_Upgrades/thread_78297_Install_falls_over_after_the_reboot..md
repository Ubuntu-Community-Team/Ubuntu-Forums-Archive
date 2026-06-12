---
title: "Install falls over after the reboot."
date: 2005-10-18
forum: Installation &amp; Upgrades
---

### Post by muffinresearch on 2005-10-18
When installing breezy on my Compaq E500 at the point where the machine spits out the CD-rom and reboots, the installation always fails at some point installing the extra packages. 

In the end I just rebooted, got to shell and manually installed Gnome, Xorg etc with apt-get. I am now up and running but I would be interested to know if anyone else has experienced the same problem and if so what did they do to fix it?

---

### Post by mcpish on 2005-10-19
I'm having the exact same problem at exactly the same point.. after the reboot when it tries to install the additional packages it says it cant copy them over and then kicks me out of the install program to a shell.
I have no clue how to fix this.

---

### Post by muffinresearch on 2005-10-19
I played around with this again last night and you are probably best to do this when kicked out to shell run:

sudo dpkg --configure -a

Let that run and see what it digs up. I had particular probs with cupsys not finding files. what I did was used touch (sudo touch path-to-missing-file) to create the missing files and then end up doing this:

sudo apt-get install ubuntu-desktop

This installed shedloads of packages without error. Now if I were you I would try running this first (after fixing the dpkg error), but you may have to fix cupsys (I say fix it may still be broke) before you can install ubuntu-desktop. 

Now I am up and running and everything seems stable so far. Someone may have better advice for you but if not try the above. 

As for why I have no idea maybe someone else does but if you follow the above you should at least be able to get up and running.

---

### Post by mcpish on 2005-10-19
Here is the EXACT error message I"m getting while it's trying to install the extra packages after the reboot:

> There was a problem installing the selected software.  

One or more packages failed to install. This may be due to bugs in the packages, or you may be out of disk space or experiencing some other problem.

Simply trying to install these packages (or a slightly different set of packages) again may work around the problem, or at least move the installation process along a little further. If you want, you can go back to the package select step, and try again.

If you decide not to try again, bear in mind that some packages on your system will be in a broken state until you manually resolve the problem. 
I can install 5.04 just fine and disk space isn't an issue, but 5.10 always fails at this point :(

I tried doing that " sudo dpkg --configure -a" command but this is what I get:

> 
dpkg: ../../src/packages.c:191: process_queue: Assertion `dependtry <= 4' failed.
Aborted


I think i might stick with 5.04 until all the bugs get worked out of 5.10

---

### Post by muffinresearch on 2005-10-20
Yep I had that exact same meesage.

Does it let you run sudo apt-get install ubuntu-desktop? 

I agree it's an annoying one though.

---

### Post by mcpish on 2005-10-20
I figured out the problem... BAD RAM!

I had just bought an extra stick of 512MB of RAM over the past weekend  which is the only thing that I changed in the last little while. I wondered why I couldn't reinstall Ubuntu when it had installed perfectly fine in the past.  So I tried to remove the new stick of RAM and reinstalled Ubuntu with only my remaining single stick of RAM.  It installs perfectly without a hitch or any error messages.  I'm going to take back this new stick of RAM to the store and get it replaced.  Maybe you are having the same problem?

---

