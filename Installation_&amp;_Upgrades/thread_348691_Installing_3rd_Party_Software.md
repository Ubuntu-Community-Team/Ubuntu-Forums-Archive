---
title: "Installing 3rd Party Software"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by satyagunturi on 2007-01-29
Hi 

I recently installed 6.10 Edgy Eft from Live CD on my Intel x86 PC.  Everything is working fine but I am just not able to install any new software.  For example I tried installing Real Player.  I downloaded the tar file, tried tar -zxvf only to find the ./configure returns errors.  So I thought I will try the RPM way but looks like ubuntu does not support RPMs!  When I type in "rpm -qa" on command prompt I get an error saying rpm: command not found.  I tried to use synaptic but dont see an option in it to install an already downloaded rpm/tar and I dont know how to make synaptic/apt-get download and install new software such as this.

I am stumped for ideas and help will be greatly appreciated!

Satya

---

### Post by renzokuken on 2007-01-29
you probably have to install the build-essentials package to build from source.

```
sudo apt-get install build-essential
```

RPMs can be installed in ubuntu, but they have to be converted to debs first using a program called "alien".

i would use Synaptic Package Manager to find and install programs though, its in one of the menus

have a read of this [https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware) and this [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by mdumka on 2007-01-29
Hi there thanks for all of the info  ...

But I think I am in the same boat, I have downloaded a tar.bz2 file to my desktop, now how do I install this using Synaptic as I can not find an option to find local files ... 

Thanks

Mike

---

### Post by renzokuken on 2007-01-29
ok, a tar.bz2 file is a compressed file, same as a .zip or .rar file.

right click on it and choose, "extract here". 

Synaptic only deals with .deb files, which are different, and they are ready made for ubuntu and stored in ubuntu's online repositories for easy find and install.

if you have a program which came in a .tar.bz or tar.gz file, chances are it is the source and you have to compile it yourself.

extract the folder and look for the readme or an install file which should give you instructions. most commonly, compiling from source requires you to run the following commands (although they may vary)

```

cd /to/the/directory/containg/the/source/you/have/just/downloaded
./configure
make
sudo make install

```

in order to do this you need to install the build-essential package first, which can be found and installed in Synaptic, or via the command line using

```
sudo apt-get install build-essential
```

syanptic simply does all the "sudo apt-get install whatever" for you with a nice graphical interface

which package are you specifically trying to install?

---

### Post by satyagunturi on 2007-01-30
Thanks a ton!  I will try it and post back.

Rgds.

---

### Post by satyagunturi on 2007-01-31
Using the instructions given by renzokuken I was able to install the software (Real Player).  Now when I query in Synaptic it shows Real Player as installed.

But strangely I dont see any way to run the Real Player!  There is no icon on the desktop, no entry in any of the menus.  I even tried running it from command line but it is not recognized.

Am I missing a step here?  I am aware that unlike in Windows in Linux you dont automatically get an icon on the desktop after installation.  But in suse and redhat there is at least an entry in the menu.  How do I get the same thing to happen in ubuntu?

Thanks once again for the guidance so far!

---

