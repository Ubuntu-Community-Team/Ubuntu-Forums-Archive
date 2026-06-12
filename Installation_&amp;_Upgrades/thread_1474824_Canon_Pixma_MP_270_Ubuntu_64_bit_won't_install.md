---
title: "Canon Pixma MP 270 Ubuntu 64 bit won't install"
date: 2010-05-06
forum: Installation &amp; Upgrades
---

### Post by eekfonky on 2010-05-06
Canon Pixma MP 270 Ubuntu 64 bit won't install
I downloaded the source files from Canon and used the correct PPD
However it now says I need the 'pstocanonij' file
I have found the folder of that name but have no clue as to what to do

Please Help!!

---

### Post by eekfonky on 2010-05-15
Can anyone help? I need an idiots guide to make this work? Aaarrghhh I going mental here!

---

### Post by renmush on 2010-05-21
Hi, this worked for me. Its a lot easier than compiling the messy sources:

Go here and download the Debian driver pack
[http://software.canon-europe.com/products/0010753.asp](http://software.canon-europe.com/products/0010753.asp)
Extract the archives until you find the two 32 bit .deb packages
Open a terminal and enter

```

sudo dpkg -i --force-architecture ./cnijfilter-common_3.20-1_i386.deb
sudo dpkg -i --force-architecture ./cnijfilter-mp270series_3.20-1_i386.deb
```

You are done.

Support for scanning is included in sane and scangear install doesn't work by this method.

I hope this helps, mark it as solved if it works.
Smiles

---

### Post by eekfonky on 2010-05-21
This worked a treat thanks, to add to that to get the scanner working with:
```
http://ppa.launchpad.net/robert-ancell/sane-backends/ubuntu
```

added to my sources list

Cheers:)

---

### Post by freakalad on 2010-06-29
> **eekfonky said:**
> This worked a treat thanks, to add to that to get the scanner working with:
```
http://ppa.launchpad.net/robert-ancell/sane-backends/ubuntu
```

added to my sources list

Cheers:)

Nice work, guys.

For the sake of completion:
```

sudo -s

DISTRO=lucid
HASH=3A852646149D38A7

echo "deb http://ppa.launchpad.net/robert-ancell/sane-backends/ubuntu $DISTRO main" >> /etc/apt/sources.list.d/new-sane.list

gpg --recv-keys $HASH --keyserver keyserver.ubuntu.com
gpg --export --armor $HASH | sudo apt-key add -

apt-get update && apt-get upgrade

```

---

### Post by ActionParsnip on 2010-09-05
or just use:

sudo add-apt-repository ppa:robert-ancell/simple-scan && apt-get update; apt-get upgrade

If you use Lucid, much more elegant

---

### Post by loganbell45 on 2011-02-04
> **renmush said:**
> Hi, this worked for me. Its a lot easier than compiling the messy sources:

Go here and download the Debian driver pack
[http://software.canon-europe.com/products/0010753.asp](http://software.canon-europe.com/products/0010753.asp)
Extract the archives until you find the two 32 bit .deb packages
Open a terminal and enter

```

sudo dpkg -i --force-architecture ./cnijfilter-common_3.20-1_i386.deb
sudo dpkg -i --force-architecture ./cnijfilter-mp270series_3.20-1_i386.deb
```

You are done.

Support for scanning is included in sane and scangear install doesn't work by this method.

I hope this helps, mark it as solved if it works.
Smiles

like to personally thank you for this :guitar:

---

### Post by shade5 on 2011-08-27
Sometimes my MP270 will not print. It says that the printer is not plugged in even if it is. Plugging in and out the USB cable sometimes does help. What could that be?

Thanks.

---

