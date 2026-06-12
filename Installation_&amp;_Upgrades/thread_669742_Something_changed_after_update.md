---
title: "Something changed after update"
date: 2008-01-16
forum: Installation &amp; Upgrades
---

### Post by dodgingspam on 2008-01-16
I use Ubuntu on my laptop. In order to connect to wireless Internet I use a card, which I had to install with ndiswrapper. 

Everything worked fine until I ran some sort of update in late December. From that moment on every time I need to connect to Internet I have to open Terminal and manually type the following lines:

[PHP]
sudo modprobe ndiswrapper
sudo ndiswrapper -m  
[/PHP]

Is there a way to enter it in some settings to avoid this typing in step?

Thanks.

---

