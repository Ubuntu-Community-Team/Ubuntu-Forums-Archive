---
title: "wine stable installation"
date: 2020-01-22
forum: Installation &amp; Upgrades
---

### Post by mashal555 on 2020-01-22
Hi
Im new to ubuntu(16.04 xenial 64 bit) and Im trying to install wine and unable to do so I did the follwoing steps

1. sudo dpkg --add-architecture i386  to enable 32 bit
2.wget -nc  [https://dl.winehq.org/wine-builds/winehq.key](https://dl.winehq.org/wine-builds/winehq.key)  to get the key
3. sudo apt-key add winehq.key  add the key
4.sudo apt-add-repository 'deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) [COLOR=#222222][FONT=&amp]xenial main'
5. [/FONT][/COLOR]sudo apt update
6.sudo apt install --install-recommends winehq-stable

After the step 6 I got the error umet dependencies

The following packages have unmet dependencies.
wine-stable : Depends: wine-stable-i386 (= 4.0.3~xenial)
E: Unable to correct problems, you have held broken packages.

So I did the follwoing to resolve the dependencies

7.sudo aptitude install winehq-stable

I get the follwoing error
     Keep the following packages at their current version:                                               
1)      gcc-5-base:i386 [Not Installed]                                                                   
2)      libasound2-plugins:i386 [Not Installed]                                                           
3)      libboost-filesystem1.58.0:i386 [Not Installed]                                                    
4)      libboost-system1.58.0:i386 [Not Installed]                                                        
5)      libcapnp-0.5.3:i386 [Not Installed]                                                               
6)      libegl1-mesa:i386 [Not Installed]                                                                 
7)      libfontconfig1:i386 [Not Installed]                                                               
8)      libgd3:i386 [Not Installed]                                                                       
9)      libgl1-mesa-dri:i386 [Not Installed]                                                              
10)     libgl1-mesa-glx:i386 [Not Installed]                                                              
11)     libglu1-mesa:i386 [Not Installed]                                                                 
12)     libgphoto2-6:i386 [Not Installed]                                                                 
13)     libicu55:i386 [Not Installed]                                                                     
14)     libjack-jackd2-0:i386 [Not Installed]                                                             
15)     libllvm6.0:i386 [Not Installed]                                                                   
16)     libmirclient9:i386 [Not Installed]                                                                
17)     libmircommon7:i386 [Not Installed]                                                                
18)     libmircore1:i386 [Not Installed]                                                                  
19)     libmirprotobuf3:i386 [Not Installed]                                                              
20)     libosmesa6:i386 [Not Installed]                                                                   
21)     libprotobuf-lite9v5:i386 [Not Installed]                                                          
22)     libsane:i386 [Not Installed]                                                                      
23)     libsdl2-2.0-0:i386 [Not Installed]                                                                
24)     libstdc++6:i386 [Not Installed]                                                                   
25)     libtxc-dxtn-s2tc0:i386 [Not Installed]                                                            
26)     libwayland-egl1-mesa:i386 [Not Installed]                                                         
27)     libxml2:i386 [Not Installed]                                                                      
28)     libxslt1.1:i386 [Not Installed]                                                                   
29)     wine-stable [Not Installed]                                                                       
30)     wine-stable-i386:i386 [Not Installed]                                                             
31)     winehq-stable [Not Installed]                                                                     


      Leave the following dependencies unresolved:                                                        
32)     libgl1-mesa-dri:i386 recommends libtxc-dxtn-s2tc:i386 | libtxc-dxtn-s2tc0:i386 | libtxc-dxtn0:i386
33)     wine-stable-i386:i386 recommends libfontconfig1:i386                                              
34)     wine-stable-i386:i386 recommends libglu1-mesa:i386 | libglu1:i386                                 
35)     wine-stable-i386:i386 recommends libosmesa6:i386                                                  
36)     wine-stable-i386:i386 recommends libsane:i386 | libsane1:i386                                     
37)     wine-stable-i386:i386 recommends libsdl2-2.0-0:i386                                               
38)     wine-stable-i386:i386 recommends libxslt1.1:i386  

Accept this solution? [Y/n/q/?] y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

so basically its not able to install the dependency I tried mmany solution ith wine-stable or winehq-staging etc and even try to add the dependencies manually but still no luck

---

### Post by CelticWarrior on 2020-01-22
If you want stability then please use the version already in the official repositories instead of WineHQ's PPA or the direct download that you apparently tried.

