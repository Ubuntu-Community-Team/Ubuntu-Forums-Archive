---
title: "USB Install Not Registering"
date: 2014-10-06
forum: Installation &amp; Upgrades
---

### Post by vermox on 2014-10-06
I am trying to do a fresh install to upgrade from 13.04 to 14.04 LTS. I have made two seperate USB drives, one using the startup disk creator in Ubuntu and the other with Unetbootin. I downloaded the ISO off the Ubuntu site. The problem is that whenever I go to boot my computer from the USB it either goes to a blank screen or tells me that there has been a startup disc error. I've downloaded the ISO twice to make sure it wasn't an error in the first download but got the same result. What am I doing wrong?

---

### Post by sudodus on 2014-10-06
0. I suggest that you try the version 14.04.1 (and not the original 14.04). Several bugs are squashed in 14.04.1, and it needs much less updating afterwards.

1. Check that the download was successful with md5sum

```
md5sum your-downloaded-file.iso
```

should give you the same string as found at this link

[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

2. Try another tool to flash the installer to the USB pendrive, if you suspect that might be the problem. I think mkusb is very reliable, but Unetbootin works well for me too. See this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

3. You may have problems with a driver for some hardware in the computer. Usually it is detected and a suitable driver selected automatically, but sometimes you need a proprietary driver, or there is no linux driver at all. More information makes it easier to help, so please specify your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

4. You can try with some boot options. Start with **nomodeset**, but try also the other options (more than one each time is possible).

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by vermox on 2014-10-06
I am actually trying to install 14.04.1. Apologies for not being clearer about that. I checked the hashes and they match. I tried another Linux Live USB to flash the drive but still no luck.

This is a Pentium Dual Core E5200 2.50GHz, 2gb RAM, Gallium 0.4 on NV92. I'm using just a USB wireless adapter. 

I'm not quite sure why I'm having such difficulty. I installed the previous version of Ubuntu without any problems.

---

### Post by sudodus on 2014-10-06
I think the problem is some driver, either for graphics, where nomodeset might help,

or for wifi. You can test if it will work without the USB wireless adapter.

If still no luck, I suggest that you go back to the still maintained ***version 12.04 LTS***: standard ***Ubuntu*** with Unity and ***Kubuntu*** with KDE is supported until April 2017. Xubuntu is only supported until April 2015 and that version of Lubuntu has already passed end of life. An alternative is to try a community re-spin based on Ubuntu 12.04 LTS, for example ***Bento, Bodhi, LXLE*** or ***Linux Mint***, which also promise support until April 2017.

The drivers in 12.04 LTS are often better with old hardware, while the drivers of newer versions are better with new hardware. And 12.04 LTS has been gradually updated/upgraded, so it is up to date concerning security and other bug-fixes.

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu,  ...) before installing it]("http://ubuntuforums.org/showthread.php?t=2230389")

---

### Post by vermox on 2014-10-06
I've tried without the USB wireless adaptor and it's still a problem. I'm currently downloading version 12.04. How do I go about using nomodeset? (Sorry, I'm still very stupid when it comes to linux)

---

### Post by sudodus on 2014-10-06
I think there is a good description in the following link (use the mini-menu that is displayed when you press the F6 key)

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

