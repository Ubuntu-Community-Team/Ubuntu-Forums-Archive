---
title: "Ubuntu server 20.04.03 does not boot on Raspberry Pi 3 Model B Plus Rev 1.3"
date: 2022-01-20
forum: Installation &amp; Upgrades
---

### Post by tobbey-hick on 2022-01-20
Dear all,

I was previously using this image on my raspberry Pi 4 (rev 1.1) and it worked wonderfully. Then I decided to upgrade my Raspi 3B+ with the very same image. Unfortunately, all I can see during boot process is this:
[IMG]https://i.ibb.co/VtCY7Py/20220120-090422.jpg[/IMG]

I tried with 2 different SD cards, and I got the exact same result. On the other side, Raspi 3B+ boots well on an old raspbian image:
Raspbian GNU/Linux 10 (buster)
Linux RasPiV2 4.19.118-v7+ #1311 SMP Mon Apr 27 14:21:24 BST 2020 armv7l GNU/Linux

And the image I try to use (from SD card) works perfectly with my raspberry pi 4 (rev 1.1). I looked and version=20.04.3&architecture=server-arm64+raspi should be compatible with my 3B+ can someone help me here ? I really don't know what is happening.

---

### Post by tobbey-hick on 2022-01-20
Ok simply typing "boot" in the uboot cmdline starts the boot process (and it boots successfully). However, that's a server image, I don't want to plug in a keyboard everytime I want to boot this machine. Any tips how to enable auto boot ? (that works perfectly fine with my raspberry pi4) ? Thank you in advance for your help

---

### Post by tobbey-hick on 2022-01-20
Now I need to understand how I can edit this bootdelay variable BEFORE generating my ubuntu img, or directly from userspace.
I tried to run
fw_printenv
But it returns
Configuration file wrong or corrupted
Not sure what to do

---

### Post by tobbey-hick on 2022-01-20
ok there are some example of
/etc/fw_env.config
inside
cat /usr/share/doc/u-boot-tools/examples/fw_env.config

---

### Post by ActionParsnip on 2022-01-20
If you get fully updated does it help?

---

### Post by MAFoElffen on 2022-01-21
> **tobbey-hick said:**
> However, that's a server image.
Yes... Your Raspberry Pi 3 Model B Plus can only run Server Edition.. And? 

What exactly do you want to do? Sound like at least to run headless right?

---

