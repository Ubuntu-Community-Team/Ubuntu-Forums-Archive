---
title: "Where can I get Kernel Source Code?"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by blkmax on 2006-06-20
Any ideas where I can download the Kernel Source code for 6.06?

thanks

Marc

---

### Post by mority on 2006-06-20
You will have to enable the repositories for the source packages in synaptic package manager. Start synaptic with *System -> Administration -> Synaptic Package Manger* and there go to *Settings -> Repositories*.

Or you do it by editing the file */etc/apt/sources.list*. You will have to use sudo to get the file permissions to write this file. You can find information on how to edit the file in the [APT HOWTO](http://www.debian.org/doc/manuals/apt-howto/ch-basico.en.html#s-sources.list). The Howto is written for a Debian system, but since Ubuntu is based on Debian and uses the same package management system, the information there should still be useful.

And then you just have to install the package with the kernel sources. You can use synaptic to search for it. It will be named something with "linux-image-2.6" in its name.

---

### Post by jchau on 2006-06-20
I'm pretty sure the linux-image is not the source, but the compiled linux kernel.
For me to point you to the right package, I'd need to know what you plan to use it for.  Do you plan to compile a new kernel?  Compile drivers?  Or just to look at it?

To compile a new kernel, you'd want the "kernel-package" and the "linux-source" package.  To compile drivers, you'd only need the appropriate "linux-header" package for your kernel (eg. if you have the 686 kernel, you would get "linux-header-686").

---

### Post by Mattias on 2006-06-20
There is a package called linux-source-2.6.15
"Linux kernel source for version 2.6.15 with Ubuntu patches"
I think this will be what blk-max wants.

---

### Post by mority on 2006-06-21
[QUOTE=jchau]I'm pretty sure the linux-image is not the source, but the compiled linux kernel.
[/QUOTE]

Yeah, that's right. Sorry, my fault. So it should be something like "linux-source-2.6.15".

---

### Post by az on 2006-06-21
[QUOTE=blkmax]Any ideas where I can download the Kernel Source code for 6.06?

thanks

Marc[/QUOTE]
Do you need to rebuild your kernel or just add an extra module to it?  If it is the latter,  don't use the whole kernel source (which you have to install, unpack, configure, and compile before using) juts use the headers.  If you are running the stock kernel, just install linux-headers-386 and you are good to go.

---

### Post by blkmax on 2006-06-21
Sorry, I should of been more clear. I'm trying to install the Cisco VPN Client. it is prompting me for the Kernel Source code. I cannot seem to see it in /USR/SRC.

I have followed the instructions above and was able to see the kernel Source, but everything had a green square in front of it and only let me uninstall it.

I am new to Ubunto but not Linux. I do not seem to understand the Synaptics manager. How can I add the Kernel source using the Synaptics.?

regards

Marc

---

### Post by mority on 2006-06-21
[QUOTE=blkmax]I am new to Ubunto but not Linux. I do not seem to understand the Synaptics manager. How can I add the Kernel source using the Synaptics.?
[/QUOTE]

Well, if you are not new to Linux you should have no problem with using the CLI. So you don't have to bother about synaptic if you don't like to. I myself use it rarely cause I think it is too slow. I use aptitude instead. If you start aptitude on the CLI without any options (with root permissions, i.e. *sudo aptitude*) you get a ncurses style interface. But I prefer using it like apt-get with direct commands on the CLI.

The most important commands are:
```

aptitude search <pattern>
aptitude install <package-name>
aptitude remove <package-name>

```

So you would do the following to get your kernel sources:
Get a shell with root permissions...
```

sudo -s

```
Search for packages.
```

aptitude search linux-source-2.6.15

```
Point out which package matches your installed kernel. Get information about the running kernel with:
```

uname -a

```
Then install the matching package (compare the exact version indicators including suffixes like '386' or 'amd64' depending on your hardware).
```

aptitude install linux-source-2.6.15-25-386
# this one is just an example! use the appropriate package name.

```

---

### Post by thasheep on 2006-06-21
You can use synaptic to get the linux-source package (search for it, double click on it and then click "apply"). It's a dummy package that will always depend on the latest linux-source package (in this case linux-source-2.6.15). You'll need to unpack it so you may as well do the whole lot by hand instead of with synaptic.
```
sudo apt-get install linux-source  # or use synaptic
cd /usr/src
sudo tar -jxf linux-source-2.6.15.tar.bz2  # unpack the source
sudo ln -s linux-source-2.6.15 linux  # create a link because some things expect to find the source at /usr/src/linux
```
I actually prefer to unpack and compile the source in my home directory because I like to keep good habits and avoid using root/sudo wherever possible - however either way works and if some tool expects it to be at /usr/src/linux then you can't really argue with it.

---

### Post by blkmax on 2006-06-21
I get the following while trying Mority's method. I used the package name from my uname -a, but it cant find any packages. Did I miss something?



marc@iitm50ws0144:~$ su root
Password:
root@iitm50ws0144:/home/marc# aptitude search linux-source-2.6.15
p   linux-source-2.6.15                          - Linux kernel source for version 2.6.15 with Ubuntu patroot@iitm50ws0144:/home/marc#
root@iitm50ws0144:/home/marc# uname -a
Linux iitm50ws0144 2.6.15-23-386 #1 PREEMPT Tue May 23 13:49:40 UTC 2006 i686 GNU/Linux
root@iitm50ws0144:/home/marc# aptitude install linux-source-2.6.15-23-386
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "linux-source-2.6.15-23-386"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
root@iitm50ws0144:/home/marc#

thanks

Marc

---

### Post by thasheep on 2006-06-21
The package is called linux-source-2.6.15 (will also be pulled in by the package linux-source). The version number shouldn't be specified. Also, the architecture (386/686/k7/etc) isn't needed because sources (not just for the kernel) are archecture independent.

---

### Post by mority on 2006-06-21
I didn't know that the sources are architecture independent. When you searched for 'linux-source-2.6.15' (with *aptitude search linux-source-2.6.15*) you saw that there was no result like 'linux-source-2.6.15-23-386'. That's because you could not install such a package.

---

### Post by blkmax on 2006-06-21
It found linux-source-2.6.15 but not the linux-source-2.6.15-23xxxxx. I will try with just linux-source-2.6.15


Thanks

Marc

---

### Post by mority on 2006-06-21
[QUOTE=blkmax]It found linux-source-2.6.15 but not the linux-source-2.6.15-23xxxxx. I will try with just linux-source-2.6.15[/QUOTE]

Yes, that's the package you have to install since there is no architecture specific kernel source as thasheep stated above. Good Luck!

---

### Post by az on 2006-06-21
[QUOTE=blkmax]Sorry, I should of been more clear. I'm trying to install the Cisco VPN Client. it is prompting me for the Kernel Source code. I cannot seem to see it in /USR/SRC.
[/QUOTE]

You don't need the full source code.

Install the linux-headers-386 package and the installer for the VPN client should stop asking you for the source - it shoud find the headers and use that automagically.

---

### Post by blkmax on 2006-06-22
Thanks,  it copied the tar.bz2 file in /usr/src. I untared it and all is in /usr/src/linux-source-2.6.15.  I will create the link and retry my VPN installation.

thanks for all your quick replies?

Marc

---

### Post by mority on 2006-06-22
[QUOTE=blkmax]Thanks,  it copied the tar.bz2 file in /usr/src. I untared it and all is in /usr/src/linux-source-2.6.15.  I will create the link and retry my VPN installation.

thanks for all your quick replies?

Marc[/QUOTE]

That's nice, but please also listen to what azz says: You don't actualy need the kernel sources to build a module or something like that. But you will need the kernel headers. Search for them with 'aptitude search ...' and install them before you try to build that VPN thing again.

---

### Post by blkmax on 2006-06-22
thanks, but I had already got the source code before reading his post. would of saved me some time.


Marc

---

### Post by halfFAST on 2007-10-31
I know this post is a bit old, but this turned out to be just what I needed to know to finish installing drivers for an NVIDIA graphics card, so I am going to sum up what worked for me to get the kernel headers for Feisty:

$ aptitude search linux-headers

(it might be good to resize the window width as much as you can before running this command - the aptitude search does not wrap long lines for you)

$ uname -a
Linux *system.name* 2.6.20-15-generic #2 SMP Sun Apr 15 06:17:24 UTC 2007 x86_64 GNU/Linux

Now I match that bit of info with what comes back from the package search results and it looks like this is the package that I need:
p     linux-headers-2.6.20-15-generic        - Linux kernel headers for version 2.6.20 on x86/x86_64

$ aptitude install linux-headers-2.6.20-15-generic
(You might need to sudo some of these commands, I can't exactly remember if I had to or not.)

Thanks for the info, worked like a champ (Not to mention, I finally got UT2004 up and running with some decent frame rates!)

---

### Post by Calvino on 2007-12-17
Hi All,

I am using Kubuntu 7.10 and stock kernel 2.6.22-14-generic and I would like to rebuild the kernel using the very same source that the 7.10 distro uses. However, if I download source code using apt, I will get source code 2.6.22.9. And when I use the /boot/config-2.6.22.14-generic for the .config and rebuild the source my wireless card and sound card doesn't work any more. So, obviously there is difference between 2.6.22-14-generic and 2.6.22.9.

So, where can I find the source for 2.6.22-14-generic that was used for Kubuntu 7.10 distro?

Br, C

background: I have Asus G1S with 4GB RAM. The kernel needs a simple patch so that X can work properly with nVidia 8600MT graphics card.

---

