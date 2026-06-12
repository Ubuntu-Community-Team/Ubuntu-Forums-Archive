---
title: "Having trouble installing openoffice.org"
date: 2011-09-04
forum: Installation &amp; Upgrades
---

### Post by the-new-x on 2011-09-04
Hey guys, been a while since I've been on this website...
Anyways, I am trying to install OpenOffice.org on my laptop, so when I click the setup file, I get an error regarding Java, here is a screen-shot below:

[IMG]http://i1236.photobucket.com/albums/ff445/iareX/Screenshot-16.png[/IMG]

---

### Post by spiky001 on 2011-09-04
Is there a reason you dont want libre office? Open office is in the software centre

---

### Post by the-new-x on 2011-09-05
> **spiky001 said:**
> Is there a reason you dont want libre office? Open office is in the software centre
I couldn't find it in the software center, this is why I resorted to downloading, and I want OpenOffice.org since I read that it is much better, so I want to try it!

---

### Post by raja.genupula on 2011-09-05
i just got this from a documentation provided by Ooo . 
hope this gonna help you 
```
Java installer
This is the recommended method of installing on Linux.
Note: The Java package of the software is required to use this installer.
Installation
1. To install the software for all users, sudo to become superuser.
2. Extract the package with the following command:
tar -xvf Ooo_3.1.0_LinuxIntel_install_wJRE_en-US.tar.gz
Note: The example filename might differ from the file you have on your system.
3. cd to the folder that the tar command created.
4. To install the software for all users, type the following to become superuser:
su -
5. Grant permission to open a graphical display for root, using the authority from your user
account. This is necessary for security reasons on some systems, while on other systems
adequate security is provided without this.
XAUTHORITY=/home/{username}/.Xauthority; export XAUTHORITY
DISPLAY=:0.0; export DISPLAY
6. Start the setup program and follow the instructions.
./setup
7. If you su to install for all users, exit the superuser shell:
exit
```

---

### Post by mörgæs on 2011-09-05
It might be recommended from OOo's point of view, but not from Ubuntu's. 

As mentioned above, best is to install both Java and OO from the repositories (or even better, choose Libre Office).

---

### Post by the-new-x on 2011-09-05
> **mörgæs said:**
> It might be recommended from OOo's point of view, but not from Ubuntu's. 

As mentioned above, best is to install both Java and OO from the repositories (or even better, choose Libre Office).
is Libreoffice better than OpenOffice.org!?

---

### Post by the-new-x on 2011-09-05
> **raja.genupula said:**
> i just got this from a documentation provided by Ooo . 
hope this gonna help you 
```
Java installer
This is the recommended method of installing on Linux.
Note: The Java package of the software is required to use this installer.
Installation
1. To install the software for all users, sudo to become superuser.
2. Extract the package with the following command:
tar -xvf Ooo_3.1.0_LinuxIntel_install_wJRE_en-US.tar.gz
Note: The example filename might differ from the file you have on your system.
3. cd to the folder that the tar command created.
4. To install the software for all users, type the following to become superuser:
su -
5. Grant permission to open a graphical display for root, using the authority from your user
account. This is necessary for security reasons on some systems, while on other systems
adequate security is provided without this.
XAUTHORITY=/home/{username}/.Xauthority; export XAUTHORITY
DISPLAY=:0.0; export DISPLAY
6. Start the setup program and follow the instructions.
./setup
7. If you su to install for all users, exit the superuser shell:
exit
```
I tried this, and I am still getting errors related to Java!

---

### Post by the-new-x on 2011-09-05
> **mörgæs said:**
> It might be recommended from OOo's point of view, but not from Ubuntu's. 

As mentioned above, best is to install both Java and OO from the repositories (or even better, choose Libre Office).
I installed Java from repositories, but I can't find OpenOffice.org in there, this is why I downloaded it!

---

### Post by mörgæs on 2011-09-05
Sorry, I was wrong. From 11.04 only Libre is in the repositories:

[http://techie-buzz.com/foss/libreoffice-finally-lands-as-default-in-ubuntu-11-04-natty-narhwal.html](http://techie-buzz.com/foss/libreoffice-finally-lands-as-default-in-ubuntu-11-04-natty-narhwal.html)

What is 'better' is a difficult question to answer. Most people prefer Libre, also because a lot more developers are supporting it. OO is unlikely to be developed in the same speed. 


If you really want OO, you could try this:
[http://www.webupd8.org/2010/03/install-upgrade-openoffice-32-from-ppa.html](http://www.webupd8.org/2010/03/install-upgrade-openoffice-32-from-ppa.html)

---

### Post by the-new-x on 2011-09-05
> **mörgæs said:**
> Sorry, I was wrong. From 11.04 only Libre is in the repositories:

[http://techie-buzz.com/foss/libreoffice-finally-lands-as-default-in-ubuntu-11-04-natty-narhwal.html](http://techie-buzz.com/foss/libreoffice-finally-lands-as-default-in-ubuntu-11-04-natty-narhwal.html)

What is 'better' is a difficult question to answer. Most people prefer Libre, also because a lot more developers are supporting it. OO is unlikely to be developed in the same speed. 


If you really want OO, you could try this:
[http://www.webupd8.org/2010/03/install-upgrade-openoffice-32-from-ppa.html](http://www.webupd8.org/2010/03/install-upgrade-openoffice-32-from-ppa.html)
Thanks for the help guys, it worked (special thanks to morgaes)

---

### Post by mörgæs on 2011-09-05
You are welcome. Please mark the thread 'solved'.

---

### Post by the-new-x on 2011-09-05
> **mörgæs said:**
> You are welcome. Please mark the thread 'solved'.
Forgot to mark it earlier, my bad, again, thanks!

---

