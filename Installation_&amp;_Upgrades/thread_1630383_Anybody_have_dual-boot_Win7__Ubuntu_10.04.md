---
title: "Anybody have dual-boot Win7 / Ubuntu 10.04 ?"
date: 2010-11-25
forum: Installation &amp; Upgrades
---

### Post by Unterseeboot_234 on 2010-11-25
Hi, I do have problems with Ubuntu 10.04 dropping menus. I have 64-bit Windows 7 (yech) and Ubuntu 10.04 with the Radeon HD 5400 PCIe.

I wished I had the nVidia graphics card, seems to be less trouble on my other Ubuntu box running Ubuntu 9.10.

On my Radeon 64-bit machine, I can not change GUI language. I keep losing my Shutdown menu. I don't know whether to blame Windows 7, the Radeon Preferences (update) or Ubuntu 10.04. I mention Windows 7 because it is a known fact that a Reboot from Win7 is not the same as a cold start. The Windows 7 restart maintains its idea of time and screws up the Ubuntu clock because Win7 bypasses the first BIOS screen when discovering hard drives.

The spookiest glitch is Ubuntu at shutdown says there is unsent Evolution email to send. I have never set up Evolution for any mail accounts.

The Radeon works on a clean install, and then of course Ubuntu wants to update with a massive download. That update does require the radeon driver update also. If the Radeon is interfering with Ubuntu, I will consider a nVidia replacement. I'd hate to spend the money tho'.

So, before I go through yet another reformat, install of Ubuntu, does anybody else have dual-boot Win7 / Ubuntu? And what version of Ubuntu? I'm considering going back to Ubuntu 9.10. I like the interface better in 10.04 but I see a lot of people on these forums losing GUI panels or they can not change GUI language. I mean I have to reinstall the top toolbar every other day to get Shutdown panel back. And that machine is the office machine and the staff is getting frustrated.

Your thoughts? Your experiences?

thanks.

---

### Post by efflandt on 2010-11-25
Not sure what is going on with your top panel.  The only version I had an issue with the top panel, where the menu with my name would sometimes replicate and cover the shutdown icon was 10.10.  And I never noticed "when" it happened (if I dragged the mouse on the top panel?), only "after" it happened.

My solution was simply to add another shutdown applet to the left of everything in the upper right.  But that has not happened lately, so maybe that was an issue that has been fixed.

If all else fails, you can open a terminal and do: **sudo shutdown -h now**

---

### Post by Mark Phelps on 2010-11-25
Yes ... I'm dual-booting Win7 and Ubuntu 10.04.

The "time problem" you mentioned is NOT Win7's "fault" -- it is because the default, is that Ubuntu uses UTC time, and Win7 does not.

I encountered this same problem switching back and forth until I discovered that the "fix" was in Ubuntu (NOT Win7) and involved editing the file /etc/default/rcS and changing the string "UTC=yes" to "UTC=no". 

After that, there was no more "time problem" when switching back and forth.

---

