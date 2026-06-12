---
title: "how to install /lib64 absent in ubuntu 12.04"
date: 2012-07-30
forum: Installation &amp; Upgrades
---

### Post by sanatkrtiwari86 on 2012-07-30
I am trying to install lahey fortran compiler on ubuntu 12.04 64 bit.
but it is asking for /usr/lib64/ folder and some files in it ...like libelf.
how to install them.
please help

---

### Post by TheFu on 2012-07-30
> **sanatkrtiwari86 said:**
> I am trying to install lahey fortran compiler on ubuntu 12.04 64 bit.
but it is asking for /usr/lib64/ folder and some files in it ...like libelf.
how to install them.
please help

I don't have any experience with Lahey Fortran in many, many years. Could it be that their installation script is out of date and the required files are just in different locations?  Perhaps /lib or /usr/lib?  

I find the easiest way to find where files are is to use the **locate** command. It might not be installed, so install it and force it to update the DB.
```
sudo apt-get install locate
sudo updatedb

```

Now use locate to find all those libraries one at a time.
```
locate libelf
```

On my box, it found 
/usr/lib/x86_64-linux-gnu/libelf-0.152.so
/usr/lib/x86_64-linux-gnu/libelf.so.1

One of those was a softlink to the other. 

If that's the case you have a few options.
* fix the installation script to find the libraries already installed in different locations
* if all the required libs are in 1 directory, softlink that directory to /usr/lib64.
* if all the required libs are in multiple directories, softlink each into  /usr/lib64.
* if all the required libs are in multiple directories, hardlink each file into  /usr/lib64.

There are issues with soft-linking to either types, since any package  update could remove them.  You could use a hardlink to the exact library  and that will keep it around, but that could cause other issues.  A complete understanding of soft and hard  links would help with your decision.  [http://linuxgazette.net/105/pitcher.html](http://linuxgazette.net/105/pitcher.html) can help.

Softlinks are also known as **symbolic links**.

---

### Post by sanatkrtiwari86 on 2012-07-31
thanks for your reply..
But there are lot of files expected in /usr/lib64 folder.
actually it seems, this folder is needed for various other packages.

This /usr/lib64 was already present in earlier versions of ubuntu.
Is it possible to install in this 12.04 LTS version.

---

### Post by rcm0 on 2012-12-16
> **sanatkrtiwari86 said:**
> thanks for your reply..
But there are lot of files expected in /usr/lib64 folder.
actually it seems, this folder is needed for various other packages.

This /usr/lib64 was already present in earlier versions of ubuntu.
Is it possible to install in this 12.04 LTS version.
I got it Lahey FORTRAN installed under 12.04 LTS.

First install    	 	 	 	 	elfutils, libelf-dev, and lib32gcc1 packages.

Create /usr/lib64, as this directory does not exist in 12.04.

Then link with sudo ln -s /usr/lib/x86_64-linux-gnu /usr/lib64.

Install Lahey

---

