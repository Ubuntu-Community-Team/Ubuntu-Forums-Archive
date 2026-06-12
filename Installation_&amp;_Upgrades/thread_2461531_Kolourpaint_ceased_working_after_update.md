---
title: "Kolourpaint ceased working after update"
date: 2021-05-02
forum: Installation &amp; Upgrades
---

### Post by voxpopili on 2021-05-02
Hi People ,

I have been using KolourPaint faultlessly for 6 months , Ubuntu told me i had software updates available so i allowed it to install them however i noticed the next day that Kolourpaint will not open.

The icon is still on my desktop quick start menu but if i click on it nothing happens , if i go to a Kolourpaint drawing and attempt to open it it wont open that way either.

 What is the best way to fix this issue ?

I had a similar problem 2 months ago when LibreOffice Writer ceased working , i tried to uninstall and reinstall but that didnt help , i had to go to LibreOffice Writer 7.1 to get a working document app.

Yes i tried rebooting.

any suggestions please ?

---

### Post by Xian on 2021-05-02
First let's verify the package install:

$ sudo apt-get update
$ sudo apt-get -f install
$ sudo apt-get install --reinstall kolourpaint

If no change then run program from a terminal and post the output:

$ kolourpaint

---

### Post by voxpopili on 2021-05-03
thankyou for reply

$  kolourpaint
kolourpaint: /snap/kolourpaint/62/kf5/usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.26' not found (required by /snap/kolourpaint/62/usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5)
kolourpaint: /snap/kolourpaint/62/kf5/usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.28' not found (required by /snap/kolourpaint/62/usr/lib/x86_64-linux-gnu/libQt5Widgets.so.5)
kolourpaint: /snap/kolourpaint/62/kf5/usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.26' not found (required by /snap/kolourpaint/62/usr/lib/x86_64-linux-gnu/libQt5Core.so.5)
kolourpaint: /snap/kolourpaint/62/kf5/usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.28' not found (required by /snap/kolourpaint/62/usr/lib/x86_64-linux-gnu/libQt5Core.so.5)
kolourpaint: /snap/kolourpaint/62/kf5/usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.28' not found (required by /snap/kolourpaint/62/usr/lib/x86_64-linux-gnu/libQt5Xml.so.5)
kolourpaint: /snap/kolourpaint/62/kf5/usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.26' not found (required by /snap/kolourpaint/62/usr/lib/x86_64-linux-gnu/libQt5Xml.so.5)
kolourpaint: /snap/kolourpaint/62/kf5/usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.26' not found (required by /snap/kolourpaint/62/usr/lib/x86_64-linux-gnu/libQt5WaylandClient.so.5)
kolourpaint: /snap/kolourpaint/62/kf5/usr/lib/x86_64-linux-gnu/libstdc++.so.6: version `GLIBCXX_3.4.28' not found (required by /snap/kolourpaint/62/usr/lib/x86_64-linux-gnu/libQt5WaylandClient.so.5)

---

### Post by voxpopili on 2021-05-03
apt-get update

Ign:1 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable InRelease
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [109 kB]                                                        
Hit:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease                                                                           
Hit:4 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal InRelease                                            
Get:5 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates InRelease [114 kB]     
Get:6 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable Release [933 B]
Get:7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 DEP-11 Metadata [24.4 kB]
Get:8 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable Release.gpg [819 B]                                         
Get:9 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main DEP-11 48x48 Icons [7,339 B]  
Get:10 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 DEP-11 Metadata [58.2 kB]
Ign:8 [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable Release.gpg                                         
Get:11 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-backports InRelease [101 kB]
Get:12 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages [951 kB]
Get:13 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates/main i386 Packages [465 kB]
Get:14 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata [265 kB]
Get:15 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 Packages [765 kB]
Get:16 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 DEP-11 Metadata [303 kB]
Get:17 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-updates/multiverse amd64 DEP-11 Metadata [2,468 B]
Get:18 [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) focal-backports/universe amd64 DEP-11 Metadata [1,768 B]
Reading package lists... Done                     
W: GPG error: [http://dl.google.com/linux/earth/deb](http://dl.google.com/linux/earth/deb) stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 78BD65473CB3BD13
E: The repository 'http://dl.google.com/linux/earth/deb stable Release' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.

---

### Post by voxpopili on 2021-05-03
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libfprint-2-tod1 libllvm9
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 73 not to upgrade

---

### Post by voxpopili on 2021-05-03
brilliant thankyou !

I went through the above , sorry for reverse order , at first it wouldnt work until i rebooted , but i opened it from terminal and deleted the old Kolourpaint icons from quickstart and main program menu , then from main menu , added the icon to quickstart and it fires up every time now.

much appreciated :)

---

