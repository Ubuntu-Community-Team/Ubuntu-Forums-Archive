---
title: "Fedora liveusb-creator tar.bz2"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by stephenmac7 on 2010-02-24
How do I install the Fedora liveusb-creator from tar.bz2:confused:

---

### Post by wojox on 2010-02-24
What's wrong with your Ubuntu one?

---

### Post by stephenmac7 on 2010-02-24
It does not put feroda on a usb, only ubuntu, I want to install fedora on a external so I can use both fedora 12 and Ubuntu 9.10

---

### Post by stephenmac7 on 2010-03-06
I was so blind... 

Use dolphin to extract the file to make it easy in kubunu or openSUSE kde version
Ubuntu:
Downloads the tar.bz2 into /home/<your user name>/Downloads from fedorahosted.org/liveusb-creator then extract to folder and write
```

cd Downloads
cd liveusb-creator-<your version here>
sudo ./liveusb-creator
<your password here>

```
After you finish you can delete the files.
openSUSE:
Download the files to /home/<your user name>/Download, extract them to folder and write this in the command line:
```

cd Download
cd liveusb-creator-<your version here>
su
<your password here>
./liveusb-creator

```

That is a weird way to do this but it is easy and it works... so much better than a .bin file which I still have problems with...

---

### Post by Fersure on 2010-03-15
And if you'd rather use the terminal to extract the .tar.bz2:

```
$ tar xjf /path/to/file.tar.bz2
```

---

### Post by stephenmac7 on 2010-03-28
> **stephenmac7 said:**
> I was so blind... 

Use dolphin to extract the file to make it easy in kubunu or openSUSE kde version
Ubuntu:
Downloads the tar.bz2 into /home/<your user name>/Downloads from fedorahosted.org/liveusb-creator then extract to folder and write
```

cd Downloads
cd liveusb-creator-<your version here>
sudo ./liveusb-creator
<your password here>

```
After you finish you can delete the files.
openSUSE:
Download the files to /home/<your user name>/Download, extract them to folder and write this in the command line:
```

cd Download
cd liveusb-creator-<your version here>
su
<your password here>
./liveusb-creator

```

That is a weird way to do this but it is easy and it works... so much better than a .bin file which I still have problems with...

Actually that does not work, I still can't use the liveusb-creator the creator will open but it won't create anything.

---

### Post by N2G(bn#7+ on 2012-06-03
You need to install some dependencies first.
```
sudo apt-get install python-parted isomd5sum python-pyisomd5sum python-urlgrabber extlinux
```
There are detailed instructions posted here: [http://ifireball.wordpress.com/2011/10/14/running-fedoras-liveusb-creator-on-ubuntu/](http://ifireball.wordpress.com/2011/10/14/running-fedoras-liveusb-creator-on-ubuntu/)

---

