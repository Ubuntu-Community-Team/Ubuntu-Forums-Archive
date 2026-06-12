---
title: "Failed to start X Server error while installing on my ThinkPad"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by eman245 on 2007-06-21
I have a brand new ThinkPad T60 that I wanted to dual boot. So popped in the live CD and it seemed to boot fine until it gave me the error:

"Failed to start the X Server (your graphical inerface). It is likely that it is not set up correctly..."

The error report says "Fatal server error: Caught signal 11. Server aborting"

I have read some other forum posts which recommended using "sudo dpkg-reconfigure xserver-xorg" to reconfigure the file and temporarily change the driver to vesa, but that didn't work for me. After I restarted the gdk I got the same "Failed to start the X Server" error. I've tried to reconfigure using both the ati and vesa drivers, neither works.

I have a 256MB ATI Mobility FireGL V5250 graphics card.

Any suggestions on what I can do would be appreciated...
Also, I'm kind of a noob at linux, so you might have to explain a little bit...
-Thanks

---

### Post by palisaide on 2007-08-20
I too am getting the same Fatal Server Error on a Thinkpad T60.  Any advice would be greatly appreciated.  Thanks!

---

### Post by Deramin on 2007-08-20
boot into the bios and change the raid driver to computability mode. This worked on a t61. I'm not 100% sure if the same will hold true on a t60, but it's worth a shot.

---

