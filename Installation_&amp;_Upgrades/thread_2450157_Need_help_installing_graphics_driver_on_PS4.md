---
title: "Need help installing graphics driver on PS4"
date: 2020-09-08
forum: Installation &amp; Upgrades
---

### Post by dpyro2 on 2020-09-08
I want to try getting Ubuntu working on my PS4 and need some help. At the moment I installed Ubuntu to USB using virtualbox and it boots fine but when I try on PS4 all I get is a black screen. I was thinking it's because the drivers are missing so I'm wondering if anyone can help me with compiling them in virtualbox.

[https://github.com/fail0verflow/ps4-radeon-patches](https://github.com/fail0verflow/ps4-radeon-patches)

---

### Post by CelticWarrior on 2020-09-08
Welcome.

In a VM you're using virtualized hardware. What would be the point of compiling for hardware that isn't there?
And I'm not sure about what you're trying to achieve here. A VM wouldn't run in a bare metal PC let alone a PS4?

---

### Post by dpyro2 on 2020-09-08
Ubuntu isn't installed as a VM, I'm just using virtualbox to install to USB.

[https://www.youtube.com/watch?v=VtRbtkCKvBM](https://www.youtube.com/watch?v=VtRbtkCKvBM)

I can boot off the usb on my PC and it works fine so not sure what's different to the video.

---

### Post by CelticWarrior on 2020-09-08
That's what happens when we don't understand things.
The only reason to use the complicated Virtualbox route is to have only one USB (installation target). Otherwise we'd need the installation media as well, another USB stick. That's all.

Now, if the installed system boots normally on a PC then you no longer need Virtualbox. 
The video and pretty much all instructions for what you want - a waste of time, being honest - were for Ubuntu 16.04 (original release, not point releases. The patch you're asking about is so old that probably won't compile for anything newer than the amdgpu version in that specific release. And then, even if it does, updates will screw it.

---

### Post by dpyro2 on 2020-09-08
What about the drivers for arch linux?
[https://github.com/Ps3itaTeam/ps4linux-video-drivers](https://github.com/Ps3itaTeam/ps4linux-video-drivers)

---

### Post by CelticWarrior on 2020-09-08
New for sure but won't install in Ubuntu.

---

### Post by ActionParsnip on 2020-09-08
Is there a homebrew distribution made for the PS4 rather than using Ubuntu? Could be easier

---

### Post by CelticWarrior on 2020-09-08
> **ActionParsnip said:**
> Is there a homebrew distribution made for the PS4 rather than using Ubuntu? Could be easier

Like there was one (officially) for PS2? No such thing now I'm afraid. Sony has been actively blocking those attempts. That's why they call it now "jailbreaking", a term originally associated only with Apple products.
In a nutshell, it's a lot of work for meh results.

PS - And now that I'm thinking about it... This very likely breaks the forum rules because the process implies a violation of the Sony's terms of use.

---

### Post by dpyro2 on 2020-09-08
> **ActionParsnip said:**
> Is there a homebrew distribution made for the PS4 rather than using Ubuntu? Could be easier
I have another stick running psxita but I wanted to see if I could get Ubuntu working as I prefer it to arch linux.

---

