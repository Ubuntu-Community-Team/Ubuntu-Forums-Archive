---
title: "Run Ubuntu 7.10 from Windows using USB portable HD"
date: 2008-03-19
forum: Installation &amp; Upgrades
---

### Post by bapaknyaAnak2 on 2008-03-19
Hello Guys,

I did this: [http://www.pendrivelinux.com/2008/01/11/run-ubuntu-710-from-windows/](http://www.pendrivelinux.com/2008/01/11/run-ubuntu-710-from-windows/)

It works great, but I could not browse internet with it. I use sierra wireless AC 875. Anyone can help me ?? By the way, do I need to press install button on UBUNTU 7.10 desktop and going through the procesess ?? As you can see on my questions, I am totally new:confused:. Pls advice anyone.

---

### Post by dstew on 2008-03-20
> I use sierra wireless AC 875. Anyone can help me ??First, update your Ubuntu system (System --> Administration --> Update Manager). Then, check in the Restricted Drivers Manager for a driver. If you see one, click and install it. If not, you may already have the driver installed. Go to the Network menu and see if the card is there. Click Properties and see how it is configured.

If the card doesn't show up in the Network panel, open a terminal (Applications --> Accessories --> Terminal) and on the command line enter ```
lspci
```Post the results to the forum.

> do I need to press install buttonOnly if you want to install Ubuntu onto your hard drive.

---

