---
title: "Deleting old updates"
date: 2012-05-24
forum: Installation &amp; Upgrades
---

### Post by tazz4vr on 2012-05-24
Sorry for the newbie question, but.....

I am using Ubuntu 12.04.  Normally I will allow all updates that are showing in my Update Manager.  My question is when these new updates are installed, do they automatically over-ride any previous ones?  If not, should I be deleting them?

---

### Post by madverb on 2012-05-24
No, you don't need to worry about that.

---

### Post by raja.genupula on 2012-05-24
> **tazz4vr said:**
> Sorry for the newbie question, but.....

I am using Ubuntu 12.04.  Normally I will allow all updates that are showing in my Update Manager.  My question is when these new updates are installed, do they automatically over-ride any previous ones?  If not, should I be deleting them?

what ever the updates they will be in /var/cache/apt location and you can remove them and unwanted ,not necessary updates you can remove by doing like

```
sudo apt-get autoclean
sudo apt-get autoremove
```

this will take care .

---

### Post by tazz4vr on 2012-05-25
Thank you both for info... I guess my only concern would be manually removing something that is thought to be old or not needed, and in turn, I really needed it!

So for now, I think I will stick with the 'auto' part of the clean up.

---

### Post by raja.genupula on 2012-05-25
[LEFT]cool ! now mark the thread as solved from thread tools . 
[/LEFT]

---

