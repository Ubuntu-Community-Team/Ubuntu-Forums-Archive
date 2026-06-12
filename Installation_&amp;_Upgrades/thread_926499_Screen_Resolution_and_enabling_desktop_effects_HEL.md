---
title: "Screen Resolution and enabling desktop effects HELP!!!"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by racsoarias on 2008-09-22
I am new at linux and I can't get 1024x860 resolution in my LG Studioworks 553V monitor, I plug other monitor and I got up to 1440x1024, now I am using my LG 553V at 832x624 75Hz and I can't stand it anymore and I have no idea what to do, please HELP!!!!!! I need an higher resolution, everything looks huge!!

Also, if anyone can help me, I want to enable desktop effects, this is my system information
MOTHERBOARD MODEL: BIOSTAR K8M800 Micro AM2
INTEGRATED VIDEO: VIA S3 UniChrome Pro, Memory Share Up to 64MB 
There is one chipset I get to see: VT8237R PLUS, I think it is the responsible of making everything to work, nevertheless, if someone can help me I will appreciated it ... a lot... and I will get all the information needed.

Thank you :)

---

### Post by Ryadt on 2008-09-22
For your resolution, try ```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by wolterh on 2008-09-22
Well, what Ryadt just posted will reset your configuration so that any error with your graphics card that you made would be restored as in a fresh installation of ubuntu.

Now, I think that the problem may be that your card is not fully supported by the OS; but, do not trust my word, for I am just guessing

---

### Post by racsoarias on 2008-09-22
It did not worked even when it was a fresh copy, How can I know if it is now fully supported? or even better, how can I make it work!?

---

