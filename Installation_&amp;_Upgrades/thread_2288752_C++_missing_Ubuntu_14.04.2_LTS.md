---
title: "C++ missing Ubuntu 14.04.2 LTS"
date: 2015-07-29
forum: Installation &amp; Upgrades
---

### Post by john433 on 2015-07-29
Hello.I am trying to get Ubuntu 14.04.2 LTS working to use OpenFOAM-2.4.0.Now I do not have internet.I load to my BlackBerry Curve then then copy to PC.I need C++ but do not know how or where to find it.There is information how to install,but nothing to download and sutiable for Ubuntu 14.04.Why also do I have so many files missing.I load one then it says I need another.Does Ubuntu not come ready to use.I have been at this for a month and still got nowhere.Any help is appreciated.Thank John

---

### Post by TheFu on 2015-07-29
Linux distros use a "package manager" to install packages over the network.  This is important because these packages have dependencies and those dependencies need to be installed before the compiler is installed.

You didn't say which version of Ubuntu was installed. The "minimal" doesn't have a compiler, for example.

It is unclear how much Unix knowledge you have, so just in-case it is minimal, [http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html](http://www.dedoimedo.com/computers/ultimate-linux-guide-for-windows-users.html) is written for people moving to Linux from Windows.

---

### Post by john433 on 2015-07-29
Thanks for answering.I downloaded Ubuntu 14.04.2 LTS from website.Trusty Tar.Why then does it say gcc and c++ missing.

---

### Post by steeldriver on 2015-07-29
Ubuntu comes ready to use - as a desktop (or as a server, if you choose the server ISO). It doesn't come ready to use as a C/C++ development platform.

 I don't recall gcc being installed out-of-the-box in either case: the usual recommendation is to install the [FONT=courier new]build-essential[/FONT] meta-package which includes gcc, g++, make and the libc6-dev libraries.

In the same way, Windows doesn't ship with Visual C/C++ / Studio.

If you really can't connect the machine to the net, there are some tricks to make it a little easier to assemble dependencies offline - such as the --print-uris option of apt-get. However it's still likely to be a slow and frustrating experience - particularly if you are using complex third-party software such as openfoam.

---

### Post by ubfan1 on 2015-07-29
Since gcc is a standard part of the distribution (and g++ isn't), probably the downloaded iso needs the update/install done to bring in all the standard packages over the minimal/old set on the iso.  Without internet, This is a problem.   If you can get an internet connection, run the software updater, then explicitly add the build-essential package (which I think brings in the g++ compiler along with other necessary headers).  Or in a terminal
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install build-essential

---

### Post by TheFu on 2015-07-29
> **steeldriver said:**
> 
In the same way, Windows doesn't ship with Visual C/C++ / Studio.


In the really old days, Unix systems came with the system C compiler.  That all changed around 1995 when IBM AIX started charging for their C compiler. All the other Unix vendors followed suite very quickly.

Most Ubuntu users have ZERO need for a C compiler, so it isn't installed by default. We get to select that kind of package ourselves.  Read about a way to tell APT to use the DVD/CD as the only source for packages - but it was an old link and didn't want to provide 10.04 instructions for a 14.04 system to someone new to Linux.  I bet it would work, but if there were any issues, I'd be blamed.

There is a command called **apt-cdrom**. Then do the normal update/install stuff.

---

### Post by john433 on 2015-07-30
Thanks once again guys.I will try that tonight.Why does a program like OpenFOAM need a C compiler then?

---

### Post by john433 on 2015-07-30
When I tried to load build-essential it said x11 file missing too

---

### Post by TheFu on 2015-07-30
> **john433 said:**
> Thanks once again guys.I will try that tonight.Why does a program like OpenFOAM need a C compiler then?

Because the developers don't provide it in pre-built, compatible-with-your-system, form, as a ready to install binary package and they wrote the program in C. 

In short, don't ask us - ask the OpenFOAM guys why they don't create Ubuntu or Debian binanary packages?  OTOH, they might only provide packages for 1 release and only for 64-bit, so anyone on a different release or 32-bit would still have to compile the program themselves.  Perhaps there are compiled in options, that some people need, but most people do not. It is very flexible.

BTW - if you like, you can make packages for Ubuntu and create a PPA for others to use which makes deploying this program just as easy as installing almost any other program. Just be certain to choose the most widely used options at compile time to help the most people.

Make sense?  There is almost always a good reason for things done the way they are. Unix is very flexible. That flexibility is extremely powerful, but sometimes it comes with more complexity.  BTW - programs are distributed for other OSes as C/C++ course code too.

---

### Post by steeldriver on 2015-07-30
FWIW OpenFOAM do provide a pre-built binary deb for Ubuntu: [http://www.openfoam.org/download/ubuntu.php](http://www.openfoam.org/download/ubuntu.php)

---

### Post by TheFu on 2015-07-30
> **steeldriver said:**
> FWIW OpenFOAM do provide a pre-built binary deb for Ubuntu: [http://www.openfoam.org/download/ubuntu.php](http://www.openfoam.org/download/ubuntu.php)

Do they discuss the dangers of installing a .deb file directly, outside a package manager?

For a system that is off-the-net, single purpose, not an issue.  Locking dependencies at a specific version like installing a .deb file does, would be bad for a system that has more general use, is on a network and needs to be maintained.

---

### Post by john433 on 2015-07-30
Thanks for all the help and advice.I have to install zlib1g-dev for OpenFOAM.I have unpacked zlib1g-dev_1.2.8.dfsg-1ubuntu1_amd64.How do install it.Do I use configure,compile or make.Have tried all but no luck.

---

### Post by TheFu on 2015-07-30
> **john433 said:**
> Thanks for all the help and advice.I have to install zlib1g-dev for OpenFOAM.I have unpacked zlib1g-dev_1.2.8.dfsg-1ubuntu1_amd64.How do install it.Do I use configure,compile or make.Have tried all but no luck.

If the file came as a .deb package - use **dpkg -i** to install. 
 Be ready for more dependencies to crop up.

---

