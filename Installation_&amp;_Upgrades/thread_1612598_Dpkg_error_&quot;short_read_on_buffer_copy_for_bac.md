---
title: "Dpkg error &quot;short read on buffer copy for backend dpkg-deb&quot;"
date: 2010-11-03
forum: Installation &amp; Upgrades
---

### Post by Crazedpsyc on 2010-11-03
Often, when I try to install packages right out of the ubuntu repository (from any mirror) I get a bunch of error messages and dpkg fails. That happened to me when I tried to upgrade from 10.04 to 10.10 which was what broke the system. Now they are happening again in my brand new install of 10.10. Here are some of the error messages I have gotten:
```
E: /var/cache/apt/archives/mdns-scan_0.5-1_amd64.deb: short read on buffer copy for backend dpkg-deb during `./usr/bin/mdns-scan'
E: /var/cache/apt/archives/service-discovery-applet_0.4.4-4.1ubuntu1_all.deb: short read on buffer copy for backend dpkg-deb during `./usr/bin/service-discovery-applet'
```

and:
```
(Reading database ... 157956 files and directories currently installed.) 
Unpacking libcheese-gtk18 (from .../libcheese-gtk18_2.32.0-0ubuntu1_amd64.deb) ... 
dpkg: error processing /var/cache/apt/archives/libcheese-gtk18_2.32.0-0ubuntu1_amd64.deb (--unpack): 
 corrupted filesystem tarfile - corrupted package archive 
No apport report written because MaxReports is reached already
Unpacking cheese-common (from .../cheese-common_2.32.0-0ubuntu1_all.deb) ... 
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid code lengths set' 
dpkg-deb: subprocess <decompress> returned error exit status 2 
dpkg: error processing /var/cache/apt/archives/cheese-common_2.32.0-0ubuntu1_all.deb (--unpack): 
 short read on buffer copy for backend dpkg-deb during `./usr/share/gnome/help/cheese/C/legal.xml' 
No apport report written because MaxReports is reached already
Unpacking cheese (from .../cheese_2.32.0-0ubuntu1_amd64.deb) ... 
dpkg-deb (subprocess): data: internal gzip read error: '<fd:0>: invalid distance too far back' 
dpkg-deb: subprocess <decompress> returned error exit status 2 
dpkg: error processing /var/cache/apt/archives/cheese_2.32.0-0ubuntu1_amd64.deb (--unpack): 
 corrupted filesystem tarfile - corrupted package archive 
No apport report written because MaxReports is reached already
Processing triggers for man-db ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/libcheese-gtk18_2.32.0-0ubuntu1_amd64.deb 
 /var/cache/apt/archives/cheese-common_2.32.0-0ubuntu1_all.deb 
 /var/cache/apt/archives/cheese_2.32.0-0ubuntu1_amd64.deb 

```
the worst one though is that I tried to update a few things like the linux kernel and ubuntu software center today and so now they are broken as well as their dependencies such as ubuntu-desktop. Please Help! I don't want to reinstall ubuntu *again!:(*

EDIT: Now firefox froze and when I restarted it all I got was this error message and it doesn't open. Luckily I already had midori installed:
```
/usr/lib/firefox-3.6.12/firefox-bin: error while loading shared libraries: libasound.so.2: cannot open shared object file: No such file or directory

```

---

### Post by Crazedpsyc on 2010-11-03
Got it! ESET NOD32 av breaks dpkg! Could somebody report this as a bug please

---

### Post by Crazedpsyc on 2010-11-03
And could a moderator mark this as solved? Midori won't let me use the drop-down menus

---

### Post by tommcd on 2010-11-03
> **Crazedpsyc said:**
> Got it! ESET NOD32 av breaks dpkg! Could somebody report this as a bug please
Where do you have NOD32 installed? Do you dual boot with Windows, and have NOD32 installed on your Windows partition? Or did you manage to install NOD32 in Ubuntu with Wine somehow?
Did you install Ubuntu inside Windows with Wubi? Or is this a real Ubuntu install to a dedicated linux partition on your hard drive?
IF NOD32 is installed to a Windows partition, and Ubuntu is on it's own linux partition, then I don't see how NOD32 could affect Ubuntu.

NOD32 is a great antivirus for Windows; but you do not need any antivirus programs for linux.

---

### Post by Crazedpsyc on 2010-11-03
I had the linux beta version. And trust me, in my location, with my local network users, I definitaly need antivirus, firewall, ids, psad, etc. ;)

---

### Post by tommcd on 2010-11-03
> **Crazedpsyc said:**
> I had the linux beta version. And trust me, in my location, with my local network users, I definitaly need antivirus, firewall, ids, psad, etc. ;)
I didn't know NOD32 had a linux version available. I used their Windows version for a couple years and I thought it was excellent. If NOD32 linux version is causing problems for you, you should report it to them.

If you are a sysadmin with multiple users on a network, then you may be justified in using an antivirus, especially if there are Windows computers that share the network. It is possible to lock down a linux system and maintain security without an antivirus though.
 A firewall is always a good idea.
For most home linux users an antivirus is not needed:
[http://www.linux.com/news/software/applications/8261-note-to-new-linux-users-no-antivirus-needed](http://www.linux.com/news/software/applications/8261-note-to-new-linux-users-no-antivirus-needed)
You can get **clamav** antivirus from the Ubuntu repos:
[http://packages.ubuntu.com/maverick/clamav](http://packages.ubuntu.com/maverick/clamav)

---

### Post by Crazedpsyc on 2010-11-04
I knew about clamav and it is great for doing a scan every so often but it takes so long! I also love having live antivirus protection :(
And FYI I am not just in any old crowded office building, I am in a brand new crowded office building with a bunch of guys who spend their time playing with toys from thinkgeek and inventing usb powered bacon fryers. Along with the occasional invention of a zero day exploit or a BSOD emulator or some such thing lol ;)

---

### Post by earthwormdan on 2011-01-21
I too installed the eset beta antivirus after using it for many years on my windows machine and started having problems installing/upgrading packages ever since... Had no idea it could be the antivirus though!

Just to confirm I am experiencing the same problems on ubuntu 10.10 x64 bit since last night. Has anyone had any luck solving this or contacting eset?

Oh, and to the above poster claiming no need for an antivirus, respectivly.. you are mistaken. people never saw a need for antivirus when windows was first produced. and neither did people think we needed condoms for many hundreds of years. but sadly they were wrong, and it pays to play it safe.

---

### Post by Crazedpsyc on 2011-01-27
Thanks, Yes I got the same problem with the latest NOD32 on my new 10.10 x86_64 system. It also crashed my apache2 server several times before I killed it. Along with that, It deleted files without asking (including metasploit of course ;) and caused my django dev server to throw out a  million errors before crashing.
 It looks like this project really needs some work.

---

### Post by rhertzog on 2011-06-28
FWIW, the dpkg error message simply means that the .deb files are corrupted, see the explanation in this article:
[http://raphaelhertzog.com/2011/06/27/deciphering-one-of-dpkgs-weirdest-errors-short-read-on-buffer-copy/](http://raphaelhertzog.com/2011/06/27/deciphering-one-of-dpkgs-weirdest-errors-short-read-on-buffer-copy/)

---

