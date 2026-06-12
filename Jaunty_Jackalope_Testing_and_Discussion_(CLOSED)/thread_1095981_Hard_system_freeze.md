---
title: "Hard system freeze"
date: 2009-03-14
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by DoeRayMe on 2009-03-14
im using Ubuntu Alpha 6 fresh install

Im not sure whats causing it, but i think its related to the new nvidia drivers

When i dont have the nvidia drivers installed, i never get system freezes, with them i do

anyone got any ideas?

i got a Geforce 7200

---

### Post by zenarcher on 2009-03-14
I'm going to guess it might be related to the Nvidia driver.  I'm not getting hard freezes with mine, but one known issue is that you cannot reboot, due to the Nvidia driver....you have to reboot from the terminal.  Likewise, I find that if I edit the menu and save after doing so, (with Kubuntu and GeForce 8400 video cards and the current Nvidia driver), everything freezes and the only way I can shut down is to push the power button.

Cheers,
zenarcher

---

### Post by DoeRayMe on 2009-03-14
i had to revert to the xorg driver, cos nvidia one causes me nothing but problems :<

---

### Post by kj74 on 2009-03-14
Nvidia drivers can cause those freezes.

If those freezes are random, i don't think there is a way to fix them unless you want to buy new motherboard. They are bretty much impossible to debug. I have exactly same problem. Some nvidia cards do work with binary drivers but most causes hard freezes randomly.

---

### Post by kj74 on 2009-03-14
Nouveau drivers are slighty better than awful nv ones but don't support 3d at the moment.

---

### Post by nyarnon on 2009-03-14
Just finished a machine with the same problem, wasn't even able to complete an ubuntu install. Update the bios and everything went well no more freezes. Don't say this will solve your problem but might be worth looking in to.

---

### Post by LinuxLars on 2009-03-14
This may well be related to an issue with Intel 4965 wireless starting with 8.10 which has not been resolved yet (to my knowledge):

[http://ubuntuforums.org/showthread.php?t=969621](http://ubuntuforums.org/showthread.php?t=969621)
[https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/300693](https://bugs.launchpad.net/ubuntu/+source/linux-meta/+bug/300693)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/303276](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/303276)
[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/293200](https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/293200)

---

### Post by Nullack on 2009-03-14
Keeping the BIOS up to date is good practice anyway.

Anyway, what NVIDIA driver version are you using? Have your tried the range of re-release or beta drivers to see if its still a problem?

Checkout nvnews on the linux nvidia section of the forum.

---

