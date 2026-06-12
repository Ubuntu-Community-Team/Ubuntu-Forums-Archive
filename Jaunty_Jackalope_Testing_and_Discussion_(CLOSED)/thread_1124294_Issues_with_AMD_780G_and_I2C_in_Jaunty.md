---
title: "Issues with AMD 780G and I2C in Jaunty?"
date: 2009-04-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by _gpf_ on 2009-04-13
I have been attempting to get my Pinnacle HDTV Stick (801e SE) to work in Jaunty for quite some time now without much success.  After trying no less than a dozen times, I gave up and tried it on different hardware, and, as if by magic, it worked flawlessly after copying the proper firmware.

The first system (the failed one) is a desktop PC with an Asus M3A78-EM motherboard, 4GB of DDR2, and a 250GB hard disk running Jaunty amd64 with all the most recent (as of Sunday night) updates.  The second system is a Dell Vostro 1700 laptop with 2GB of RAM also running a fully-updated Jaunty amd64.

Whenever I attempt to run scan/dvbscan/w_scan on the failed system, dmesg becomes clogged with:

```

s5h1411_writereg: writereg error 0x19 0xf5 0x0000, ret == 0)
dib0700: i2c write error (status = -108)

```

and the resulting scan attempt fails to find any signal.

On the laptop, I am able to run w_scan -fa -x to get tuning data, and then pick up local channels with scan and play in Totem.

lpsci outputs for both systems:

[Non-working]("http://pastebin.com/fa80c2f7")
[Working]("http://pastebin.com/f31efd30a")

Apart from the i2c failures, I'm stuck.  Are there known issues with the i2c bus on 780G chipsets or this motherboard?  My weak Google-fu couldn't find anything.

Thanks for any and all help.

---

### Post by _gpf_ on 2009-04-22
It turns out that the issues I was having were completely unrelated to the v4l driver and/or Jaunty.  I added a PCI USB 2.0 card and plugged the tuner stick into that and things are working right out of the box after doing a clean install of the Jaunty RC.

Thanks much to Devin Heitmueller at linuxtv.org for all his help.  This actually is an issue with the USB host controller on the AMD SB700, so the PCI card was a great and inexpensive (~10 USD) workaround.

---

