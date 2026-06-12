---
title: "Strange Glitches, incomplete or failed Upgrade to 8.04?"
date: 2008-05-03
forum: Installation &amp; Upgrades
---

### Post by llirium on 2008-05-03
Sorry if this sounds like a complicated problem, but I'm trying to get all the details in that I can.

I think I failed to exit all programs when upgrading to 8.04 from 7.10 using the Update Manager.  Now I'm not sure what to do...

I'd thought that there wasn't anything open when I started, but then it said something about Evolution (a program only my partner uses) shutting down suddenly in some error logs, when it had nearly completed the upgrade.  Perhaps he was still logged in with programs open, I don't know for sure.

It was supposed to "dpkg-configure a" after that, though I don't remember clearly if it said that.  But then the Upgrading program itself seemed to crash completely, leaving me with just the regular desktop.

I thought it would undo its configuration and go back to being 7.10, from what the errors seemed to be saying before it crashed, but nothing seemed to be happening.

So, optimistically, I restarted.  Xorg messed up on me and I started in a 800x600 desktop cloned environment when prompted.  The old monitor and graphics settings were messed up, but then a *second* restart brought back things to normal, save that the Login image is ridiculously huge in scale (one corner of the Blubuntu image takes up the whole LCD screen) and I can't see what I'm typing in.

Synaptic seemed fine after I put in Medibuntu, Wine and Swiftweasel's 8.04 repositories.  It says that it's 8.04 in the kernel and the Heron repositories seem to accept that the installation is genuine, but there are glitches that pop up.  There aren't any Broken packages reported by it.

What do I do?  Should I burn the alternate install 8.04 ISO so I can keep GRUB's settings? (I dual-boot with Windows XP)  Or is there a simpler solution?

---

### Post by dstew on 2008-05-03
It sounds like it is working. You can re-set the login screen resolution by editing your /etc/X11/xorg.conf file. Put the resolution you want for the login screen at the beginning of the list of modes. The other resolutions will still be available, but now the login will be visible. See [this thread]("http://ubuntuforums.org/showthread.php?t=753376") for an example.

If you are still worried that your install is not pristine, you can install from a CD as you suggested. However, you will have to reinstall your programs, and re-set your configurations. Also, be sure to back up your data, because the CD install will re-format the partition that has your data (unless you have a separate /home partition).

---

### Post by llirium on 2008-05-06
> **dstew said:**
> Put the resolution you want for the login screen at the beginning of the list of modes. The other resolutions will still be available, but now the login will be visible. See [this thread]("http://ubuntuforums.org/showthread.php?t=753376") for an example.

That worked ok, though I think there's another problem.  All the xorg.conf settings are using generic settings, not ones that detected our hardware.  

> **dstew said:**
> Also, be sure to back up your data, because the CD install will re-format the partition that has your data (unless you have a separate /home partition).

My partner has a lot of foresight, and we do have our /home on a separate partition (been that way from our very first Edgy install).  That will simplify things, since we don't have very many packages from other non-default repositories.

Not sure if we have the time to do a reinstall, but it would help put my mind at ease that nothing else has gone wrong.

---

### Post by dstew on 2008-05-07
With 8.04 you can do a complete re-configuration of your xserver if you want. Get a command line with alt-F2, and enter```
gksudo displayconfig-gtk
```I haven't done this myself yet, so I can't say for sure how it goes, but others have used it with good results.

---

### Post by llirium on 2008-05-09
Decided to downgrade back to Gutsy 7.10 so that things would be a little more stable for our PC.  It seems to be working well. :)

And I found out what the problem was for the sound, I had the "Analog/Digital Jack Output" switch ticked 'on' in the Mixer (sound card is an Audigy).

Thanks a lot for all the help, dstew! ^_^

---

### Post by fesk on 2008-08-27
so how did you manage to downgrade to 7.10? I won't get passed the logging screen so I can't type any commands either. Anyone know what to do ? Can I copy some files from the cd ? If there is no way to downgrade my system, how do I save all my stuff? Easiest way ? 

Thanks people, I hope some of you can be helpfull!!

---

