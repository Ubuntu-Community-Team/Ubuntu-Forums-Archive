---
title: "Upgraded my Ubuntu installation to 10.04 and now it won't log in"
date: 2010-11-09
forum: Installation &amp; Upgrades
---

### Post by steiner470 on 2010-11-09
Upgraded my Ubuntu installation to 10.04 and now it won't log in. When the system boots up it says 

"Ubuntu is running in low-graphics mode. The following error was encountered. You may need to update your configuration to solve this. (EE) NV(0): No valid initial configuration found. (EE) Screen(s) found, but none have a useable configuration"

"What would you like to do
- Run Ubuntu in low graphics mode for just one session
- Reconfigure Graphics
- Troubleshoot the error
- Exit to console login
- Restart X"

Then I can get to the login screen and attempt to login but the screen just flashes black and then returns me to the login screen again.  I know the password is correct because if I type in a different password it says "Incorrect Password."

 The symptoms are exactly as described here:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/589520](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-openchrome/+bug/589520)

I tried changing my /etc/X11/xorg.conf to read
Section "ServerFlags"
    Option "AIGLX" "off"
EndSection

And that makes the error message dissapear on bootup but it will still not login. How can I fix this?

---

### Post by dino99 on 2010-11-09
your problem is: 

**** (EE) NV(0): No valid initial configuration found. (EE) Screen(s) found, but none have a useable configuration"
****

so remove xorg.conf , actual kernel directly deal with X anyway

sudo rm -f /etc/X11/xorg.conf

then reboot and check driver activation (system admin additional driver)

---

### Post by steiner470 on 2010-11-09
> **dino99 said:**
> your problem is: 

**** (EE) NV(0): No valid initial configuration found. (EE) Screen(s) found, but none have a useable configuration"
****

so remove xorg.conf , actual kernel directly deal with X anyway

sudo rm -f /etc/X11/xorg.conf

then reboot and check driver activation (system admin additional driver)

Thanks for the idea but I don't think that can be correct. The reason I say this is because /etc/X11/xorg.conf already did *not* exist during the time this error was occurring. And as I stated I tried to troubleshoot the problem by creating the file /etc/X11/xorg.conf with the following contents: 

Section "ServerFlags"
    Option "AIGLX" "off"
EndSection

That stopped the error message from appearing at bootup however the system still will not login to either normal Gnome or Failsafe.

---

### Post by steiner470 on 2010-11-09
Update: I ran through the instructions on this page ([http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html](http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html)) to remove and reinstall xserver-xorg but it did not help.
I did notice however that the command sudo apt-get remove --purge xserver-xorg did NOT remove or alter the /etc/X11 directory or any files within it.

---

