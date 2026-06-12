---
title: "Hooking machine up to 65&quot; tv"
date: 2022-07-05
forum: Installation &amp; Upgrades
---

### Post by jgw on 2022-07-05
I just connected a computer to a 65" tv through a denon receiver.   After I plugged it in I check the system setting.  The old display was 1920x1080  and now its 3840x2160.  There was a button to adjust for tv but it left about 3 inches on both sides of the tv.  It thinks thats the tv is a denon (which is my receiver which was odd.  I also set the scale at 150%   I just wanted to know if anybody had any thoughts on this or should I just leave it alone?

Thank you...........

---

### Post by MAFoElffen on 2022-07-06
That is because the Linux Graphics Layer queries and sees what is connected to it's video ports. It correctly see's the Denon Receiver, but the receiver does not report what it is connected to... (Especially with NVidia and it's drivers.) The same happens with KVM Switches...

What to do, to adjust or compensate for that, is to set your video mode in the Grub default file, so that the Kernel can use KMS to set your mode, during boot... That is the best method to do that. Please refer to Post #1 in my Graphics Resolution Sticky, in my signature line for reference... Or if you do not understand those instructions, please ask.

---

