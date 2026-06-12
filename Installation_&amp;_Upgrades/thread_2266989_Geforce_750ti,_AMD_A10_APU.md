---
title: "Geforce 750ti, AMD A10 APU"
date: 2015-02-26
forum: Installation &amp; Upgrades
---

### Post by gupyfish on 2015-02-26
Every time I try to install Ubuntu it doesn't work. First the bios screen comes up then the purple Ubuntu installing screen then after a few moments the screen goes black, not making it to the options page. Not sure what is causing the problem. In my computer I have 2 500 gb HDD, 1 geforce 750ti, an amd a10 APU, 8gb of corsair ram and 500watt PSU.

---

### Post by v3.xx on 2015-02-26
Got several hits on Geforce 750

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=geforce+750&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=geforce+750&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by mörgæs on 2015-02-27
Nvidia often needs either the nomodeset boot option or closed-source drivers. At least the former is easy to try.

---

### Post by efflandt on 2015-02-27
When I initially installed 64-bit 14.04.1 with GTX 750 Ti, I used **nomodeset** boot option for live/install and that worked fine. To do that press any key when booting live/install and you see purple screen with keyboard mouse icons at bottom, select your language, then press **F6** and use space bar to select **nomodeset**, then Esc back to boot menu.

But when I booted the installed system I don't think I could even get to gui login, and when I tried to log into a text console it would display the motd for an instant and immediately went back to login prompt. And nvidia-current did not support that new card. So I would suggest booting to recovery, enable networking, wait if that does not seem to return right away, then go to a root console from that menu. Then assuming it is a fresh install or you purged any other nvidia drivers (you don't need to use sudo from root console like you normally would elsewhere):```
apt-get update
apt-get install nvidia-331-updates
```
PS: For anyone with a laptop looking at this I heard that nomodeset does not work for hybrid Intel/Nvidia graphics. So when I recently installed 64-bit 14.04.1 to mSATA SSD on laptop in my sig, I did not use that, but installed the same nvidia-331-updates. And that works fine

---

