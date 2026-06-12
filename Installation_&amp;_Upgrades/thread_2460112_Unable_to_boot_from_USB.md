---
title: "Unable to boot from USB"
date: 2021-04-02
forum: Installation &amp; Upgrades
---

### Post by davoudi on 2021-04-02
So I created a bootable USB derive with several software, Etcher, UUI and refus. Unfortunately, I cannot boot from USB from my desktop in order to install Ubuntu 20.04 LTS. I used the same USB in my laptop and it booted without any problem. Is that possible to burn a DVD in order to install Ubuntu?

Any help is appreciated.

---

### Post by CatKiller on 2021-04-02
> **davoudi said:**
> Unfortunately, I cannot boot from USB from my desktop in order to install Ubuntu 20.04 LTS. 

The settings for boot order and boot devices will be in your UEFI settings. Where they are and what they're called will vary by UEFI manufacturer. Some will also have a button to press for a one-time boot menu to let you boot a non-default device. 

> Is that possible to burn a DVD in order to install Ubuntu?

Of course. Just burn the image to the DVD with your favourite DVD-burning software. Then boot the machine from the DVD.

---

### Post by crip720 on 2021-04-02
I have a Dell laptop.  When trying to install, I had same problem.  With some googling, found that I had to enable booting from a USB in bios/UEFI.  Most other laptops, just had to plug in USB/DVD and away I go.

---

### Post by hikariws on 2021-04-02
On my office's PC, UEFI is very old (or is it still BIOS?) and they didn't expect us to boot from USB. But flash drives are recognized as HD. We need to put HD on top order, then enter HD, and we see flash USB listed there together with HD.

U should try to troubleshoot ur laptop. But yes, u can burn the ISO to an optical media and boot from it.

---

### Post by davoudi on 2021-04-03
Thanks for information. I did it by changing the order of booting. Somehow the booting order has changed without me noticing it.

---

