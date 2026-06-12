---
title: "GUI fails to start (mostly)"
date: 2004-11-19
forum: Installation &amp; Upgrades
---

### Post by shakey on 2004-11-19
I decided to install ubuntu after trying the live cd (which worked perfectly), so I downloaded, burnt and installed the iso. That all went fine, it even let me set up a user account.

But when I attempt the first real boot, it does all the loading stuff, tries to start gnome (so it says), goes to a blank screen, then starts what I assume is meant to be a login screen. Except it's not.

I can see and use the mouse cursor (yay!) but thats it. The backgroung is a heavily scrambles version of whatever the last image the gfx card diplayed (usually xp shutdown screen), or a complete mess of colours (if my pc has been turned off for a while.  And that's it, it just sits there. Tried typing in user name and password to no effect.

I'm assuming it's something to do with my graphics card (Radeon 9200SE) as i've heared Xfree can have problems with ati cards. But how do I fix it?

Damn that's a long first post. Cheers for any help you can give me.

---

### Post by shakey on 2004-11-20
*bump* please?

---

### Post by xenon2050 on 2005-02-01
I'm having very simular problems except I'm using Gnome have an NVidia graphics card and am virtual PCing it. But other wise your problem sounds exactely the same as mine...

---

### Post by crane on 2005-02-01
You could try hitting >ctrl>alt>f1 to drop to console. from there either try to reconfigure the X-server or even install video driver through apt. 

sudo apt-get install nvidia-glx.
sudo apt-get install nvidia-settings
sudo nvidia-glx-config enable
nautilus applications:///System

If all else fails you could boot back to live CD where X was working and try comparing or even swapping the config file to the X11 file on you system.

---

### Post by xenon2050 on 2005-02-01
I tried what you said but it replied saying that the package is missing... What's up with that? I'm assuming that means that I'll have to download it from somewhere but I'm not sure how to do that...

---

### Post by offcenter on 2005-02-05
I've a similar problem; I have and nVidia GeForce 2. But even with the Live CD everything loads great except after logging in I have no mouse or keyboard functions. That is typing my login works okay but I have no mouse, then when Gnome starts there is no mouse or keyboard.

Help

BTW, I have tried manually reconfiguring "X" but I got the response

Cannot write changes to file

---

### Post by offcenter on 2005-02-05
Just to let everyone here on this thread know, I believe I have an answer to all our problems. Give me a few hours to try my theory and if it works, it should correct all those "X" bugs we've been writing about. If successful, I'll probably post it as a separate thread so other users who stumble upon the problem can read it more readily.

---

### Post by llamakc on 2005-02-05
First off, the 9200SE is NOT an NVidia card. It is an ATI product and the OP should know what hardware they have. 
 
 So, do this:
 
 reboot and get to a console. Type `startx` and let it fail as it will. Let us see your /var/log/XFree86.0.log (if you are on Warty). 
 
 This will help others diagnose your issue.
 
 Otherwise you could edit /etc/X11/XF86Config-4 and make sure you are using the ati driver. If you need a conf file let me know. I use the exact same card without fail.

---

