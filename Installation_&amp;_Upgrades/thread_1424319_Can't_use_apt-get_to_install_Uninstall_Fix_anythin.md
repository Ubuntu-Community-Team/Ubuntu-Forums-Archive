---
title: "Can't use apt-get to install Uninstall Fix anything"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by andytof47 on 2010-03-07
Hi Guys, really need help with this one as I can't find an answer anywhere.

My problem started with DVDrip and I mad an apt-on-cd DVD and installed from there rather than download the packages for my twop systems running karmic.

I don't know  what has happened but now if I try to install/upgrade/remove anything i get the following.

```
The following packages have unmet dependencies:
  libevent-execflow-perl: Depends: libanyevent-perl but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

So

```
$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  anyevent-perl libnet-ssleay-perl libevent-rpc-perl python-mmkeys
  linux-headers-2.6.31-14 linux-headers-2.6.31-14-generic libnet-libidn-perl
  libio-socket-ssl-perl
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libanyevent-perl
Suggested packages:
  libjson-perl libjson-xs-perl libguard-perl
The following NEW packages will be installed:
  libanyevent-perl
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
1 not fully installed or removed.
Need to get 0B/343kB of archives.
After this operation, 852kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Media change: please insert the disc labelled
 'APTonCD for ubuntu karmic - amd64 (2010-03-05 23:29) DVD1'
in the drive '/cdrom/' and press enter

(Reading database ... 144377 files and directories currently installed.)
Unpacking libanyevent-perl (from .../libanyevent-perl_5.240-1_all.deb) ...
dpkg: error processing /cdrom//packages/libanyevent-perl_5.240-1_all.deb (--unpack):
 trying to overwrite '/usr/share/man/man3/AnyEvent.3pm.gz', which is also in package anyevent-perl 0:1.02-0.2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /cdrom//packages/libanyevent-perl_5.240-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So i'm stuck, how can I fix this - I would be willing to nuke the installation but if thats gonna happen I'd need to know where the Badblocks file is kept so I can make a backup (took twleve hours on a 750gb drive) 

Please could someone please help 

cheers

---

### Post by andytof47 on 2010-03-08
Wow Guys, These forums have changed so much since I first started using Ubuntu. What set it apart was you could get an answer from the forums....... 


So please Bump! (Why have forums in the first place, I say that with respect for the work all the devolpers put in, but half baking the cake is still not good enough, and I know this is because of DVDrip, it's a broken package and they still have it in the official channels, WHY?)

---

### Post by oldos2er on 2010-03-08
Look up the **dpkg-divert** command. I don't recall the proper syntax, but **man dpkg-divert** should help.

---

### Post by andytof47 on 2010-03-21
i'll keep it in mind for next time, I nuked it and started from scratch but really appreciate the reply

---

### Post by teacosy on 2010-04-19
hi... 
im having a similar issue while trying to add the RareWares Debian GNU / Linux Repository to my apt source list... 

apt-get install -f returns: 
```

Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  ogmtools anyevent-perl libasound2-plugins binfmt-support
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libanyevent-perl
The following NEW packages will be installed:
  libanyevent-perl
0 upgraded, 1 newly installed, 0 to remove and 1 not upgraded.
2 not fully installed or removed.
Need to get 0B/210kB of archives.
After this operation, 537kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 190557 files and directories currently installed.)
Unpacking libanyevent-perl (from .../libanyevent-perl_4.410-1_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libanyevent-perl_4.410-1_all.deb (--unpack):
 trying to overwrite '/usr/share/man/man3/AnyEvent.3pm.gz', which is also in package anyevent-perl 0:1.02-0.2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Processing triggers for man-db ...
Errors were encountered while processing:
 /var/cache/apt/archives/libanyevent-perl_4.410-1_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```im not too familiar with the dpkg-divert command... 
ive read the man dpkg-divert page and thought i needed to add a diversion for the /var/cache/apt/archives/libanyevent-perl_4.410-1_all.deb file... 

i did that and tried install -f again but same result...

im sure im missing something... 

can anybody help me out on this?

thanks

t

---

### Post by teacosy on 2010-04-21
ha... i thought so...

as soon as i made a post i would find a solution...

found something of interest here: 

[http://biostat.mc.vanderbilt.edu/wik...ependFixDebian]("http://biostat.mc.vanderbilt.edu/wiki/Main/DependFixDebian") 

i used dkpg to force the overwrite of the package:
cd /var/cache/apt/archives/
dpkg -i --force-overwrite libanyevent-perl_4.410-1_all.deb

now it seems my dependencies have been resolved... 

had created a thread on this here:

[http://ubuntuforums.org/showthread.php?p=9153548#post9153548](http://ubuntuforums.org/showthread.php?p=9153548#post9153548)


thanks

---

