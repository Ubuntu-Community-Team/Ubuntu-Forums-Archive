---
title: "Installing audio/video"
date: 2011-08-31
forum: Installation &amp; Upgrades
---

### Post by mobayu on 2011-08-31
I got difficulty on playing audio/video files on 11.04 ubuntu am unable to update and I got recommendation for installing VLC then I need to Install VLC but still it says package not installed....please help me

---

### Post by saltmarshlamb on 2011-08-31
Make sure that you have repos enabled.

From the Ubuntu Software Centre - Edit - Software Sources.

Enable main, universe and restricted, multiverse if you want those as well. Reload when asked to do so. Then try installing VLC again. 

If you still have issues, open a terminal and run the following - paste the output so we can see what's happening

```
sudo apt-get update &&sudo apt-get install vlc
```


[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

