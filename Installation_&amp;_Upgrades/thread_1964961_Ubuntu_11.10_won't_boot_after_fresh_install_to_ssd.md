---
title: "Ubuntu 11.10 won't boot after fresh install to ssd"
date: 2012-04-24
forum: Installation &amp; Upgrades
---

### Post by jjmatt on 2012-04-24
So I just installed an SSD in my computer. Previously I had ubuntu and windows 7 installed side by side on the same system (without the ssd). However after installing windows 7, if I go to install ubuntu 11.10 x64 (with the alt cd) the install goes through fine, but upon rebooting into ubuntu I can only get to a red screen (right after grub) where it hangs. I can't hit ctrl+alt+f1 to get any more details. I have tried disconnecting all drives (two 1.5 tb hdds and a bluray drive) and that doesn't fix the issue. Anyone have any thoughts?

Let me know if there's any info you need that may help get to the bottom of this.

System:
SSD: Samsung 830 256GB
HDD: Two 1.5TB Seagate Drives
RAM: 16GB DDR3 PC3-16000
Mobo: P8P67 EVO
CPU: i7-2600k
Video Card: Nvidia GoForce GTX 570

---

### Post by techsupport on 2012-04-24
> **jjmatt said:**
> So I just installed an SSD in my computer. Previously I had ubuntu and windows 7 installed side by side on the same system (without the ssd). However after installing windows 7, if I go to install ubuntu 11.10 x64 (with the alt cd) the install goes through fine, but upon rebooting into ubuntu I can only get to a red screen (right after grub) where it hangs. I can't hit ctrl+alt+f1 to get any more details. I have tried disconnecting all drives (two 1.5 tb hdds and a bluray drive) and that doesn't fix the issue. Anyone have any thoughts?

Let me know if there's any info you need that may help get to the bottom of this.

System:
SSD: Samsung 830 256GB
HDD: Two 1.5TB Seagate Drives
RAM: 16GB DDR3 PC3-16000
Mobo: P8P67 EVO
CPU: i7-2600k
Video Card: Nvidia GoForce GTX 570

Did you use Clonezilla to clone your OS onto the new SSD?

---

### Post by jjmatt on 2012-04-24
> **techsupport said:**
> Did you use Clonezilla to clone your OS onto the new SSD?
Nope, fresh install

---

### Post by techsupport on 2012-04-24
> **jjmatt said:**
> Nope, fresh install

Hang in there for a few days until someone who has an SSD and has Windows might know what to do. There is always:

[http://www.ubuntu.com/business/services/overview](http://www.ubuntu.com/business/services/overview)

---

### Post by darkod on 2012-04-25
Sounds like video driver issue.

Try to boot with the nomodeset parameter to see if that loads the OS. If it does, you can update the driver. If it still doesn't go away, you can make nomodeset permanent.

In the grub2 boot menu, highlight the ubuntu entry and hit 'e' for edit. That will show the boot lines. Use the arrows to go to the end of the line starting with linux, and after the 'quiet splash' add 'nomodeset'. Press Ctrl + X to boot.

---

### Post by jjmatt on 2012-04-25
> **darkod said:**
> Sounds like video driver issue.

Try to boot with the nomodeset parameter to see if that loads the OS. If it does, you can update the driver. If it still doesn't go away, you can make nomodeset permanent.

In the grub2 boot menu, highlight the ubuntu entry and hit 'e' for edit. That will show the boot lines. Use the arrows to go to the end of the line starting with linux, and after the 'quiet splash' add 'nomodeset'. Press Ctrl + X to boot.
Cool, that worked, thanks darkod. Not sure why I didn't think of that myself...

Anyway, for anyone reading this now, all I had to do was install my gpu drivers 

```
sudo apt-get install nvidia-current
```

for me, and restart and everything worked fine. w00t

---

