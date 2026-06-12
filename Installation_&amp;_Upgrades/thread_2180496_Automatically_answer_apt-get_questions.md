---
title: "Automatically answer apt-get questions"
date: 2013-10-13
forum: Installation &amp; Upgrades
---

### Post by Adonosonix on 2013-10-13
Dear All,

I am trying to automate an Ubuntu 12.04 web server installation (perfect server guide on how to forge)
Starting from an already installed Ubuntu 12.04, I only need to do some *apt-get install …* and to patch some configuration files to alter them appropriately.

However, during some apt-get install, questions are asked that require answers. For instance :

During the installation of apache and phpmyadmin, these questions are asked :
[COLOR=#000000][FONT=Courier New]*Web server to reconfigure automatically:*[/FONT][/COLOR][COLOR=#000000][FONT=verdana] [/FONT][/COLOR][COLOR=#FF0000][FONT=Georgia]_<-- apache2_[/FONT][/COLOR]
[COLOR=#000000][FONT=Courier New]*Configure database for phpmyadmin with dbconfig-common?*[/FONT][/COLOR][COLOR=#000000][FONT=verdana] [/FONT][/COLOR][COLOR=#FF0000][FONT=Georgia][U]<-- No
[/U][/FONT][/COLOR]
How can I answer them automatically ? Thanks for your help.

---

### Post by markbl on 2013-10-13
man apt-get (see -y)

---

### Post by varunendra on 2013-10-14
> **markbl said:**
> man apt-get (see -y)
Or rather the "-c" option to define a custom config file. For details of its syntax -
```
man apt.conf
```

However, as far as I know, questions like this -
> **Adonosonix said:**
> [COLOR=#000000][FONT=Courier New]*Web server to reconfigure automatically:*[/FONT][/COLOR][COLOR=#000000][FONT=verdana] [/FONT][/COLOR][COLOR=#FF0000][FONT=Georgia]_<-- apache2_[/FONT][/COLOR]
..are asked not by apt, but by the scripts being executed during the installation, and most of the times these scripts are part of the .deb package itself that is being installed.

As such, you may have to set these variables in those scripts and re-insert them in the .deb file(s) replacing the original ones (if that is possible, else rebuild the .deb package with modified scripts, which I don't have experience with, but shouldn't be difficult). To see how exactly the package is going to install (what goes where, what is executed in what sequence etc.), take a look at the contents of "DEBIAN" directory within the .deb package.

You may have to do some research yourself if you wish to go with building/modifying packages. These maybe helpful to get you started -
Building .deb packages from scripts/binaries: [http://askubuntu.com/a/27731](http://askubuntu.com/a/27731)
Similar : [http://askubuntu.com/a/146353](http://askubuntu.com/a/146353)
Links to various guides : [https://wiki.ubuntu.com/UbuntuDevelopment#Working_with_Debian-format_Packages](https://wiki.ubuntu.com/UbuntuDevelopment#Working_with_Debian-format_Packages)

Since you'd be just modifying *some* scripts or installation directives in an already structured package, it should be just one or two steps needed. But it's good to have a fundamental knowledge of the packaging system.

---

### Post by steeldriver on 2013-10-14
You could probably spawn the apt-get install from within an expect script - that should work so long as the config scripts just present questions on stdout (iirc some packages - like mysql - actually pop up a curses-based GUI)

---

### Post by Jake Sweeney on 2013-10-14
You can type "-y" at the end of the command to answer the Y/N question regarding the installation of the package. for example:

sudo apt-get update && sudo apt-get upgrade -y

---

### Post by Adonosonix on 2013-10-16
Thank you all for your replies. I use the -y option in my scripts, however, it does not cover everything. It took me some time to answer, because I was investigating all possibilities. I understand now how it works, and though tearing apart packages, tuning the installation scripts and putting them back together would work, it is too much of a hassle for my needs (be able to quickly reinstall & reconfigure my server in the event of a disk crash).

The solution I choose is to have a re-installation script along with many patches for all the config files I edited during the installation. It is not perfect, since I have to answer all the questions along the way, but it is as close as I can get without spending a lot more time perfecting the process.

Again, thank you for the time you took to enlighten me.

---

### Post by tgalati4 on 2013-10-16
The package system includes both pre and post installation scripts.  Many packages don't need scripts, but some do like apache and mysql.  Some of those scripts will bring up dialogs (like ncurses) and it is difficult to automate those.  Depending on the number of servers that have to be built, it might be easier to set up one server the way you want, then respin it as an ISO and use that to clone the others.  If these are virtual servers then there are better ways to spin up new instances.

---

