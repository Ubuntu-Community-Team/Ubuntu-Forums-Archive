---
title: "Alien Linmodem Catch22 [Resolved]"
date: 2007-01-21
forum: Installation &amp; Upgrades
---

### Post by gwm on 2007-01-21
:confused: I have a catch 22 problem. Without a modem driver, I can't get to the repositories on the internet. That means I can't install Alien. So I can't convert the rpm driver that came with the hardware to a .deb file. That means I can't get my modem working under Linux (I am using Windows to post this).
Is there someway that I could download Alien.deb using Windows. Then I could copy it to a shared FAT32 partition and try to proceed from there. Perhaps Alien depends on other things.
Someone told me that he found a converter on the Breezy release CD.
This is a major problem for me. It is preventing me from using Ubuntu.
Any help would be appreciated.

---

### Post by taurus on 2007-01-21
Do you have the installer CD with you?  If alien in the CD, you can mount and install it from the CD with

Applications -> Accessories -> Terminal
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install alien
```
Otherwise, you can download it and the dependencies from here.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by gwm on 2007-01-21
Thanks taurus,
I found it on the CD but

sudo apt-get update

requires internet access!
I ignored the failure and tried the next line

sudo apt-get install alien

This started ok but was soon trying to access the internet as well.

Couldn't Ubuntu release a goodies DVD or something to help people like me?

You also suggested [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Of course I could get their with windows. I found Alien all right. But then I haven't a clue what to do next. Suppose I manage to download all the main deb files and on down the chain, all their dependencies. What would I need to do with these files (i.e. how should I arrange them? In what kind of folder tree should I put them?) so that apt-get can use them?

Thanks for your help so far, I feel I'm sort of slowly getting into this Linux thing.

---

### Post by taurus on 2007-01-21
Transfer your downloads to some directory like ~/Desktop and install all of them at once with

```
sudo dpkg -i *.deb
```

---

### Post by gwm on 2007-01-23
Thanks Taurus,
These bits of info, such as your last post help one to gain confidence that one is understanding these processes correctly.
I used Windows to fetch the free deb release of a driver from [http://www.linuxant.com](http://www.linuxant.com) and put that in a shared partition. From there, I used dpkg (as above) to install the driver. Next I went on line and used Synaptic to install Alien from the repositories. Then I went to bed.
Tomorrow night, I'll try converting the rpm file from the modem's release disk to see if their driver, which I've already paid for and which is probably the same one that I got from Linuxant, is faster than 14400. If not, I'll buy the faster one from Linuxant.
Thanks again for all the help.

p.s. down here in Southern Africa, we live in a third world country. Internet access is expensive!!! In the spirit of Ubuntu, a CD or DVD with things like Alien, SSH, GIMP's help file etc on them would be much appreciated. For example, at our access speeds. GIMP help is a two hour download and we pay for our telephone calls by the second!! While I still have a job, I can afford it but the majority of our citizens are not that fortunate and who knows, perhaps soon I won't be either.

---

