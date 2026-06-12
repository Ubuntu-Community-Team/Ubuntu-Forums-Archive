---
title: "I have some problems with HP1020 printer"
date: 2006-04-23
forum: Installation &amp; Upgrades
---

### Post by ntsb on 2006-04-23
Hi, guys,

I wanted to install HP 1020 driver in UBUNTU. But I couldn't install it. 

I downloaded foo2zjs.tar.gz

$ tar zxf foo2zjs.tar.gz
$ cd /home/user_name/foo2zjs

then I don't know what to do. I tried followings.

$ sudo make install or make install,
command not found
# make install
command not found

Pls help me!

---

### Post by amohanty on 2006-04-23
From the file: **foo2zjs/INSTALL**

> INSTALLATION
------------
Unpack:
    $ wget -O foo2zjs.tar.gz [http://foo2zjs.rkkda.com/foo2zjs.tar.gz](http://foo2zjs.rkkda.com/foo2zjs.tar.gz)
    $ tar zxf foo2zjs.tar.gz
    $ cd foo2zjs

Compile:
    $ make

Optional: Get extra files from the web, such as .ICM profiles (for
color correction) and firmware for HP 1000/1005 printers:
    $ ./getweb 2300	# Get Minolta 2300 DL .ICM files
    $ ./getweb 2200	# Get Minolta 2200 DL .ICM files
    $ ./getweb cpwl	# Get Minolta Color PageWorks/Pro L .ICM files
    $ ./getweb 1005	# Get HP LJ1005 firmware file
    $ ./getweb 1000	# Get HP LJ1000 firmware file
    $ ./getweb update	# Get latest version of this software.

Install driver, foomatic XML files, PPD files, and extra files:
    $ su		OR	$ sudo make install
    # make install

If you use CUPS to manage your printers, you must restart cupsd:
    # make cups		OR	$ sudo make cups

....

Usually in source packages there will be a file called README or INSTALL and in many cases both will be there. These files will usually contain instructions as to how to go about installing stuff.

HTH
AM

---

### Post by ntsb on 2006-04-23
I tried above.

But it did not work.

after writing $ sudo make install, there was error like "command not found"

---

### Post by Sef on 2006-04-23
To compile, you have to download build-essential first. If you don't, you can't compile.

sudo apt-get update

sudo apt-get install build-essential

---

### Post by ntsb on 2006-04-24
Hi, Sef,

I wrote your advide. But there is a still error.

The following packages have unmet dependencies:
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 3:3.3) but it is not going to be installed
E: Broken packages

hope you help me.

Thanks

---

### Post by Sef on 2006-04-26
Go to packages.ubuntu.com and in the search type the name of the missing dependencies and see if you can download them with apt-get.  Applications > Accessories > Terminal  then type 

sudo apt-get update

sudo apt-get install package-name

---

