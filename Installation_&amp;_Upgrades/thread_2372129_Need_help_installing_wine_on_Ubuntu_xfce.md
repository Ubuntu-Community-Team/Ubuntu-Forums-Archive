---
title: "Need help installing wine on Ubuntu xfce"
date: 2017-09-21
forum: Installation &amp; Upgrades
---

### Post by dachihuahuabot on 2017-09-21
I am new to Ubuntu and I am trying to install Wine so that I can play windows games. I am running Ubuntu via Crouton on a chrmebook with a arm proccessor. Whenever I enter the command "sudo apt-get install --install-recommends winehq-stable" I receive the error message saying that either the package cannot be found or that I have "held broken packages". The console log for the latter is here:

 [SIZE=2][I]Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 winehq-stable:i386 : Depends: wine-stable:i386 (= 2.0.2~xenial) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

Please help me with this problem.[/I][/SIZE]

---

### Post by mörgæs on 2017-09-23
Hi, welcome to the fora.

Please run **sudo apt update** and **sudo apt dist-upgrade** and post the output in CODE (not QUOTE) tags.

---

### Post by dachihuahuabot on 2017-09-25
```
sudo apt-get update: Hit:1 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial InRelease
Hit:2 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates InRelease
Hit:3 [https://dl.winehq.org/wine-builds/ubuntu](https://dl.winehq.org/wine-builds/ubuntu) xenial InRelease
Hit:4 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-security InRelease
Ign:5 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main i386 Packages
Ign:6 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/restricted i386 Packages
Ign:7 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe i386 Packages
Ign:8 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/multiverse i386 Packages
Ign:9 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main i386 Packages
Ign:10 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/restricted i386 Packages
Ign:11 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/universe i386 Packages
Ign:12 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/multiverse i386 Packages
Ign:5 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main i386 Packages
Ign:6 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/restricted i386 Packages
Ign:7 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe i386 Packages
Ign:8 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/multiverse i386 Packages
Ign:9 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main i386 Packages
Ign:10 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/restricted i386 Packages
Ign:11 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/universe i386 Packages
Ign:12 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/multiverse i386 Packages
Ign:5 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main i386 Packages
Ign:13 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-security/main i386 Packages
Ign:14 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-security/restricted i386 Packages
Ign:15 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-security/universe i386 Packages
Ign:16 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-security/multiverse i386 Packages
Ign:6 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/restricted i386 Packages
Ign:7 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe i386 Packages
Ign:8 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/multiverse i386 Packages
Ign:9 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main i386 Packages
Ign:10 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/restricted i386 Packages
Ign:11 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/universe i386 Packages
Ign:12 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/multiverse i386 Packages
Err:5 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/main i386 Packages
  404  Not Found [IP: 91.189.88.150 80]
Ign:13 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-security/main i386 Packages
Ign:14 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-security/restricted i386 Packages
Ign:15 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-security/universe i386 Packages
Ign:16 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-security/multiverse i386 Packages
Ign:6 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/restricted i386 Packages
Ign:7 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/universe i386 Packages
Ign:8 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial/multiverse i386 Packages
Err:9 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/main i386 Packages
  404  Not Found [IP: 91.189.88.150 80]
Ign:10 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/restricted i386 Packages
Ign:11 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/universe i386 Packages
Ign:12 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-updates/multiverse i386 Packages
Ign:13 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-security/main i386 Packages
Ign:14 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-security/restricted i386 Packages
Ign:15 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-security/universe i386 Packages
Ign:16 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-security/multiverse i386 Packages
Err:13 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-security/main i386 Packages
  404  Not Found [IP: 91.189.88.150 80]
Ign:14 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-security/restricted i386 Packages
Ign:15 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-security/universe i386 Packages
Ign:16 [http://ports.ubuntu.com/ubuntu-ports](http://ports.ubuntu.com/ubuntu-ports) xenial-security/multiverse i386 Packages
Reading package lists... Done
N: Skipping acquire of configured file 'main/binary-arm64/Packages' as repository 'https://dl.winehq.org/wine-builds/ubuntu xenial InRelease' doesn't support architecture 'arm64'
E: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/xenial/main/binary-i386/Packages](http://ports.ubuntu.com/ubuntu-ports/dists/xenial/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.150 80]
E: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/xenial-updates/main/binary-i386/Packages](http://ports.ubuntu.com/ubuntu-ports/dists/xenial-updates/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.150 80]
E: Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/dists/xenial-security/main/binary-i386/Packages](http://ports.ubuntu.com/ubuntu-ports/dists/xenial-security/main/binary-i386/Packages)  404  Not Found [IP: 91.189.88.150 80]
E: Some index files failed to download. They have been ignored, or old ones used instead.
[U][B]
sudo apt dist-upgrade:[/B][/U] Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by mörgæs on 2017-09-26
I am not familiar enough with neither Wine nor ARM to advise you here; actually I don't use any of them. The reason why I asked for the output was so other posters might be able to see something.

The only thing I can suggest is to change mirror to see if any of the errors disappear.

---

### Post by doncolleyjr on 2017-09-28
The reason you came to ubuntu, to learn and do.  [http://ubuntuhandbook.org/index.php/2017/01/install-wine-2-0-ubuntu-16-04-14-04-16-10/](http://ubuntuhandbook.org/index.php/2017/01/install-wine-2-0-ubuntu-16-04-14-04-16-10/) 
Here you go.  Follow the comments.  You can also for an earlier version [http://ubuntuhandbook.org/index.php/2015/12/install-wine-1-8-stable-new-ppa/](http://ubuntuhandbook.org/index.php/2015/12/install-wine-1-8-stable-new-ppa/)

---

