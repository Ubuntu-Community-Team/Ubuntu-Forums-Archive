---
title: "Question on HAL/fdi"
date: 2009-06-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2009-06-22
According to dmesg the brightness keys of my laptop are unknown (they work without a problem thought). The messages says I can make them known via typing:
```
setkeycode <scancode> <keycode>
```

So I looked up the keycode in /usr/include/linux/input.h and added:
```
setkeycode e011 224
setkeycode e015 225
```

to the /etc/rc.local - errors gone, everything fine. But it should be possible to pack this information into a (custom) *.fdi file and let HAL do the work, right? And there I failed. I've put:```

<device>
  <match key="system.hardware.vendor" prefix="MySystemVendor"> 
    <append key="input.keymap.data" type="strlist">e011:brightnessup</append>
    <append key="input.keymap.data" type="strlist">e015:brightnessdown</append>
  </match> 
</device>
```
in every place where I could find fdi-files but it didn't work - dmesg still showed errors when pressing the buttons.

Could someone please give me a link or explain how this fdi-file-thing works? What should work and what shouldn't work?

---

### Post by chrisccoulson on 2009-06-22
That is because HAL no longer handles keymaps in Karmic. This is done with udev-extras now, which AFAIK, ships its own keymaps. It might be worth you grabbing the udev-extras source and having a look:

```
apt-get source udev-extras
```

---

### Post by MacUntu on 2009-06-22
> **chrisccoulson said:**
> That is because HAL no longer handles keymaps in Karmic

](*,)

Thanks for the hint!

---

### Post by 23meg on 2009-06-22
More information on the transition to udev-extras:

[http://martinpitt.wordpress.com/2009/05/08/devicekit-update-future-handling-of-fn-key-maps/](http://martinpitt.wordpress.com/2009/05/08/devicekit-update-future-handling-of-fn-key-maps/)
[https://wiki.ubuntu.com/Halsectomy](https://wiki.ubuntu.com/Halsectomy)

---

### Post by MacUntu on 2009-06-22
Thank you as well. :)

---

### Post by plun on 2009-06-22
I have similar trouble but worse with a USB 3G modem from Option.

It was earlier added to the kernel but seems to be wrong detected now...

Probably to just file a bug but against which package ????

---

