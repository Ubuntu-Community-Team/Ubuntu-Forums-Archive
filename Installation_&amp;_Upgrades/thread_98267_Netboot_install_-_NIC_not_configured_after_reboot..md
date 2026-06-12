---
title: "Netboot install - NIC not configured after reboot."
date: 2005-12-02
forum: Installation &amp; Upgrades
---

### Post by rorywohl on 2005-12-02
My problem is similar to this thread - [http://www.ubuntuforums.org/showthread.php?t=95580]("http://www.ubuntuforums.org/showthread.php?t=95580") - but different.

I'm installing ubuntu via netboot using a cd made from the mini.iso image. (My cd-rom works enough to boot the mini installer, but not enough to perform a full ubuntu install.)

The first half is fine.  The installer boots, configures the network, and runs the install by downloading everything it needs. GRUB is installed and the installer wants to reboot. I reboot, hitting no keys and choosing no options.  The installer continues and tries to download the remaining packages.  After a couple of minutes, it errors out with a message saying that one or more packages failed to install, and something about bugs in the packages or out of disk space. blah, blah, blah.

It says I can go back and try again, or go back to the package selecting step, but all it gives me is an OK. After hitting OK it drops me to the console and that's that. 

The one thing I noticed is that during the reboot it gets to the point where it says:

Synchronizing the clock to ntp.ubuntulinux.org ...... [fail]

The error message in the Alt+F8 window (I don't know what that's called) says "Error: Temporary failure in name resolution."

So that got me thinking that maybe the NIC isn't configured.  So, I logged in and did an ifconfig with the following results:

[FONT=Courier New]lo     Link encap:Local Loopback[/FONT][FONT=Courier New]
     inet addr: 127.0.0.1  Mask:255.0.0.0[/FONT]
      [FONT=Courier New]UP LOOPBACK RUNNING  MTU:16436  Metric:1[/FONT]

and some other stuff about packets received and transmitted.

I don't know much about ifconfig, but I know enough to know that it's telling me my NIC isn't configured.

I think it's really wierd that the NIC was configured by the installer to download the packages but not by the actual system install.

Any suggestions on how I can proceed from here?  My skills with ifconfig are really weak and I have no idea how to manually configure the interface.

Thanks,
- Rory

---

### Post by mlomker on 2005-12-03
You'd have to know what driver your card uses and then use **sudo modprobe *drivername*** to load it.  From there you could run **sudo dhclient** to get an address.

I'd normally suggest that you boot Knoppix and see if it configures the card.  **lsmod** would tell you what driver is being used.

---

