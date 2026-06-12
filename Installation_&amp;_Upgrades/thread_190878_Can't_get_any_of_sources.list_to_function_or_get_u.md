---
title: "Can't get any of sources.list to function or get updates"
date: 2006-06-06
forum: Installation &amp; Upgrades
---

### Post by racsw on 2006-06-06
Hi,
I don't know why, but none of my /etc/apt/sources.list will function.
The errors are below.
All my email and browser works fine.  I'm connected through a router to a DSL Modem into the internet connection.  I use DHCP.
Everything worked fine using 5.10, but not 6.06.  This problem is also preventing me from getting any updates to the original install, so I'd really appreciate some help here.

Thanks,
Robert

Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg
  Connection failed
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Connection failed [IP: 85.133.25.8 80]
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release.gpg
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg
  Connection failed [IP: 85.133.25.8 80]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg
  Connection failed [IP: 85.133.25.8 80]
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Ign [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Packages
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Packages
  Connection failed
Ign [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/free Sources
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Err [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper/non-free Sources
  Connection failed
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Packages
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Err [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/multiverse Sources
  Connection failed
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
  Connection failed [IP: 85.133.25.8 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/dapper-security/Release.gpg)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/Release.gpg)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/Release.gpg)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/source/Sources.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/free/source/Sources.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/binary-i386/Packages.gz)  Connection failed
Failed to fetch [http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/source/Sources.gz](http://packages.freecontrib.org/ubuntu/plf/dists/dapper/non-free/source/Sources.gz)  Connection failed
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/main/source/Sources.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/restricted/source/Sources.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/universe/source/Sources.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/dapper-security/multiverse/source/Sources.gz)  Connection failed
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/universe/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper/multiverse/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/multiverse/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/binary-i386/Packages.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/main/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/restricted/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/universe/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/dapper-backports/multiverse/source/Sources.gz)  Connection failed [IP: 85.133.25.8 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by rado_london on 2006-06-06
can you post your sources.list as well please?

---

### Post by racsw on 2006-06-06
Absolutely!
This is not the original one that was installed, but the original didn't work either.  This was taken from one of the Help guides on Installing 6.06 that is listed on the Umbutu site.
Under DNS Servers, I have only 192.168.0.1, which is the router address.

Thanks,
Robert


## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free
deb-src [http://packages.freecontrib.org/ubuntu/plf](http://packages.freecontrib.org/ubuntu/plf) dapper free non-free

---

### Post by rado_london on 2006-06-06
I think it isnt the list itself. It looks like it has trouble getting the connection. Very strange. I will have a look at it tomorow because I will go to sleep.
If you solve it tonight post the answer as i am well interested in it.:D

---

### Post by Nano Geek on 2006-06-06
Make your /etc/apt/apt.conf file look like this.```
APT::Authentication::TrustCDROM "true";
```Then type sudo apt-get update.

---

### Post by racsw on 2006-06-06
Hi,
   I can actually see the apt-get accessing the internet through the DSL modem, so I know it's able to access the internet through the router.

  On the suggestion about adding that line to the /apt.conf file, what does this accomplish?

I need to get some sleep myself right now.  I'll continue this tomorrow.

Thank you so far for your help.
Robert

---

### Post by racsw on 2006-06-06
I tried the apt.conf file suggestion, it didn't work.  Same results.

Robert

---

### Post by racsw on 2006-06-06
I should also note that none of the URL's on the sources list are actually at that location.  I looked them all up.

They are not found at ../ubuntu/dapper/.. like the sources list claims.
They are found at ../ubuntu/dists/dapper/..

I changed them to this, and they still didn't work.  Maybe I typed them wrong, don't know for sure.

Robert

---

### Post by rcarring on 2006-06-06
Get the alternate cd and use that as your repository.

apt-cdrom add

In synaptic remove all other repositories.

You should then have only the cdrom for synaptic to work from.

---

### Post by Nano Geek on 2006-06-06
[QUOTE=racsw]On the suggestion about adding that line to the /apt.conf file, what does this accomplish?[/QUOTE]I ment for you to delete what was in that file and change it to what I posted. You could also try giving the file a different name such as: apt.conf1 by typing **sudo cp /ect/apt/apt.conf /ect/apt/apt.conf1** in the command line, and then try **sudo apt-get update**.

---

### Post by racsw on 2006-06-07
OK, we're halfway home, I identified the problem.

First, I made the change to the apt.conf file to test apt-get.  Everything worked perfectly accessing from the CDROM.

Then, I changed apt.conf back, and shut down the computer.
I disconnected the cable from the router and plugged it in directly to the PC.  So now  the DSL Modem output goes directly to the PC.

After startup, I did an apt-get update, and once again, it worked perfectly, downloaded all the appropriate files and updated my system.  Perfect.

Now we know the problem is the router. 
Can one of you guys tell me what I need to do next?  

Thank you for the help so far,
Robert

---

### Post by arob on 2006-06-13
Well if anyone cares check your router for poxy filtering and disable it.

---

### Post by racsw on 2006-06-14
No proxy filtering on the router.

Robert

---

