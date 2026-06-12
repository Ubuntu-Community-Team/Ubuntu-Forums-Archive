---
title: "My NVIDIA/GLX solution"
date: 2005-04-10
forum: Installation &amp; Upgrades
---

### Post by farnsworth on 2005-04-10
Like many of you I spent all day yesterday trying numerous fixes for the segmentation faults in mplayer, vlc, etc.  The ONLY thing that helped was the installation of an older NVIDIA driver set, v. 1.0-6629, as the GLX module in this set isn't broken.  for the newbies I'll step through the procedure.

EDIT:  I was wrong.  the NVIDIA GLX module in 7174 isn't broken, it's the runlevel 2 and 6 rc scripts that are at fault.  If you're still using "nv" and can't run mplayer try the fix below.

---

### Post by c_dog on 2005-04-10
6229 has problems also. Many even worse then 7167.  There's a new 7174 nvidia-nlx & nvidia-kernel-common debs in the restricted repositories or you can find them in the final release Hoary DVD /pool folder. Not sure if they are on the CD versions.

7174 has been working just great on my 6600GT for the last 3 days. The compositing in 7174 w/ xorg 6.8.2 works much better than 6229 or 7167 ever did. I really wouldn't suggest anyone go back to 6229. EiIther compile the 7174 modules with a the run script (which works correctly under 32-bit Hoary without much effort finally) or installed 7174 debs.

---

### Post by daniels on 2005-04-10
7174 is on the CDs as well, and is what is installed if you just run 'sudo apt-get install nvidia-glx' from a Hoary system.

---

### Post by farnsworth on 2005-04-10
yeah, I know it's not the proper thing to do, but 7174 does NOTHING but crash xserver and throw segfaults around like confetti.  I really couldn't care less which version is officially offered by the distro if it doesn't work with my hardware (and doesn't let me play ut2004).  This is a fix for people who've tried everything else.

---

### Post by farnsworth on 2005-04-11
or... another bad idea that works

The chiding I received for downgrading my nvidia driver made me want to give 7174 another try.  And... It works!! nvidia AGP kernel module, X driver, glx, everything with NO slowdown or sigfaults.  the trick is...

download the latest binary installer from the nvidia website, and
```

sudo -s
apt-get install nvidia-kernel-common nvidia-glx
rm -f /etc/rc2.d/S20nvidia-glx
rm -f /etc/rc6.d/K20nvidia-glx
./NVIDIA-Linux-x86-1.0-7174-pkg1.run
nvidia-glx-config enable

```

Thats right, those rc scripts have to go.  This is probably the result of a botched upgrade (I followed the official directions), but the problem is definitely the scripts.  Maybe when ldconfig is run something goes awry, or maybe all that rm'ing of TLS files messes with something.

Either way, only the nvidia-glx package installs these files, the official NviDIA binary doesn't.  Once you're done, run startx to test.  Try glxinfo in a terminal.  It works?  REBOOT!  Those scripts aren't there to crap on your glx libraries anymore, so no matter how many times you reboot you'll never see that blue screen of death(I rebooted 4 times so far, just to make sure)  And if the thought of stale TLS libs keeps you up at night, just rerun "nvidia-glx-config enable"

---

### Post by sleytr on 2005-04-12
[QUOTE=farnsworth]

download the latest binary installer from the nvidia website, and
```

sudo -s
apt-get install nvidia-kernel-common nvidia-glx
rm -f /etc/rc2.d/S20nvidia-glx
rm -f /etc/rc6.d/K20nvidia-glx
./NVIDIA-Linux-x86-1.0-7174-pkg1.run
nvidia-glx-config enable

```
[/QUOTE]



YES!!! That's worked for me too! Thanks..

---

