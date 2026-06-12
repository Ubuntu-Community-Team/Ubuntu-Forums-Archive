---
title: "cant install kernel headers"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by markusb on 2008-02-18
Hi

I'm trying to install the NVidia driver on my ubuntu system and I can't install the kernel headers. All the help I can find for this uses apt-get which seems to require either an internet connection or the CD and unfortunatley I have neither.

Is there a way I can download them on another computer and install them independently? What files do I need and where do I get them?

My system is an Intel Pentium 4 3.00 GHz with 1Gig of memory. My kernel version is 2.6.17-11-386.

Many thanks

---

### Post by richardjennings on 2008-02-18
I presume you are using edgy?

[http://packages.ubuntu.com/edgy/devel/linux-headers-2.6.17-11](http://packages.ubuntu.com/edgy/devel/linux-headers-2.6.17-11)

---

### Post by markusb on 2008-02-21
To be honest, I don't know. A friend installed it for me, which is why I don't have the CD. How can I find out? Thanks for the reply.

---

### Post by PmDematagoda on 2008-02-21
Please post the output of:-
```
cat /etc/lsb-release
```

---

### Post by markusb on 2008-02-24
Hi, here it is. Looks like it is edgy

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=6.10
DISTRIB_CODENAME=edgy
DISTRIB_DISCRIPTION="Ubuntu 6.10"

---

### Post by PmDematagoda on 2008-02-24
You can get the required packages from the [Ubuntu Packages]("http://packages.ubuntu.com/") web site. By the way, you will need to obtain the packages for Ubuntu Edgy:).

---

### Post by markusb on 2008-02-25
Hi, thanks for that. I went to the web link and typed "kernel headers" in the search box. It came up with this:

gutsy: Virtual package 
provided by: linux-libc-dev 

Is that right? Sorry if I sound a bit dense but I'm not a linux expert. Thanks for the help.

---

### Post by PmDematagoda on 2008-02-25
Just use the search phrase "linux", that will get you the headers.

---

### Post by markusb on 2008-03-25
Hi, Sorry for the long wait, I've been away for a while. This is the current situation regarding my NVidia installation, I downloaded the file linux-2.6.22.14.21_i386.deb from the site listed above, when I tried to install it it said that it required the linux restricted modules. I downloaded and installed the following files: linux-restricted-modules-generic_2.6.17.12.1_i386.deb and linux-restricted-modules-common_2.6.17.9-12.4_all.deb. However, when I tried to install linux-2.6.22.14.21_i386.deb, it continued to say that it needed the  linux restricted modules. I installed from the deb file using the package manager. All the  linux restricted modules installations returned RESULT=0, which I assumed meant successful installation. Does anyone know what is going wrong?

Thanks

---

### Post by warp99 on 2008-03-25
Unless you have the all of the dependencies met for Nvidia you're going to have a difficult time installing the restricted drivers for Nvidia since you need many different .debs, it would be best if you had internet access or the install CD or at least the install ISO since you can mount the ISO just like a CD, then point your sources.list to the ISO:

```
sudo apt-cdrom -m -d /mount_point_of_ISO add
```

Your can try to use the Nvidia installer from the Nvidia download site:

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

Then go to packages.ubuntu.com and look for the following files for edgy:

linux-headers-2.6.17-11-386
linux-headers-2.6.17-11

install the deb files with dpkg:

```
sudo dpkg -i linux-headers-2.6.17-11*
```

Then use the Nvidia installer for the drivers:

```
sudo chmod +x NVIDIA-Linux-x86-xx.xx.xx-pkg1.run
sudo ./NVIDIA-Linux-x86-xx.xx.xx-pkg1.run
```

If all of your dependencies are met the drivers will install, but if there is an error that you haven't meet the dependencies you will need either internet access, the CD, or the ISO to complete the install. :)

---

### Post by kevdog on 2008-03-25
Or you could do the following

sudo apt-cdrom add (adds the cd to the sources list)
sudo aptitude install linux-headers-`uname -r`

Might then want to edit your apt sources list to remove the cd rom as a possible repository.

---

### Post by markusb on 2008-03-26
Hi,thanks for that, it did seem like it was going on forever. Which CD would I need for my version, or is it easy enough to upgrade?

