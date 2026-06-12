---
title: "How could i enter ubuntu with basic video mode at the time of installation?"
date: 2013-03-08
forum: Installation &amp; Upgrades
---

### Post by 50shashwat on 2013-03-08
I want to start linux so my best choice was with ubuntu. But i got struck in installation procedure, ubuntu fails to start display compatible with my graphics (nvidia 9200 M G integrated/ no intel HD). After its logo of ubuntu it freezes, even on terminal(ctrl+alt+f2) when i start to type xandr.. (for revering display from 1280*800 to 1024*768) the command of nouvou fails channel2, channel3 (here is picture [IMG]http://softwarehome.tk/linux/nouvou%20fails.jpg[/IMG])
then it starts a series of these commands followed by distorted display as shown below

[IMG]http://softwarehome.tk/linux/distorted%20display.jpg[/IMG]

So i am not able to type anything in terminal and besides this some of the commands may require sudo privillege (i have not installed yet to enter username or password).

Best solution i could find for this yet:
At the installation boot screen (On fedora 17 and fedora 18) on pressing ESC it ask me either to enter fedora normally or in basic video mode (Basic video drops screen resoltuin to 1024*768 but it manages to start fedora easily). But i want to install ubuntu. Is there any way we could get the same option to appear at boot screen. (remember i am not able to get through any sort of terminal of ubuntu)
I need solution to this.

---

### Post by MAFoElffen on 2013-03-09
With Nvidia-

With the LiveCD. First panel is a augerine (blackish/purple) panel with a keyboard/person icon at the bottom. Press a key. Low res language box wil pop up. Press <enter>. You will be at the Advanced Install menu. Arrow to highligh the selection you want to do. 

Before leaving that menu, press <F6>. Arrow down to "nomodeset" press <enter>, <esc>. Back at the Advanced Install menu, press enter.

After the install, when it reboots, just atfer the bios messages, press the left <shift> key. At the grub menu, press an arrow key to stop the menu from disappearing. Press the <e> key to get into edit mode. <Arrow-down> to the line the starts with "linux". Arrow over to just after where is says "quiet splash" and before "$vt_handoff" and type in "nomodeset" (without the quotes). Press <cntrl><X> to boot.

When the GUI starts up and you get into the desktop, make sure you install your nVidia driver.

If you need more info, details or pictures, vist my Graphics Resolution sticky (link in my sig line). First half of post #3 has the LiveCD Instructions. Post #2 has links to how to temporarily edit the grub menu and links to install nVidia drivers.

---

