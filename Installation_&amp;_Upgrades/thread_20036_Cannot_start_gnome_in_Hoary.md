---
title: "Cannot start gnome in Hoary"
date: 2005-03-14
forum: Installation &amp; Upgrades
---

### Post by Dromio on 2005-03-14
I have an A64 with an nvidia video card.  I've tried the default install of Hoary off the preview CD.  The installation seems to go fine all the way to the GDM logon screen.  

When I logon to my initial user, the screen goes brown, I get the nice arrow cursor (not the X one), and I hear the startup sound.   But then nothing else happens.  

The exact same thing seems to happen when I try the i386 install.  I have not specified the nvidia driver yet, I don't think Hoary has installed it without telling me.  

I can't even figure out where to look to troubleshoot the problem.  Xorg.log shows that several font renderers are already registered, down to this:

> 
Warning: font renderer for ".pmf" already registered at priority 0
Could not init font path element unix/:7100, removing from list!


What else should I look for?

---

