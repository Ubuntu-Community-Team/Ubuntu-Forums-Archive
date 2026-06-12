---
title: "Problem while installing -n- shuttind down Ubuntu."
date: 2008-02-03
forum: Installation &amp; Upgrades
---

### Post by Mr.Carioca on 2008-02-03
Good-Evening Folks,

Well here is my story: I'm trying to install Ubuntu on my Compaq Presario V6210US (AMD Turion 64 - nvidia 6150Go) but when I'm about to go for the login screen I get this white lines with black stripes all over the screen. I tried on running with the extra command on the end of the booting line, that worked but every time I try on shuting down the white lines comes back and just freeze the system. and If I want to view my ubuntu file I need to add a extra line on the booting screen.
I had used the Atl. installation (since the Live CD didn't even want to get into the login screen.
Trying to install: 7.10

here is a pic: [IMG]http://i91.photobucket.com/albums/k311/DiscoveryVACEO/Picture001.jpg[/IMG]

thank you very much for reading.
(Mod please delete my other thread under Laptop.. please)

---

### Post by overdrank on 2008-02-03
> **Mr.Carioca said:**
> Good-Evening Folks,

Well here is my story: I'm trying to install Ubuntu on my Compaq Presario V6210US (AMD Turion 64 - nvidia 6150Go) but when I'm about to go for the login screen I get this white lines with black stripes all over the screen. I tried on running with the extra command on the end of the booting line, that worked but every time I try on shuting down the white lines comes back and just freeze the system. and If I want to view my ubuntu file I need to add a extra line on the booting screen.
I had used the Atl. installation (since the Live CD didn't even want to get into the login screen.
Trying to install: 7.10

here is a pic: [IMG]http://i91.photobucket.com/albums/k311/DiscoveryVACEO/Picture001.jpg[/IMG]

thank you very much for reading.
(Mod please delete my other thread under Laptop.. please)

HI and welcome, ok you have Ubuntu installed via the alternate cd. You are not able to boot to a desktop. You can try and boot into recovery mode which is usually the second choice on the grub and login then reconfigure your xorg with this command. ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Mr.Carioca on 2008-02-04
> **overdrank said:**
> HI and welcome, ok you have Ubuntu installed via the alternate cd. You are not able to boot to a desktop. You can try and boot into recovery mode which is usually the second choice on the grub and login then reconfigure your xorg with this command. ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

No problem was found, isn't that a "Disk Check"?

---

### Post by overdrank on 2008-02-04
> **Mr.Carioca said:**
> No problem was found, isn't that a "Disk Check"?

HI and no that will reconfigure your xorg and hopes that will return you to a desktop. Are you able to boot to the desktop?

---

### Post by Mr.Carioca on 2008-02-04
> **overdrank said:**
> HI and no that will reconfigure your xorg and hopes that will return you to a desktop. Are you able to boot to the desktop?

Nope..

---

