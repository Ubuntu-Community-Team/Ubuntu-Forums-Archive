---
title: "Synaptic Pac. Man. not reading CD-ROM"
date: 2006-10-14
forum: Installation &amp; Upgrades
---

### Post by Raval on 2006-10-14
I'm trying to install build essential and Linux-headers-386 in order to use my modem (Agere PCI modem with SV9P chipset)  with Ubuntu. But I can't seem to get Synaptic Pac. Man. to find my Ubuntu 6.06 CD. Can anyone help me to understand how to I can correct this problem?

File I need:
binutils (version 2.16.1cvs20060117-1ubuntu2.1) will be installed
build-essential (version 11.1) will be installed
dpkg-dev (version 1.13.11ubuntu6) will be installed
g++ (version 4:4.0.3-1) will be installed
g++-4.0 (version 4.0.3-1ubuntu5) will be installed
gcc (version 4:4.0.3-1) will be installed
gcc-4.0 (version 4.0.3-1ubuntu5) will be installed
libstdc++6-4.0-dev (version 4.0.3-1ubuntu5) will be installed
linux-headers-2.6.15-27 (version 2.6.15-27.48) will be installed
linux-headers-2.6.15-27-386 (version 2.6.15-27.48) will be installed
linux-headers-386 (version 2.6.15.25) will be installed


error: Please insert the disk labeled:
Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)
in drive /cdrom/

CD ROM:
Device /dev/hdc
access path /media/cdrom1

The following problems were found on your system:

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.16.1cvs20060117-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/b/binutils/binutils_2.16.1cvs20060117-1ubuntu2.1_i386.deb)
  Temporary failure resolving 'security.ubuntu.com'

The following problems were found on your system:
W: Failed to fetch cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/pool/main/g/gcc-4.0/gcc-4.0_4.0.3-1ubuntu5_i386.deb

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-27_2.6.15-27.48_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-27_2.6.15-27.48_i386.deb)

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-27-386_2.6.15-27.48_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-27-386_2.6.15-27.48_i386.deb)
  
W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-386_2.6.15.25_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-386_2.6.15.25_i386.deb)

---

### Post by catlett on 2006-10-14
Do you only have 1 cd drive? If you have 2, try the other one.
Try ading the cd manually. Put the cd in the drive. Open up Synaptic package manager. Select "settings" and then "repositories". First make sure the cd entry is checked off and then go to the right and click on "add cdrom". It will scan your drive for a cd and add it to the menu. Post if you have errors.
Does the computer you are posting on have a cd burner? If it does, you can download the debs you need from the ubuntu package site, copy them to a cd and install the debs off the cd on your dapper system [http://packages.ubuntu.com/dapper/](http://packages.ubuntu.com/dapper/)

---

### Post by aysiu on 2006-10-14
I'm with catlett on this one. It sounds as if it's looking for the CD in the wrong CD-ROM drive.

If you're not afraid of the command-line, you can also install build-essential with these commands: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

---

### Post by Raval on 2006-10-14
> **aysiu said:**
> I'm with catlett on this one. It sounds as if it's looking for the CD in the wrong CD-ROM drive.

If you're not afraid of the command-line, you can also install build-essential with these commands: ```
sudo apt-cdrom add
sudo aptitude update
sudo aptitude install build-essential
```

I'm not afraid of the CLI, I only wish I knew what the commands meant (generally speaking) I know that’s my fault because I haven't spent the time looking them up. 

I wish I could print a few pages with commands and their meaning so I could paste them to my wall for reference.

If the GUI method doesn't work I’ll try yours they seems easy enough.

---

### Post by aysiu on 2006-10-15
It may not make a difference, but I figure it's worth a shot.

The first command adds the CD-ROM as a repository.
The second command updates the list of what's available in the repositories.
The third command install *build-essential*.

---

### Post by Raval on 2006-10-15
> **aysiu said:**
> It may not make a difference, but I figure it's worth a shot.

The first command adds the CD-ROM as a repository.
The second command updates the list of what's available in the repositories.
The third command install *build-essential*.

any input would always be welcomed. your method seems much easier and less time consuming than the GUI method.

Thank you.

---

### Post by Raval on 2006-10-15
> **catlett said:**
> Do you only have 1 cd drive? If you have 2, try the other one.
Try ading the cd manually. Put the cd in the drive. Open up Synaptic package manager. Select "settings" and then "repositories". First make sure the cd entry is checked off and then go to the right and click on "add cdrom". It will scan your drive for a cd and add it to the menu. Post if you have errors.
Does the computer you are posting on have a cd burner? If it does, you can download the debs you need from the ubuntu package site, copy them to a cd and install the debs off the cd on your dapper system [http://packages.ubuntu.com/dapper/](http://packages.ubuntu.com/dapper/)
I tried what you said and first it says place CD in drive even though it is already there I click for it to rety and it says mounting, then indexing and so on but then it says unmounting CD and thats it, it does nothing else and if you click close the repositry list is frozen.

I also tried installing the files from a CD and it says something about the CD not being a Debian CD and thats it.

I tried using sudo apt-get install because i now have all the files including the security files in a folder but it says something about can't find the folder.

thanks for your help but I think i've had enough of Ubuntu for a few days. I was up till 3am and then from 9:30am to 4pm today trying to fix this. After this post I rather not see the word or Logo Ubuntu for awhile.

---

### Post by Raval on 2006-11-02
OK i'm ready to try again, anyone got any advice on what I should do now?

---

