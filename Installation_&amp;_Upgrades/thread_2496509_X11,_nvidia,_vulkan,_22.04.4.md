---
title: "X11, nvidia, vulkan, 22.04.4"
date: 2024-04-01
forum: Installation &amp; Upgrades
---

### Post by yuralamov on 2024-04-01
After the update on 22.04.4 there were delays. Most noticeable in the terminal. If you switch to wayland, there are no delays. But then the games don't work ;(
On 22.04.3 everything worked.

---

### Post by ubfan1 on 2024-04-01
Which Nvidia hardware?  Laptop?  Did you switch to the 6.5 kernel on this upgrade?  Some old Nvidia cards may have trouble with the 6.5 kernel. Post the output of xrandr --listproviders (when running X) -- sometimes the source/sink get reversed and need environment variables to switch back.

---

### Post by yuralamov on 2024-04-01
Desktop i5-9500F GTX1650
Providers: number : 1
Provider 0: id: 0x1b7 cap: 0x1, Source Output crtcs: 4 outputs: 4 associated providers: 0 name:NVIDIA-0

---

### Post by MAFoElffen on 2024-04-02
I have NVidia GTX 1650 Ti, using driver nvidia-driver-535...

Here is my workarounds for compiling the drivers for kernel 6.5.0: [https://ubuntuforums.org/showthread.php?t=2494273&p=14175164#post14175164](https://ubuntuforums.org/showthread.php?t=2494273&p=14175164#post14175164)...

There are more in that same thread. I tested a few and posted them there for users to find and/or for members to refer to.

---

### Post by yuralamov on 2024-04-02
I compile without errors. Nvidia-drivers 535 and 550 from ubuntu, Cuda-drivers 535 and 550 from nvidia developer. All Ok.
I also fixed kernel 6.2.0.26 without hwe from 22.04.3 and then upgraged. Also in the grub I disabled the wayland. But the delays and jerks did not disappear.
Also everything works in ubuntu 22.04.3. but if you upgrade or installed to ubuntu 22.04.4....
I got tired and installed xubuntu 22.04.4. Everything works without problems here. And toys and development tools.
I am 58 years old. I won't live to see wayland become friends with vulkan. I remember the time when I danced around the mandrake. Do not want anymore.

---

