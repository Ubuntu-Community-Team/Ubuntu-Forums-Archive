---
title: "Problems after upgrading Lubuntu 16.04 to 18.04.4"
date: 2020-03-07
forum: Installation &amp; Upgrades
---

### Post by Brent_Santin on 2020-03-07
I recently upgraded from Lubuntu 16.04 to 18.04.4, but the upgrade didn't go entirely smoothly.

Problem 1: In the Lubuntu "Software & Update" tool, after selecting the "Other Software" tab, I can see but no longer check and uncheck repositories do disable/enable them. Nothing happens when I click the checkbox.

Problem 2: I now have both a "System Tools/Software Updater" icon and a "Preferences/Software and Updates" icon in my shortcut menu, and they both start the same "check for updates" utility.

Problem 3: The Synaptic Software Center icon is in my shortcuts menu, but it will not start, the cursor just stays at "busy" (spinning) without it loading. This is what I get when I try to start it from the command line:

> ==== AUTHENTICATING FOR com.ubuntu.pkexec.synaptic ===
Authentication is required to run the Synaptic Package Manager
Authenticating as: Brent,,, (brent)
Password: 
polkit-agent-helper-1: error response to PolicyKit daemon: GDBus.Error:org.freedesktop.PolicyKit1.Error.Failed: No session for cookie
==== AUTHENTICATION FAILED ===
Error executing command as another user: Not authorized

This incident has been reported.

Problem 4: There is no Lubuntu "app store" available anymore. The Software Center or "Software" option in my shortcuts (applications) menu. So without Synaptic or the Lubuntu Software app "store" I have no way of downloading or removing software through the GUI.

Problem 5: When I first turn on my computer, after the BIOS bootstrap screen I see a quick flash of a phrase "ERROR: NO SYMBOL TABLE" at the top of a black screen, then it goes into the early startup menu where I get to choose to boot from "UBUNTU" [even though I have Lubuntu - but this is normal] or "WINXP". Missing are the old options for the MEMTEST, etc. Then when I choose UBUNTU, it goes to a black screen which says at the top "Press ENTER TO CONTINUE...." (With the E and part of N cut off). I don't actually have to press enter or anything, it still seems to boot, however.

Can anyone please help?  Thanks.

---

### Post by Brent_Santin on 2020-03-07
Problem 1 seems to have resolved itself after logging out / in again several times after changing Policykit setting (see solution for Problem 3 below).
Problem 3 fixed by starting Peferences/Default Applications for LXSession, choosing Autostart and check-marking "Policykit Authentication Agent".
Problem 4 fixed by issuing the command: sudo apt install gnome-software

Problem 5 remains.

---

### Post by mörgæs on 2020-03-09
This seems like typical problems related to upgrades. 

Lubuntu has abandoned the LXDE GUI from the 18.04 days and uses now LXQT. If it were my system I would let go of the 16.04/18.04 hybrid and do a clean install of 19.10.

---

