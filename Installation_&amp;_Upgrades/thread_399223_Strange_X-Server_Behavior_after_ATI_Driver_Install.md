---
title: "Strange X-Server Behavior after ATI Driver Install"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by ambien on 2007-04-02
Hello, when I first installed Ubuntu I noticed that scrolling and moving of "windows" was very slow. After a bit of browsing through I came across: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

I followed the instructions, and everything worked...so I rebooted my system. Then the problems started. I don't really know how to describe what the problem is, because I've never seen anything like it really. The closest I can come to describing it is a common windows experience, when you have way too many things running, and you start closing them with ctrl+alt+del, and for a moment any window you move just sort of leaves mouse trails, or parts of them become transparent. It's like the windows aren't refreshing themselves?

When I am in the web browser, I have to scroll with pgup or pgdwn, otherwise the screen overwrites itself, and text is illegible. When I move windows, they respond as if I am resizing them, and I must click the resize button to in order to see the contents of that window again!

Sorry for the HUGE question, I tried to describe the problem the best I could, for example, my cursor doesn't blink, if anyone is still reading this, please help!

---

### Post by ambien on 2007-04-02
I fixed the problem by deleting the "composite" line in /etc/usr/X11...whatever, but now I get no hardware acceleration, so at atm I'm happy. I found a fix:
"
 Graphical Anomalies

This was experienced with an ATI Radeon X1600 Pro 512mb:

After following instructions for both Method 1 and Method 2, whenever the Composite Extension is disabled, the display would be almost unusable, but the fglrxinfo command would display the correct information. If the Composite Extension is re-enabled the display would be usable, but fglrxinfo would report using mesa drivers.

To resolve the problem it maybe needed to lower the AGP Aperture setting in my BIOS to 128mb (or lower worked too). The AGP Aperture was initially set to 256mb. After setting the AGP Aperture to 128mb, everything worked perfectly; the Composite Extension is disabled, fglrxinfo reports the correct drivers, and direct rendering is enabled. Some systems may require setting the AGP Aperture to the highest setting (256mb or 512mb).
"

But I don't know how to go about doing ^that. 

Thanks in advance for your help

---

