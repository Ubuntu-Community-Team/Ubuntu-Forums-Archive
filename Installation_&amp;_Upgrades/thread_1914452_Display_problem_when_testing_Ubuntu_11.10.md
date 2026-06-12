---
title: "Display problem when testing Ubuntu 11.10"
date: 2012-01-24
forum: Installation &amp; Upgrades
---

### Post by joelstitch on 2012-01-24
I have Ubuntu 11.10 on a USB drive and I boot from it just fine but the display looks all weird. I have a HP Pavilion dv6629us with a NVIDIA GeForce 7150m. I have the same issue when I boot Lucid bot on Lucid Im able to download the driver from **Administrator>Hardware Drivers** but for some reason on 11.10 it doesnt list the NVIDIA driver. I tried installing the DEB file but the Install button is alway unclickable. Any ideas?

---

### Post by Gstrazds on 2012-01-26
Hi there... Your notebook screen is not syncing. You need to select a lower resolution or sync speed 60hz.. or use the generic driver 

report problem to [https://answers](https://answers).**launchpad**.net/**ubuntu**/+**questions**


I have nvidia - it makes front window go blank if there are to many open windows.. 

Glenn

---

### Post by The Almighty Plum on 2012-04-11
I get the same problem. Has anyone found a solution?

---

### Post by The Almighty Plum on 2012-04-20
No one has found a solution for this?

---

### Post by keforex on 2012-04-20
Same problem here. I have a NVIDIA GeForce 8800 GTX and I can't even install these last two versions (11 and 12) of ubuntu. The screen will flicker and I can't see anything. Upon using the "nomodeset" parameter at booting the install disk, I can install ubuntu, but after starting using the restricted nvivia driver to get to the correct resolution, nothing behaves correctly. The mouse won't move, no menus, etc...

With older versions of ubuntu I have no problems at all. What gives?

---

### Post by DraganDragon on 2012-04-20
Im having the same problem. I have a list of NVIDIA graphic drivers and none of them are activated. I tried activating one last night when i just installed linux and when my comp started up my screen was black and white stripes, i had to re install it. Works fine since i havent updated those drivers but im wondering if here is a solution to it?

One of them says " NVIDIA accelerated graphics driver (version current) [Recommended] " but im still not sure if i should activate it?

---

### Post by keforex on 2012-04-22
An update:

I installed ubuntu using "nomodeset" and choosing to download updates during the install.

After the install and reboot, I was able to see the desktop in the native resolution of my screen (2560 - 30 inch monitor) but the screen doesn't work right.

The mouse pointer stops/goes in a pattern as I try to move it around. After clicking, there is a long delay to the action to happen on screen. A simple click on any icon, or any context menu, causes the freezing of the mouse pointer for about 15 seconds.

I can use the system, but it is just not functional, and it's annoying.

My take on this is that maybe the window manager is having issues with this latest nvidia driver.

Until this issue isn't solved, either by ubuntu or nvidia, the OS is unusable.

I wish I could use 9.10 with its original nvidia drivers from the past. It was easy, lightning fast, and I had my two 30" monitors working as one giant desktop without any issues whatsoever.

For the record, my nVidia card is a dual DVI GForce 8800 GTX.

I hope this issue is resolved soon.

---

### Post by keforex on 2012-04-22
And another update:

Decided to install Open Suse (latest 64bit version) and the problem is exactly the same, BUT..... I was able to go systems settings --> Desktop Effects and UNcheck the option called "Enable desktop effects at startup" -- that solved it. Now I can use the computer as usual.

The only reason I found this out is because Open Suse gave me a warning that said "effects don't appear to be working properly, they were turned off. You can choose your preferences on system settings->Desktop effects".

So.... My guess is that the problem is with Compiz after the new nVidia driver.

---

