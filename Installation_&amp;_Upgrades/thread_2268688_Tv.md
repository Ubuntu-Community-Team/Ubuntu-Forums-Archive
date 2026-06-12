---
title: "Tv?"
date: 2015-03-10
forum: Installation &amp; Upgrades
---

### Post by katrina3 on 2015-03-10
Hi 
I have just installed 10.04 and then upgraded to 12.04..
On rebooting i was offered the latest Nvidia driver the recommended one , so i chose to install it.
On rebooting , which went fine , i changed my resolution to the next one below ...something like 1024 .
I have my Notebook attached via HDMI cable to my TV.
On resetting the resolution the screen went blue 
Rebooting didnt fix the problem ,  just blue screen.
Other attempts , on removing the HDMI cable have thrown up a message ...which i cant remember , sorry.
Now when i reboot it goes into the screen where it asks for user ID and password...then it goes to the curser....what am i suppose to do from there.

I tried the boot in safe graphic mode but that also came up with errors. any help would be appreciated , thank you. :mad::mad::mad:

---

### Post by grahammechanical on 2015-03-10
"Errors" is not at all helpful. The wording of errors can be useful in determining what is wrong. I can only guess that there is some kind of a video driver problem. I am assuming that you get a Grub boot menu. Select Recovery mode and at the recovery menu select Resume. That may get you to a desktop and from there you can use Additional Drivers to change video drivers.

I am also guessing that the screen with the user ID and password is actually a black Linux command line. At this point Ubuntu would normally login in your name and load to a GUI login screen or directly to the desktop depending on whether you have automatic login selected. The failure of Ubuntu desktop to take over from Linux may be related to the video driver problem but may be not.

Here is some information. When Linux loads it queries the screen to get the manufacturer's recommended screen resolution. Now, in your case is this the resolution of the notebook screen or the resolution of the TV?

I suggest that you only use the notebook screen until this problem is fixed and then connect the TV and then run the Nvidia Xserver settings manager to detect displays so that the OS knows it has a choice of displays.

You may have selected a setting that was compatible with the notebook screen but not compatible with the TV screen.

Regards.

---

### Post by papibe on 2015-03-10
Hi katrina3. Welcome to the forum ):P

Boot normally so you can login in text mode.

Once you get a prompt, run this commands:
```
sudo rm -f /etc/X11/xorg.conf

rm -f ~/.nvidia-settings-rc
```
That should remove any graphic setting you had.

Now reboot the computer by running:
```
sudo reboot
```
Hope it helps. Let us know how that goes.
Regards.

EDIT: if that works OK, from now on, use 'Nvidia X Server Settings' to set any graphic settings including the netbook display and the TV over HDMI.

---

### Post by SeijiSensei on 2015-03-11
If I might ask, why did you go through the process of installing 10.04 then upgrading to 12.04, when you could have installed 14.04 in the first place?  On new installations, that's the version you should be using.

---

