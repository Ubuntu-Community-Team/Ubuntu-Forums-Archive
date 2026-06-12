---
title: "Install Ubuntu 11.10 on AMD 3850 and ATI 6570"
date: 2011-10-18
forum: Installation &amp; Upgrades
---

### Post by matismasters on 2011-10-18
This is my hardware:

Asus F1A75-M
ATI Radeon 6570
AMD A3850 (with APU)

I downloaded the Ubuntu ISO from Ubuntu download page, burned the Image, and Installed it, with the option for download updates checked. What I did get was a screen with about 10 pixels at the top where I could actually see the mouse moving, and the rest of the screen in black. CTRL + F1 take me to a black screen too.

Then I reinstalled Ubuntu, using the option to "Update ubuntu 11.10 to Ubuntu 11.10" from the installation menu, this time without checking the option to download updates. Everything worked out, I was able to log in, without graphic drivers. Then I moved to install the graphic drivers. After some Issues with emacs installation, and a very very slow wired connection, I activated the propietary drivers that didn't have the (post-release updates), because that ones ended with errors. That actually worked out, and in Sys info I got VESA: TURKED, or something like that.

Graphics acceleration didn't work out, so I tried downloading the Drivers from AMD, Catalyst 11.9. It asked to uninstall the current drivers, so I did using purge. And then I couldn't not log into the system. Logged in recovery mode, and installed the new driver that I just downloaded. Now the screen shows FAIL, in an OpenGl library, and stops at all in the line that says, Checking battery status.

My questions: What should be the proper set up for this Hardware?
How do I make Ubuntu use the default drivers, that has no acceleration?

THX.

---

