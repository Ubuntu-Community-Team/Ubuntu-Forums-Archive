---
title: "Restore MBR after Windows install?"
date: 2006-03-14
forum: Installation &amp; Upgrades
---

### Post by danhm on 2006-03-14
I have to install Windows so I can play [The Elder Scrolls IV: Oblivion](http://elderscrolls.com/home/home.htm). The only problem is that it'll take over the MBR and not let me boot into Ubuntu after...how can I restore it? 

I have a /boot partition, which I assume would be useful for this sort of thing.

---

### Post by cronholio on 2006-03-14
You will need to boot a Live CD (Knoppix, Ubuntu Live or something...) and run grub. Do:

```
root (hd0,0) 
setup (hd0) 
```

I assume your Ubuntu is on /dev/hda1. Otherwise change parameters accordingly. You will also need to include Windoze in /boot/grub/menu.lst. There is a sample entry in that file that you can uncomment. Just set it to the appropriate partition.

And don't tell me you are playing Oblivion already... Isn't it due for next Monday?:o

---

### Post by danhm on 2006-03-14
Thanks!

I'm not playing it yet, just getting ready.

---

### Post by kaamos on 2006-03-14
Here is some more info: [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows](https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows)

---

