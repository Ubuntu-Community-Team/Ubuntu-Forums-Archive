---
title: "Screen Goes Black/Blank After Trying to Run Xubuntu"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by EpicTTR on 2011-10-30
I just used Wubi to install Xubuntu to my computer. The install seemed successful. I rebooted my computer, and I selected Xubuntu from the options (the two options were Xubuntu and Windows 7, my default OS). However, Xubuntu just sort of flashes some text across the screen then lets me choose from a few "boot modes", I choose the Normal mode, and then I'm taken to a blank screen (black background, flashing white cursor, can't type anything in, nothing happens). And within around a minute of the blank screen, its like my laptop monitor completely shuts down (everything goes black, and the monitor isn't displaying black, but its completely off).

How can I fix this?

---

### Post by bcbc on 2011-10-30
Please post your computer brand/model/graphics card.

---

### Post by EpicTTR on 2011-10-30
> **bcbc said:**
> Please post your computer brand/model/graphics card.

I have an HP Pavilion g7 laptop. I'm not entirely sure, but I believe this is the one I purchased: [http://www.bestbuy.com/site/HP+-+Pavilion+Laptop+/+Intel%AE+Core%26%23153%3B+i3+Processor+/+17.3%26%2334%3B+Display+/+4GB+Memory+-+Pewter/3441304.p?id=1218402868391&skuId=3441304&st=HP%20Pavilion%20g7&cp=1&lp=1]("http://www.bestbuy.com/site/HP+-+Pavilion+Laptop+/+Intel%AE+Core%26%23153%3B+i3+Processor+/+17.3%26%2334%3B+Display+/+4GB+Memory+-+Pewter/3441304.p?id=1218402868391&skuId=3441304&st=HP%20Pavilion%20g7&cp=1&lp=1")

It comes with Windows 7 by default and I'm trying to use Wubi to install the latest version of Xubuntu.

---

### Post by bcbc on 2011-10-30
Some intel graphics chips have a problem with the backlight not coming on with Ubuntu - I thought this was patched for Ubuntu 11.10 though - but check anyway: if you look closely at the screen you should be able to tell whether the screen is on (with no blacklight) or whether it's truly off.

Another thing: remove 'quiet splash' and add 'nomodeset' instead. Instructions here: [http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) (wubi specific in post #8)

---

