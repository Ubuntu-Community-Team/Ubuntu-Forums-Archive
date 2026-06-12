---
title: "Recent updates have broken graphics"
date: 2012-06-08
forum: Installation &amp; Upgrades
---

### Post by therog726 on 2012-06-08
I updated a whole lot of things this morning, then after restarting later, my graphics were broken. I'll try and detail as much of this as I think may be relevant but if you need more info, you may need to tell me how to get it.

I'm using precise with gnome shell. I have a HP Pavilion with an AMD graphics card (6770M).

I'm not sure what the updates included since there were 40+ of them, I presume though that one of them was a kernel update since I had to restart and it now says kernel version 3.2.x where before I think it was 3.0.x.
When I rebooted, it came up with a window saying something like: ```
"graphics have failed. Your graphics, input 
devices and <something else> will not function properly"
```
Sure enough, after hitting enter to close that window, everything stopped working after that. There was a black screen, with a box in the middle saying something about the graphics, which I couldn't interact with since keyboard and mouse were dead.

I eventually managed to restore the graphics to their "previous state" through the recovery boot option. So now I at least have life, and ubuntu boots all the way to the login shell. However, only gnome classic works. Gnome shell (my preferred), Unity and Cinnamon all fail to load the shell. I can run terminals, but can't see anything else apart from the background image.

Also, I noticed the updates screwed up my pretty BURG loader screen and it has reverted to "grub 1.99". Just a purple screen with lines for Ubuntu, Mem test & Windows. Not sure if this is at all related, but thought I'd include it.

I've tried ```
apt-get purge gnome-shell
``` and then reinstalling with no luck. I've tried 
```
apt-get clean
apt-get autoclean
apt-get autoremove
```
and anything else apt-get offered that looked like it would help.

Can someone please help me? I have no idea where to start looking to fix this now.

Thank you!

---

