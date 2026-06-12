---
title: "Dual boot failure of 13.04 Studio and Windows Starter"
date: 2013-08-22
forum: Installation &amp; Upgrades
---

### Post by skyemoor on 2013-08-22
Dell Inspiron Mini 1012
Intel Atom N450
BIOS A11
2G mem
250G HD
Windows 7 Starter
13.04 Ubuntu Studio 386 32 bit 
unetbootin

There was no "Try Ubuntu first"

The install went well, and the guided partitioning was easy, I freed up 100G for the Ubuntu load.

SCSI1 (0,0,0) (sda) - 250 GB ATA Toshiba MK2565GS
  #1 Primary 41.1 MB     fat16
  #2 primary 15.7 GB B  ntfs
  #3 primary 108 GB      ntfs
  #4 logical   124 GB     ext4
  #6 logical    2.1 GB  F swap  swap
  

When it came time to "select and install software" (or something like that) that were above and beyond the core, I selected all of the video/music/graphics/photo studio package sets.

It then came up with a "Fail" page, suggesting I retry or otherwise finish the install.

I removed the 1st package and tried again. Failure.

I removed all the studio packages and continued. Failure.

I decided I would load them later, and finished the install (which then went very smoothly). I loaded Grub in the MBR, as it suggested.

I rebooted and the menu came up to the selection of Ubuntu or Windows, I tried Windows.

Screen blanked, and the cursor hung halfway down the left side. After waiting a long time, I hit the power button.

What appeared to be a shutdown script ("acpid exiting")started looking for unattended update scripts, then executed a few more lines then turned off.

I rebooted and tried to start with Ubuntu Studio this time, but the same result occurred.

I retried several times, with and without the USB drive inserted. Same results.

I ran diagnostics, and everything checked out.

I booted from the USB and tried "Help", which took me right back through the Install process.

I tried booting from the USB in Rescue mode and ended up with basically the same result as "Help"

I then tried booting from the menu with the Ubuntu Recovery mode, and it ran through a blitz of instructions, eventually putting my at root at a command line. I haven't run real Unix in 20 years (and even then just barely knew how to find my way around), so didn't know what to do, but thought that it was a sign that *something* wasn't altogether wrong.

Where have I gone wrong and what should I do?

---

### Post by skyemoor on 2013-08-22
It turns out if I'm fast enough, I can select the Windows option and it *does* now boot to Windows. 

Still no luck booting Ubuntu Studio, though

---

### Post by BazBear on 2013-08-22
Have you tried F5,8 whatever (it varies by vendor, never owned a Dell, I'm sure it's Googleable) when the machine's on it's Dell boot screen to get to the BIOS boot options? At least you'll be able to use your Windows installation (I'm also assuming it's Windows 7 starter), and maybe fix the other issues from that side. Just a thought.

Edit to add - A Google search indicates F8 seems to be the key you want, also keep tapping it through the boot process.

---

### Post by skyemoor on 2013-08-23
F12 gives the boot options, which is only where I want to to boot from. 

I did try F8, and it seems to show the execution of a script, which goes on and on like the following;

* Stopping cold plug devices             [OK]
* Stopping log initial device creation   [OK]
* Starting configure network device security [OK]
    art  configure network devices
    opp  ...
    art  mount network file systems
    art  ...
    art  Sys V initialization compatibility 
    opp mount network file systems
Checking for running unattended-upgrades:
* Stopping Failsafe Boot Delay
* Stopping Sys V initialization compatibility
* Starting Sys V runlevel compatibility
* ...
fsck from util-linux 2.19.1
/dev/sda5: clean ...blocks...files
* Starting configure network device security
* Starting mount network file systems.
(etc, etc)

The last 8 lines are a repeat of the "Checking for running unattended-upgrades" set above

If I hit the power button, it then says:

"acpid exiting" and then goes through a shutdown in a few seconds.

Why is it hung? What do I need to do?

---

### Post by BazBear on 2013-08-23
Sorry, I had missed your second post that said you already could boot into Windows. Have you checked out this [thread]("http://ubuntuforums.org/showthread.php?t=1769482")?

---

### Post by skyemoor on 2013-08-23
> **BazBear said:**
> Sorry, I had missed your second post that said you already could boot into Windows. Have you checked out this [thread]("http://ubuntuforums.org/showthread.php?t=1769482")?

That thread says, "Boot-Repair can be installed & used from any Ubuntu session (normal session, or live-CD, or live-USB). "

I cannot boot into an Ubuntu session other than Rescue mode that only gives me the command line.

Update: I'm trying an alternative to unetbootin through Startup Disk Creator on another US13.04 machine, though it has crashed.

---

