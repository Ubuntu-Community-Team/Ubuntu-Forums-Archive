---
title: "wireless for Toshiba Satellite C855-1UT"
date: 2013-01-12
forum: Installation &amp; Upgrades
---

### Post by hirohitosan on 2013-01-12
Hi there

I just bought an Toshiba Satellite C855-1UT laptop and I installed ubuntu 12.10, but the wireless doesn't work. Does anyone knows where to find wireless driver for it?

Thanks

---

### Post by forkandles on 2013-01-12
Your driver should be the Realtek RTL8273AE-BT.

Check your driver in Terminal:

```
sudo lshw -C network
```


Follow the instructions for whichever route you prefer:
[http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized](http://askubuntu.com/questions/139632/wireless-card-realtek-rtl8723ae-bt-is-not-recognized)

---

