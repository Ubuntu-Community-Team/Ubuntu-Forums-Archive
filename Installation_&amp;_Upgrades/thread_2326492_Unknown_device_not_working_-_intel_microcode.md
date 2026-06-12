---
title: "Unknown device not working - intel microcode"
date: 2016-06-01
forum: Installation &amp; Upgrades
---

### Post by jub2 on 2016-06-01
I've done a few installs of various Ubuntu flavors. The only device that shows up in Synaptic > Additional Drivers is a device that uses intel cpu microcode. I've used the proprietary driver it suggests without any problem. On this last install, I ticked the circle to use the proprietary driver, and selected 'Apply Changes'. It went on forever, so I closed Synaptic and restarted.

Now under Additional Drivers, it shows "Unknown: Unknown", "This device is not working". And trying to apply the suggested proprietary driver does not work.

Any suggestions on fixing this without redoing the installation?

---

### Post by grahammechanical on 2016-06-01
"Unknown: Unknown" is what shows up in Additional Drivers on my system and always has done ever since the Intel microcode driver was made available. That label does not trouble me. Even when activated the driver is still listed as "Unknown: Unknown."

I activate this Intel Microcode driver using Additional Drivers & not Synaptic and it takes about 2 minutes. Were you connected to the Internet at the time? It is my guess that you have an incomplete process and that is what is preventing Additional Drivers from activating this driver. Have you re-started? The only other thing I can think of is to try again with Synaptic. Let it complete the process.

Regards.

---

### Post by jub2 on 2016-06-03
On a subsequent fresh install, I got it to work. 

> **jub2 said:**
> On this last install, I ticked the circle to use the proprietary driver, and selected 'Apply Changes'. It went on forever, so I closed Synaptic and restarted.
^ That was the problem. I should have let it run. Ubuntu seems to provide very little feedback (like a progress bar) on running processes like this and, coming from Windows, it's easy to assume the process is hung and try to shut it down.

So the solution is to let it run for a long time.

Have run into similar issues elsewhere in installing and setting up Ubuntu. Without any progress indicators, I have to remind myself to just let it run so long as the mouse is still moving and the GUI is responsive to the mouse.

---

### Post by jub2 on 2016-06-04
Even better (and quicker) - install via Synaptic: [https://sites.google.com/site/easylinuxtipsproject/microcode](https://sites.google.com/site/easylinuxtipsproject/microcode)

---

