---
title: "how do I install things I downloaded"
date: 2008-11-01
forum: Installation &amp; Upgrades
---

### Post by flyingsliverfin on 2008-11-01
I am trying to find out how to install things I download off the internet, because (unlike on windows) there isn't just an executable you can click on. 

Is there some kind of file that is common to everything I download? (that I can click on)

---

### Post by Partyboi2 on 2008-11-01
Try find a .deb package for the program you want to install and check the ubuntu repos first to see if its not already available. To install a deb package you can just double click on it.  If you cannot find a deb package then you can download the source and compile it (a whole lot of fun)

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by ugm6hr on 2008-11-01
[http://ubuntuforums.org/showthread.php?p=5004960#post5004960](http://ubuntuforums.org/showthread.php?p=5004960#post5004960)

---

### Post by flyingsliverfin on 2008-11-04
what if it isn't a .deb file? and I don't do it through the terminal?

---

### Post by pirattrev on 2008-11-04
if it isn't a .deb file then "just clicking on it" won't work, just like in windows if you're given a folder full of files it doesn't just work sometimes and you need to put them in the right place.  To do this, depending on the "thing" you're getting, look for the readme.txt, or the install.txt.  If if is a program that can work on ubuntu (ie it's not an executable for another system such as a Fedora .rpm) there should be instructions on how to "make" it.

*note: usually what will happen if it's a program that isn't a .deb but is meant to work on multiple systems is it will be a .tar.gz archive.  This archive is just a compression of a folder filled with the working files for the program. Because different systems handle information differently it isn't compiled as a .deb or a .rpm (which is system dependent) so instead they leave it open to interpretation (As I like to say).  So usually in the command line you have to execute a few commands [make and makeinstall are common] that'll compile those files for your computer.

---

### Post by Therion on 2008-11-04
> **flyingsliverfin said:**
> what if it isn't a .deb file? and I don't do it through the terminal?
To boil it down you really have three ways of installing software in Ubuntu:

1.  Synaptic.  You search for something in the repository and install it using Synaptic Package Manager.  This is the easiest, safest way (IMO, and I think most would agree) to install software on Ubuntu.

2.  Find a .deb (also called a package) for the application you want. These .deb files are the closest thing you will find to an .exe file like you would have for Windows.  This is not always possible as not all applications come as .deb files.

3.  Install from source.  This means you would download a "tarball" -- a compressed file, usually a *.tar.gz file that needs to be uncompressed and then installed using the Terminal.  The specifics of installing from source are more complicated and vary depending on what, exactly, it is you want to install.

---

### Post by pirattrev on 2008-11-04
and just so you know, the synaptic method mentioned above is just getting the .debs for you from secure sources and installing them.  Although getting .debs from sites works well, the site could give you a "bad" package which contains malicious code, therefore the repo provided .debs in Synaptic are recommended (and additionally are more stable and maintained).

---

### Post by Partyboi2 on 2008-11-04
> **flyingsliverfin said:**
> what if it isn't a .deb file? and I don't do it through the terminal?
Do you have a program in mind that you are wanting to install?

---

### Post by lisati on 2008-11-04
Many of the programs available from the Synaptic manager can also be installed from the "Add/Remove software" menu, which can also be a little less daunting fore newcomers to Ubuntu.

---

### Post by flyingsliverfin on 2008-11-05
I'll find an example on the weekend, too much homework today and day after that and day after that. 


srry

yes I also do know about add/removem but thanx anyway

---

### Post by flyingsliverfin on 2008-11-06
lets try to install the splix at 

[http://www.openprinting.org/show_driver.cgi?driver=splix](http://www.openprinting.org/show_driver.cgi?driver=splix)

and from the choices the first one in the x86 64 (RPM for LSB 3.2)
how would I do that without looking at the instructions?

---

### Post by Partyboi2 on 2008-11-06
Rpm are what redhat distros use, ubuntu is derived from debian so to install a .rpm you would need to convert it to a .deb and install it, but converting a rpm to deb does not always install well. So what you could do when you come across a program you would like to install from the net is to open up synaptic (System>Admin>Synaptic Package Manager) and do a search for it. In the case of splix you would see that there is already a version of it in the ubuntu repos. So you can install it from synapitc. Or from a terminal (Applications>Accessories>Terminal)
```
 sudo apt-get install splix
```

---

### Post by flyingsliverfin on 2008-11-06
just so I know for the future, how to you change the RPM to a DEB?

---

### Post by Partyboi2 on 2008-11-06
You would need to install a package called alien which is used to convert rpms to debs
See [[COLOR=Blue]here[/COLOR]]("http://ubuntu.wordpress.com/2005/09/23/installing-using-an-rpm-file/")

---

