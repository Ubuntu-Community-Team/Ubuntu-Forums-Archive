---
title: "Wubi does not install 14.04.1"
date: 2014-07-29
forum: Installation &amp; Upgrades
---

### Post by Flame_Evance on 2014-07-29
Hi.
I've downloaded lubuntu 14.04.1, mounted it, then run wubi.exe.
And instead of installing 14.04.1 its starting to download 14.04.

I've tried placing 14.04.1 iso in same directory with wubi.exe but this doesnt work, its still downloading 14.04.

---

### Post by Mark Phelps on 2014-07-29
Wubi has been discontinued; you would do best NOT using it anymore.

---

### Post by Flame_Evance on 2014-07-29
> **Mark Phelps said:**
> Wubi has been discontinued; you would do best NOT using it anymore.
Thank you for response, I didnt know this. I wonder why its still inside ISO then...

---

### Post by coffeecat on 2014-07-29
Not so much discontinued as no longer maintained. And it won't work in Windows 8/UEFI systems at all.

I had a look at the wubi.exe file in the Lubuntu 14.04.1 ISO and the file save date is 14 April this year, so it appears not to have been modified since 14.04 was released. Perhaps this is why it is downloading the 14.04 ISO rather than using the 14.04.1 ISO that you have correctly placed in the same directory.

---

### Post by QIII on 2014-07-29
So do most of us...

---

### Post by hakuna_matata on 2014-07-29
> **Flame_Evance said:**
> 
I've tried placing 14.04.1 iso in same directory with wubi.exe but this doesnt work, its still downloading 14.04.
Did you download 32-bit PC (386) or 64-bit PC (AMD64) desktop image ?

IMHO 64-bit PC (AMD64) desktop image for Lubuntu contains only **casper/vmlinuz.efi** but Wubi default for 64-bit Lubuntu is **casper/vmlinuz**.

If this is your problem, you can use either 32-bit version or add the red line to **data/isolist.ini**
```
[Lubuntu-amd64]
arch=amd64
name=Lubuntu
packages=lubuntu-desktop
[COLOR=#ff0000]kernel=casper/vmlinuz.efi[/COLOR]
metalink=http://cdimage.ubuntu.com/lubuntu/releases/14.04/release/lubuntu-14.04-desktop-amd64.metalink
metalink2=http://cdimage.ubuntu.com/lubuntu/daily-live/current/trusty-desktop-amd64.metalink
website=http://lubuntu.net
ordering=7

```
**data/isolist.ini** is part of wubi.exe. wubi.exe is a self-extracting [7zip]("http://7-zip.org/") archive.

Your Wubi log in your Windows temp folder (%temp%) would be helpful.

---

