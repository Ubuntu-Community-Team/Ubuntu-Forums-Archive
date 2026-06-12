---
title: "Package manager broken"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by joshli on 2010-01-18
Hello.

When I try to use apt-get, Ubuntu Software Center, or Synaptics manager, it will have an error and says that the installer is broken.

So, I run the command ```
sudo apt-get install -f
```
It installs everything except for this one package called splashy. I keep trying to use this command and it still doesn't work. I can not install anything else because of this.

```

root@www:~# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  splashy
Suggested packages:
  console-common
The following NEW packages will be installed:
  splashy
0 upgraded, 1 newly installed, 0 to remove and 43 not upgraded.
6 not fully installed or removed.
Need to get 0B/1,181kB of archives.
After this operation, 1,839kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 177641 files and directories currently installed.)
Unpacking splashy (from .../splashy_0.3.13-5ubuntu1_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/splashy_0.3.13-5ubuntu1_i386.deb (--unpack):
 trying to overwrite '/etc/lsb-base-logging.sh', which is also in package lsb-base 0:4.0-0ubuntu5
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/splashy_0.3.13-5ubuntu1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

If I use Synaptic Package Manager and I press fix broken packages, this is what comes up:
```

E: /var/cache/apt/archives/splashy_0.3.13-5ubuntu1_i386.deb: trying
 to overwrite '/etc/lsb-base-logging.sh', which is also in package lsb-base 0

```
Thanks for your help.

---

### Post by phillw on 2010-01-18
Hi,

have you tried ```
sudo dpkg --configure -a
```

That usually gets it back happy.

Regards,

Phill.

---

### Post by joshli on 2010-01-20
Nope. It still does not work ):

```
joshli@www:~$ sudo dpkg --configure -a
[sudo] password for joshli: 
dpkg: dependency problems prevent configuration of splashy-themes:
 splashy-themes depends on splashy (>= 0.3.12-1); however:
  Package splashy is not installed.
dpkg: error processing splashy-themes (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 splashy-themes
```

Is there a way to force remove splashy-themes? Or manually install the dependency for splashy?

---

### Post by lykwydchykyn on 2010-01-20
I don't think it will. dpkg -configure -a simply re-runs the configuration portion of the apt install, which is where things are breaking down for you.

What's happening is that the "splashy" package contains a file which is also in another package lsb-base.  Package managers don't allow packages to overwrite files in other packages as a safeguard.  You have basically three options to fix this:

 - Remove splashy; it's a legacy bootsplash system which you can safely remove, but you may end up with no bootsplash (only a cosmetic issue). If you want the original Ubuntu bootsplash back, install usplash.

 - Remove lsb-base: I wouldn't recommend this, as it was likely installed as a dependency for something.  

 - Force overwrite:  You can just force the package manager to overwrite the file even though it's in another package.  Just enter this:

```

sudo dpkg -i --force-all /var/cache/apt/archives/splashy_0.3.13-5ubuntu1_i386.deb

```
Of course, you run the risk of breaking the other package if the contents of that file are different.

---

### Post by joshli on 2010-01-20
> **lykwydchykyn said:**
> 
 - Force overwrite:  You can just force the package manager to overwrite the file even though it's in another package.  Just enter this:

```

sudo dpkg -i --force-all /var/cache/apt/archives/splashy_0.3.13-5ubuntu1_i386.deb

```


Thank you very much. This fix worked.

---

