---
title: "Ubuntu boots to purple screen"
date: 2019-07-07
forum: Installation &amp; Upgrades
---

### Post by Vinodh Moodley on 2019-07-07
I installed Ubuntu 19.04 on my PC running a AMD 2700X and a RTX 2070. When I boot to the live USB, additional drivers indicates that my RTX 2070 is detected. When I actually install Ubuntu and reboot the first time, it just gets to a purple screen and gets stuck there.I tried pressing Esc or Shift or any other button to get to grub to insert the "nomodeset" option but grub refuses to open. It always goes directly to booting Ubuntu and getting stuck. I tried lugging in a wired USB keyboard but it does the same.

I then tried ubuntu 18.04. It installs but doesn't detect my GPU via additional drivers. I installed Nvidia drivers manually via terminal but it goes to a orange splash screen on reboot and gets stuck there.

I've disabled secure boot and did a clean install of 19.04 and it does the same. My other PC that has identical hardware except that the GPU is a GTX 1080 instead of an RTX 2070 works fine with Ubuntu 19.04, 18.04, Manjaro etc

Anyone have any ideas?

---

### Post by CatKiller on 2019-07-07
> **Vinodh Moodley said:**
> 
I then tried ubuntu 18.04. It installs but doesn't detect my GPU via additional drivers. I installed Nvidia drivers manually via terminal but it goes to a orange splash screen on reboot and gets stuck there.

Support for the Turing cards came in with the 410 branch, which is newer than the ones included in the 18.04 repository. You'll need to add the [graphics drivers PPA](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa).

You should also really be using UEFI rather than Legacy BIOS.

---

### Post by Vinodh Moodley on 2019-07-07
I installed the Nvidia driver 430 manually. This is the driver that causes the issue. Also, i'm only running in UEFI, not BIOS mode.

Either way, it still won't explain why 19.04 has the same issue.

---

### Post by CatKiller on 2019-07-07
> **Vinodh Moodley said:**
> Also, i'm only running in UEFI, not BIOS mode.

> **Vinodh Moodley said:**
> When I actually install Ubuntu and reboot the first time, it just gets to a purple screen and gets stuck there.

Purple means that it's in Legacy BIOS mode.

You'll need the Compatability Support Module turned off, and to have booted your install media in UEFI mode, to have a successful UEFI installation. Otherwise it will fail to boot. 

To get to the Grub menu you hold the Shift key from a BIOS install, or spam the Esc key in UEFI mode. 

You should probably also see if there is an updated BIOS/UEFI from your motherboard manufacturer.

---

### Post by Vinodh Moodley on 2019-07-07
Thanks. It is definitely in UEFI mode but CSM is still on. I'll switch it off and try again. 

I've tried the Esc key and the Shift key (both left and right) and no response. Hopefully switching off CSM will fix it.

---

### Post by Vinodh Moodley on 2019-07-07
I finally figured it out: I had a second screen hooked up that I assumed was unplugged. It wasn’t. It was just switched off. The purple screen just meant that the login window was on the other display that was off. I felt like a moron when I realized my mistake but I’m just glad it’s fixed. Thanks for the help anyway. It’s appreciated. 

[[IMG]https://i.ibb.co/G0HpxFm/2-D67-C66-E-0-BFE-4-E2-B-A69-D-DB59742687-FB.jpg[/IMG]]("https://ibb.co/FKH3xnp")

---

### Post by CatKiller on 2019-07-07
Haha, awesome :) Glad you're up and running.

---

