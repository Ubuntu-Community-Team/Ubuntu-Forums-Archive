---
title: "After Upgrade to 11.10 - Start Up Hangs - Can Boot Into Desktop From Recovery Mode"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by The Sunburned Surveyor on 2011-10-18
I tried the automatic upgrade from 11.10 a couple of days ago. (I'm running Ubuntu on my Dell Desktop. I've been using Ubuntu on this computer for several years with few problems.)

During or shortly after the installation the computer locked up with a black screen. (The mouse cursor was visible.) After I restarted the computer it would hang on the Ubuntu 11.10 splash screen.

I was able to successfully get to a command prompt when I booted into recovery mode from Grub. Once there, I can get into the GNOME desktop using "sudo startx".

I also ran dpkg to complete any updates that didn't finish during the install, which appeared to complete without problems.

I still get the hang at the splash screen.

I'm downloading and burning a 11.10 disk today. However, I'd like to try to fix this problem before I do a reinstall from CD. I think I would learn more that way.

Is there any way I can find out what is causing the hang on start-up from the command prompt in recovery mode? (I'm not a Linux expert, but I know enough to be dangerous, and I've got some programming experience.)

If this is a waste of time, just tell me, and I'll reinstall. Hopefully I can do this in a way that preserves the files in my user directory under /home.

Here are some error messages I'm getting.

When logging into the GNOME desktop using "sudo startx" the following two (2) messages are displayed:

"Could not connect to WICD's D-Bus interface. Check the WICD log for error messages."

"The WICD daemon has shut down. The UI will not function property until it is restarted."

Note: I uninstalled WICD from the recovery mode command prompt using apt-get, and I still get these two messages when logging into the GNOME desktop. I was using WICD before the update to log into my wireless internet connection.

During a normal start-up, this message is displayed before the hang on the splash screen:

"* Checing Battery State [OK]"

I've got a NVidia graphics card installed. 

Thanks for the help.

The Sunburned Surveyor

---

