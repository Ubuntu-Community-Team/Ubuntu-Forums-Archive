---
title: "D/L Ubuntu outside of Ubuntu"
date: 2008-05-04
forum: Installation &amp; Upgrades
---

### Post by thomasyo on 2008-05-04
where i live at the moment i currently only have my dads wireless usb internet and that only has drivers for windows platforms. Is there anywhere i can go to download ubuntu software without needing to do it direct while im using ubuntu???

---

### Post by Pumalite on 2008-05-04
You can download it in Windows from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by thomasyo on 2008-05-04
sorry friend i should have made myself more clear. I have hardy heron but i cannot connect to the internet while running it because  it is a windows only internet connection because of its required drivers. is there somewhere i can get the ubuntu software to dl to my comp and install it once on ubuntu again?

---

### Post by Pumalite on 2008-05-04
You can order the disks.

---

### Post by thomasyo on 2008-05-04
Hmm very well I see my options are limited until i get some real internet in my life again. Thankyou for your help.

---

### Post by MattBD on 2008-05-04
> **thomasyo said:**
> sorry friend i should have made myself more clear. I have hardy heron but i cannot connect to the internet while running it because  it is a windows only internet connection because of its required drivers. is there somewhere i can get the ubuntu software to dl to my comp and install it once on ubuntu again?

It's difficult to do that because of the dependencies many packages will have - for instance, to install one thing, you may need to install somethings else, which then may need something else, so it's not easy to do.

You might want to check out [AptonCD]("http://aptoncd.sourceforge.net/index.html"), which you can use to get copies of packages and burn them to a CD, but that still needs you to be able to connect to the Internet to get them in the first place.

A very convoluted way you could do it would be to install VirtualBox on the Windows install, put Ubuntu on there, add APTonCD to that install, install the packages on that one, use APTonCD to burn them to a CD then use the CD to install them, but that's quite a bit of work.

Only other thing I can suggest is buy a new router with Ethernet sockets - USB routers have a terrible reputation.

---

