---
title: "I goofed my kernel upgrade"
date: 2012-09-08
forum: Installation &amp; Upgrades
---

### Post by afbase on 2012-09-08
I was upgrading the linux kernel and now none of my drivers (mouse, NIC, wireless, video card, etc) work.  My computer won't connect to the internet (I am writing this in windows 7).

I typed
```
sudo apt-get install linux-generic

```
and then I restarted.   How can I fix this?

FYI,  is it possible to download debian packages onto a usb drive (hopefully it can see USB)?  Or better yet, could I boot from a USB 12.04 live cd and recover/repair my kernel?

---

### Post by coffeecat on 2012-09-08
If you are dual-booting, at the grub menu choose "previous Linux versions" and then boot into a previous kernel, one that was working. If you do not see the grub menu when you first start your system, press the shift key when the POST screen is showing to reveal the menu, and then as before.

It's unusual for a kernel upgrade to break so comprehensively. Which version of Ubuntu are you running, what was the version number of the kernel which is not working, and do you have the proposed repository enabled? (If you don't, don't enable it.)

---

### Post by afbase on 2012-09-08
> **coffeecat said:**
> If you are dual-booting, at the grub menu choose "previous Linux versions" and then boot into a previous kernel, one that was working. If you do not see the grub menu when you first start your system, press the shift key when the POST screen is showing to reveal the menu, and then as before.

It's unusual for a kernel upgrade to break so comprehensively. Which version of Ubuntu are you running, what was the version number of the kernel which is not working, and do you have the proposed repository enabled? (If you don't, don't enable it.)
I will look for the older kernel versions when I get home.

The reason why it is unusual is because I manually tried to install the new kernel.  I made a big goof.

---

