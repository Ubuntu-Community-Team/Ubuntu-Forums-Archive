---
title: "Build gnu radio"
date: 2012-02-18
forum: Installation &amp; Upgrades
---

### Post by bahermawlawi on 2012-02-18
I want to build gnu radio but before building i need to install some dependencies.
I am using ubuntu 11.04.
This is an example of my problem..Thanks for your help.

[COLOR=#FF0000]sudo apt-get install git-core[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=#FF0000]E: Unable to locate package git-core[/COLOR]
[COLOR=#FF0000]sudo apt-get install autoconf [/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=#FF0000]Package autoconf is not available, but is referred to by another package.[/COLOR]
This may mean that the package is missing, has been obsoleted, or
is only available from another source

---

### Post by Rodney9 on 2012-02-18
gnuradio is available in Synaptic, much easier then trying to build it.

Rodney

---

### Post by bahermawlawi on 2012-02-18
I know but I want to build since i am not end user.
Thanks any way.

---

### Post by lkraemer on 2012-02-19
From the GNU Radio Web Site for Ubuntu 11.04:
[http://gnuradio.org/redmine/projects/gnuradio/wiki/UbuntuInstall](http://gnuradio.org/redmine/projects/gnuradio/wiki/UbuntuInstall)

To execute the script copy & paste the relevant command line into a terminal.

[B]
Install Dependencies[/B]

The following command line scripts will install all the required dependencies. Before running them **you should ensure that the Universe repository are enabled in "Software Sources**".

```

sudo apt-get -y install git-core autoconf automake  libtool g++ python-dev swig \
pkg-config libboost-all-dev libfftw3-dev libcppunit-dev libgsl0-dev \
libusb-dev sdcc libsdl1.2-dev python-wxgtk2.8 python-numpy \
python-cheetah python-lxml doxygen python-qt4 python-qwt5-qt4 libxi-dev \
libqt4-opengl-dev libqwt5-qt4-dev libfontconfig1-dev libxrender-dev 

```

I'd suggest you use the stable release tarball versus the BLEEDING Edge Code from the git.  But, that
is your choice.......Then refer to:
[B]
III. Start the build process[/B]
at [http://gnuradio.org/redmine/projects/gnuradio/wiki/BuildGuide](http://gnuradio.org/redmine/projects/gnuradio/wiki/BuildGuide)

Also since you are going to compile code you also need the Linux Headers and Build-Essential installed.  You also, most likely need to setup your
environment for the correct paths, so the Linker finds the LIB's.
(You can always try the Compile and see if it works and correct the errors, as you go, if needed).

REF:
[http://ubuntuforums.org/showthread.php?t=1908852&highlight=build-essential](http://ubuntuforums.org/showthread.php?t=1908852&highlight=build-essential)
Posting #2

If you can compile the Stable Code, then you can always try the Development Code.

If you have never compiled any code you are likely in for a Long Haul.

You may also need to set up your Environment, so your LIB's are found.

lk

---

### Post by bahermawlawi on 2012-02-19
Thank you...I know these things..But my problem is in the first step..
I have errors with git installer..(see red characters as input and errors)

[COLOR=#FF0000]sudo apt-get install git-core[/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=#FF0000]E: Unable to locate package git-core[/COLOR]
[COLOR=#FF0000]sudo apt-get install autoconf [/COLOR]
Reading package lists... Done
Building dependency tree       
Reading state information... Done
[COLOR=#FF0000]Package autoconf is not available, but is referred to by another package.[/COLOR]
This may mean that the package is missing, has been obsoleted, or
is only available from another source

---

### Post by lkraemer on 2012-02-19
Are you 100% sure that the Universe repository are enabled in "Software Sources"?

lk

---

### Post by bahermawlawi on 2012-02-20
How can I be sure?
Thanks

---

### Post by bahermawlawi on 2012-02-20
sudo add-apt-repository ppa:pdoes/ppa/ubuntu

Error reading [https://launchpad.net/api/1.0/~pdoes/+archive/ppa:]("https://launchpad.net/api/1.0/%7Epdoes/+archive/ppa:") <urlopen error [Errno 113] No route to host>

---

### Post by bahermawlawi on 2012-02-20
And i have these errors:
$ sudo apt-get update
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty InRelease                                   
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty InRelease                                   
  
Err [http://extras.ubuntu.com](http://extras.ubuntu.com) natty Release.gpg                                 
  Unable to connect to extras.ubuntu.com:http:
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
  Unable to connect to ppa.launchpad.net:http:
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) natty InRelease                               
  
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) natty-updates InRelease                       
  
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) natty Release.gpg                                 
  Unable to connect to ppa.launchpad.net:http:
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) natty Release.gpg                             
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) natty-updates Release.gpg                     
  Unable to connect to fr.archive.ubuntu.com:http:
Err [http://archive.canonical.com](http://archive.canonical.com) natty InRelease                               
  
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security InRelease                        
  
Err [http://security.ubuntu.com](http://security.ubuntu.com) natty-security Release.gpg
  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]
Err [http://archive.canonical.com](http://archive.canonical.com) natty Release.gpg
  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.191 80]
Reading package lists... Done
W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/natty/InRelease](http://fr.archive.ubuntu.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease](http://fr.archive.ubuntu.com/ubuntu/dists/natty-updates/InRelease)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/InRelease](http://security.ubuntu.com/ubuntu/dists/natty-security/InRelease)  

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/InRelease](http://archive.canonical.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/InRelease](http://extras.ubuntu.com/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/pdoes/ppa/ubuntu/dists/natty/InRelease](http://ppa.launchpad.net/pdoes/ppa/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/yorba/ppa/ubuntu/dists/natty/InRelease](http://ppa.launchpad.net/yorba/ppa/ubuntu/dists/natty/InRelease)  

W: Failed to fetch [http://ppa.launchpad.net/pdoes/ppa/ubuntu/dists/natty/Release.gpg](http://ppa.launchpad.net/pdoes/ppa/ubuntu/dists/natty/Release.gpg)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://extras.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to extras.ubuntu.com:http:

W: Failed to fetch [http://ppa.launchpad.net/yorba/ppa/ubuntu/dists/natty/Release.gpg](http://ppa.launchpad.net/yorba/ppa/ubuntu/dists/natty/Release.gpg)  Unable to connect to ppa.launchpad.net:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg](http://fr.archive.ubuntu.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://fr.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg](http://fr.archive.ubuntu.com/ubuntu/dists/natty-updates/Release.gpg)  Unable to connect to fr.archive.ubuntu.com:http:

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/natty/Release.gpg](http://archive.canonical.com/ubuntu/dists/natty/Release.gpg)  Unable to connect to archive.canonical.com:http: [IP: 91.189.92.191 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/natty-security/Release.gpg)  Unable to connect to security.ubuntu.com:http: [IP: 91.189.92.166 80]

W: Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by lkraemer on 2012-02-20
Check your settings for:
SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES 
and check all except source code, and server for United States.

If those are checked you have Mulit-Universe enabled.
This was on Ubuntu 10.04 LTS.

lk

---

