---
title: "sun-java6-bin"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by vasja on 2007-04-20
I can't setup sun-java on fiesty

```

Preconfiguring packages ...
Selecting previously deselected package sun-java6-bin.
(Reading database ... 82230 files and directories currently installed.)
Unpacking sun-java6-bin (from .../sun-java6-bin_6-00-2ubuntu2_i386.deb) ...
Selecting previously deselected package sun-java6-jre.
Unpacking sun-java6-jre (from .../sun-java6-jre_6-00-2ubuntu2_all.deb) ...
sun-dlj-v1-1 license has already been accepted
Setting up sun-java6-jre (6-00-2ubuntu2) ...

Setting up sun-java6-bin (6-00-2ubuntu2) ...
/usr/lib/jvm/java-6-sun-1.6.0.00/bin/java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 sun-java6-bin
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up sun-java6-bin (6-00-2ubuntu2) ...
/usr/lib/jvm/java-6-sun-1.6.0.00/bin/java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 sun-java6-bin

```

Thanks in Advance for any Help

Vasja

---

### Post by Brks on 2007-04-23
Hi, I'm also experiencing the same error.  Can anyone explain please?  Thanks.

---

### Post by zvacet on 2007-04-24
> Click Applications &#8594; Add/Remove. In the top right, change the setting to All available applications. Then select Other in the left panel and then select the Ubuntu restricted extras package. Click OK.

This will give you Java and other stuff.

---

### Post by Premi0815 on 2007-04-25
I think this is not the answer to the question.
Same error for me. Can anyone help?

---

### Post by elias4444 on 2007-08-18
I've also gotten this error... has a fix been posted yet?

---

### Post by jamesstansell on 2007-08-27
I spoke with someone today who was getting the same error on 6.10 (using the edgy-backports I believe)

The root problem may be messed up symbolic links.  He had also tried automatix, without success, and we're not sure to what extent that may be involved.

apt-get --purge wouldn't clear it up so he's planning to do a fresh install of 7.10 feisty.

---

### Post by jamesstansell on 2007-08-28
Just  an update.  Using the feisty + usb persistence patches he still gets this error.

Looks like a problem with how sun-java loads dynamic libraries not working in a chroot environment.

-james.

---

### Post by hazza96 on 2007-09-20
> **jamesstansell said:**
> Looks like a problem with how sun-java loads dynamic libraries not working in a chroot environment.
I am customising my own version of Ubuntu using the instructions from the Linux Format magazine and it is only in the chroot environment that I am getting this error.

---

### Post by studo77 on 2007-11-21
aaww, crap.

I got the same error and have re-installed in the last week. And now i have to do it again... bommer.

---

### Post by azbarcea on 2007-11-21
let's take it easy:

```

$ sudo apt-get install sun-java6-jre

```

and it get's u the output:

> 
Setting up sun-java6-bin (6-00-2ubuntu2) ...
/usr/lib/jvm/java-6-sun-1.6.0.00/bin/java: error while loading shared libraries: libjli.so: cannot open shared object file: No such file or directory
dpkg: error processing sun-java6-bin (--configure):
 subprocess post-installation script returned error exit status 127


----
That means something is wrong with **libjli**

so:
```

$ sudo apt-get purge libjline-java sun-java6-jre
$ sudo apt-get install libjline-java sun-java6-jre

```

what's happening now?
and I hoepe u're using these repositories: [http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Manual_Method)

---

### Post by Joshua Swink on 2007-12-13
Here's a workaround. It's for making the package install and configure properly, not for actually running java in the chrooted environment.

1. Install sun-java6-bin. It fails to configure.
2. Find out where libjli.so is. Do "locate libjli.so". In my case it was here:

/opt/jdk1.7.0/jre/lib/i386/jli/libjli.so

3. Set the LD_LIBRARY_PATH variable so that the package can configure properly. Enter the following command (using your location of libjli.so):

```
LD_LIBRARY_PATH=/opt/jdk1.7.0/jre/lib/i386/jli dpkg --configure -a
```

Hopefully it's now installed and configured correctly.

---

### Post by whit on 2008-03-08
Just to make things fun, "locate" doesn't work in the chroot, even after running updatedb. (Of course, it can be run outside of the chroot, and then its results adapted to use within it.)

---

### Post by aMeR1CaN_aUsSie on 2008-06-15
Hey guys, for anyone else with this problem, I just made a tutorial here:

[http://ubuntuforums.org/showthread.php?t=829866]("http://ubuntuforums.org/showthread.php?t=829866")

Enjoy.

aMeR1CaN_aUsSiE

---