### Post by mastablasta on 2014-07-30
if you have at least 2 GB ram you will find it easier and safer to install & use the OS via virtualbox. here is a nice how to: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by robert94 on 2014-09-03
I have the same issue. Did anyone successfully use Wubi 14.04 to install 14.04.[COLOR=#ff0000]**1**[/COLOR] [Lubuntu or Ubuntu]

Tomorrow I will see if Wubi 14.04 will install Ubuntu 14.04 [as opposed to 14.04.1]

---

### Post by hakuna_matata on 2014-09-07
> **robert94 said:**
> Did anyone successfully use Wubi 14.04 to install 14.04.[COLOR=#ff0000]**1**[/COLOR] [Lubuntu or Ubuntu]

Yes, I did for testing purpose. wubi.exe is a self extracting 7-zip archive. 7-zip is available here: [http://www.7-zip.org](http://www.7-zip.org) You can modify** /data/isolist.ini** 

At least you need
```
version=14.04.**1**
```

An example of a modified wubi.exe (wubi1404**1**.exe for 14.04.**1**) is here: [https://www.dropbox.com/sh/6uqomp8l1frcd1y/AAAhSCimTaYE-94egbmc1X_na](https://www.dropbox.com/sh/6uqomp8l1frcd1y/AAAhSCimTaYE-94egbmc1X_na)

I modified wubi.exe for installing on UEFI systems but modified wubi.exe should work on none UEFI systems, too.

---

### Post by Frogs Hair on 2014-09-07
The upgrade to 14.04.1 would be achieved by running the update manger post installation. If the goal is to get around the updates see the post by [COLOR=#000000]hakuna_matata. AFIK wubi has never installed point releases. [/COLOR]

---

### Post by hakuna_matata on 2014-09-07
> **Frogs Hair said:**
> [COLOR=#000000]AFIK wubi has never installed point releases.[/COLOR]
FYI Current version of [http://releases.ubuntu.com/precise/wubi.exe](http://releases.ubuntu.com/precise/wubi.exe) installs a point release (12.04.**5)**

---

### Post by Frogs Hair on 2014-09-07
> **hakuna_matata said:**
> FYI Current version of [http://releases.ubuntu.com/precise/wubi.exe](http://releases.ubuntu.com/precise/wubi.exe) installs a point release (12.04.**5)**

Thanks , Wubi was still supported when 12.04 was released.

---

### Post by robert94 on 2014-09-12
Hi all 

Thank you for taking time to reply. In the end I downloaded the Ubunutu 14.04 64-bit PC (AMD64) desktop image and installed locally with the included Wubi [so there was no download during the Wubi install]

I then installed lxde as an alternative to Unity. The later was very cpu intensive due to the compiz process using a lot of cpu. Something I have yet to investigate but a quick search shows it as a known issue...

How do I now upgrade to 14.04**.1** as that is not coming up in software update. Maybe that will fix the compiz cpu issue ?

BTW the PC is a Hp 210 mini netbook with N550 and GMA3150 GPU

---

### Post by Frogs Hair on 2014-09-12
My Ubuntu 14.04 installation installed in April was updated to 14.04.1  via the update manager.

Edit: Install all available updates and run the following command.```
 lsb_release -a
```

---

### Post by grahammechanical on 2014-09-12
> [COLOR=#000000] In the end I downloaded the Ubunutu 14.04 64-bit PC[/COLOR]

If you did that recently then you would have downloaded 14.04.1. To check run

```
lsb_release -a
```

Regards

---

### Post by riahc3 on 2014-11-20
> **hakuna_matata said:**
> Yes, I did for testing purpose. wubi.exe is a self extracting 7-zip archive. 7-zip is available here: [http://www.7-zip.org](http://www.7-zip.org) You can modify** /data/isolist.ini** 

At least you need
```
version=14.04.**1**
```

An example of a modified wubi.exe (wubi1404**1**.exe for 14.04.**1**) is here: [https://www.dropbox.com/sh/6uqomp8l1frcd1y/AAAhSCimTaYE-94egbmc1X_na](https://www.dropbox.com/sh/6uqomp8l1frcd1y/AAAhSCimTaYE-94egbmc1X_na)

I modified wubi.exe for installing on UEFI systems but modified wubi.exe should work on none UEFI systems, too.
A manual guide on how to do it would be nice so we can know how to modify our own ISOs

---

### Post by hakuna_matata on 2014-11-20
> **riahc3 said:**
> A manual guide on how to do it would be nice so we can know how to modify our own ISOs
Meanwhile, there is also a workaround without changing wubi.exe: [http://ubuntu-with-wubi.blogspot.ca/2014/10/installing-ubuntu-14041-with-wubi.html](http://ubuntu-with-wubi.blogspot.ca/2014/10/installing-ubuntu-14041-with-wubi.html)

Changing with Ubuntu:
[LIST]
[*]install 7zip ```
sudo apt-get install p7zip-full
``` 
[*]download wubi.exe ```
wget http://releases.ubuntu.com/trusty/wubi.exe
``` 
[/LIST]
     
[LIST]
[*]make a temporary folder ```
mkdir wubi-temp
``` 
[*]go to temporary folder ```
cd wubi-temp
``` 
[*]extract wubi.exe ```
7z x ../wubi.exe
``` 
[*]make your changes e.g. with gedit ```
gedit data/isolist.ini
``` 
[/LIST]
[INDENT]at least, change the second line from
```
version=14.04
```
to
```
version=14.04.1
```

and the metalink line for 32 bit from
```
metalink=http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-i386.metalink
```
to  
```
metalink=http://releases.ubuntu.com/14.04.1/ubuntu-14.04.1-desktop-i386.metalink
```
and the metalink line for 64 bit from
```
metalink=http://releases.ubuntu.com/14.04/ubuntu-14.04-desktop-amd64.metalink
```
to
```
metalink=http://releases.ubuntu.com/14.04.1/ubuntu-14.04.1-desktop-amd64.metalink
```
[/INDENT]

[LIST]
[*]update your wubi.exe ```
7z u ../wubi.exe
``` 
[/LIST]

Changing with Windows is similar. I hope it helps.

---

