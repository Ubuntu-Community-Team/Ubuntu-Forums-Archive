---
title: "Where is add-apt-repository?"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by pbaumer on 2010-08-29
Hi,

I am running an Ubuntu/X64 10.04. I am trying to install bazaar from bazaar.canonical.com. The PPA of bazaar ([https://launchpad.net/~bzr/+archive/ppa](https://launchpad.net/~bzr/+archive/ppa)) page tells me to use the add-apt-repository.

However my system doesn't have it. 

```
>add-apt-repository
bash: add-apt-repository: command not found


> dpkg -S add-apt-repository
dpkg: *add-apt-repository* not found.
```

Some pages tell me it is in the python-software-properties. But it is not.

```
>dpkg -L python-software-properties
/.
/usr
/usr/bin
/usr/share
/usr/share/doc
/usr/share/doc/python-software-properties
/usr/share/doc/python-software-properties/README
/usr/share/doc/python-software-properties/TODO
/usr/share/doc/python-software-properties/AUTHORS
/usr/share/doc/python-software-properties/BUGS
/usr/share/doc/python-software-properties/copyright
/usr/share/doc/python-software-properties/changelog.gz
/usr/share/pyshared
/usr/share/pyshared/softwareproperties
/usr/share/pyshared/softwareproperties/__init__.py
/usr/share/pyshared/softwareproperties/AptAuth.py
/usr/share/pyshared/softwareproperties/CountryInformation.py
/usr/share/pyshared/softwareproperties/distro.py
/usr/share/pyshared/softwareproperties/MirrorTest.py
/usr/share/pyshared/softwareproperties/SoftwareProperties.py
/usr/share/pyshared-data
/usr/share/pyshared-data/python-software-properties
```

Any help is seriously appreciated ! :confused:

---

### Post by howefield on 2010-08-29
Try this in terminal...

```
sudo add-apt-repository ppa:bzr/ppa
```

---

### Post by pbaumer on 2010-08-29
> **howefield said:**
> Try this in terminal...

```
sudo add-apt-repository ppa:bzr/ppa
```

sudo add-apt-repository ppa:bzr/ppa
sudo: add-apt-repository: command not found

---

### Post by howefield on 2010-08-29
Not sure why it wouldn't work for you assuming no typos. Seems fine for me - (see screenshot).

You could try the "long" way...

[https://launchpad.net/~bzr/+archive/ppa](https://launchpad.net/~bzr/+archive/ppa)

Open a terminal (Applications > Accessories > Terminal) and type

```
gksudo gedit /etc/apt/sources.list
```

Add the following to the end of the file and save...

```
deb http://ppa.launchpad.net/bzr/ppa/ubuntu lucid main 
deb-src http://ppa.launchpad.net/bzr/ppa/ubuntu lucid main
```

Then add the authentication key - copy the contents of the following webpage to a text file on your desktop.
 
[http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xD702BF6B8C6C1EFD](http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0xD702BF6B8C6C1EFD)

and go to System > Administration > Software Sources > Authentication and import the key file that you just created.

Then reload your software sources.

---

### Post by pbaumer on 2010-08-29
Thanks Howefeld, with your help and some more attention, I have found "my" problem. 

Thanks.

---

### Post by lidex on 2010-08-29
Interesting...try this:
```
sudo apt-get install --reinstall python-software-properties && sudo dpkg-reconfigure python-software-properties
```

---

### Post by y3ahright on 2011-06-08
> **lidex said:**
> Interesting...try this:
```
sudo apt-get install --reinstall python-software-properties && sudo dpkg-reconfigure python-software-properties
```

Thanks that did the trick for me.  (better then having to go into /etc/apt/sources.list and manually fixing it.

---

### Post by Frogs Hair on 2011-06-08
Glad it's solved , I think you were looking for this.```
sudo add-apt-repository ppa:bzr-explorer-dev/ppa
```

---

