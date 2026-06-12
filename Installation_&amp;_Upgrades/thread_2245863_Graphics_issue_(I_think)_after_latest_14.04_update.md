---
title: "Graphics issue (I think?) after latest 14.04 update"
date: 2014-09-26
forum: Installation &amp; Upgrades
---

### Post by jafoti on 2014-09-26
Ubuntu n00b/student/curious manchild trying to resolve issues with the latest 14.04 update.

Today I went through the latest update push for 14.04 on my box.  Nothing fancy, 3.40 GHz core i5, 8GB RAM, no 3rd party audio or graphics cards.  After the upgrade my machine started to perform "less than optimally."  What research I've done points to issues with graphics drivers, but they appear to be centered around nVidia (or other third party) drivers.

What is happening:

- Clicking on icons on desktop to start programs results in the "spinning wheel" and then the program *maybe* opening after 1 minute
- Once a program does open, like Firefox, any typing in the search field or address window can take over a second per letter to appear.
- If I manage to get a program open like System Monitor, attempting to switch tabs in the window can make it dim for a prolonged period then freeze the screen for at least a minute before finally switching views.
- System Monitor shows no high CPU usage at all.
- Memory test from boot passes all tests.
- HDD indicator light staying lit for prolonged periods (> 1min) when experiencing screen freeze.
- HDD sounds like it's trying to read every 2 seconds, I can hear what sounds clicking of read heads.
- Terminal mostly works fine, but can be subject to screen freeze at times, like when trying to execute **sudo lshw** or **apt-get update**.

I have rebooted, then rebooted into safe mode and cannot resolve the issue.  

I have tried:
- Fixing broken packages in Safe Mode after enabling networking in Safe Mode
- Booting in failsafe graphics mode, seems to just bring me back to Safe Mode menu.

After booting normally from Safe Mode menu, I can see a "fail" message when trying to start rollback graphics.  I do see one or 2 other "fail" messages, but they scroll off the screen too quick for my older eyes to capture.  Is there a way to capture these messages?

I'm not familiar enough with Ubuntu to have a decent idea of where to start troubleshooting.  Not looking for all the answers, just a place to start.  If someone could provide that, I'd appreciate it!

---

### Post by jafoti on 2014-10-02
I believe I've found an issue with the Unity desktop.  When any attempt is made to upgrade this, I experience all the symptoms I listed in my first post.  This happens both when I uprade via Software Update or command line.

Any attempt to install another desktop package like lxde results in this - "dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."  

Executing **sudo dpkg --configure -a** just hangs and ties up the HDDn and I'm back at Square 1.

---

