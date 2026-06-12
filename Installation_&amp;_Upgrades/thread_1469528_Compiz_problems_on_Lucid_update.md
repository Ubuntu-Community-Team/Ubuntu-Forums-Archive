---
title: "Compiz problems on Lucid update"
date: 2010-05-02
forum: Installation &amp; Upgrades
---

### Post by sixpounder on 2010-05-02
Hi everyone. After updating from karmic to lucid everything worked just fine, except for compiz. I use NVIDIA 9800 GT on a 64 bit system with manually compiled proprietary drivers (195.36.24) downloaded from nvidia site. Of course, I had to recompile them on after-update reboot cause the kernel changed, and again everything worked fine.
But something strange happens on compiz: with sync_to_vblank activated (as it is since always on my computer) effects like scale and expo have very low fps rate and I can't figure out how to fix this. My xorg.conf didn't changed, neither my compiz setup did. Can someone help me?
Thanks everybody

---

### Post by dennymallow on 2010-05-02
Same here, after a fresh distro upgrade to Lucid.
After first reboot, no driver was loaded because Ubuntu searched for old "nvidia" module as the xorg.conf line stated.
So I went in package-manager and installed **nvidia-current** package, which corresponds to 195.36 version of nvidia drivers
So i didn't compile 195.36 nvidia modules manually for the kernel, but I think that the resulting driver situation is exactly the same as yours, sixpounder.
This drivers enabled 3D acceleration, but some compiz animations have a crappy framerate, and nvidia "sync to vblank" setting doesn't seem to work properly.

---

### Post by sixpounder on 2010-05-02
Ok folks I figured it out.
First of all, blacklist this modules on /etc/modprobe.d/blacklist.conf:

```
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
```

Then, compile nvidia drivers as usual (remember to stop gdm on X before you do that)

Log back into gnome and open compiz fusion icon. Check that loose binding is enabled and indirect rendering is disabled. Then open CompizConfig Settings Manager and go to general. Once you are there, check the sync to vblank option, uncheck the "Detect refresh rate" option and set refresh rate manually to 90-100.

Then, reboot the system (it is not enough to reboot gdm).

That fixed the problem for me.

Bye.

---

### Post by sixpounder on 2010-05-02
Ok, that was too quick. Same problem again, did nothing and changed nothing but after reboot problem is there again. I'm losing hope :(

---

### Post by dennymallow on 2010-05-02
> **Chauncellor said:**
> I have also realized that switching my desktops takes about half of my CPU during the animation.

I distinctly remember (since I have a monitor applet on my panel) noticing that switching my desktop usually takes nearly no cpu usage at all for me. It really used to be able to handle an intense amount of switching before it would start getting high. Now it's a regular thing..... :(

Also for me... and I made an "lsmod", but the only module in use among the list of modules to be blacklisted is vga16fb. There's no nouveau module running, I suppose...
Maybe these problems are to be investigated in some interaction between nvidia drivers and the new kernel?
:confused:
3D is very, very fast, by the way... UT2004 gives wonderful fps values. It's just a matter of the effects for what I can see here.

---

### Post by sixpounder on 2010-05-02
Ok this time I really think I figured out the problem. But I have no idea how to fix it!

Here is the thing: I had in startup applications a call to nvidia-settings --load-config-only, so that digital vibrance and stuff would load at login. I tried to uncheck it and... surprise! Compiz work smooth and fine! Plus, if you start nvidia-settings after login your settings will apply and compiz will continue to work at good fps and syncing to vertical blanking.

Now I guess it is something on startup that nvidia-settings "crush" with. But having to start nvidia-settings MANUALLY after the login is a bit annoying -.-'

Bump! Any ideas?

---

### Post by sixpounder on 2010-05-02
Quick solution: a script which delays the start of nvidia-settings

```
#!/bin/bash
sleep 5
nvidia-settings --load-config-only

```

Anyway, if you reload compiz for some reason with this solution the problem will still be there.

Any other ideas?

---

### Post by sixpounder on 2010-05-02
As far as I know, it should. However this worked for me, compiz works like a charm now! I suggest you to review your nvidia/xorg settings to find something to edit ;)

---

### Post by dennymallow on 2010-05-03
> **Chauncellor said:**
> I submitted a bug report:

[https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/574069](https://bugs.launchpad.net/ubuntu/+source/nvidia-settings/+bug/574069)

Did launchpad give you the problems you were mentioning in post #9?
Here's what I did yesterday evening, before falling asleep to the ground (XD):
[LIST]
[*]Disabled the startup entry that used to load the nvidia settings before (like vibrance as stated by sixpounder some posts ago).
[*]Disabled indirect rendering after I realized that I'm a bit foolish and I did not see it was checked out in fusion icon (ok ok I'm a newbie :P).
[*]Rebooted.
[/LIST]
After these steps, Compiz was as fast as lightning, but when I went to launchpad to verify what Chauncellor said about it, I realized he was right... Carrying Firefox window with the focus on launchpad site's tab among desktops screws the CPU and Compiz framerate falls down again, and also going to expo and bringing around the window in the Expo view...

In addiction, after that, Namoroka (I have the development version of Firefox, another thing I'll do soon will be to try to put back original Firefox version from official repos) Namoroka terminated abnormally and vanished from screen.
I launched it again, plus some nautilus windows and a terminal: ***but they didn't show up***, and after a few other clicks desktop _*launchers vanished*_ themselves and the only thing remained on the screen was gnome-do docker, with the effects still running as fast as hell.... Only thing I could do after that was going to root shell with Ctrl+Alt+F1 and hit a *sudo shutdown -h now*, and go to bed!
:confused:

---

### Post by dennymallow on 2010-05-03
> **Chauncellor said:**
> In addition to the previously stated, if I reload compiz, Firefox crashes.
so I guess you are running the repo's version of firefox and not the developer version, Namoroka... And I think this nasty thing is independent from which Firefox version one uses.

Edit: 
> **Chauncellor said:**
> 
This thread may be of use:
[http://ubuntuforums.org/showthread.php?p=7506398](http://ubuntuforums.org/showthread.php?p=7506398)
I added my case there, and subscribed to launchpad bug you opened... I think this thing should have visibility, because it's not reasonable to throw away a wonderful Distro like Lucid for this poor but annoying problem.

---

