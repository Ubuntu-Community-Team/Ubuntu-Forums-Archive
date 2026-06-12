---
title: "Downgrading to Gutsy in Inspiron 1520"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by readingitsideways on 2008-04-27
Couldn't get Hardy to work properly on my Dell Inspiron 1520.

Many of the little bugs with Gutsy, like the sound buttons, sound etc worked out of the box, but bigger problems have crept in:

The Wireless doesn't work, and even using ndiswrapper and following several tutorials I couldn't get it to work. Also the nvidia cards are buggy, with pink halos around windows instead of shadows... Apparently installing the official nvidia drivers fixes it, but I couldn't figure out how to do that, and it will break again when there's a Hardy update - so guaranteed frustration.

So, I'm back on Gutsy. I'll try again in a month or so when all the bugs are worked out...

---

### Post by bsell on 2008-04-27
Install EnvyNG and follow the instructions. It will load the new Nvidia drivers. 

```
sudo apt-get install envyng
```

---

### Post by readingitsideways on 2008-04-27
I tried envyNG - no luck

---

### Post by bsell on 2008-04-27
You can try the command below or install the packages through Synaptic. 

                           ```
sudo apt-get remove nvidia-glx nvidia-glx-dev nvidia-kernel-source && apt-get install nvidia-glx-new nvidia-glx-new-dev nvidia-kernel-common nvidia-new-kernel-source nvidia-settings
   
  
```

---

### Post by readingitsideways on 2008-04-27
apparently the problem is with nvidia-glx-new. Anyway, the wireless issue is also there and even if I fixed the nvidia problem it would be back with updates. I'm back on Gutsy now and happy. I'll wait for someone to put a walkthrough for Hardy on the Inspiron 1520. Gutsy is good, so no worries.

---

### Post by amyst on 2008-04-27
I have 1520 too and have similar problems. Some of the auxiliary packages (compiz-fusion, etc) don't work - unlike Gutsy, a bit search on the forum wouldn't fix these problems on Hardy.

---

### Post by twright on 2008-04-27
you if you run the upgrade from gutsy the gutsy kernel can still be selected at bootup so wireless will work and you will get all the new program versions

---

