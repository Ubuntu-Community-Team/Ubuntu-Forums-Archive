---
title: "Graphics get corrupted after a week or so"
date: 2010-07-07
forum: Installation &amp; Upgrades
---

### Post by MisterH on 2010-07-07
Hi guys, I'm not sure if I have a hardware problem or if something is going wrong following one of the updates. I have an old NVidia card and I manage to get Ubuntu 10.4 installed and the enhanced graphics enabled after loading the recommended Nvidia driver.
 
But after a while the graphics get corrupted - like there is a memory leak, things don't get drawn or they appear with pixels missing or stripey patterns that disappear when I roll-over. Sometimes window controls aren't drawn properly and the window can't be closed.
 
There was also a power cut last night and since then, my PC now won't display the GUI - I sometimes see the ubuntu splash screen, but then I get a green stripe about 25% from the left, I eventually hear the little drum, which means the logon screen has loaded, but the screen is black.
 
I can get the system into a console, if I press ctrl-shift & F1 before I hear the drum.
 
before I log-in to the console session, I see this error at the top of the screen;
 
 
```
Error requesting Region 4300 .. 433F for SMB2nforce2_smbus_0000:00:01.1: Error probing SMB2
```
(which may be a red herring)
 
and when I type these metacity commands to try and turn off the enhanced graphics I get 
 
```
 
metacity --replace
Window manager error: unable to open X display

```and
 
```
 
metacity --display=:0.0 --replace &
Window manager error: Unable to open X display :0.0

```
for the long version.
 
Last time this happened I ended up re-installing ubuntu from the CD but this time I have loaded quite a lot of stuff plus I have a hot girl on my desktop wallpaper :smile:
 
Is there a way to recover without rebuilding please?
 
Can I get more diagnostic info somehow?
 
Should I buy a new PC? This one is a bit old - 2 years or so, so I might be better off with a multi-core CPU and a newer graphics card... What is the minimum Nvidia chipset number I should get? (need to keep costs down)
 
Thanks for any help you can offer - it's a bit frustrating, but I want to learn how to fix it.

---

