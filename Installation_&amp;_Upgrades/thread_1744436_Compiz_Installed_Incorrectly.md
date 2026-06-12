---
title: "Compiz Installed Incorrectly?"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by crashed111 on 2011-04-30
Hi

I have been doing some research on problems I have been having and I have narrows Compiz down to being the problem. 

I am running the prop Nvidea driver.

I can use Unity 2d fine however I cannot use Unity at all I just get a blank screen with the mouse cursor no desktop ever loads. 

I have tried switching between gdm and kdm. I have now worked out that compiz looks like the problem. 

If I issue a compiz --replace at the terminal I get the same sort of problem I get when I log into the Unity 3d. 

I loose my left hand monitor (it goes black but I can move my mouse around) and on my right hand monitor I can operate things using the keyboard but when you click with the mouse it does not work although you can move it around fine. 

Never used Compiz and I dont know if anyone knows any troubleshooting I can try I have exhausted what I could find on the Internet (A few exports of global variables but none fixed anything)

Thanks

---

### Post by crashed111 on 2011-04-30
FIXED!!!

Turns out the issue is with Xinearama.

If you are running Dual Monitors use TwinView as opposed to Xinearama. If you are running two single headed cards which require the use of Xinearama Unity will not work for you. If you are running a Dual Headed card use Twinview and it will work fine.

Twinview also is nicer to configure and has fixed another glitch I have had with my screens for ages.

---

