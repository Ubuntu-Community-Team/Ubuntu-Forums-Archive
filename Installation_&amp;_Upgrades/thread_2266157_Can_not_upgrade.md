---
title: "Can not upgrade"
date: 2015-02-20
forum: Installation &amp; Upgrades
---

### Post by Jonners59 on 2015-02-20
I get the "Upgrade available" message, and select to upgrade now, but it fails, saying it could not proceed due to
[HTML]Could not determine the upgrade

An unresolvable problem occurred while calculating the upgrade.

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug using the command 'ubuntu-bug ubuntu-release-upgrader-core' in a terminal.
[/HTML]

System details below:

[HTML]p { margin-bottom: 0.25cm; line-height: 120%; }   Ubuntu 10.04 trusty
 

 baronipc@baronipc:~$ head /proc/version 
 Linux version 3.13.0-45-generic (buildd@phianna) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #74-Ubuntu SMP Tue Jan 13 19:36:28 UTC 2015 
 

 baronipc@baronipc:~$ head /proc/meminfo 
 MemTotal:       16415508 kB   15.7GB 
 MemFree:         5527532 kB 
 Buffers:         1026680 kB 
 Cached:          3796324 kB 
 SwapCached:            0 kB 
 Active:          7927100 kB 
 Inactive:        1834100 kB 
 Active(anon):    4958508 kB 
 Inactive(anon):    71948 kB 
 Active(file):    2968592 kB 
 

 baronipc@baronipc:~$ head /proc/cpuinfo 
 processor    : 0 
 vendor_id    : GenuineIntel 
 cpu family    : 6 
 model        : 42 
 model name    : Intel(R) Core(TM) i5-2500K CPU @ 3.30GHz 
 stepping    : 7 
 microcode    : 0x14 
 cpu MHz        : 2200.000 
 cache size    : 6144 KB 
 physical id    : 0 
 

 baronipc@baronipc:~$ sudo dmidecode -t 2 
 [sudo] password for baronipc:  
 # dmidecode 2.12 
 SMBIOS 2.6 present. 
  Handle 0x0002, DMI type 2, 15 bytes 
 Base Board Information 
     Manufacturer: ASUSTeK Computer INC. 
     Product Name: P8P67-M PRO 
     Version: Rev X.0X 
     Serial Number: MT7014018601056 
     Asset Tag: To be filled by O.E.M. 
     Features: 
         Board is a hosting board 
         Board is replaceable 
     Location In Chassis: To be filled by O.E.M. 
     Chassis Handle: 0x0003 
     Type: Motherboard 
     Contained Object Handles: 0 

[/HTML]

---

### Post by grahammechanical on 2015-02-20
For a few minutes I was fooled by this

> Ubuntu 10.04 trusty

Please edit the post to read Ubuntu 14.04 trusty. If that is indeed the version of Ubuntu installed.

It this a normal update/upgrade through Software Updater. Or are you being offered to upgrade to the 14.04.2 hardware enablement stack? That upgrade has only just been released. Waiting a day or two might be what solves this problem. Unless it is caused by a break in the internet connection. Can you run?

```
sudo apt-get update
sudo apt-get upgrade
```

What errors, if any do you get?

Regards.

---

### Post by Jonners59 on 2015-02-20
Arrgggh  Sorry, typo.  And I thought I was so smart giving as much info as I could.  Defo 14.04

Can't edit now, it does not let me.

> It this a normal update/upgrade through Software Updater. Or are you  being offered to upgrade to the 14.04.2 hardware enablement stack?
It is the upgrade from 14.04 to 14.10.

No errors with, bar some broken sources:
```
sudo apt-get update sudo apt-get upgrade
```

```
Ign http://ppa.launchpad.net precise/main Translation-en                       
Err http://download.skype.com stable/non-free amd64 Packages                   
  404  Not Found [IP: 77.67.28.51 80]
Hit http://download.ebz.epson.net lsb3.2/main Translation-en                   
Ign http://linux.dropbox.com trusty/main Translation-en_GB            
Ign http://download.skype.com stable/non-free Translation-en_GB
Ign http://download.skype.com stable/non-free Translation-en
Ign http://linux.dropbox.com trusty/main Translation-en
Fetched 2,552 kB in 2s (1,035 kB/s)
W: GPG error: http://mirrors.dotsrc.org precise-getdeb InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF
W: Failed to fetch http://ddebs.ubuntu.com/dists/raring/main/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ddebs.ubuntu.com/dists/raring/restricted/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ddebs.ubuntu.com/dists/raring/universe/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ddebs.ubuntu.com/dists/raring/multiverse/binary-amd64/Packages  404  Not Found

W: Failed to fetch http://ddebs.ubuntu.com/dists/raring/main/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ddebs.ubuntu.com/dists/raring/restricted/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ddebs.ubuntu.com/dists/raring/universe/binary-i386/Packages  404  Not Found

W: Failed to fetch http://ddebs.ubuntu.com/dists/raring/multiverse/binary-i386/Packages  404  Not Found

W: Failed to fetch http://debian.scribus.net/debian/dists/testing/Release  Unable to find expected entry 'non-free/binary-amd64/Packages' in Release file (Wrong sources.list entry or malformed file)

W: Failed to fetch http://download.skype.com/linux/repos/debian/dists/stable/non-free/binary-amd64/Packages  404  Not Found [IP: 77.67.28.51 80]

E: Some index files failed to download. They have been ignored, or old ones used instead.
baronipc@baron
```

```
baronipc@baronipc:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  grub-customizer libgegl-0.2-0 liblcms2-2 warzone2100 warzone2100-data
0 to upgrade, 0 to newly install, 0 to remove and 5 not to upgrade.
baronipc@baronipc:~$ 


```

---

### Post by bapoumba on 2015-02-20
Please disable your ppas before running the upgrade process. Depending on which packages you installed from these ppas, you may want to revert them to the distribution version.
To have a look at your sources :
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

---

### Post by Jonners59 on 2015-02-22
> **bapoumba said:**
> Please disable your ppas before running the upgrade process. Depending on which packages you installed from these ppas, you may want to revert them to the distribution version.
To have a look at your sources :
```
cat -n /etc/apt/sources.list
ls -la /etc/apt/sources.list.d
tail -v -n +1 /etc/apt/sources.list.d/*
```

Thanks bapoumba
But whilst I understood what the sources lists are/were, I did not understand how to disable anything, and they are large lists, so what I did was open the list such.
```
sudo gedit /etc/apt/sources.list
```

Then made a copy.  I then deleted everything in the list above the line about unsupported sources and saved as sources.list and everything below as sources.list.bak

I then ran the upgrade
 and add the sources back after.

---

### Post by bapoumba on 2015-02-22
OK, did it work ? You also could have unchecked the ppas from the Software Sources.
When adding a ppa back, please make sure it has a 14.10 repository.

---

### Post by Jonners59 on 2015-02-24
Sorry for the delay.....  I had to rebuild the PC...

Did it work?  In a way yes.  It did do the upgrade.  HOWEVER.  I then hit the nvidia bug that is going round with the upgrade and could not get it to work, so I am now trying to rebuild everything.  I am going to start another thread on Backing up, as I am fed-up of building the PC I want over months and then loosing all my apps and settings and having to start all over again.  Upgrades on Ubuntu are still very hit and miss.

---

### Post by bapoumba on 2015-02-24
Yeah. My laptop is 8-9 years old. I choose it for having an Intel video chip. A few years back I thought it was not a good choice.. Now that it shows some signs of aging, I'm pondering which replacement I'll get.

---

