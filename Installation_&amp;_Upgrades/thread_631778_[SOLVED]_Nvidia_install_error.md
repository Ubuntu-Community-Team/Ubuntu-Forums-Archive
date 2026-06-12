---
title: "[SOLVED] Nvidia install error"
date: 2007-12-04
forum: Installation &amp; Upgrades
---

### Post by Mindflux0 on 2007-12-04
I'm trying to install my video card.  I'm running 64bit version.
I did this:
ctrl-alt-f1
sudo /etc/init.d/xfs stop
sudo <nvidia file>

and it starts then I get

ERROR: You do not appear to have libc header files installed on your system.  Please install your distribution's libc development package.

I don't know what any of this means.  Help would be appreciated
looking around I think I need to install "build essential" how do I do that?

---

### Post by Pumalite on 2007-12-04
sudo apt-get install linux-headers-`uname -r`

---

### Post by Mindflux0 on 2007-12-04
running linux is slowly making me feel retarded
what do you mean by `uname -r` ?

---

### Post by Pumalite on 2007-12-04
Copy and paste in your Terminal and run it. That will make sure you have headers matching your kernel.

---

### Post by Mindflux0 on 2007-12-04
I did and it said that it didn't need to update anything.  The nvidia drivers still won't run. another post said I need build essentials, how do I install that?

---

### Post by Pumalite on 2007-12-04
sudo apt-get install build-essential

---

### Post by Mindflux0 on 2007-12-04
ok, I did that and it worked but it randomly spit out: "bcm43xx: Error: Microcode 'bcm43xx_microcode5.fw' not available or load failed"
it actually does this about every 30s when console is open.
(the install seems to have worked, restarted and am back to desktop at least)

---

