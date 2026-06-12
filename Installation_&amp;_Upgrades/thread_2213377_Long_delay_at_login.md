---
title: "Long delay at login"
date: 2014-03-26
forum: Installation &amp; Upgrades
---

### Post by frankdn01 on 2014-03-26
I used the upgrade utility to bring my Dell laptop from 13.04 to 13.10, and the upgrade completed without a hitch.

But now when I boot (and booting to the login screen is right quick, thanks!), progress just stops at the login screen.  The disk is almost continuously busy, the WiFi icon is lit more than it's dark, the login dialog appears, but the blinking 'I' never appears so I can't enter my password.  I've let it run for more than 5 minutes.  I once let it run for an hour and when I came back, the login box was finally activated, I logged in and the system seemed to run fine.

What the heck is Ubuntu doing, that it takes so long to get to login?  What log file might give me a clue, after I wait the requisite hour?

---

### Post by grahammechanical on 2014-03-26
You are confusing me. You say that booting to the login screen is "right quick" but then you speak of waiting for something like an hour before the login screen is "finally activated."

Do you have alternative desktops installed on this system? There could be some kind of conflict between configuration files that Ubuntu (actually LightDM) is taking some time to resolve. Many users?

Regards.

---

### Post by buzzingrobot on 2014-03-26
Blinking 'I' = mouse cursor??  The login box appears but when you click in the password field the field doesn't get the focus (display the mouse cursor)?  But, you can login after a very long wait?

---

### Post by frankdn01 on 2014-03-28
Yes, I apologize for not knowing the correct terms.   What I'm seeing is this: the boot appears to go normally right up to the point that the login box appears, but then begins a very long wait (up to an hour) before the mouse cursor appears.  Meantime, the disk is almost continuously busy and the WiFi light is on more than it's off.

Eventually the cursor does appear and I can log in, and the system behaves as it did under 13.04.  I suspected there might be a circular loop of symbolic links and booted to siingleuser (which went fine) and fsck'd the disk, but no errors were found.

I did the 13.04->13.10 upgrade using the upgrade utility and accepted all the defaults as the process completed without difficulty.

---

### Post by buzzingrobot on 2014-03-28
No problem.  I don't upgrade in place, though, so at this point I can only offer generic advice.

The system should be returned to as close as its default status as possible before an upgrade to a new release. If any PPA's weren't purged, you might look in that direction.

Something is causing the disk activity, and something is causing the wifi activity.  Might be the same thing, might not be.  The fact that the system eventually comes up could indicate that it is repeatedly trying something, and eventually letting it time out.  One thing it *might* be unsuccessfully trying is establishing a net connection. If you are able to turn off your wifi card, or disable it temporarily in the BIOS, reboot and see what happens. If it boots normally, then you've probably located the problem.

---

### Post by frankdn01 on 2014-04-01
Well, lightdm appears to be the culprit.  (Booting with the WiFi transciever swiched off did nothing.)

Background: I have a cleanup script that I usually run when logging out.  It makes heavy use of srm which is a slow process, and it often takes many, many minutes to complete; I added 'shutdown now' at the end and usually just start the script and walk away.  What I had forgotten was that in my long-ago attempts to get unity/lightdm to run this script, I added a session-cleanup-script entry to lightdm.conf; but this actually did nothing under 13.04.

In 13.10, however, lightdm is now running my very time-consuming cleanup script.  At startup.  ;)

Turns out, this is a reported bug (# 1249515).  Deleting the cleanup line from lightdm.conf "solved" the problem.

(**Thank you **for helping!)

---

