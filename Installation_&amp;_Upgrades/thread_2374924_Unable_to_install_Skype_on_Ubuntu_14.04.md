---
title: "Unable to install Skype on Ubuntu 14.04"
date: 2017-10-20
forum: Installation &amp; Upgrades
---

### Post by dmitriano on 2017-10-20
I did the steps described [here]("http://www.krizna.com/ubuntu/install-skype-ubuntu-14-04/") :

sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) $(lsb_release -sc) partner"
sudo apt-get update
sudo apt-get install skype

but Skype does not install.

The command

```
sudo apt-get install skype
```

outputs:

E: Unable to locate package skype.

What can be the problem?

The system architecture is i386.

If I do 

```
apt-cache search skype
```

some plugins are listed but not 'skype' package.

Probably the package was removed from the repository?

---

### Post by ajgreeny on 2017-10-20
Those instructions are now outdated as skype has moved to version 5.# which you need to download from [https://go.skype.com/linux.deb](https://go.skype.com/linux.deb) and install it. I recommend using **gdebi** to install it as it will deal with the dependencies.  It will also add the new repository for skype to your sources so it will stay updated like everything else.

However, it is now available for 64 bit OSs only, so as I have only just noticed you are still using a 32 bit system, I'm afraid you will have to use the "Skype for Web" in a browser window [https://web.skype.com/](https://web.skype.com/) which should still work.

---

### Post by dmitriano on 2017-10-24
I way able to install 32bit Skype with this link : [www.skype.com/go/getskype-linux-beta-ubuntu-32](www.skype.com/go/getskype-linux-beta-ubuntu-32)

---

### Post by ajgreeny on 2017-10-24
> **dmitriano said:**
> I way able to install 32bit Skype with this link : [www.skype.com/go/getskype-linux-beta-ubuntu-32](www.skype.com/go/getskype-linux-beta-ubuntu-32)
But does it actually work?

Version 4.3.0.37 was reported as stopping from working after July this year; has Microsoft decided not to pull the plug on it after all; I wonder?

---

### Post by strixtux on 2017-10-25
tried it on my 32 bit Dell - no avail, won't even install.

---

### Post by dmitriano on 2017-10-25
Yes, it works on my Acer Aspire One netbook! And even with video!

---

