---
title: "build-essential without Internet connection?"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2008-08-03
I got a problem! I need to compile the driver for the Ethernet card and need therefore build-essential. However, as I read, it depends on a lot of other things, which I cannot find, or found newer ones:

> binutils_2.18.1~cvs20080103-0ubuntu1_i386.deb 
perl-modules_5.8.8-12_all.deb 
build-essential_11.3ubuntu1_i386.deb 
bzip2_1.0.4-2ubuntu4_i386.deb 
cpio_2.9-6ubuntu1_i386.deb 
cpp_4.2.3-1ubuntu3_i386.deb 
cpp-4.2_4.2.3-2ubuntu7_i386.deb 
dpkg-dev_1.14.16.6ubuntu3_all.deb 
g++_4.2.3-1ubuntu3_i386.deb 
g++-4.2_4.2.3-2ubuntu7_i386.deb 
gcc-4.2_4.2.3-2ubuntu7_i386.deb 
gcc-4.2-base_4.2.3-2ubuntu7_i386.deb 
libbz2-1.0_1.0.4-2ubuntu4_i386.deb 
libc6_2.7-10ubuntu3_i386.deb 
libc6-dev_2.7-10ubuntu3_i386.deb 
libgcc1_4.2.3-2ubuntu7_i386.deb 
libgomp1_4.2.3-2ubuntu7_i386.deb 
libstdc++6-4.2-dev_4.2.3-2ubuntu7_i386.deb 
libtimedate-perl_1.1600-9_all.deb 
linux-libc-dev_2.6.24-19.36_i386.deb 
lzma_4.43-12ubuntu1_i386.deb 
make_3.81-3build1_i386.deb 
patch_2.5.9-4_i386.deb 


I found so far:
> binutils_2.18.50.20080707-0ubuntu1_i386.deb
build-essential_11.4_i386.deb
bzip2_1.0.5-0.1ubuntu1_i386.deb
cpio_2.9-13ubuntu1_i386.deb
cpp-4.2_4.2.4-3ubuntu2_i386.deb
g++-4.2_4.2.4-3ubuntu2_i386.deb
gcc-4.2-base_4.2.4-3ubuntu2_i386.deb
libbz2-1.0_1.0.5-0.1ubuntu1_i386.deb
lzma_4.43-14ubuntu1_i386.deb
make_3.81-5_i386.deb
patch_2.5.9-5_i386.deb
perl-modules_5.10.0-11.1ubuntu2_all.deb


1. Are these ok?
2. Where do I find the other files?

Thanks!

bye

R.

---

### Post by tamoneya on 2008-08-03
use APTonCD.
[http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)

It will make youre life a lot easier.

---

### Post by ELMIT on 2008-08-03
Thanks, that  is what I want.

But wait, how do I get the packages onto the CD? Are these all what I need? Are there more? Are these the right ones? Where are the others, which I have not found?

bye

R.

---

### Post by tamoneya on 2008-08-03
you get the packages onto the CD the same way you would have gotten the deb Files you listed.  I cannot confirm that your list is everything you need since I honestly dont know.  AptonCD hwoever should get you everything you need.

---

### Post by BGFG on 2008-08-03
Correct me if i am wrong, but Aptoncd works with packages already downloaded. if ELMIT is looking for the packages external to his machine with no net connection then how does aptoncd apply ?

You could try using the live cd on a machine with a net connection. Then use the live synaptic to download your build-essential packages.
Then 
```

sudo nautilus

```
and copy the contents of
```

/var/cache/apt/archives/

```
to a usb drive, then copy this stuff into the same directory on your machine and execute your necessary commands. I did that before once when i un-installed my hal.

Best of Luck.

---

### Post by ELMIT on 2008-08-03
BGBF, you are correct!

Is there a way to get all the information before I burn a CD?
My desktop is a AMD, so packages from there will not work.

An idea would be to install a virtual machine (infotek Virtualbox) with a i386 environment (how do I define that?) and use apt-get with download only (how do I do that? or where are the packages stored, and move all these to the CD?)

If I could get something like that to work, than I would have solved the source location of ALL packages and the dependencies. 

bye

R.

---

### Post by BGFG on 2008-08-03
> **ELMIT said:**
> BGBF, you are correct!

Is there a way to get all the information before I burn a CD?
My desktop is a AMD, so packages from there will not work.

An idea would be to install a virtual machine (infotek Virtualbox) with a i386 environment (how do I define that?) and use apt-get with download only (how do I do that? or where are the packages stored, and move all these to the CD?)

If I could get something like that to work, than I would have solved the source location of ALL packages and the dependencies. 

bye

R.

I use SunVB and that supports up to i586 so i think you should be cool with a VM. As for apt-get you can enter:
```

sudo apt-get -d 'package'

```
To download only.

You can also use synaptic and when you hit apply and the dialog appears you can click 'download only'

I believe all packages are stored in the same place:
/var/cache/apt/archives/

So once your VM is up and running, then begins the fun :)

For help with all apt-get and aptitude commands use :
```

apt-get -h
aptitude -h

```

---

### Post by utopiananarchist on 2008-08-27
I know this thread has been dead for a few weeks, but I have a situation similar to ELMIT's first post. I have my hp laptop set up as a dual-boot b/w xp & ubuntu, and of course like most of the other newbies I have seen posting in this forum, I couldn't get an internet connection in Ubuntu. I looked over several tutorials & found that I need to install build-essential but it has several dependencies. I have found all that seem to apply on the Ubuntu package manager website, but now I've hit a brick wall. I've gotten to where I need to install g++-4.2 & libstdc++6-4.2 . . . but when I try to install either of them they both say that they depend on the other one being installed first!! What do I do??

---

### Post by ELMIT on 2008-08-28
I had no idea anymore how to solve it, so I gone that way below:

1. downloaded the ENTIRE UBUNTU package tree, and deleted amd64 packages, leaving you still more than 20 GB !!!
2. I put all onto an external USB hard disk

(at that moment the eeepc kernel was ready and I used that one, but my plan was:)

3. use Add CD to install packages from the CD/USB hard drive

I keep now this harddisk with the 8.04.1 CD ready for any other 386 installation try. So I start from a clean point and can then, when the connection is established upgrade to the next level.

Good luck!

bye

R.

---

