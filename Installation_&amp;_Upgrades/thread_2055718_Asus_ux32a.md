---
title: "Asus ux32a"
date: 2012-09-10
forum: Installation &amp; Upgrades
---

### Post by daniel38301 on 2012-09-10
Hi i try to install ubuntu 12.04.1 on my laptop but i always get a black screen just after select run ubuntu or install on hard drive.

---

### Post by 2F4U on 2012-09-10
Did you already try to use the nomodeset grub kernel parameter?

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

If that doesn't help, post your complete hardware specs.

---

### Post by killtroubles on 2012-09-10
You must be using CD , right??
using CD/DVD is the ugliest option as it sucks a lot of time .. causes a lot of errors .

Well i urge you to make a bootable USB ( 1GB or more ) stick using Unetbootin [http://unetbootin.net/](http://unetbootin.net/)
use the disk image option and browse iso , and go.

boot using that , you will barely face any probs!!

---

### Post by daniel38301 on 2012-09-10
No im not using cd/dvd my laptop doenst have one anyway.

---

### Post by BandedHawk on 2012-09-18
You can get the install to work when you connect to an external (HDMI) monitor. However, the kernel problem remains with the install (at least for me). You need to get a Quantal Kernel (from kernel.ubuntu.com/~kernel-ppa). I've got the last stable kernel (3.5.4). It works ok, but you still need to boot with nomodeset or i195.modeset=0. Also, if you installed the main system on the SSD, you may get kernel panics (someone theorized it is a timing issue, as on the second boot, going through the Grub recovery, everything works fine - my experience too). Also, it won't detect both the external and internal monitors in this mode - so if you plug the external one, it will default to that, and you can't switch to the laptop monitor.

Basically, I guess because our UX32a's are so new, the kernel support sucks for them. I'll probably try the 3.6 release candidates next.

---

### Post by opennomad on 2012-09-20
I'm running a ux32a and it is functional. I used most of the suggestions at: [https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)

I had to make sure that I used the 64bit installer which detects the UEFI booting scheme.

One odditity I've noticed is that the screen occasionally remains black. Not turned off but black. In that case the Fn-F1 still works to suspend and the screen normally comes back normal after resume. Sometimes it takes 2 or 3 tries. running xrandr or the display utility can also cause that behavior.

Other than that everything works excellently.

---

