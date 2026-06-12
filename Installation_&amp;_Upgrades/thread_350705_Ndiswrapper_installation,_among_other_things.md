---
title: "Ndiswrapper installation, among other things"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by trenog on 2007-01-31
Hello. I recently installed Ubuntu Dapper and I wanted to try and get my DWL-G132 to start working so I went searching for information about it and ndiswrapper. That's my ultimate problem but not my immediate problem.

My problem is this: I went to the ndiswrapper wiki page in order to find out how to install ndiswrapper but the thing is though it is not working for whatever reason. The terminal output was the following from my input of (sudo apt-get install linux-headers-$(uname -r)) to first get the headers installed:

```
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  linux-headers-2.6.15-26
The following NEW packages will be installed:
  linux-headers-2.6.15-26 linux-headers-2.6.15-26-386
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 7759kB of archives.
After unpacking, 79.6MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Err http://security.ubuntu.com dapper-security/main linux-headers-2.6.15-26 2.6.15-26.46
  Temporary failure resolving 'security.ubuntu.com'
Err http://security.ubuntu.com dapper-security/main linux-headers-2.6.15-26-386 2.6.15-26.46
  Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-26_2.6.15-26.46_i386.deb Temporary failure resolving 'security.ubuntu.com'
Failed to fetch http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-26-386_2.6.15-26.46_i386.deb Temporary failure resolving 'security.ubuntu.com'
E: Unable to fetch some archives, try running apt-get update or apt-get --fix-missing.
```

When I tried the second part of the process in the wiki (sudo apt-get install dh-make fakeroot gcc-3.4 build-essential) I got the following:

```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package dh-make
```

And finally when I tried the step that would start the installation process, I got the following from this (```
trenog@trenog-desktop:~/Desktop/ndiswrapper-1.35$ sudo make uninstall
```
)

```
sudo: make: command not found
```

Anyone got any help to give to me?

Thanks

---

### Post by trenog on 2007-02-01
So it appears that despite the fact that Ubuntu was trying to connect to the internet, which is what I don't have right now, it was looking for files that don't exist. The closest files that I found that match them were these:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-26_2.6.15-26.47_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-26_2.6.15-26.47_i386.deb)
[http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-26-386_2.6.15-26.47_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-26-386_2.6.15-26.47_i386.deb)

instead of the files it was looking for that were these:

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-26_2.6.15-26.46_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-26_2.6.15-26.46_i386.deb)
[http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-26-386_2.6.15-26.46_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-26-386_2.6.15-26.46_i386.deb)

How would I install these or should I be doing something else?

Also, what's the deal with the dh-make package problem?

---

### Post by trenog on 2007-02-04
Is there no one who knows what's going on with my installation? No advice?

---

### Post by pmshirey on 2007-02-04
Here is what I always do.[LIST=1]
[*]Insert the live CD
[*]Go to synaptic package manager
[*]click on search
[*]type in ndiswrapper
[*]mark ndiswrapper-common for installation
[*]mark ndiswrapper 1.8 utils for installation
[*]click apply
[/LIST]
And that is how i install ndiswrapper

---

### Post by trenog on 2007-02-04
Thanks for the info. Looking at the package manager really helped as it seems like many packages weren't installed with my initial Dapper installation, including make :( .

Since installing the packages I needed I managed to get ndiswrapper installed and my DWL-G132 recognized and working. I'm happily posting from ubuntu :)

---

