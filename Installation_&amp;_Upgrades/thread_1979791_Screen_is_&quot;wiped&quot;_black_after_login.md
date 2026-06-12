---
title: "Screen is &quot;wiped&quot; black after login"
date: 2012-05-14
forum: Installation &amp; Upgrades
---

### Post by pepperjinks on 2012-05-14
Running 12.04, just got done installing it in a dual boot configuration with Windows 7. I'm brand new to Linux and I cannot overemphasize how profoundly I don't know what I'm doing when it comes to this OS.

I boot up my laptop, boot into Ubuntu, and I'm taken to the login screen. This is right after I successfully installed Ubuntu. At this point I can see the status bar (time, settings cog icon, etc.) and the option for a guest session, etc. Everything's good. I input my password and log in.

After this the screen is "wiped" black; the wallpaper disappears top to bottom. If I right click the context menu comes up and I was actually able to select a different wallpaper doing this, but the screen remains black.

The first time this happened there was something about compiz crashing and the terminal popped up before that because I had opted to encrypt my home folder and was going to be given the passkey. I couldn't actually input text into the terminal, though.

 The second time I tried booting past the login screen the same thing happened, and the terminal popped up and blocked the text of another error message.

I probably shouldn't have, but I booted into recovery mode the third time and selected fsck-check all file systems. Didn't do anything to help, though. I considered trying dpkg but thought better of it.

Windows 7 runs perfectly, it's just Ubuntu with the issues.

What should I do? Thanks in advance.

---

### Post by 2F4U on 2012-05-14
What are your hardware specs? Do you have this problem for the beginning or did it work directly after the installation?

---

### Post by roelforg on 2012-05-14
It's a clean install, so try reinstalling w/o encrypted home.
I think somehow it doesn't start decrypting on boot.

---

### Post by pepperjinks on 2012-05-14
Specs: 1GB RAM, AMD Athlon 64 X2 1.7GHz, NVIDIA GeForce Go 6150.

The Live CD worked fine--it's just when I actually tried booting into Ubuntu without it that it happened. I haven't actually been able to get Ubuntu to work yet.

I'll try to re-install and deselect encryption later today, then. I'll edit my post when I do if there aren't any more replies. Thanks for the help, guys, I appreciate it.

**edit**: It works now! I re-installed and had the same problem, but changing Ubuntu to Ubuntu 2D helped fix it. I think it had something to do with Unity not supporting NVIDIA drivers or something. Either way, it works now. Thanks everyone.

---

