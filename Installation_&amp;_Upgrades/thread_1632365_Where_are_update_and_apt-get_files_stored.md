---
title: "Where are update and apt-get files stored?"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by kiwinuck on 2010-11-27
I am trying to install Lubuntu 10.10 in a VirtualBox 3.0.14 guest on Mac OS X 10.4 with the hopes of getting Guest Additions installed and working.

From prior experience I tend to go through the install process more than once which involves downloading the updates and any necessary apt-get files multiple times.

So, where do these files get stored?  I would like to then save them to a separate disk mount, so I can use them on a subsequent install...which is second question...how can do that?

---

### Post by oldos2er on 2010-11-27
/var/cache/apt/archives

You can copy the contents of this folder wherever you need to. Don't run *apt-get clean* or you will lose everything there.

---

### Post by kiwinuck on 2010-11-27
Thanks for that!  I've stored them to a second hd mounted as xfer. Now lets say I create a new Lubuntu install and mount xfer.

How do I get Lubuntu to grab the files from xfer locally rather than downloading them externally?

---

### Post by oldos2er on 2010-11-28
Copy the files back to /var/cache/apt/archives, then run ```
sudo apt-get install --no-download <package name>
```

---

### Post by manish671 on 2012-01-30
[SIZE=3]Copy all those files to some location e.g. Desktop/abc then in terminal
 
sudo dpkg -i ~/Desktop/abc/*.deb

All the packages will get included.[/SIZE]

---

### Post by raja.genupula on 2012-01-30
one small thing , first any package have to install means the dependencies satisfaction is must .

so if we give like that **above posts** how the dependencies gonna take in order ? 

all the package gonna install by on what order ? 

 

Thanks in advance .

---

### Post by oldos2er on 2012-01-30
Closed, necromancy.

---

