---
title: "Installed with 19&quot; monitor but user has  17&quot;; virtual/pan problem"
date: 2004-11-02
forum: Installation &amp; Upgrades
---

### Post by emperor on 2004-11-02
I installed Ubuntu with my Samsung 19" monitor attached. Now I want to move the machine into another room that has a 17" monitor. Seems simple enough, but when I connect the 17" monitor and boot the machine the screen is in virtual or pan mode, starting with the login screen. The monitor resolution stays in 640x480 60Hz mode.
  
 In an effort to solve the problem I have edited the XF86Config-4 file and setup the Vertical & Horizonal Freg ranges and also set the Monitor DisplaySize values ( 313 by 235) for the 17". I have the settings in XF86Config-4 within tolerance for the 17". The only differences between the 2 monitors is the size of the display and the maximum Horzontal Freg is 70 Khz as opposed to 96 khz for the 19". In the past, I have only had to lower the Horzontal Freq value and the 17" monitor works fine. In fact I did this a few days ago with another system running Ubuntu and the display was fine on the 17".
  
 I am sync'd with the current state of warty and do believe that Ubuntu's XFree86 was updated a few days ago. The video card is a radeon 7000 series.
  
  Anyone had a similar problem and know how to fix this one?
  
 Would generating a new XF86Config file with the 17" monitor attached be worth a try? If so how do I do that? The debian "dexconf" seems to only restore the original XF86Config-4 file when I installed Warty.
  
  Anyone's who has any ideas feel free to comment!

---

