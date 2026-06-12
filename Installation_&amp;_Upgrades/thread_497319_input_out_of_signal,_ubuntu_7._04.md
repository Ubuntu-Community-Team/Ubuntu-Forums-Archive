---
title: "input out of signal, ubuntu 7. 04"
date: 2007-07-10
forum: Installation &amp; Upgrades
---

### Post by dzul1 on 2007-07-10
Hello, I am installing ubuntu 7 and my monitor goes blank and reads " input out of signal" , any suggestions? thank you.

---

### Post by Qrk on 2007-07-10
Try pressing and holding <ctrl><alt><backspace>, or <ctrl><alt><f2>. If your monitor displays a login prompt, (text based) type in "ubuntu"(no quotes, of course). If not, I really am not sure what you should do.

If this works (I don't think you'll need a password), type in this code:

```
sudo dpkg-reconfigure xserver-xorg
```

On the second screen, it will ask you to choose a display driver for your monitor. If you are not sure which to pick, I'd recommend "vesa"
 
Go through the rest of the options as best you can. Most of the defaults are just fine. 

Once you have done all of this, try starting the GUI again, with

```
startx
```

---

### Post by dzul1 on 2007-07-10
Thank you very much for your time and for this info, I am going to try it, and once again thank you very much

---

