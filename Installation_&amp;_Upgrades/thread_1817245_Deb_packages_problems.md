---
title: "Deb packages problems"
date: 2011-08-03
forum: Installation &amp; Upgrades
---

### Post by Windstyle on 2011-08-03
Hi guys ive recently installed ubuntu and im quite a noob at this things.I whant to install programs but i cant.Ive tried apt-get and it gives me this

Windstyle@(none):~$ sudo apt-get install skype.deb
sudo: unable to resolve host (none)
[sudo] password for Windstyle: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
N: Ignoring file 'local-packages.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
E: Unable to locate package skype.deb
E: Couldn't find any package by regex 'skype.deb'

i know i have skype.deb package but it doesnt locate it could someone tell me how to start installing packages via terminal.Sorry for the stupid questions :D

---

### Post by spcwingo on 2011-08-03
Try this:

```
echo "deb http://download.skype.com/linux/repos/debian/ stable non-free #Skype" | sudo tee -a /etc/apt/sources.list > /dev/null
```

That will add the Skype repository.  Then do this:

```
sudo apt-key adv --keyserver pgp.mit.edu --recv-keys 0xd66b746e
```

This will get the Apt key for you.  Finally run this:

```
sudo apt-get update && sudo apt-get install skype
```

This will refresh your sources and install Skype.

---

### Post by Windstyle on 2011-08-03
:confused: OMG its so hard to install a single package.However idk if its installed after i typed your commands it says 

N: Ignoring file 'local-packages.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-powerpc/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-powerpc/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by westie457 on 2011-08-03
> **Windstyle said:**
> :confused: OMG its so hard to install a single package.However idk if its installed after i typed your commands it says 

N: Ignoring file 'local-packages.list.save' in directory '/etc/apt/sources.list.d/' as it has an invalid filename extension
W: Failed to fetch [http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-powerpc/Packages.gz](http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-powerpc/Packages.gz)  404  Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

Skype is in the repositories, install with ```
sudo apt-get install skype
```

---

### Post by Windstyle on 2011-08-03
Again the same as the first post nothing changed

---

### Post by westie457 on 2011-08-03
Go to here [http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/downloading.ubuntu32](http://www.skype.com/intl/en-us/get-skype/on-your-computer/linux/downloading.ubuntu32) and download the package for your distro. If your distro is newer than the options give select the newest available. When download is complete locate the file and double-click it. Software Centre should open and allow you to install. Enjoy

---

### Post by spcwingo on 2011-08-03
Please post the output of this command:

```
uname -a
```

The reason I want to see this is this line that you posted:

```
W: Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-powerpc/Packages.gz 404 Not Found
```

most notably, the "powerpc" part.

---

### Post by Windstyle on 2011-08-03
Here you go Spcwingo Linux (none) 2.6.38-powerpc64 #18 SMP Sun Jun 26 19:25:24 UTC 2011 ppc64 GNU/Linux

---

### Post by spcwingo on 2011-08-03
Well, there's your problem.  There's no PPC build of Skype for Linux.  With Skype being closed source, the best that you can do is try to contact the developers and beg for a Linux PPC binary.  Good luck.

---

### Post by Windstyle on 2011-08-03
I whant to install some programs not just skype i mean when i download them.directly to install them.I think im on debian or im not quite sure.Could you give me the easiest way to get the programs running no matter which way :)

---

### Post by spcwingo on 2011-08-04
The preferred way of installing packages is by pulling them in through the repos...if what you're after isn't in the repos just download the DEB package (if available).  Then open a terminal, change directory (cd) to where you downloaded them and run this command:

```
sudo dpkg -i ./package_name.deb
```

By the way, to see what distro you're running just run this command in a terminal:

```
lsb_release -a
```

---

### Post by ottosykora on 2011-08-04
well if I have a -deb file which I did not get via ubuntu repository, then I right click on it, and select open with gdebi and this will do the rest.

If you do not have gdebi, then install it first, this is certainly in the repository.



However skype might be available from repository too.

---

