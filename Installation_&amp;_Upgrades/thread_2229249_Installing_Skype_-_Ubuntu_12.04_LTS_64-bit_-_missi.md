---
title: "Installing Skype - Ubuntu 12.04 LTS 64-bit - missing dependencies"
date: 2014-06-12
forum: Installation &amp; Upgrades
---

### Post by evenstevensm on 2014-06-12
I am running Ubuntu 12.04 LTS 64-bit.  

  1) When I try installing Skype using the command 
  ```
sudo apt-get install skype

```  I get the following
  ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package skype:i386 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'skype:i386' has no installation candidate

``` 

 2) I then downloaded Skype from Mircrosoft's site for Ubuntu 12.04 LTS  multiarch. The filename is 'skype-ubuntu-precise_4.2.0.13-1_i386.deb'. On trying to  install this using Ubuntu Software Center, I get the error 'Cannot  install "libqtgui:i386"'.
  

3) I tried running the following command as suggested in [Install Skype on Ubuntu 12.04 LTS 64-bit]("http://askubuntu.com/questions/284725/install-skype-on-ubuntu-12-04-lts-64-bit")
  ```
sudo apt-get install libqt4-dbus:i386 libqt4-network:i386 libqt4-xml:i386 libqtcore4:i386 libqtgui4:i386 libqtwebkit4:i386 sni-qt:i386

```  This is the output
  ```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt4-dbus:i386 is already the newest version.
libqt4-network:i386 is already the newest version.
libqt4-xml:i386 is already the newest version.
libqtcore4:i386 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
libqtgui4:i386 : Depends: libfontconfig1:i386 (>= 2.8.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```  

4) I tried the following 
```
sudo apt-get -f install
```
which did not help

How can I get Skype installed?
  Thanks in advance.

---

### Post by mastablasta on 2014-06-12
As per the site you linked try

> ```
sudo dpkg --add-architecture i386
sudo apt-get install ia32-libs
sudo apt-get update
wget http://download.skype.com/linux/skype-ubuntu-lucid_4.2.0.11-1_i386.deb
sudo dpkg -i skype-ubuntu-lucid_4.2.0.11-1_i386.deb
```

After all of this run in terminal sudo apt-get install sni-qt:i386; This will restore the skype contact window

or this one:

```
sudo apt-get install libqt4-dbus:i386 libqt4-network:i386 libqt4-xml:i386 libqtcore4:i386 libqtgui4:i386 libqtwebkit4:i386 sni-qt:i386

wget http://download.skype.com/linux/skype-debian_4.2.0.13-1_i386.deb

sudo dpkg -i skype-debian_4.2.0.13-1_i386.deb

```

---

### Post by evenstevensm on 2014-06-12
Hi mastablasta,

Thanks for your two suggestions.

As for suggestion 2, 

```
sudo dpkg --add-architecture i386
```
I had already tried it, as mentioned in my original post. The output I got was 


```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libqt4-dbus:i386 is already the newest version.
libqt4-network:i386 is already the newest version.
libqt4-xml:i386 is already the newest version.
libqtcore4:i386 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.


```
How can I avoid this?
As for your first suggestion, here is the output to the command
```
sudo dpkg --add-architecture i386
```

Output:
```
dpkg: error: unknown option --add-architecture

Type dpkg --help for help about installing and deinstalling packages 
[*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;

Options marked 
[*] produce a lot of output - pipe it through `less' or `more' !
```

How can I get around this?

---

### Post by mastablasta on 2014-06-12
so what happens if you put ```
sudo dpkg -i skype-debian_4.2.0.13-1_i386.deb
``` ? after you downloaded skype .deb file?

---

### Post by evenstevensm on 2014-06-12
I tried 
```
sudo dpkg -i skype-ubuntu-precise_4.2.0.13-1_i386.deb
```

as you suggested.
This was the output

```
Selecting previously unselected package skype:i386.
(Reading database ... 185476 files and directories currently installed.)
Unpacking skype:i386 (from skype-ubuntu-precise_4.2.0.13-1_i386.deb) ...
dpkg: dependency problems prevent configuration of skype:i386:
 skype:i386 depends on libqtgui4 (>= 4:4.8.0).
 skype:i386 depends on libqtwebkit4 (>= 2.2~2011week36).
dpkg: error processing skype:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for hicolor-icon-theme ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 skype:i386
```

---

### Post by mastablasta on 2014-06-13
ok now open synaptic package manager and search for 
libqtgui4:i386 
ibqtwebkit4:i386

of you can just run:

sudo apt-get install libqtgui4:i386 libqtwebkit4:i386
 
then check that the versions installed (if they are installed) are equal or higher than specified: 

skype:i386 depends on libqtgui4 (>= 4:4.8.0).
 skype:i386 depends on libqtwebkit4 (>= 2.2~2011week36).

if they are not installed, install them. hopefully this will let the instalation to smoothly continue.

one thing to note if the older versions of packages are in repositories it would mean that new skype does not support older Ubuntu version. so the option is to install the version from repositories by enabling partner repositories (in software sources) and then searching for skype in software center. the alternative is to install newer version of packages to older ubuntu and then hope you don't get into dependency hell.

---

### Post by evenstevensm on 2014-06-13
I tried 
```
sudo apt-get install libqtgui4:i386 libqtwebkit4:i386
```

and this was the result
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libqtgui4:i386 : Depends: libfontconfig1:i386 (>= 2.8.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```



I also tried installing via Synaptic, and got the same dependency errors

---

### Post by mastablasta on 2014-06-13
it seems that for some reason you are in dependency hell -> one depends on the other that depends on yet another that depends on yet another...
you could try and find older version of skype (or option i indicated above) or upgrade the whole thing to 14.04. is there a particular reason you are still on 12.04 ?


another thing is why there is a broken packages message. so try solution here: [http://ubuntuforums.org/showthread.php?t=947124](http://ubuntuforums.org/showthread.php?t=947124)

to clean it all and reinstall.



sudo apt-get update 

should throw out possible issues with packages. you did run
sudo apt-get update
sudo apt-get upgrade

before attempting the install?

---

