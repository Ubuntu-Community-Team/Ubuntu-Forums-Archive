---
title: "* no longer a wild card in apt?"
date: 2021-01-18
forum: Installation &amp; Upgrades
---

### Post by kansasnoob on 2021-01-18
I haven't found any documentation for this but it used to be you could use * as a wild card to search packages, or maybe I had a bad dream :D

Anyway, if I'm right about the past, has that changed? Is there a replacement? I have looked at the apt man pages but sometimes something can be right in front of my nose and I don't see it.

---

### Post by ubfan1 on 2021-01-18
Well, apt-cache pkgnames never took wild cards, i pipe its output to grep.  Other apt-cache commands like show do. so depends upon what you are doing.

---

### Post by CatKiller on 2021-01-19
AFAIK, the apt command has never taken the * character as a wildcard. The older apt-get does, though, so you might be thinking of that.

---

### Post by Paddy Landau on 2021-01-19
Are you perhaps remembering dpkg and dpkg-query? They allow wildcards. Remember to quote the query string. For example:
```
dpkg-query --list 'libc6*'
```

---

### Post by kansasnoob on 2021-01-19
So being more specific here's one example. Let's say I wanted to search all packages (both installed and just available) that begin with "linux-generic". If I know the full package name I can:

```
lance@lance-desktop:~$ apt policy linux-generic
linux-generic:
  Installed: 5.4.0.62.65
  Candidate: 5.4.0.62.65
  Version table:
 *** 5.4.0.62.65 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 Packages
        100 /var/lib/dpkg/status
     5.4.0.26.32 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main amd64 Packages
lance@lance-desktop:~$ apt policy linux-generic-hwe-20.04
linux-generic-hwe-20.04:
  Installed: (none)
  Candidate: 5.8.0.38.43~20.04.23
  Version table:
     5.8.0.38.43~20.04.23 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages
        500 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 Packages
     5.4.0.26.32 500
        500 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal/main amd64 Packages
]
```

But is there a way to get a search for all packages beginning with "linux-generic" to display? Like there is actually also a 'linux-generic-hwe-18.04':

```
lance@lance-desktop:~$ apt policy linux-generic-hwe-18.04
linux-generic-hwe-18.04:
  Installed: (none)
  Candidate: 5.4.0.62.65
  Version table:
     5.4.0.62.65 500
        500 http://us.archive.ubuntu.com/ubuntu focal-updates/main amd64 Packages
        500 http://security.ubuntu.com/ubuntu focal-security/main amd64 Packages
     5.4.0.26.32 500
        500 http://us.archive.ubuntu.com/ubuntu focal/main amd64 Packages

```

Another example would be searching all 'nvidia' packages. Like I might know that my puter uses 'nvidia-340' but I also may have no idea what version of nvidia drivers I have installed. Is there a way to see from TTY what nvidia packages are installed in one fell swoop? Things like this can be very helpful if the UI is broken and you suspect kernel issues or graphics issues and you can only get into the system via TTY, possibly even in a chroot.

A third example might be examining 'grub' although in that case you could use Boot Repair to produce a report and likely find what you needed to know or at least enough to point you in the right direction.

If it's at all possible to get a working UI with the addition of a specific boot parameter my preferred method is just using Synaptic package manger - the lazy man's way out (just my speed) :D

---

### Post by CatKiller on 2021-01-19
> **kansasnoob said:**
> But is there a way to get a search for all packages beginning with "linux-generic" to display? Like there is actually also a 'linux-generic-hwe-18.04'
I would use ```
aptitude search linux-generic
``` which will return a list of matching packages and their installed status, followed by ```
aptitude show <package name>
``` if I wanted to know something particular about the versions that are installed or available.

---

### Post by #&amp;thj^% on 2021-01-19
I love aptitude, just have to be cautious mixing with "Apt" installations, not a thing wrong using it for searches though.

---

### Post by kansasnoob on 2021-01-26
> **Paddy Landau said:**
> Are you perhaps remembering dpkg and dpkg-query? They allow wildcards. Remember to quote the query string. For example:
```
dpkg-query --list 'libc6*'
```

