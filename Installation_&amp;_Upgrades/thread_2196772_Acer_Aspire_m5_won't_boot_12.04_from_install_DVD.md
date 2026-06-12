---
title: "Acer Aspire m5 won't boot 12.04 from install DVD"
date: 2013-12-31
forum: Installation &amp; Upgrades
---

### Post by weaselman on 2013-12-31
I am trying to install 12.04 on my Acer Aspire. It boots to the first screen (the dark magenta image with  icons of a keyboard, and a little man in a circle - whatever that means - at the bottom), then the screen goes dark. The drive keeps spinning for a while, with the light flashing, then it stops and the light goes off ... the screen remains dark. 
I tried it in EFI and legacy modes with the same result. Secure boot is disabled. MD5 is a match. I am able to boot my desktop from the same DVD. 

Any ideas?

Thanks!

---

### Post by sudodus on 2013-12-31
Press the Enter key, when you see those symbols at the bottom of the page. Then you should be able to select language (at least in BIOS mode) and then continue. But if you have Windows installed in UEFI mode and want dual booting, you need Ubuntu 64-bit and to install it in UEFI mode too.

Maybe you have problems with the graphics chip/card. Try the boot option ***nomodeset*** (and maybe also some other boot options). See

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by weaselman on 2014-01-01
Yes, nomodeset did it, thanks!
I was able to boot, and do the install. 
Now the next problem is that when I boot to the installed system, it seems to be working ... except, that it does not respond to mouse (trackpad) at all - neither to clicks nor to movements. 
Any ideas?

---

### Post by sudodus on 2014-01-01
That is probably a hardware driver issue too. Is it possible to connect a standard USB mouse and test if it works? I don't know about the trackpad. Can you find anything on the internet about it?

If I understand correctly, you have installed 12.04 LTS. It might also be a good idea to test with the version 13.10. The drivers have probably improved for new hardware, so you might have better luck.

---

### Post by weaselman on 2014-01-01
Well, what I don't understand is, if it is a driver problem, then how come it works fine when I boot from the dvd (not only the trackpad, but even touch screen works)? Why can't the installed system use the same driver?

---

### Post by sudodus on 2014-01-01
What works live is supposed to work installed too. This is strange.

---

### Post by weaselman on 2014-01-02
Yes, that's exactly my thinking. However, this is what I get. I even tried reinstalling (several times), and still got the same result :(

---

### Post by sudodus on 2014-01-02
Try to install another flavour of Ubuntu 12.04 LTS: Kubuntu, Xubuntu, Lubuntu or even Ubuntu Studio or Ubuntu Gnome.

Kubuntu has a fancy KDE desktop environment
Xubuntu has a medium light XFCE desktop environment
Lubuntu has an ultra-light LXDE desktop environment
Ubuntu Gnome has the medium light Gnome desktop environment
Ubuntu Studio has the medium light XFCE desktop environment (at least the 12.04 LTS version)

The iso files are somewhat different, and you might have better luck with one of those. The engine under the hood is the same - Ubuntu - in all these flavours.

---

