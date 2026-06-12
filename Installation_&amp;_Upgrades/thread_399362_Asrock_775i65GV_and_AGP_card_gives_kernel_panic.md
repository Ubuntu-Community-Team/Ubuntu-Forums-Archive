---
title: "Asrock 775i65GV and AGP card gives kernel panic"
date: 2007-04-02
forum: Installation &amp; Upgrades
---

### Post by zeeclor on 2007-04-02
I'm having problems booting feisty on an Asrock 775i65GV with an NVidia FX 5500. The system boots when using the onboard graphics chip but kernel panics when using the AGP NVidia card. Others have reported similar problems and wormhole [describes]("http://www.linuxquestions.org/questions/showthread.php?t=531308") how to inactivate the onboard card detection in SuSE to get things working.

"The easy way.
boot with the option init=/bin/bash
rename the file /etc/init.d/boot.udev to anything."

I've poked around in /etc/udev/rules and /etc/init.d/ but cannot see the debian / ubuntu equivalent of what he suggests and would be grateful for any advice.

Addit:
FWIW the kernel panic finishes with
[ 33.893846] [<c010334b0>] work_notifysig+0x13/0x18
[ 33.893961] ===============

---

### Post by todoporron on 2007-04-02
Hi 

About a year ago, I had the same problem with an Asrock board with embeded graphics and my Nvidia card.

The solution:

Edit your /etc/modprobe.d/blacklist file:

```
sudo gedit /etc/modprobe.d/blacklist
```

and add the following line:
```
blacklist intel_agp
```

After that, you have to install your Nvidia drivers if you have not done it yet. 

On your BIOS setup, disable your onboard graphics and enable your Nvidia card. This should solve the problem .

---

### Post by zeeclor on 2007-04-11
Thank todoprron blacklist was what I needed. 

David

---

### Post by Faust942 on 2007-07-06
This worked perfectly for me! Thanks!

---

