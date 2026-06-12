---
title: "ubuntu 10.04 no sound"
date: 2010-11-11
forum: Installation &amp; Upgrades
---

### Post by grrrbob on 2010-11-11
i have installed 10.04 lucid ubuntu fresh and there is no sound. 

i have nvidia geforce gt220 graphics card and the motherboard is by intel. i have installed nvidia proprietary driver and also upgraded alsa. 

alsamixer has been checked to ensure nothing is muted but still no sound. alsamixer does recognise my card

any ideas?

my previous install had sound working on both my monitor and through hdmi to my lcd tv. however that went messy after upgrading which has resulted in this fresh install.

kind regards

---

### Post by Dudutzu on 2010-11-11
It happend to me as well the only thing that worked was to reinstall ALSA
Uninstall :
```

 sudo apt-get purge linux-sound-base alsa-base alsa-utils

``` 

and reinstall :  
 ```

sudo apt-get install linux-sound-base alsa-base alsa-utils gdm ubuntu-desktop

```

---

