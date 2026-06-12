---
title: "Repairing my Ubuntu installation after a bad 32-bit library support installation"
date: 2016-09-07
forum: Installation &amp; Upgrades
---

### Post by jdowdster on 2016-09-07
Many months ago I tried to install the 32-bit library support into my 64-bit installation of Kubuntu 14.04LTS. Since then I'm unable to update packages.

For instance, if I try to run the "apt-get update" command, it runs for a bit and then at the end I get:

Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty Release   
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse amd64 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse i386 Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Translation-en_CA                 
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/main Translation-en                    
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Translation-en              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Translation-en              
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Translation-en_CA             
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/universe Translation-en                
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/multiverse Translation-en_CA           
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) trusty/restricted Translation-en_CA           
Fetched 1,550 kB in 7s (196 kB/s)                                              
W: There is no public key available for the following key IDs:
1397BC53640DB551
W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release](http://dl.google.com/linux/chrome/deb/dists/stable/Release)  Unable to find expected entry 'main/binary-i386/Packages' in Release file (Wrong sources.list entry or malformed file)

E: Some index files failed to download. They have been ignored, or old ones used instead.

If I try to install some package like "efibootmgr' for instance, here are the errors:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 cpp-4.8 : Depends: gcc-4.8-base (= 4.8.4-2ubuntu1~14.04) but 4.8.4-2ubuntu1~14.04.3 is to be installed
 g++-4.8 : Depends: gcc-4.8-base (= 4.8.4-2ubuntu1~14.04) but 4.8.4-2ubuntu1~14.04.3 is to be installed
 gcc-4.8 : Depends: gcc-4.8-base (= 4.8.4-2ubuntu1~14.04) but 4.8.4-2ubuntu1~14.04.3 is to be installed
 gcc-4.8-multilib : Depends: gcc-4.8 (= 4.8.4-2ubuntu1~14.04.3) but 4.8.4-2ubuntu1~14.04 is to be installed
                    Depends: libc6-dev-i386 (>= 2.11) but it is not going to be installed
 libc6-dev-x32 : Depends: libc6-dev-i386 (= 2.19-0ubuntu6.9) but it is not going to be installed
 libgcc-4.8-dev : Depends: gcc-4.8-base (= 4.8.4-2ubuntu1~14.04) but 4.8.4-2ubuntu1~14.04.3 is to be installed
 libstdc++-4.8-dev : Depends: gcc-4.8-base (= 4.8.4-2ubuntu1~14.04) but 4.8.4-2ubuntu1~14.04.3 is to be installed
                     Depends: libstdc++6 (>= 4.8.4-2ubuntu1~14.04) but 4.8.2-19ubuntu1 is to be installed
 libstdc++6 : Depends: gcc-4.8-base (= 4.8.2-19ubuntu1) but 4.8.4-2ubuntu1~14.04.3 is to be installed
 libstdc++6:i386 : Depends: gcc-4.8-base:i386 (= 4.8.2-19ubuntu1) but 4.8.4-2ubuntu1~14.04.3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

I have tried the suggestion of running "apt-get -f install" and here is its result:

jdowd@new-guy:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  cpp-4.8 g++-4.8 gcc-4.8 libc6-dev-i386 libgcc-4.8-dev libstdc++-4.8-dev
  libstdc++6 libstdc++6:i386
Suggested packages:
  gcc-4.8-locales g++-4.8-multilib gcc-4.8-doc libstdc++6-4.8-dbg libgcc1-dbg
  libgomp1-dbg libitm1-dbg libatomic1-dbg libasan0-dbg libtsan0-dbg
  libquadmath0-dbg libstdc++-4.8-doc
The following NEW packages will be installed:
  libc6-dev-i386
The following packages will be upgraded:
  cpp-4.8 g++-4.8 gcc-4.8 libgcc-4.8-dev libstdc++-4.8-dev libstdc++6
  libstdc++6:i386
7 upgraded, 1 newly installed, 0 to remove and 459 not upgraded.
107 not fully installed or removed.
Need to get 0 B/32.2 MB of archives.
After this operation, 9,680 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 488557 files and directories currently installed.)
Preparing to unpack .../g++-4.8_4.8.4-2ubuntu1~14.04.3_amd64.deb ...
Unpacking g++-4.8 (4.8.4-2ubuntu1~14.04.3) over (4.8.4-2ubuntu1~14.04) ...
Preparing to unpack .../libstdc++-4.8-dev_4.8.4-2ubuntu1~14.04.3_amd64.deb ...
Unpacking libstdc++-4.8-dev:amd64 (4.8.4-2ubuntu1~14.04.3) over (4.8.4-2ubuntu1~14.04) ...
Preparing to unpack .../libgcc-4.8-dev_4.8.4-2ubuntu1~14.04.3_amd64.deb ...
Unpacking libgcc-4.8-dev:amd64 (4.8.4-2ubuntu1~14.04.3) over (4.8.4-2ubuntu1~14.04) ...
Preparing to unpack .../libstdc++6_4.8.4-2ubuntu1~14.04.3_amd64.deb ...
De-configuring libstdc++6:i386 (4.8.2-19ubuntu1) ...
Unpacking libstdc++6:amd64 (4.8.4-2ubuntu1~14.04.3) over (4.8.2-19ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libstdc++6_4.8.4-2ubuntu1~14.04.3_amd64.deb (--unpack):
 trying to overwrite '/usr/share/gcc-4.8/python/libstdcxx/__init__.py', which is also in package libstdc++-arm-none-eabi-newlib 4.8.3-11ubuntu1+4
Preparing to unpack .../libstdc++6_4.8.4-2ubuntu1~14.04.3_i386.deb ...
De-configuring libstdc++6:amd64 (4.8.2-19ubuntu1) ...
Unpacking libstdc++6:i386 (4.8.4-2ubuntu1~14.04.3) over (4.8.2-19ubuntu1) ...
dpkg: error processing archive /var/cache/apt/archives/libstdc++6_4.8.4-2ubuntu1~14.04.3_i386.deb (--unpack):
 trying to overwrite '/usr/share/gcc-4.8/python/libstdcxx/__init__.py', which is also in package libstdc++-arm-none-eabi-newlib 4.8.3-11ubuntu1+4
Preparing to unpack .../gcc-4.8_4.8.4-2ubuntu1~14.04.3_amd64.deb ...
Unpacking gcc-4.8 (4.8.4-2ubuntu1~14.04.3) over (4.8.4-2ubuntu1~14.04) ...
Preparing to unpack .../cpp-4.8_4.8.4-2ubuntu1~14.04.3_amd64.deb ...
Unpacking cpp-4.8 (4.8.4-2ubuntu1~14.04.3) over (4.8.4-2ubuntu1~14.04) ...
Preparing to unpack .../libc6-dev-i386_2.19-0ubuntu6.9_amd64.deb ...
Unpacking libc6-dev-i386 (2.19-0ubuntu6.9) ...
dpkg: error processing archive /var/cache/apt/archives/libc6-dev-i386_2.19-0ubuntu6.9_amd64.deb (--unpack):
 trying to overwrite '/usr/include/bits', which is also in package libc6-dev-amd64 2.19-0ubuntu6.9
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libstdc++6_4.8.4-2ubuntu1~14.04.3_amd64.deb
 /var/cache/apt/archives/libstdc++6_4.8.4-2ubuntu1~14.04.3_i386.deb
 /var/cache/apt/archives/libc6-dev-i386_2.19-0ubuntu6.9_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

So now I'm pretty much back at the beginning of the issue.

Does anyone know how I should proceed from here?

Cheers!!

---

### Post by ian-weisser on 2016-09-07
Here are your three key errors:
```

[COLOR=#000000]dpkg: error processing archive /var/cache/apt/archives/libstdc++6_4.8.4-2ubuntu1~14.04.3_amd64.deb (--unpack):[/COLOR]
[COLOR=#000000]trying to overwrite '/usr/share/gcc-4.8/python/libstdcxx/__init__.py', which is also in package libstdc++-arm-none-eabi-newlib 4.8.3-11ubuntu1+4
[...]
[/COLOR][COLOR=#000000]dpkg: error processing archive /var/cache/apt/archives/libstdc++6_4.8.4-2ubuntu1~14.04.3_i386.deb (--unpack):[/COLOR]
[COLOR=#000000]trying to overwrite '/usr/share/gcc-4.8/python/libstdcxx/__init__.py', which is also in package libstdc++-arm-none-eabi-newlib 4.8.3-11ubuntu1+4[/COLOR]
[COLOR=#000000][...]
[/COLOR][COLOR=#000000]dpkg: error processing archive /var/cache/apt/archives/libc6-dev-i386_2.19-0ubuntu6.9_amd64.deb (--unpack):[/COLOR]
[COLOR=#000000]trying to overwrite '/usr/include/bits', which is also in package libc6-dev-amd64 2.19-0ubuntu6.9
```

In Debian/Ubuntu's package system, each system file can be provided by one (and only one) installed package.
Two packages cannot provide the same file at the same time. If so, they *conflict.*
You are telling the system to install conflicting packages, which may break your system quite horribly. Your system is trying to protect you by refusing.
[/COLOR]
1) Decide which of the packages you actually want.
2) Uninstall the packages you don't want.
3) Install the packages you do want.

---

### Post by jdowdster on 2016-09-07
thanks for the reply...

I removed packages using the dpkg app instead of the apt app. It seems to have done the trick. Thanks!!

Cheers!!

---

### Post by oldos2er on 2016-09-07
Hi jdowdster, would you please mark your thread 'Solved' under Thread Tools at the top of the page? It will assist others who might be having the same problem. Thanks.

---

