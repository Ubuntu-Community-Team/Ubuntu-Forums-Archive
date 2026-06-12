---
title: "Installing Ubuntu on new Toshiba Satellite A100 laptop"
date: 2006-03-04
forum: Installation &amp; Upgrades
---

### Post by ZMaster on 2006-03-04
Has anybody gotten any tips about installing Ubuntu on a Toshiba Satellite A100 laptop? Since this is a relatively new model, I did not find much infos on the net.

Main specs are :
- Intel Centrinio Duo processor 1.66 Ghz
- Intel Golan wireless card (abg)
- ATI X1600 128mb - will I be able to install ATI drivers?

I heard that on some laptops the bios was located on the HDD, is it the case with that model?

Precision : I used Ubuntu on a previous laptop (Toshiba Satellite A20) which was working well.

Thanks.

---

### Post by XPiS on 2006-04-21
I've installed Ubuntu 5.10 on this laptop without serious problems, installed drivers for video, audio (alsa), modem driver not works for now.

---

### Post by Chris W on 2006-04-28
I've installed Ubuntu 5.10 on the A100/4600, even using the latest nvidia driver was a bit iffy, but it works fine without accelleration with the nv driver.  
e1000 ethernet needs latest driver from intel to work
ipw3945 also works fine with latest driver from intel
Intel HDA works, not well with 2.6.12, but with 2.6.16 it's pretty good

No bluetooth, toshiba_acpi doesn't work

If anyone has any ideas about the bluetooth i'd love to hear them, i've had a look around, nothing suggested for other Toshiba laptops seems to work for me

---