Reading the dpkg man pages led me to using this:

dpkg --list | grep <partial-package-name>, eg:

```
lance@lance-desktop:~$ ls /boot
config-5.4.0-62-generic      memtest86+.elf
config-5.4.0-64-generic      memtest86+_multiboot.bin
grub                         System.map-5.4.0-62-generic
initrd.img                   System.map-5.4.0-64-generic
initrd.img-5.4.0-62-generic  vmlinuz
initrd.img-5.4.0-64-generic  vmlinuz-5.4.0-62-generic
initrd.img.old               vmlinuz-5.4.0-64-generic
memtest86+.bin               vmlinuz.old
lance@lance-desktop:~$ **dpkg --list | grep 5.4.0-62**
ii  linux-headers-5.4.0-62                     5.4.0-62.70                         all          Header files related to Linux kernel version 5.4.0
ii  linux-headers-5.4.0-62-generic             5.4.0-62.70                         amd64        Linux kernel headers for version 5.4.0 on 64 bit x86 SMP
ii  linux-image-5.4.0-62-generic               5.4.0-62.70                         amd64        Signed kernel image generic
ii  linux-modules-5.4.0-62-generic             5.4.0-62.70                         amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
ii  linux-modules-extra-5.4.0-62-generic       5.4.0-62.70                         amd64        Linux kernel extra modules for version 5.4.0 on 64 bit x86 SMP
```

It's not a one-size-fits-all approach but dpkg does get the job done if you're willing to study the man pages, and it does so without the need of installing additional packages.

---

### Post by Paddy Landau on 2021-01-27
> **kansasnoob said:**
> It's not a one-size-fits-all approach but dpkg does get the job done if you're willing to study the man pages, and it does so without the need of installing additional packages.
No extra packages required. dpkg-query is installed by default.

Your query doesn't need grep, though: The following two commands will do the same thing.
```
dpkg --list '*5.4.0-62*'
dpkg-query --list '*5.4.0-62*'
```
The advantage of dpkg-query over dpkg is that it's explicitly a query, so you avoid accidentally making a change. But you don't need to use it.

---

### Post by kansasnoob on 2021-01-27
> **Paddy Landau said:**
> No extra packages required. dpkg-query is installed by default.

Your query doesn't need grep, though: The following two commands will do the same thing.
```
dpkg --list '*5.4.0-62*'
dpkg-query --list '*5.4.0-62*'
```
The advantage of dpkg-query over dpkg is that it's explicitly a query, so you avoid accidentally making a change. But you don't need to use it.

Sweet! That brings the wildcard into play as I'd inquired about. Also shows available (uninstalled) packages as well.

---

### Post by TheFu on 2021-01-27
Not sure when, but apt added some regex support in the last 1-2 months similar to what apt-get has.
I use it mostly to purge unwanted package like nano, network-manager, apt-notifier.
```
sudo apt purge nm-*
``` is an example.

It can be handy to get a list of old kernels, headers, modules to be purged so that /boot/ doesn't get filled by having 2+ lines of kernels updated.

---

### Post by kansasnoob on 2021-01-27
> **TheFu said:**
> Not sure when, but apt added some regex support in the last 1-2 months similar to what apt-get has.
I use it mostly to purge unwanted package like nano, network-manager, apt-notifier.
```
sudo apt purge nm-*
``` is an example.

It can be handy to get a list of old kernels, headers, modules to be purged so that /boot/ doesn't get filled by having 2+ lines of kernels updated.

I'll have to experiment a bit with that. One recent project involved purging nvidia drivers from TTY but it took me a long time to figure out exactly what version and what the full package name was.

---

### Post by ubfan1 on 2021-01-27
Of course, it never hurts to quote the name with the wildcard, to avoid any possible expansion into a local filename. ;^)

---

### Post by TheFu on 2021-01-28
> **kansasnoob said:**
>  but it took me a long time to figure out exactly what version and what the full package name was.

There are multiple ways to have APT tell us things.  My most common things are:

