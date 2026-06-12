---
title: "Trying to install from CD, but computer just keeps rebooting"
date: 2012-08-01
forum: Installation &amp; Upgrades
---

### Post by LakeHMM on 2012-08-01
I'm trying to install the latest version of Lubuntu from a CD on a computer currently running Ubuntu Dapper Drake.  There are no other partitions on the hard drive and no other removable media in the computer aside from the Lubuntu CD.  When I turn it on to try to boot from the Lubuntu CD, the computer goes directly to a black command line screen with nothing but a blinking underscore cursor thing in the top left corner.  After about 15 seconds, the computer appears to reboot (screen goes blank, keyboard lights flash) and then returns to the blinking underscore command line screen.  Then, it does the whole thing over again, rebooting over and over.  I've tried leaving it for a little while, and it seems to be an unending cycle of rebooting.  At no point does the computer display anything besides the flashing underscore - no logo of the computer manufacturer or BIOS information.  The BIOS is set to load from the CD before hard drive, as evidenced by the fact that it goes into this cycle as opposed to booting Ubuntu.

FYI, this is on a Dell Dimension 4100 that has no problem running Ubuntu, aside from being a little slow.

What's the problem here?  How do I end this rebooting cycle and install Lubuntu?  I'm new to Linux, so I don't know how to go about figuring out what the problem is.

---

### Post by Version Dependency on 2012-08-01
I'm not sure why your live CD keeps rebooting, maybe others will have suggestions for that.  But I will say this...your hardware is pretty old.  You say it is running Dapper (6 years old now) and it runs it slowly.  I believe it since the 4100 Dell's are around 10 years old.  I have a couple of computers that around the same age, and they struggle to run the graphical installs of the various flavors of Ubuntu...including Lubuntu.  But I have had great success downloading the Ubuntu Server ISO (make sure it's the 32 bit version as your older hardware won't run 64 -bit) and install that.  The server install is text-based but still rather simple...skip installing all the server-related stuff...so the install takes about 15 minutes.  When you are done all you have is a command line.  Type in:

```
sudo apt-get install lubuntu-desktop
```

Let that run until complete (takes a few minutes).  Reboot and you have Lubuntu.

---

