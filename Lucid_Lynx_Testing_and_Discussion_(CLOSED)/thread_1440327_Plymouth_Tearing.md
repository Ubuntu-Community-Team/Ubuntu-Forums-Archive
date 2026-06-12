---
title: "Plymouth Tearing"
date: 2010-03-27
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by MichealH on 2010-03-27
Hmmm Plymouth... Where has it EVER gone right?

I installed Ubuntu 10.04 but after installing I was greeted by this:

Should I install HAL? What should I do Please Help

Micheal

---

### Post by MichealH on 2010-03-27
C'mon anyone have a Idea to fix this?

---

### Post by dino99 on 2010-03-27
> **MichealH said:**
> C'mon anyone have a Idea to fix this?

HAL ?
a quick glance at synaptyic: plymouth depend on udev, so ignore it i guess

---

### Post by vishalrao on 2010-03-27
useful post with lack of details. can you post your hardware? ati? intel? nvidia? what?

and what version are you using? latest? beta1? alpha3? 10.04?

there are some tweaks/fixes posted in other threads like:

echo FRAMEBUFFER=y | sudo tee /etc/initramfs-tools/conf.d/splash

also boot with nomodeset modeset=0 nouveau.modeset=0 intel.modeset=0

stuff like that should work...

and just update to the latest if you want to file bug reports...

---

### Post by MichealH on 2010-03-27
Upgrading to the latest plymouth has resulted in BETA1 breakege I will post It when reinstalled in the morning (of course :D)

I do know its SiS but It should be stable.

---

### Post by vishalrao on 2010-03-27
looks stable for me after updated a few minutes ago from main archives...

---

### Post by MichealH on 2010-03-28
Bump :/

---

### Post by emarkay on 2010-03-28
Packard Bell???

Maybe you need to check to see if the tubes are glowing! :)

FWIW, I have a old laptop that does this at times - I just "thwack" the top of the thing - the display sliding contacts are worn and it sometimes needs to cut through the goo in there.

We still need the specs on the hardware and software, and any changes/differences from "stock" thereof.

---

### Post by MichealH on 2010-03-28
CPU: Intel Celeron T1400 @ 1.75GHz
RAM: 1.5GB [SIZE="1"]*[COLOR="Silver"](Added 512MB from the stock[/COLOR]**[COLOR="Silver"])[/COLOR]*[/SIZE]
HDD: 111GB (Roughly)
Graphics: SiS Mirage 3 M671/771
GPU: 256MB total:128 to Ubuntu, 128 spare.

Oh and when on Desktop its fine :)

---

### Post by MichealH on 2010-04-05
Fixed, I used this from someone elses post

> the solution is easy; 
open a terminal;
become root
```
sudo bash
```
type;
```
echo blacklist vga16fb > /etc/modprobe.d/blacklist-vga16fb.conf
```
type;
```
update-initramfs -u
```
```
reboot
```
Everything is working like a charm.

---

### Post by dannyboy79 on 2010-04-05
another great fix is to just remove splash from your boot options and plymoth isn't even used! getting into grub menu can be tricky sometimes though

---

