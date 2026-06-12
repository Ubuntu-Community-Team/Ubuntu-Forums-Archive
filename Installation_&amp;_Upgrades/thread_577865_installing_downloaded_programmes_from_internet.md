---
title: "installing downloaded programmes from internet"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by Eddie Parker on 2007-10-16
I have downloaded from the internet to my Ubuntu 7.04 Desktop Picasa2 and Google Earth.Now I don't know how to open them. Picasa2 gives me the message "cannot open /home/eddie/Desktop/picasaweb-current-setup.exe. No application suitable for automatic installation is available for handling this type of file".
GoogleEarth's message is" cannot open the file /home/eddie/Desktop/GoogleEarthLinux.bin  using this character coding".
If anyone is able to help could they be specific in their instructions please.
Thanks
Eddie

---

### Post by VVebbie on 2007-10-16
Picasa - it looks like you downloaded the Windows version. There are actually good setup instructions for Ubuntu starting here:
[http://picasa.google.com/linux/](http://picasa.google.com/linux/)

---

### Post by forestpixie on 2007-10-16
you can get google earth from medibuntu

put these into a terminal and enter after each, will need password
```

echo "deb http://packages.medibuntu.org/ feisty free non-free" | sudo tee -a /etc/apt/sources.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

```
sudo apt-get install googleearth googleearth-data
```

---

