---
title: "Where to download Proprietary Hardware Drivers?"
date: 2011-12-28
forum: Installation &amp; Upgrades
---

### Post by wkulecz on 2011-12-28
I've cloned a Ubuntu 10.04 system drive for use at a remote location without Internet access, but its video card needs a different version of the Nvidia driver than the one used in the original system.

Where can I find the files that the System->Administration->Hardware Drivers tools downloads and how would I install them?

The Ubuntu way has automatically worked very well and is much preferred, but for this system I'll need to do it the "hard way" :(

I assume there is other stuff going on in the Hardware Drivers tool as what it offers depends on the video card in the system its running, I'd need to manually do the equivalent.

---

### Post by kalfusisagod on 2011-12-28
Nvidia's website has great linux driver support. Just goto [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us) and select your video card along with 32/64 bit Linux. I haven't had a chance to actually test out the Linux drivers because I'm running a Ubuntu virtual machine which masks my GTX460M from Linux. 

I'd go to the site, download the 32 and 64 bit .run file and throw it onto a thumbdrive. Then goto the system that needs the driver, and mount the stick and run the file. Hope this helps.

---

### Post by wkulecz on 2011-12-28
Thanks, that's a start, but I'm having trouble mapping the drivers to the actual cards.  The Hardware Drivers tool does this automagically.  The three options it offers would likely be all I need for the forseeable future:

Current (recommended) 195
174
93

Going from memory on the numbers, since the system I'm on now only offers the 195 current driver as an option.

I've set up about ten of these cloned systems and the "Recommended" 195 driver works for most of them, this is only the second time I've hit this and most inconvienent since I've no network access for this system :(

---

### Post by kalfusisagod on 2011-12-28
When I ran the .run file, it threw me into the CLI but I couldn't go past the first few screens because of my VM. Not sure how you can map drivers to the cards but it *might* show up in hardware drivers when installed with the propriety NVIDIA ones

---

