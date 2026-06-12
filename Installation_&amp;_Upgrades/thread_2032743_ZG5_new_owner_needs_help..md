---
title: "ZG5 new owner needs help."
date: 2012-07-24
forum: Installation &amp; Upgrades
---

### Post by horsegun on 2012-07-24
[SIZE=3][FONT=Calibri]Evening,[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Hope I can trouble someone for some help. I have worked with Windows lots and would not class myself as a novice but I am a bit overwhelmed by Ubuntu.[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]I have been given an Acer one ZG5 with a 120Gig HD that has been previously used by my brother-in-law. It is running Ubunto 10.04. I want a fresh install as the ZG5 still has his name, files, settings etc. [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]What is the best version that I can run on a ZG5?[/FONT][/SIZE]
[SIZE=3][FONT=Calibri]How do I install a fresh version of the Ubunto? Will it wipe everything inc drivers? [/FONT][/SIZE]
[SIZE=3][FONT=Calibri]Thank you in advance.[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Mark[/FONT][/SIZE]

---

### Post by oldfred on 2012-07-26
Welcome to the forums.

Not familar with specific model. How much RAM and is it 32 or 64 bit?

A new install will erase everything, so backup any data you may want first. If you do an upgrade it would keep old settings.

You can use gparted to erase everything and do a auto install which only has / (root) and swap. Or use Something Else manual install which lets you choose existing / as new / and you specify format (usually ext4). It finds swap. Normally if you have an existing /home as a separate partition you would not reformat it, but in your case wanting a totally clean install and new user you should also reformat it. Did I mention backup first? :)

Always best to test liveCD/USB first to see if new version has any issues. The 12.04 changes to Unity as the default but you can modify to be similar to the old menu type (gnome-panel or fallback) which is similar to what you have now.

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to CD.
[http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

If you only have 512MB of RAM, a lighter weight version may be better.
Lubuntu, which uses the LXDE desktop environment, targeted at "normal computers" with 128 MB
With 512Mb of RAM and almost any processor, Lubuntu will perform more than adequately out-of-the box. 
[https://help.ubuntu.com/community/LubuntuLinks](https://help.ubuntu.com/community/LubuntuLinks)

---

