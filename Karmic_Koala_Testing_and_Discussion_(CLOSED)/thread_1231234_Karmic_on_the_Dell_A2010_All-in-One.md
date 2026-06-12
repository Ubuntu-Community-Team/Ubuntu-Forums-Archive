---
title: "Karmic on the Dell A2010 All-in-One"
date: 2009-08-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by rondackcpu on 2009-08-04
I have been trying Ubuntu on the Dell A2010 (an all-in-one desktop) for a couple of releases.  Now, Karmic shows great hope.  Using the Karmic Alpha3 i386 Desktop iso installed on a USB stick (by 'usb-creator'), I had the following results on my Dell A2010:

1.  The wired internet connection was active at boot up.  The wirelss internet connection was not active, and I did not try to activate it.  It is a Broadcom device and should work with a little effort.

2.  The Bluetooth keyboard and mouse were detected and operated normally at boot up.

3.  The audio device was detected and the speakers worked although at full volume at boot up. Lowering volume on the panel worked.

4.  The display was detected and worked normally except that its lamp was at full brightness and the dimming key did not reduce the lamp's intensity.  Adding the "brightness applet" to the panel worked.

5.  All these things were remembered by the "persistence" file in the USB stick, and using the stick would be a (bit cumbersome) way to get Ubuntu on the A2010.

This release of Ubuntu seems to be a good candidate for the A2010.  It would be soooo grand to escape Windows on the A2010.

Then I tried installing Karmic "inside" Windows Vista with WUBI using the version of WUBI distributed with the Karmic Alpha3 Desktop i386 CD.  All seemed to go well, taking only a few minutes to complete the task and request a reboot.  But when the Windows-Ubuntu selection window came up and I selected Ubuntu, it did not boot -- just returned to the BIOS flash screen followed by the selection screen again.  Windows boots as normal as ever.

WUBI's Wiki says try running "chkdsk /r" from the Windows side.  Took forever, said it repaired a few flaws, but Ubuntu still did not boot.  Then I checked for files "C:\ubuntu\disks\root.disk" and "C:\ubuntu\disks\boot".  The files are there, but the boot folder is empty.  That may be serious.

I chose the WUBI install because I did not want to destroy the "Restore to Factory Condition" application which comes from Dell.  While I have completely removed Windows from 4 other computers, I am not just yet ready to remove Vista from the A2010.  I know, I know, "The Devil Hates a Coward."  Maybe I should learn more about the Windows application which allows editing the Master Boot Record.

Are there any ideas out there?  Would a second attempt at running WUBI be likely to make any difference?  Any one else try Karmic on the A2010?

---

### Post by psyke83 on 2009-08-04
Installing via WUBI is not the primary focus on testing at this stage, so it's not guaranteed to work until later in the development cycle.

---