Thanks again for all  the help

---

### Post by warp99 on 2008-03-26
You need this ISO:

[http://old-releases.ubuntu.com/releases/edgy/](http://old-releases.ubuntu.com/releases/edgy/)

burn the ISO to a CD, then add the CD to you apt sources.list:

```
sudo apt-cdrom add
```

then you can download the headers and all of the dependencies you need. You may want to upgrade since edgy 6.10 only has support until April 2008. 

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

You can't upgrade edgy 6.10 directly to the new version, which is going to be Hardy 8.04, so you may want to think about doing a reinstall with Hardy 8.04 once that comes out of beta in a couple of weeks. :)

---

### Post by markusb on 2008-03-31
Hi, the saga continues :-). I've got the CD (ubuntu-7.10-desktop-i386.iso), when I tried to mount the image, as you suggested, it came back with 'Unable to locate package file, perhaps this is not a debian disc'. I then cut the CD and opened it in adept manager. This appeared to show all the packages were installed, but still the nvidia installer claims it cannot find the headers. I am very mystified :confused:

---

### Post by PmDematagoda on 2008-03-31
> **markusb said:**
> Hi, the saga continues :-). I've got the CD (ubuntu-7.10-desktop-i386.iso), when I tried to mount the image, as you suggested, it came back with 'Unable to locate package file, perhaps this is not a debian disc'. I then cut the CD and opened it in adept manager. This appeared to show all the packages were installed, but still the nvidia installer claims it cannot find the headers. I am very mystified :confused:

Did you get the Ubuntu 7.10 CD or the Ubuntu 6.10 CD? If you got the Ubuntu 7.10 CD then it may not work for you, but in any case now that you have got the latest Ubuntu CD, why don't you install it? It can make things easier.

---

### Post by markusb on 2008-04-04
Hi, my last post didn't appear for some reason so I'll try again. I have finally accepted that I need the CD to do this, and have cut one (Ubuntu 7.1), when I try to install the headers from here, the Adept Package Manager indicates that all components are installed, yet the NVidia installer still claims there are no header files.

Does the nvidia installer need a path to the files? If so, where are they likely to be? I would greatly appreciate any help with this as I'm getting a bit desperate.

Thanks

---

### Post by markusb on 2008-04-04
Eek, sorry about the last post, I didn't see the 'next page' button.:redface:, I'll read the replies now. Ooops.

---

### Post by markusb on 2008-04-11
Hi, I tried to install the headers from the CD as described above, and it didn't work. This is a print out of what happened.

Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [9e764c52a792c05ad378458f4355198b-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes, 0 translation indexes and 1 signatures
Found label 'Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)'
This disc is called:
'Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)'
Copying package lists...gpgv: Signature made Wed 25 Oct 2006 03:10:29 PM BST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
Unmounting CD-ROM...Repeat this process for the rest of the CDs in your set.
dev@dev-desktop:/usr/src/linux-headers-2.6.17-11-generic$ uname -r
2.6.17-12-generic
dev@dev-desktop:/usr/src/linux-headers-2.6.17-11-generic$ sudo aptitude install linux-headers-2.6.17-12-generic
Reading package lists... Done
Building dependency tree
Reading state information... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "linux-headers-2.6.17-12-generic"
The following packages are BROKEN:
  linux linux-restricted-modules-generic
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
The following packages have unmet dependencies:
  linux: Depends: linux-restricted-modules which is a virtual package.
  linux-restricted-modules-generic: Depends: linux-restricted-modules-2.6.17-12-generic which is a virtual package.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
linux
linux-generic
linux-restricted-modules-generic

Score is -1003

Accept this solution? [Y/n/q/?] y
The following packages will be automatically REMOVED:
  linux linux-generic linux-restricted-modules-generic
The following packages will be REMOVED:
  linux linux-generic linux-restricted-modules-generic
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 160kB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
(Reading database ... 180817 files and directories currently installed.)
Removing linux ...
Removing linux-generic ...
Removing linux-restricted-modules-generic ...
dev@dev-desktop:/usr/src/linux-headers-2.6.17-11-generic$ sudo aptitude install linux-headers-'uname -r'
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "linux-headers-uname -r"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

