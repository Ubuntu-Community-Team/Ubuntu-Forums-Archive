---
title: "Problems Installing wine"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by igor_mk on 2007-02-02
Hi,
I'm new to ubuntu so someone need's to help me a little bit.
I have xubuntu 6.06 server with running xubuntu-desktop, I instaled wine, but it installed 0.9.9.
I went to the wine official site and followed the instructions for installations
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
```
sudo wget http://wine.budgetdedicated.com/apt/sources.list.d/dapper.list -O /etc/apt/sources.list.d/winehq.list
```
```
sudo apt-get update
sudo apt-get install wine
```

and this is what the shell returned:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
wine: Depends: libasound2 (> 1.0.11) but 1.0.10-2ubuntu4 is to be installed
Depends: libc6 (>= 2.4-1) but 2.3.6-0ubuntu20.2 is to be installed
Depends: libgcc1 (>= 1:4.1.1-12) but 1:4.0.3-1ubuntu5 is to be installed        
Depends: libglib2.0-0 (>= 2.12.0) but 2.10.3-0ubuntu1 is to be installed        
Depends: libgphoto2-2 (>= 2.2.1) but 2.1.6-5.2ubuntu8 is to be installed        
Depends: libgphoto2-port0 (>= 2.2.1) but 2.1.6-5.2ubuntu8 is to be installed
Depends: libstdc++6 (>= 4.1.1-12) but 4.0.3-1ubuntu5 is to be installed
Depends: libusb-0.1-4 (>= 2:0.1.12) but 2:0.1.10a-22ubuntu1 is to be installed
Depends: libxml2 (>= 2.6.26) but 2.6.24.dfsg-1ubuntu1 is to be installed        
Depends: libxslt1.1 (>= 1.1.17) but 1.1.15-1ubuntu1 is to be installed
E: Broken packages
```

Thanks in advance

---

### Post by PaulusVictor on 2007-02-14
I'm having the same problem and have yet to find a solution.

---

### Post by igor_mk on 2007-02-14
I solved the problem by directly downloading the .deb source, and installing it directly. The other repositories were downloaded automatically. 

Here is the site for the .deb sources  [http://wine.budgetdedicated.com/archive/index.html]("http://wine.budgetdedicated.com/archive/index.html")

Regards

---

### Post by killernurd on 2007-02-17
> **igor_mk said:**
> Hi,
I'm new to ubuntu so someone need's to help me a little bit.
I have xubuntu 6.06 server with running xubuntu-desktop, I instaled wine, but it installed 0.9.9.

[snipped]

Thanks in advance

You may want to see if you have the backports repositories enabled. Open a terminal, and take a look at your APT sources.list:

```

tony@lugh:~$ sudo nano -w /etc/apt/sources.list

```

I've attached my own sources.list file, so you can take a look at it.

---

