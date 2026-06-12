---
title: "no graphic desktop"
date: 2007-04-06
forum: Installation &amp; Upgrades
---

### Post by thebluejay on 2007-04-06
I installed Xubuntu from the Alternate CD and was able to boot to a text interface. I updated and upgraded as instructed with no problems. But then I tried to use sudo aptitude install xubuntu-desktop and was told to insert the Xubuntu Dapper Drake CD. If I use the same installation CD as before, it tells me that the file is not found. Do I have to download and burn a different iso to get the graphic desktop? If so, where do I find it?

---

### Post by solar george on 2007-04-06
That sounds strange.

Anyway, try the following.

Type
```
sudo nano /etc/apt/sources.list
```
enter your password,
edit the file so that it only contains the line below
```

deb http://archive.ubuntu.com/ubuntu/ edgy main restricted

```
Type 
```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```


Good luck

---

### Post by genecaldwell on 2007-04-06
in answer to your question, no, that is not normal. you should have been able to do a full install from the one CD, so I think that something may have gone wrong during the install. make sure the MD5 is correct for the image you downloaded. what the guy replied below this is prolly correct (I'm not an expert, but I know the install CD has everything on it you need) so you can try that or pull another ISO image and this time make sure you have the full ISO image and check the md5 (just google MD5 to get the windows version if you need it)

---

### Post by thebluejay on 2007-04-07
> **solar george said:**
> That sounds strange.

Anyway, try the following.

Type
```
sudo nano /etc/apt/sources.list
```
enter your password,
edit the file so that it only contains the line below
```

deb http://archive.ubuntu.com/ubuntu/ edgy main restricted

```
Type 
```
sudo apt-get update
sudo apt-get install xubuntu-desktop
```


Good luck


Thanks, George! That did it. Seems that the problem was I incorrectly edited the sources.list file so it was directing me to the wrong place. Finally got it installed and I LOVE IT. Works beautifully on a 633 processor with only 128M RAM. I've downloaded the Desktop Guide so I can now become a Linux GEEK.

You've got a convert! :)

Goodbye Windows... next move will be to install it on my main computer as soon as I get the hang of the new OS.

Cheers.

Jay

---

