---
title: "Installing Broadband software on Gusty"
date: 2008-02-16
forum: Installation &amp; Upgrades
---

### Post by Paperkraft on 2008-02-16
Hi Everyone,
                       I just installed Gusty in dualboot with XP and i want to install my ISP's(Sify) broadband client on ubuntu. They want me to install two files,

1. The main debian file called Sify-bbclient3.0 which i managed to install following a "readme" in that archive.
2. The second file looks like some kinda library called openssl which ive to install to get this software working. But the problem is that it is an RPM file and ubuntu doesnt allow me to install it.

I dont have internet connection in ubuntu so i cannot download packages from Synaptic. So please kindly tell me a way to install the library file. Im attaching bth the files.

---

### Post by bwhite82 on 2008-02-16
Another way to grab packages (sans Synaptic) is to goto the website:
[packages.ubuntu.com]("http://packages.ubuntu.com")
and search for the package specific to your version of Ubuntu. It lists dependencies when you find the package that you are looking for, so check to make sure you have the dependencies installed before you download it. Then just transfer it to a USB disk or other such removable media and install in Ubuntu.

[http://packages.ubuntu.com/gutsy/utils/openssl](http://packages.ubuntu.com/gutsy/utils/openssl)

---

### Post by Paperkraft on 2008-02-16
> **Soldierboy said:**
> Another way to grab packages (sans Synaptic) is to goto the website:
[packages.ubuntu.com]("http://packages.ubuntu.com")
and search for the package specific to your version of Ubuntu. It lists dependencies when you find the package that you are looking for, so check to make sure you have the dependencies installed before you download it. Then just transfer it to a USB disk or other such removable media and install in Ubuntu.

[http://packages.ubuntu.com/gutsy/utils/openssl](http://packages.ubuntu.com/gutsy/utils/openssl)


I tried that.. You see unike windows, a software doesnot work if you download it alone..you've to download the dependencies and then the dependencies of dependencies on so on...

:confused:

I even tried to download a software called alien to convert the rpm to deb, but it also depends on a lot of other software..

---

### Post by bwhite82 on 2008-02-16
I know, it is indeed a pain to do it this way, have done it many times in the past. But it can be accomplished. I would download as many dependencies as possible and have them ready should they be called for.

Edit: Even if you converted this package to a Debian package, dependencies will still be called for.

---

### Post by Paperkraft on 2008-02-16
> **Soldierboy said:**
> I know, it is indeed a pain to do it this way, have done it many times in the past. But it can be accomplished. I would download as many dependencies as possible and have them ready should they be called for.

Edit: Even if you converted this package to a Debian package, dependencies will still be called for.

It kinda gives a bad first impression.All i wanted was an OS that will help me **save time** by not scanning for viruses, no blue screen and so on..:(

---

### Post by dayanandasaraswati on 2008-02-16
But you don need any software to get broadband working. If your modem is not preconfigured modem sify should have given a software to enter your user name and password and connect. This can be done even without a software. Just go to 
> sudo pppoeconf
Follow the instructions given there and yuppy you'll get internet working. If your modem is preconfigured you don need anything to get internet working. Just plug in play

---

### Post by Paperkraft on 2008-02-16
> **dayanandasaraswati said:**
> But you don need any software to get broadband working. If your modem is not preconfigured modem sify should have given a software to enter your user name and password and connect. This can be done even without a software. Just go to 

Follow the instructions given there and yuppy you'll get internet working. If your modem is preconfigured you don need anything to get internet working. Just plug in play

Its not a dial-up.. it is connected by a cable to a router somewhere..

---

### Post by dayanandasaraswati on 2008-02-16
I know its not a dial up..You can still use this method for configuring broadband...I used this method to get my BSNL broadband working..

---

