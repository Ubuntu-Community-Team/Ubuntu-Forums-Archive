---
title: "[SOLVED] Modprobe abnormal exit on Ubuntu Install"
date: 2008-09-12
forum: Installation &amp; Upgrades
---

### Post by s73v3r on 2008-09-12
I'm attempting to reinstall Xubuntu 8.04 on a slightly older machine, and am running into huge problems. Whenever I start the install, I usually get an error saying '/sbin/modprobe abnormal exit'. When it doesn't, it gets so far, and then stalls in the boot up process. I've tried specifying 'noacpi', 'noapic', 'nolapic' and 'ide=nodma' at boot time, with no success. I'm downloading the Alternate Install ISO now, but has anyone had a problem like this before? And could someone point me in a direction to fix it?

Just one more note: This machine was running just fine with Mythbuntu 8.04 just a while ago. Then some bad stuff happened, and now I have a wiped hard drive, so I need to reinstall.

---

### Post by Partyboi2 on 2008-09-12
I have read that some people have got around this by going into there bios and disabling onboard lan.

---

### Post by s73v3r on 2008-09-12
Did they just disable onboard LAN for the install duration, or permanently? I don't really want to get a new NIC unless the onboard one is totally shot.

---

### Post by Partyboi2 on 2008-09-13
I would say just for the installation period.

---

### Post by s73v3r on 2008-09-13
Even with the Onboard LAN disabled, I still get the modprobe error.

---

### Post by s73v3r on 2008-09-15
Turns out I had a bigger problem than I thought. I guess the clock speed was set too high for my memory and processor, which was causing the memory to have errors, and the processor to not do some things right. So I turned down the clock speeds, and everything installed and is running just fine <knock on wood>.

---

