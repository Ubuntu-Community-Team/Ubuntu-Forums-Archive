---
title: "Hardcore ubuntu uers help me out from this serious problem."
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by catherinek1 on 2008-09-29
[B]I have been facing this problem whenever i try to install. I think that this is a serious problem. Providing you an image which shows what the problem is. 

[http://www.image-filer.com/show.php/1324_thinkpadt60pubuntuinstallfailsgraphics.jpg.html](http://www.image-filer.com/show.php/1324_thinkpadt60pubuntuinstallfailsgraphics.jpg.html)

Thanks.[/B]

---

### Post by overdrank on 2008-09-29
> **catherinek1 said:**
> [B]I have been facing this problem whenever i try to install. I think that this is a serious problem. Providing you an image which shows what the problem is. 

[http://www.image-filer.com/show.php/1324_thinkpadt60pubuntuinstallfailsgraphics.jpg.html](http://www.image-filer.com/show.php/1324_thinkpadt60pubuntuinstallfailsgraphics.jpg.html)

Thanks.[/B]

Hi and welcome, lets start with the basics. What are the specs on the system?
Have you checked the cd for errors,and if you burned the cd you may check the iso 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by DrMega on 2008-09-29
Have you installed the correct display drivers for your graphics card?

In any case, you can get your display back by activating the generic driver, then from there you can make sure you choose the correct driver.

Here's how:

1. Reboot and start Ubuntu in recovery mode. This will give you a text based system and will stop at a command prompt.

2. run the following command to back up your xorg.conf

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

3. Edit xorg.conf

```
sudo nano /etc/X11/xorg.conf
```

4. Look in the display section where Driver = *whatever*
5. Change *whatever* to MESA (so that it says Driver = Mesa
6. Save your changes and close the editor
7. Restart the machine

```
sudo shutdown now -r
```

This should give you a GUI but you won't have any hardware acceleration and will be limited to certain resolutions, but from there you can choose install the correct display drivers.

---