What package is this file in?   $ dpkg -S /bin/ls
What packages are related to kernels I have installed?   
```
$ **dpkg -S  /boot/vmlinuz-4.15.0-129-generic**
linux-image-4.15.0-129-generic: /boot/vmlinuz-4.15.0-129-generic

```From that answer, what older kernel packages should I remove?
```
$ **dpkg -l|egrep linux-image-4.15**
rc  linux-image-4.15.0-122-generic              4.15.0-122.124~16.04.1                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-123-generic              4.15.0-123.126~16.04.1                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-126-generic              4.15.0-126.129~16.04.1                          amd64        Signed kernel image generic
rc  linux-image-4.15.0-128-generic              4.15.0-128.131~16.04.1                          amd64        Signed kernel image generic
ii  linux-image-4.15.0-129-generic              4.15.0-129.132~16.04.1                          amd64        Signed kernel image generic
ii  linux-image-4.15.0-132-generic              4.15.0-132.136~16.04.1                          amd64        Signed kernel image generic
ii  linux-image-4.15.0-70-generic               4.15.0-70.79~16.04.1                            amd64        Signed kernel image generic

```
The 'ii' answers are still installed. The 'rc' answers have been removed, but may have left some cruft around - purging will remove them from the list.
To do that, 
```
$ **sudo apt purge linux-image-4.15.0-70-generic linux-image-4.15.0-12[0-8]**
....
The following package was automatically installed and is no longer required:
  linux-modules-4.15.0-70-generic
Use 'sudo apt autoremove' to remove it.
The following packages will be REMOVED:
  linux-image-4.15.0-122-generic* linux-image-4.15.0-123-generic*
  linux-image-4.15.0-126-generic* linux-image-4.15.0-128-generic*
  linux-image-4.15.0-70-generic*
0 upgraded, 0 newly installed, 5 to remove and 0 not upgraded.
After this operation, 8,205 kB disk space will be freed.
Do you want to continue? [Y/n] Y
...
```
And to clean up the kernel modules, ...
```
$ **sudo apt autoremove **
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-modules-4.15.0-70-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 64.6 MB disk space will be freed.
Do you want to continue? [Y/n] Y
....
```

Now those extra kernel modules aren't in the list causing cruft:
```
$ **dpkg -l|egrep linux-image-4.15**
ii  linux-image-4.15.0-129-generic              4.15.0-129.132~16.04.1                          amd64        Signed kernel image generic
ii  linux-image-4.15.0-132-generic              4.15.0-132.136~16.04.1                          amd64        Signed kernel image generic

```

If you don't use grep/egrep, some changes are needed to the dpkg commands:
```
$ **dpkg -l  linux-image-4.15**
dpkg-query: no packages found matching linux-image-4.15

``` It appears to perform an exact-match search, which is not what I need/want.
```
$ **dpkg -l  linux-image-4.15***
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-==================================
un  linux-image-4. <none>       <none>       (no description available)
un  linux-image-4. <none>       <none>       (no description available)
un  linux-image-4. <none>       <none>       (no description available)
un  linux-image-4. <none>       <none>       (no description available)
ii  linux-image-4. 4.15.0-129.1 amd64        Signed kernel image generic
ii  linux-image-4. 4.15.0-132.1 amd64        Signed kernel image generic
```
Add the linux-image-4.15* with or without quotes, and we get nicer output?

And **apt** can install .deb packages AND all the dependencies now.
```
sudo apt install ./Kewl-new-package-0.1.deb
```
But, as always, directly installing .deb files that aren't specific to the Ubuntu release will probably lead to a stuck "APT" packaging system due to dependencies in 3-6 months.

---

### Post by Paddy Landau on 2021-01-28
> **TheFu said:**
> ```
sudo apt purge nm-*
```
> **ubfan1 said:**
> Of course, it never hurts to quote the name with the wildcard, to avoid any possible expansion into a local filename. ;^)
This is important. Always quote your wildcards when using apt, dpkg, etc.

Example: I have a file called fontana.odt. When I run [FONT=courier new]dpkg-query --list font*[/FONT], instead of getting a list of installed fonts, I get the message, "dpkg-query: no packages found matching fontana". I avoid this with [FONT=courier new]dpkg-query --list 'font*'[/FONT].

---

