---
title: "Ubuntu preview or install not working"
date: 2012-07-26
forum: Installation &amp; Upgrades
---

### Post by codeSlinger on 2012-07-26
Hey. I just downloaded and burnt a cd of 12.4. I have a HP L2000 laptop (Presario) with 1 gig mem, 80 gig hd and an AMD processor I'm trying to install on. I first tried doing the preview off the cd that did not work. It was reading the cd then it got to the dark screen where it has UBUNTU spelled out with the little dots going back and forth then it just stopped there with no movement and stayed that way. So then I tried the windows installer and it run to the point of giving me a "dot" prompt and will accept commands but that's where it stays.

I've been in software dev for 30 yrs but new to linux. Thanks for your help.

Gary

---

### Post by nothingspecial on 2012-07-28
*Thread moved to **Installation & Upgrades**.*

---

### Post by microUgly on 2012-07-28
I'm pretty green when it comes to Linux, but I'm having a similar issue and know enough to suggest how to start the debugging process.

When the CD very first boots, press Esc.  You will then get a simple menu.

The first thing to do is the "Check disc for defects".  

If that goes ok, let the disc load again and press Esc.  This time, press F6 to display the "Other Options" menu.  Just press Esc to close the menu.  The boot options line will now display.  Press backspace to remove "quiet splash --".  Now select "Install Ubuntu" and you'll see everything that is happening during the boot.  Where it stops may indicate what is going wrong.

You can find a little more detail here - [https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

---

