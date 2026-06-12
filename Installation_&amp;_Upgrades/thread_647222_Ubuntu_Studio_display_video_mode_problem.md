---
title: "Ubuntu Studio display video mode problem"
date: 2007-12-22
forum: Installation &amp; Upgrades
---

### Post by AndyFitz on 2007-12-22
This is my SOS.

I installed Ubuntu Studio [COLOR="Blue"]/quote_fingers[/COLOR] "successfully" (dual boot with WinXP), but now after the splash screen disappears and the login screen should be in front of my face, my monitor (Dell UltraSharp 20") goes blank and says
> 1:Analog Input
Cannot Display This Video Mode
I have tried the other suggestions for similar problems, but all have failed.
Actually if I try to reconfigure xorg, my screen glitches out after trying to set the resolution.
I am begging for help from the linux gurus out there!

---

### Post by AndyFitz on 2007-12-24
The realtime kernel is the problem.
I installed vanilla Ubuntu and it worked with the restricted drivers, then I installed the Ubuntu studio packages, which enabled the RT kernel, which I found to be causing the problem (since the generic kernel works fine). But, I want to use the RT kernel for performance benefits. Is there any way to fix it?

---

