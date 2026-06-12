---
title: "build-essential need gcc,g++"
date: 2012-03-31
forum: Installation &amp; Upgrades
---

### Post by natural0 on 2012-03-31
Hi.
I use lubuntu-11.10-alternate-amd64.
because I don't have network so I download *.deb files on other computer to use.

Now I got some promble while install build-essential&#65306;

$sudo dpkg -i build-essential_11.5_amd64.deb 

Selecting previously deselected package build-essential.
(Reading database ... 98863 files and directories currently installed.)
Unpacking build-essential (from build-essential_11.5_amd64.deb) ...
dpkg: dependency problems prevent configuration of build-essential:
 build-essential depends on gcc (>= 4:4.4.3); however:
  Package gcc is not installed.
 build-essential depends on g++ (>= 4:4.4.3); however:
  Package g++ is not installed.
dpkg: error processing build-essential (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 build-essential


But I already have install :
gcc-4.6_4.6.1-9ubuntu3_amd64.deb
g++-4.6_4.6.1-9ubuntu3_amd64.deb

what can I do&#65311;

---

### Post by lkraemer on 2012-03-31
Your problem is that not all of the dependencies are satisfied for the *.deb files you have copied to your Hard Drive.
It is almost an impossible problem to get everything installed without an internet connection.........You're best bet
is pack your computer to a buddy's house and use his internet connection to install what you need........
But, you can keep trying until you finally get everything downloaded, it's going to be an ordeal....

First, thing you need is to make sure all the dependencies are installed by looking at each deb.  I've included a
Screenshot of the dependencies for build-essential (my Debian 6 install).....  You are also going to need the
linux-headers for your running kernel, along with several other -dev files........So for each of the items listed in the
dependencies for build-essential, you are going to have to find each of those (libs or debs) dependencies, and each of those
under that tree....... I just did the first....libc6-dev as an example.......and kept looking for the required dependencies.
You also need to do everything for all of the *-dev files, the linux-headers* files, and anything referenced as a dependency by 
items included......I hope you get the picture...... 

You also need to make sure that your Install CD/DVD is in the DVD/CDROM Drive and that DVD/CDROM drive is selected (Checked)
as being added as available versus the typical USA Server..........in SOFTWARE SOURCES.

REF:
[http://ubuntuforums.org/showthread.php?t=1908852&highlight=typical+compile](http://ubuntuforums.org/showthread.php?t=1908852&highlight=typical+compile)
Posting #2.

Just skip the information about compiling from source for the time being.....and start at: **INSTALL REQUIRED SOFTWARE FOR COMPILE:**


Larry

---

### Post by natural0 on 2012-03-31
Here is what I did:

$ sudo apt-get update
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/main/binary-i386/ InRelease
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/multiverse/binary-i386/ InRelease
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/restricted/binary-i386/ InRelease
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/universe/binary-i386/ InRelease
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) oneiric InRelease
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/main/binary-i386/ Release.gpg
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/multiverse/binary-i386/ Release.gpg
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/restricted/binary-i386/ Release.gpg
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/universe/binary-i386/ Release.gpg
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/main/binary-i386/ Release
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/multiverse/binary-i386/ Release
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/restricted/binary-i386/ Release
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/universe/binary-i386/ Release
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/main/binary-i386/ Packages/DiffIndex
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/multiverse/binary-i386/ Packages/DiffIndex
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/restricted/binary-i386/ Packages/DiffIndex
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/universe/binary-i386/ Packages/DiffIndex
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/main/binary-i386/ Translation-en_US
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/main/binary-i386/ Translation-en
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/main/binary-i386/ Translation-zh
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/multiverse/binary-i386/ Translation-en_US
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/multiverse/binary-i386/ Translation-en
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/multiverse/binary-i386/ Translation-zh
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/restricted/binary-i386/ Translation-en_US
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/restricted/binary-i386/ Translation-en
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/restricted/binary-i386/ Translation-zh
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/universe/binary-i386/ Translation-en_US
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/universe/binary-i386/ Translation-en
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) dists/oneiric/universe/binary-i386/ Translation-zh
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) oneiric/main TranslationIndex
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) oneiric/multiverse TranslationIndex
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) oneiric/restricted TranslationIndex
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) oneiric/universe TranslationIndex
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) oneiric/main Translation-en_US
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) oneiric/main Translation-en
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) oneiric/main Translation-zh
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) oneiric/multiverse Translation-en_US
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) oneiric/multiverse Translation-en
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) oneiric/multiverse Translation-zh
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) oneiric/restricted Translation-en_US
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) oneiric/restricted Translation-en
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) oneiric/restricted Translation-zh
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) oneiric/universe Translation-en_US
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) oneiric/universe Translation-en
Ign cdrom://Lubuntu 11.10 _Oneiric Ocelot_ - Release amd64 (20111011) oneiric/universe Translation-zh
Reading package lists... Done
++++++++++++++++++++++++++++++++++++
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
++++++++++++++++++++++++++++++++++++
$ sudo dpkg -i gcc-4.6_4.6.1-9ubuntu3_amd64.deb 
(Reading database ... 99498 files and directories currently installed.)
Preparing to replace gcc-4.6 4.6.1-9ubuntu3 (using gcc-4.6_4.6.1-9ubuntu3_amd64.deb) ...
Unpacking replacement gcc-4.6 ...
Setting up gcc-4.6 (4.6.1-9ubuntu3) ...
Processing triggers for man-db ...
+++++++++++++++++++++++++++++++++++
$ sudo dpkg -i g++-4.6_4.6.1-9ubuntu3_amd64.deb 
(Reading database ... 99498 files and directories currently installed.)
Preparing to replace g++-4.6 4.6.1-9ubuntu3 (using g++-4.6_4.6.1-9ubuntu3_amd64.deb) ...
Unpacking replacement g++-4.6 ...
Setting up g++-4.6 (4.6.1-9ubuntu3) ...
Processing triggers for man-db ...
+++++++++++++++++++++++++++++++++++
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

