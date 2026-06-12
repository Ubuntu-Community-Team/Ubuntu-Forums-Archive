---
title: "Installing SVGA II Adapter and InnoTek drivers on Ubuntu Virtual Machine"
date: 2020-04-06
forum: Installation &amp; Upgrades
---

### Post by drewpeterson1991 on 2020-04-06
Im a newbie 

I checked my drivers in software and updates and it shows I do  not have a driver for VMware: SCGA II Adapter and InnoTek Systemberatung GmbH Virtual Guest Service.

I have looked around, but I cannot find how to get those drivers.  I believe I need to manually install them from terminal.

Help please?

---

### Post by QIII on 2020-04-06
Hello!

Are you able to see your desktop and interact with the machine?

---

### Post by drewpeterson1991 on 2020-04-06
Yes, but it is DEATHLY slow.  Im a developer.  It takes 15 to something that should take one minute at the most.  Its rendering the graphics in software, I think.

---

### Post by QIII on 2020-04-06
Your virtual machine is not using your hardware GPU.  Instead, it is using a virtual one provided by the virtualization software's Hardware Abstraction Layer.  That is:  it's a software GPU with very limited capabilities.  It's not by any means intended for rendering or gaming.

---

### Post by drewpeterson1991 on 2020-04-06
Understood, this is for web development, web pages.  Not video games.  The driver screen seems to indicate I need to find drivers and manually install them.

---

### Post by QIII on 2020-04-06
The "driver" is generally supplied by the virtualization software.  You should not need to install anything.

If you want to try to beef up your graphic performance with VMWare, [this ]("https://techzone.vmware.com/resource/deploying-hardware-accelerated-graphics-vmware-horizon-7#section1")might be helpful -- or at least maybe point you in the right direction.

---

### Post by drewpeterson1991 on 2020-04-06
Thank You!

---