It's as simple as ```
sudo apt install wine
```

---

### Post by mashal555 on 2020-01-22
I got the follwoing error

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 wine : Depends: wine1.6
E: Unable to correct problems, you have held broken packages.

---

### Post by mashal555 on 2020-01-22
SO i try to do the follwoing steps
sudo apt install wine1.6
got the error


Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 wine1.6 : Depends: wine1.6-i386 (= 1:1.6.2-0ubuntu14.2)
           Recommends: fonts-droid but it is not installable
E: Unable to correct problems, you have held broken packages.



then I tried 
sudo apt install wine1.6-i386
and got the error

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 wine1.6-i386:i386 : Depends: libglu1-mesa:i386 but it is not going to be installed or
                              libglu1:i386
                     Depends: libgphoto2-6:i386 (>= 2.5.9) but it is not going to be installed
                     Depends: libxml2:i386 (>= 2.9.0) but it is not going to be installed
                     Recommends: libasound2-plugins:i386 but it is not going to be installed
                     Recommends: libfontconfig1:i386 but it is not going to be installed or
                                 libfontconfig:i386
                     Recommends: libosmesa6:i386 but it is not going to be installed
                     Recommends: libsane:i386 but it is not going to be installed
                     Recommends: libxslt1.1:i386 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by CelticWarrior on 2020-01-22
> E: Unable to correct problems, you have held broken packages.

This is the problem. It likely precedes your attempt to install Wine as I suggested -or- happens because you didn't remove the PPA before doing so. Certainly my fault for not mentioning it.

---

### Post by mashal555 on 2020-01-22
how can I remove the PPA?

---

### Post by CelticWarrior on 2020-01-22
If you CAN install software from the repositories (I'm not sure at this point) then you should try ppa-purge:

```
sudo apt install ppa-purge
sudo ppa-purge 'deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) [COLOR=#222222][FONT=&amp]xenial main'[/FONT][/COLOR]
```

Note: You actually DIDN'T install packages from that PPA, supposedly, due to dependency errors but it may have installed something nevertheless and those packages are likely to create conflicts.

The usual way without additional software (eg ppa-purge) is the same command with the --remove parameter, like this:

```
sudo add-apt-repository --remove 'deb [https://dl.winehq.org/wine-builds/ubuntu/](https://dl.winehq.org/wine-builds/ubuntu/) [COLOR=#222222][FONT=&amp]xenial main'[/FONT][/COLOR]
```

Note: This will NOT remove any packages already installed that came from the now removed PPA.


Anyway...
After removing the PPA one way or another, please fully update your system before trying to install any other software:

```
sudo apt update
sudo apt full-upgrade
```

---

### Post by mashal555 on 2020-01-22
same issue still persist. I remove the ppa and then update then upgrade and then try to install wine

 sudo apt update
Hit:1 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial InRelease
Hit:2 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease
Hit:3 [http://ppa.launchpad.net/noobslab/apps/ubuntu](http://ppa.launchpad.net/noobslab/apps/ubuntu) xenial InRelease
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-updates InRelease
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-backports InRelease
Hit:6 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) xenial-security InRelease
Get:7 [https://download.docker.com/linux/ubuntu](https://download.docker.com/linux/ubuntu) xenial InRelease [66.2 kB]
Fetched 66.2 kB in 0s (103 kB/s)                          
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up-to-date.
blank@mashal-xps-13-9370:~$ sudo apt full-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
blank@mashal-xps-13-9370:~$ sudo apt install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies.
 wine : Depends: wine1.6 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by CelticWarrior on 2020-01-22
Weird... APT doesn't spit out error but it is still failing to install Wine and then complains about broken packages.

Try running ```
sudo dpkg --configure -a
```

and then try to install Wine again.

---

### Post by mashal555 on 2020-01-22
still the same issue. I try to install synaptic package manager to fix the broken packages but still no luck

---

### Post by CelticWarrior on 2020-01-22
Sorry, I'm out of ideas.

---

### Post by mashal555 on 2020-01-22
just to let you know I install the playonlinux as well so I remove it with purge command and even I try recreating the sources.list in etc/apt/ but still no luck

---

### Post by mashal555 on 2020-01-22
ok thanks alot for all the help

---

### Post by mashal555 on 2020-01-22
thanks alot

---

