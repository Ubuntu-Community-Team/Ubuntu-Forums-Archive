---
title: "No application data found"
date: 2016-06-05
forum: Installation &amp; Upgrades
---

### Post by carlostefano on 2016-06-05
Hello,

I have tryed to use the software manager on my laptop with xubuntu. In the start it was working fine, but now I get the message "No application data found".

How can I solve it?

Greetings,

carlostefano

---

### Post by X-RED_Tech on 2016-06-05
What do you mean by "software manager"? Xubuntu release?
If you mean the default tool for installing software that up to the current release was Ubuntu Software Centre, now, since 16.04, is ubuntu-software renamed from gnome-software.

---

### Post by carlostefano on 2016-06-05
Yes, I have the last release of Xubuntu. In the menu is called like simply "software" and yes, it is the main too for installing software in the system.

---

### Post by X-RED_Tech on 2016-06-05
Open the terminal and then
```
sudo apt update
sudo apt upgrade
sudo apt full-upgrade
```

Post the error messages, if any.

If no errors then try to open the Software again.

---

### Post by carlostefano on 2016-06-05
hp6710b@hp6710b-HP-Compaq-6710b-GC016ET-ABZ:~$ sudo apt update
[sudo] password for hp6710b: 
Sorry, try again.
```
[sudo] password for hp6710b: 
Hit:1 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease
Hit:2 [http://ppa.launchpad.net/wine/wine-builds/ubuntu](http://ppa.launchpad.net/wine/wine-builds/ubuntu) xenial InRelease        
Hit:3 [http://ci.archive.ubuntu.com/ubuntu](http://ci.archive.ubuntu.com/ubuntu) xenial InRelease                     
Get:4 [http://ci.archive.ubuntu.com/ubuntu](http://ci.archive.ubuntu.com/ubuntu) xenial-updates InRelease [94,5 kB]   
Ign:5 [http://download.ebz.epson.net/dsc/op/stable/debian](http://download.ebz.epson.net/dsc/op/stable/debian) lsb3.2 InRelease      
Get:6 [http://ci.archive.ubuntu.com/ubuntu](http://ci.archive.ubuntu.com/ubuntu) xenial-backports InRelease [92,2 kB]
Hit:7 [http://download.ebz.epson.net/dsc/op/stable/debian](http://download.ebz.epson.net/dsc/op/stable/debian) lsb3.2 Release        
Get:8 [http://ci.archive.ubuntu.com/ubuntu](http://ci.archive.ubuntu.com/ubuntu) xenial-updates/main amd64 Packages [201 kB]
Ign:10 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable InRelease                  
Get:11 [http://ci.archive.ubuntu.com/ubuntu](http://ci.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [198 kB]
Get:12 [http://ci.archive.ubuntu.com/ubuntu](http://ci.archive.ubuntu.com/ubuntu) xenial-updates/universe amd64 Packages [84,4 kB]
Hit:13 [http://dl.google.com/linux/chrome/deb](http://dl.google.com/linux/chrome/deb) stable Release                    
Get:15 [http://ci.archive.ubuntu.com/ubuntu](http://ci.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [81,7 kB]
Fetched 752 kB in 5s (140 kB/s)                           
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
W: [http://download.ebz.epson.net/dsc/op/stable/debian/dists/lsb3.2/Release.gpg:](http://download.ebz.epson.net/dsc/op/stable/debian/dists/lsb3.2/Release.gpg:) Signature by key E5220FB7014D0FBDA50DFC2BE5E86C008AA65D56 uses weak digest algorithm (SHA1)
W: [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:) Signature by key 4CCA1EAF950CEE4AB83976DCA040830F7FAC5991 uses weak digest algorithm (SHA1)
W: [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg:) Signature by key 3B068FB4789ABE4AEFA3BB491397BC53640DB551 uses weak digest algorithm (SHA1)
hp6710b@hp6710b-HP-Compaq-6710b-GC016ET-ABZ:~$ 
hp6710b@hp6710b-HP-Compaq-6710b-GC016ET-ABZ:~$ 
hp6710b@hp6710b-HP-Compaq-6710b-GC016ET-ABZ:~$ 
hp6710b@hp6710b-HP-Compaq-6710b-GC016ET-ABZ:~$ 
hp6710b@hp6710b-HP-Compaq-6710b-GC016ET-ABZ:~$ sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hp6710b@hp6710b-HP-Compaq-6710b-GC016ET-ABZ:~$ 
hp6710b@hp6710b-HP-Compaq-6710b-GC016ET-ABZ:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
hp6710b@hp6710b-HP-Compaq-6710b-GC016ET-ABZ:~$
```

Still not working

---

### Post by howefield on 2016-06-05
Could be this bug..

[https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1563155](https://bugs.launchpad.net/ubuntu/+source/gnome-software/+bug/1563155)

There are a few workarounds mentioned if you work your way through it.

---

### Post by carlostefano on 2016-06-05
I have tryed to use them but they aren't working in this case (. How can I reinstall xubuntu?

---

