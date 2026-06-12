---
title: "Able to login to guest desktop but not my own?"
date: 2014-11-14
forum: Installation &amp; Upgrades
---

### Post by memilanuk on 2014-11-14
So... Ubuntu 14.04LTS running on Lenovo ThinkPad T530 w/ built-in Intel video and NVidia n5400 Optimus video, dual-boot with Win7.  Didn't do anything special for the NVidia bits, as I don't typically use them.

Recently rebooted into Win7 for something, and when I booted back into Ubuntu, I reached the lightdm login screen, entered my password and... nothing.  Just the default bruised-meat-looking purple background with the Ubuntu 14.04LTS logo in the lower left corner, and a mouse cursor.  Nothing else, nothing works besides Ctrl+Alt+F1 to switch to tty1, where I can login normally.

Ran 'sudo apt-get update' and 'sudo apt-get upgrade' to make sure everything was updated (there were some packages that needed updated), and tried again.  Same results.  Tried selecting 'Advanced Options' and then trying other older kernel versions from grub - nothing changed.  Tried booting from the failsafex option - that just hung on fsck until I hit ctrl+alt+del, where it finally took off - right before the system rebooted.  Tried it again, waiting longer - nope, system still hung up on the fsck indefinitely until I did the three-finger-salute.

Did some more reading, and tried 'sudo apt-get install nvidia-current nvidia-current-updates' and rebooted again.  Still no change.

This time, on a lark, I clicked the Guest login at the lightdm prompt.  It brought up the desktop just fine!

So any ideas what the heck is going on that I can bring up the guest desktop but I can't log into my own?

---

### Post by memilanuk on 2014-11-15
Got some help on #ubuntu in the wee hours of the morning yesterday... tried running ccsm, tried doing a number of things, but nothing seemed to work.  Finally it came down to deleting a folder in my home directory - ~/.cache/upstart.  After that, everything worked as it should.  Never did get a clear answer on why there was an upstart folder in my user directory (thought upstart was a system level thing) and how it would b0rk my gui login... if anyone reading this has a answer for either of those, I'm listening...

---

### Post by mörgæs on 2014-11-15
Thanks for an attempt at marking the thread solved, but please use Thread Tools.

---

