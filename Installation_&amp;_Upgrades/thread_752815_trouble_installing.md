---
title: "trouble installing"
date: 2008-04-12
forum: Installation &amp; Upgrades
---

### Post by husker1977 on 2008-04-12
hope someone can help,

I downloaded the disk and I am trying to put it on a older machine. the machine does not have enough memory to use the disk live so I have been trying to figure out how to install the os to the harddrive but have been unsuccessfull. the computer just wants to but from the disk and run from the disk will not install to the harddrive any help with this would be great. I am sure I have forgot something fairly simple.
please help

---

### Post by iaculallad on 2008-04-12
How much ram is in your system? If you're having <=128MB of ram, i suggest you try the kubuntu alternate CD.

---

### Post by Master Yami on 2008-04-12
> **iaculallad said:**
> How much ram is in your system? If you're having <=128MB of ram, i suggest you try the kubuntu alternate CD.

KDE sounds like a bad idea if thats the case, even after hard drive installation. I've tried myself.

Go Xubuntu or something else thats small, and avoid GNOME and KDE.

---

### Post by david_kt on 2008-04-12
> **husker1977 said:**
> hope someone can help,

I downloaded the disk and I am trying to put it on a older machine. the machine does not have enough memory to use the disk live so I have been trying to figure out how to install the os to the harddrive but have been unsuccessfull. 

Try alternate install cd (not live cd). If still fail, put the harddisk to another computer and install ubuntu from there to the harddisk. After that put back the harddisk to the old pc.

For hardy, that is all you need to do, it will auto detect your configuration.
For older release, you might need to edit the /boot/grup/menu.lst to suit the harddisk name in order to boot. But before that, you could edit while booting (temporary edit) and after able to boot, then edit the menu.lst.

And for older release, you should run below command:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

DK

---

### Post by zvacet on 2008-04-12
You can try [minimal.](http://www.psychocats.net/ubuntu/minimal#barebones)

---

### Post by iaculallad on 2008-04-12
> **Master Yami said:**
> KDE sounds like a bad idea if thats the case, even after hard drive installation. I've tried myself.

Go Xubuntu or something else thats small, and avoid GNOME and KDE.

Yap, that would be Xubuntu-Alternate instead of Kubuntu-Alternate.

---

