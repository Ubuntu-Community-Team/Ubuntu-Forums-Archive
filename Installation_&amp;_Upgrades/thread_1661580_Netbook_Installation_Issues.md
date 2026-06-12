---
title: "Netbook Installation Issues"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by Germbat on 2011-01-06
First, let me apologize if this has been posted before.  I've searched for this subject a few times, but it seems people are having slightly different issues.

I decided to install Ubuntu on my old Toshiba NB205 netbook.  I follow all the instructions *TO THE LETTER*,yet I'm still having problems.

***_Problem #1_***
- Unless I'm pressing the enter key, it doesn't appear to be setting up the installation.  The light on my USB drive will only light up if I'm on the enter key.  Not really that big of an issue, just a minor inconvenience is all...

***_Problem #2_***
- Installation seems to go rather smooth.  I see the correct screens (pick my language, keyboard, timezone, etc.) and I even get the dialog box that the computer needs to reset.  Cool, alright so far.  Now for the issue: nothing happens.  After minutes of waiting for Ubuntu to boot up, I see this lovely error message:

> Gave up waiting for root device.  Common problems:
- Boot args (cat /proc/cmdline)
  - Check rootdelay= (did the system wait long enough?)
  - Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT!  /dev/disk/by-uuid/b89e9502-9b8c-436c-b983-a5d6d40fc07c does not exist.
Dropping to a shell!

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs)


***_Problem #3_***
- What's really bothering me is that I'm able to run Ubuntu through the USB just fine.  Now granted, it does seem to take a long to boot up and run, but at least it does it.  I'm almost angry about it really.  I can run Ubuntu just fine through the USB, but not from the hard drive?!  Grr...


Yes, I'm a total noob when it comes to Linux, I'm sorry.  I'm just getting into it, and I want to learn more.  

So, there you have it.  Any help would be greatly appreciated.

Just a quick note: I have tried installing both the desktop *AND* the netbook versions, each with the same end result (problem #2 of nothing happening).

Thanks.

---

