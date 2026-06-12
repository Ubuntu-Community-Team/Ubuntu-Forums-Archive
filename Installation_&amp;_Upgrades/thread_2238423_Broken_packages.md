---
title: "Broken packages"
date: 2014-08-07
forum: Installation &amp; Upgrades
---

### Post by John Jason Jordan on 2014-08-07
I recently upgraded Xubuntu 13.10 to 14.04.1 and there were a lot of problems. At first it wouldn't even boot - came up with the grub-rescue prompt. After hours of searching I finally fixed it, but then I discovered that the upgrade removed a ton of my installed apps, up to and including LibreOffice., I have spent most of today trying to get things reinstalled, but now I am stuck with broken packages:

cpp, cpp-4.8, gcc-4.8-base, gcc-4.8-base;ie86, libasan0, libatomic1, libgcc1, libgcc1:386, libgfortran3, liubgomp1, libitml, libquadmath0, libtsan0

If I try to upgrade any of them I get a list of packages that must be removed before they can be upgraded, including dozens of packages. These are packages like Abiword, LibreOffice, and other non-trivial apps. If I try to remove them the list of packages it wants to remove is shorter, but includes things like xorg and xubuntu-desktop. Neither approach sounds like a good idea. :(

I don't know how to fix this problem. Any suggestions?

---

### Post by Rex Bouwense on 2014-08-07
Have you tried using the Synaptic package Manager?   Look in Custom Filters->Broken.

---

### Post by ian-weisser on 2014-08-07
Please show us the complete series of warnings, errors and other complaints.
```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by John Jason Jordan on 2014-08-07
> **ian-weisser said:**
> Please show us the complete series of warnings, errors and other complaints.
```
sudo apt-get update && sudo apt-get upgrade
```

I truncated the Gets and Hits because I think this is what you are looking for:

```

...
Hit http://us.archive.ubuntu.com trusty-security/main Translation-en           
Hit http://us.archive.ubuntu.com trusty-security/multiverse Translation-en     
Hit http://us.archive.ubuntu.com trusty-security/restricted Translation-en     
Hit http://us.archive.ubuntu.com trusty-security/universe Translation-en       
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Fetched 1,598 kB in 18s (87.0 kB/s)                                            
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  cpp cpp-4.8 gcc-4.8-base gcc-4.8-base:i386 libasan0 libatomic1 libgcc1
  libgcc1:i386 libgfortran3 libgomp1 libitm1 libquadmath0 libtsan0
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
```

I hope you or someone has some ideas on how to fix these packages.

---

### Post by John Jason Jordan on 2014-08-07
> **Rex Bouwense said:**
> Have you tried using the Synaptic package Manager?   Look in Custom Filters->Broken.

Yeah, I use Synaptic as my first-line attempt at package management. But thanks for the suggestion because I had never tried the Custom Filters before. Unfortunately, when I looked at Custom Filters > Broken the window was empty. 

However, the packages do all appear in the Upgradeable section. It's just that I can't upgrade or remove them without destroying the OS.

---

### Post by John Jason Jordan on 2014-08-09
I have discovered that Synaptic does not actually consider these packages broken. I should probably not titled this thread "Broken packages." In fact Synaptic considers them upgradable. The problem is that I cannot upgrade them without uninstalling most of the programs I have installed, up to and including LibreOffice. Neither can I remove them, because if I do so Synaptic says it must also delete xorg and xubuntu-desktop.

I'm wondering if it's possible to just install the newer version without doing it as an upgrade, and just let the newer version overwrite the old. For example, I have installed cpp 4:4.8.1-2ubuntu3 and the new version is 4.4.8.2-1ubuntu6. Is it possible to get a .deb package of the new version somewhere that I can just install with dpkg?

---

### Post by ian-weisser on 2014-08-09
> **John Jason Jordan said:**
> I'm wondering if it's possible to just install the newer version without doing it as an upgrade, and just let the newer version overwrite the old. For example, I have installed cpp 4:4.8.1-2ubuntu3 and the new version is 4.4.8.2-1ubuntu6. Is it possible to get a .deb package of the new version somewhere that I can just install with dpkg?

DON'T do that. It will make your problem worse. 
The package manager is choking on those upgrades for a *reason*, not because it enjoys being petulant. We must discover and resolve that problem.

Please show us the complete output from the following command
```
sudo apt-get install -f
```

---

### Post by kansasnoob on 2014-08-09
Since this is about Xubuntu instead of Ubuntu I'm not sure if this bug applies or not:

[https://bugs.launchpad.net/ubuntu/trusty/+source/apt/+bug/1347721](https://bugs.launchpad.net/ubuntu/trusty/+source/apt/+bug/1347721)

I tried recovering from that to no avail ................. it would seem that I was gaining, but after I'd get one issue resolved another would crop up, followed by another, and another :(

---

### Post by John Jason Jordan on 2014-08-09
> **ian-weisser said:**
> ```
sudo apt-get install -f
```

```
sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 13 not upgraded.
```

But there is something else that happened just before bedtime last night. I had Synaptic open and I did a Reload. Afterwards all of the packages that it said were upgradable (but that I can't upgrade or remove without creating a disaster), had disappeard from the list of upgradable packages except (listed by package name, current version and latest version):

[LIST]cpp 4:4.8.1-2ubuntu 4:4.8
[*].2-1ubuntu6
[*]cpp-4.8 4.8.1-10ubuntu9 4.8.2-19ubuntu1[/LIST]

This morning I ran the install -f command but had to shut down Synaptic to do so. After running the command I reopened Synaptic and all 13 packages listed in my first post here reappeared as upgradable. I reloaded again, but they remain. I have no explanation for why all but the above two disappeared after the reload last night and then reappeared after restarting Synaptic this morning; I mention it only because I'm grasping for any possible clues.

And here is another clue: After the dist-upgrade from 13.10 to 14.04 I was trying applications to make sure they were still working. When I launched Virtualbox it announced that there was a new version and offered to download and do the update. I did so. When I reopened Virtualbox and tried to launch one of my machines I got an error that I needed to run "sudo /etc/init.d/vboxdrv setup." When I did so it failed, producing the following error in the Virtualbox log file:

```
/bin/sh: 1: gcc: not found
make[2]: *** [/tmp/vbox.0/linux/SUPDrv-linux.o] Error 127
make[1]: *** [_module_/tmp/vbox.0] Error 2
make: *** [vboxdrv] Error 2
```

I note that the 13 packages seem to relate mostly to gcc.

---

### Post by John Jason Jordan on 2014-08-09
> **kansasnoob said:**
> [https://bugs.launchpad.net/ubuntu/trusty/+source/apt/+bug/1347721](https://bugs.launchpad.net/ubuntu/trusty/+source/apt/+bug/1347721)

I read through it but it doesn't seem to have anything to do with my problem.

---