for now,I use:
sudo apt-get -f install
sudo dpkg --configure -a
sudo aptitude install 
It's all OK, no dependencies issue.

++++++++++++++++++++++++++++++++++
sudo dpkg -i build-essential_11.5ubuntu1_amd64.deb 
Selecting previously deselected package build-essential.
(Reading database ... 99498 files and directories currently installed.)
Unpacking build-essential (from build-essential_11.5ubuntu1_amd64.deb) ...
dpkg: dependency problems prevent configuration of build-essential:
 build-essential depends on gcc (>= 4:4.4.3); however:
  Package gcc is not installed.
 build-essential depends on g++ (>= 4:4.4.3); however:
  Package g++ is not installed.
dpkg: error processing build-essential (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 build-essential
++++++++++++++++++++++++++++++++++++

And about the build-essential_11.5 dependencies you give to me,
I compare to mine&#65306;
libc6 = 2.11.3-2  
libc6 (>2.11) (<2.12) 
libc-dev-bin =2.11.3-2      

I'm both ver. 2.13-20ubuntu5.1,
But I download package form [http://packages.ubuntu.com/](http://packages.ubuntu.com/), 
there's no ver.2.11.3-2 but only my 2.13-20ubuntu5.1.

The website shows  depends,  recommends, suggests packages.
I always got all the depends files....

Is there any other things I should try,or checking?

Thanks your help, and sorry about my poor English.

---

### Post by marinara on 2012-04-01
sorry you don't hve internet.
does this help:
[http://askubuntu.com/questions/8344/package-dependency-problem-offline-install-of-wireless-drivers](http://askubuntu.com/questions/8344/package-dependency-problem-offline-install-of-wireless-drivers)

---

### Post by lkraemer on 2012-04-02
Your problem is that the current installed versions DO NOT satisfy the
dependencies for gcc, g++, build-essential, linux-headers*, etc.....
You have downloaded the NEWER *.debs for gcc, g++, build-essential, linux-headers*, etc......
and each of those NEWER FILES/debs have dependencies that have to be met
before they will install.

To see what versions of gcc & g++ are currently installed try these commands:
```

which gcc
gcc --version
which g++
g++ --version

```
You should find that it isn't the version from the *.deb that you are thinking is installed.
So, to get gcc & g++ installed you are going to need to locate all their dependencies, install
the dependencies, then try to install gcc & g++ again.  Then you will continue to build-essential,
and the linux-headers, repeating the process...........hour after hour......

I've attached a photo of the first dependency for gcc (Debian 6.0) and the other items that are installed.

Once again, the easiest thing to do is get Internet access, even if it is by modem, to update
your system and install the required dependencies.  What is preventing you from accessing the
internet?  Beg or borrow a Modem from a buddy.....Even if it takes overnight to download what
you need updated......


lk

---

### Post by natural0 on 2012-04-06
I solved the promble...
it's foolish that I did't know the gcc and gcc-4.4 are different.
I was only installed the gcc-4.4, and NEVER install gcc.....
how embarrassing.... 0.0

---

