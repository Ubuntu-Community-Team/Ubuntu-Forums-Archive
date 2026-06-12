---
title: "Upgrade LTS"
date: 2013-01-07
forum: Installation &amp; Upgrades
---

### Post by stefano91 on 2013-01-07
Hi guys!

I wanted to upgrade my Ubuntu! 

I installed ubuntu 9.10 on my netbook few days ago (it was a sort of emergency and was the only version I had in iso file). Then I decided to keep it and to upgrade it. I upgrade it to 10.04 and then I wanted to "jump" to 12.04. 

Everything fine, but when at the end I had to reboot I encounter a problem. I can see the Ubuntu loading page and then the monitor turn off, but the netbook is still on.

What's wrong? What can I do?
The recovery mode apparently works!

Thank you!

---

### Post by forkandles on 2013-01-08
stephano91,

Upgrades are fraught with danger, as you have just found out!

Remove the battery for a short while. Replace it and then do a fresh installation, in this case with 12.04 (Ubuntu/Kubuntu/Xubuntu etc) or whatever. 

You have probably installed from a USB drive previously, unless you have a USB DVD writer.
Booting from a USB drive:
I used Unetbootin (second answer down): 

[http://askubuntu.com/questions/15429...rking-in-12-04](http://askubuntu.com/questions/15429...rking-in-12-04)

Before this, I formatted the USB drive:
[http://freshtutorial.com/format-pen-...-drives-linux/](http://freshtutorial.com/format-pen-...-drives-linux/)

The USB stick must also be mounted. 
In my case:

```
sudo mkdir /media/Corsair

sudo mount /dev/sdc1 /media/Corsair
```


In the BIOS set USB drive to boot first and you should be okay.

---

