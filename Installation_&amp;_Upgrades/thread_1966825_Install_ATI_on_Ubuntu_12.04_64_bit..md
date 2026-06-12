---
title: "Install ATI on Ubuntu 12.04 64 bit."
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by c2tarun on 2012-04-27
Hi friends

I am trying to install ATI driver according to the instructions on this page. [http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

on executing the instruction 

```
sudo apt-get --purge remove fglrx*
```

it is notifying me that 220 MB of space will be free, that is an awe full lot of space. Should I remove fglrx driver first or I can directly install ATI driver?? 

Following is the details of my driver:
```

02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5400 Series]
```

---

### Post by techsupport on 2012-04-27
> **c2tarun said:**
> Hi friends

I am trying to install ATI driver according to the instructions on this page. [http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/](http://debianhelp.wordpress.com/2012/03/09/to-do-list-after-installing-ubuntu-12-04-lts-aka-precise-pangolin/)

on executing the instruction 

```
sudo apt-get --purge remove fglrx*
```it is notifying me that 220 MB of space will be free, that is an awe full lot of space. Should I remove fglrx driver first or I can directly install ATI driver?? 

Following is the details of my driver:
```

02:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Manhattan [Mobility Radeon HD 5400 Series]
```

That isn't very much space considering what you are uninstalling. Go ahead.

---

### Post by c2tarun on 2012-04-27
I am unable to find following packages in repository, are they necessary? 
dkgcc1 libc6-i386ms lib32

---

### Post by QIII on 2012-04-27
Is something telling you they are needed?

No need to download the driver.  What is in the repo already is the "pre-release" that Ubuntu always gets from ATI with a new release.  (Phoronix always complains about how Ubuntu gets the candy before anyone else).
It is the 8.960 stream, whereas the post-release version is 8.961.  The difference at this point is really just that the second is the "release" version.

To install the driver, all you need to do is go to the terminal and execute the following commands:

```
sudo apt-get install fglrx-updates
```

which will install the driver and Catalyst Control Center

Then

```
sudo aticonfig --initial
```

which will generate an initial xorg.conf.

You will have to reboot to get the driver going.

---

