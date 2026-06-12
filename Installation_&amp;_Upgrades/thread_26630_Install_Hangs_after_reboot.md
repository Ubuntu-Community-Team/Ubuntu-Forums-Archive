---
title: "Install Hangs after reboot"
date: 2005-04-13
forum: Installation &amp; Upgrades
---

### Post by txwylde on 2005-04-13
I am installing Ubuntu on a Dell Optiplex GX110 with 256 Megs RAM. It goes through the process fine with installing the software. I walk through setting up users and it tells me to remove the CD from the CDROM. It reboots, continues to go through the install and then locks up with a "-" in the upper left hand corner. I am not sure why it hangs on this spot. I tried reinstalling and watched it as it installs and it does the same thing. Any ideas?

---

### Post by RuKK on 2005-04-13
The exact same thing happens to me on a celeron 700 system I just built. I figured it was something with the fact that I turned off onboard graphics and am using a sis pci video card, and I've been trying to get to a command line so that I can try and fix the xorg.conf file. Finally I booted up damnsmall as a livecd and saw that there is NO xorg.conf file in /etc/X11/. Am I looking in the wrong place, or has it just not been generated until the first time I run X? Any ideas at all?

//edit for a little more info: I cant ctrl+alt+f1 f2 f3 etc. I can turn numlock on and off as well as capslock, I've left it in this state for over 4 hours and it doesnt do anything. I cant ctrl+alt+del or ctrl+alt+backspace either. I've tested the machines stability for over 24 hours and I have booted knoppix and damnsmall on it, so its not hardware failure unless its something truly bizzare. Help?

---

### Post by RuKK on 2005-04-13
Thanks to jintxo in #ubuntu, I have a fix for you.

Hit esc when grub first loads so that you get a menu with boot options in it. Select your normal ubuntu with arrow keys and hit e to edit it. Select the line that boots the kernel and hit e again to edit it. Add the command single to the very end of that string and hit enter. Now hit b to boot ubuntu. You should get a root command line if you did everything right. Now go lspci -X to display your devices and where they are on the bus. Pick out the video card your using from the list of hardware and make a note of its PCI:*:*:* address. Mine, for example is PCI:1:0:0.

Now go nano /etc/X11/xorg.conf and scroll down to the "device" section. change the busid to whatever your video card is at, and set the driver to whatever is correct for your video card. If you dont know, "vesa" should work fine until you can find out. If you change the device's identifier, make sure you change it to the same thing under the "device" section of "screen" as well. Now (in nano only) go ctrl+o to and hit enter to save your changes. Then ctrl+x to exit nano. Now type exit and you should be booted into runlevel 2 and GDM should load. You may have to kill it once with ctrl+alt+backspace if your image is all garbled the first time around, but the second time it loaded perfectly for me. Good luck and enjoy!

---

