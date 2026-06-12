---
title: "Help in installing AcetoneISO"
date: 2012-07-27
forum: Installation &amp; Upgrades
---

### Post by Hari5g900 on 2012-07-27
Hello guys!
I am asking for help on installing AcetoneISO.
I am running ubuntu 10.04.
Firstly I tried to install it and it gave me the following error:

```
ubuntu@ubuntu-linux:~$ sudo apt-get install acetoneiso
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  acetoneiso: Depends: mencoder but it is not installable
E: Broken packages
```

Thank You in advance

---

### Post by Kirboosy on 2012-07-27
Try installing the mencoder package manually.

[MEncoder -- Community Documentation]("https://help.ubuntu.com/community/MEncoder")

Let me know if that helps any.

Also you could run this command if it keeps complaining about broken packages

```
sudo dpkg --configure -a
sudo apt-get install -f
```

---

### Post by Hari5g900 on 2012-07-27
This is what I got when I gave the code u wrote

ubuntu@ubuntu-linux:~$ sudo dpkg --configure -a
[sudo] password for ubuntu: 
```
ubuntu@ubuntu-linux:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libmono-getoptions2.0-cil untex libxvidcore4 librsvg2-2.18-cil libqof2
  libswt-cairo-gtk-3.5-jni chromium-browser-inspector libdbi0
  libtrackerclient0 libswt-mozilla-gtk-3.5-jni qof-data wv python-bluez
  libx264-85 librecode0 libwv-1.2-3 python-bittorrent python-espeak
  libopensync0 recode libqof2-backend-qsf libwnck2.20-cil libzip1 libmaa2
  libpq5 timidity libqt3-mt odt2txt libswt-gnome-gtk-3.5-jni timidity-daemon
  stardict-plugin-gucharmap libtracker-gtk0 libnotify0.4-cil
  libgnomedesktop2.20-cil
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

Should I auto remove them?

I cannot install mencoder manually


```
ubuntu@ubuntu-linux:~$ sudo apt-get install mencoder
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package mencoder is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mencoder has no installation candidate
```

```
ubuntu@ubuntu-linux:~$ sudo apt-get install acetoneiso
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  acetoneiso: Depends: mencoder but it is not installable
E: Broken packages
```

---

### Post by Kirboosy on 2012-07-27
> **Hari5g900 said:**
> Should I auto remove them?
Autremove will not hurt anything. Its simply cleaning up unused packages.

> I cannot install mencoder manually

Do you have the [RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats") enabled?

---

### Post by Hari5g900 on 2012-07-28
If i have restricted formats enabled, how will I know it?
I haven't installed ubuntu restricted extras. Should I install it?

---

### Post by Kirboosy on 2012-07-28
Try installing mencoder manually using [this link]("http://www.ubuntuupdates.org/package/medibuntu_non_free/precise/non-free/base/mencoder") Then try to install acetoneISO once thats done installing


Installing restricted-extras won't hurt anything but if you don't want them then don't install them. You can check via the software center

---

### Post by Hari5g900 on 2012-07-29
> **Caboose885 said:**
> Try installing mencoder manually using [this link]("http://www.ubuntuupdates.org/package/medibuntu_non_free/precise/non-free/base/mencoder") Then try to install acetoneISO once thats done installing
But that version is for 12.04
I'm running 10.04
I looked for the lucid version but I cant install(the deb file) that too.

---

### Post by Kirboosy on 2012-07-30
What sort of error is it giving you?

Here is the [Lucid Package]("http://www.ubuntuupdates.org/package/lucidbleed/lucid/main/base/mencoder")

---

### Post by Hari5g900 on 2012-08-01
It says (when I opened with gdebi package manager):
Error: Dependency is not satisfiable: mplayer

---

### Post by Kirboosy on 2012-08-01
It might be looking for a newer version of mplayer...I'm not sure but I believe it wants this version  

mplayer (2:1.0~rc4.dfsg1-1ubuntu3~ppa1~lucid1)

---

### Post by Hari5g900 on 2012-08-02
> It might be looking for a newer version of mplayer...I'm not sure but I believe it wants this version 

mplayer (2:1.0~rc4.dfsg1-1ubuntu3~ppa1~lucid1)
So what should I do??
I upgraded everything a few days ago
Should I have to install the above version of mplayer separatly??

---

### Post by Hari5g900 on 2012-08-02
Why is mplayer needed for AcetoneISO anyway?

---

### Post by Kirboosy on 2012-08-02
> **Hari5g900 said:**
> Should I have to install the above version of mplayer separatly??

You could try that.

> Why is mplayer needed for AcetoneISO anyway?

I'm not sure really. I just installed acetoneiso using

```
sudo apt-get install acetoneiso
```

on my Ubuntu 12.04 64 bit box and it went no problems.

---

### Post by Hari5g900 on 2012-08-05
Is there any way to force-install mencoder or something like that?? I didn't get the version of mencoder you gave me

---

### Post by jmore9 on 2012-08-05
acetone is in the repos so just use synaptic and select it and it will install all that is needed for it.  Thats how i installed it.

---

### Post by Kirboosy on 2012-08-06
Using synaptic, software-center or apt-get should all yield the same result. You can try synaptic.


Can you run the following command for me.

```
cat /etc/apt/sources.list | grep deb
```

paste the output back here. If you disabled a repository then that might explain why its not finding anything.

---

### Post by Kai927 on 2012-08-07
Hello, I am also having some issues installing AcetoneISO. I am rather new to Ubuntu, and haven't really done anything with it before, so I fear that I am just screwing up somewhere. Anyways, I try to install it, both through the software center and through the terminal, and it gives me an error. In the terminal, this is what it says:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  language-pack-zh-hans kde-l10n-de language-pack-kde-de language-pack-kde-en
  language-pack-de-base language-pack-kde-zh-hans language-pack-kde-en-base
  kde-l10n-engb language-pack-kde-de-base kde-l10n-zhcn firefox-locale-de
  language-pack-zh-hans-base firefox-locale-zh-hans language-pack-de
  language-pack-kde-zh-hans-base
Use 'apt-get autoremove' to remove them.
Suggested packages:
  mencoder
The following NEW packages will be installed:
  acetoneiso
0 upgraded, 1 newly installed, 0 to remove and 19 not upgraded.
Need to get 0 B/1,113 kB of archives.
After this operation, 1,740 kB of additional disk space will be used.
(Reading database ... 209293 files and directories currently installed.)
Unpacking acetoneiso (from .../acetoneiso_2.3-2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/acetoneiso_2.3-2_i386.deb (--unpack):
 trying to overwrite '/usr/share/pixmaps/Acetino2.png', which is also in package acetoneiso2 2.0.1
Errors were encountered while processing:
 /var/cache/apt/archives/acetoneiso_2.3-2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)I have tried taking a look at the acetino2.png, and tried giving read and write permsissons to all groups, but nothing has changed, and I get the same error.  

Though it has a different format, the software center gives me the same error. What can I do?

Thanks in advance.

---

### Post by Hari5g900 on 2012-08-08
Here's the result you asked for
```
ubuntu@ubuntu-linux:~$ cat /etc/apt/sources.list | grep deb
# deb cdrom:[Ubuntu 10.04.1 LTS _Lucid Lynx_ - Release i386 (20100816.1)]/ lucid main restricted
deb http://archive.ubuntu.com/ubuntu lucid main
deb http://archive.ubuntu.com/ubuntu lucid universe
# deb http://in.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
# deb-src http://in.archive.ubuntu.com/ubuntu/ lucid-backports main restricted universe multiverse
deb http://archive.canonical.com/ubuntu lucid partner
deb-src http://archive.canonical.com/ubuntu lucid partner
deb http://security.ubuntu.com/ubuntu/ lucid-security universe main
```
Also, Synaptic didn't do anything different

---

### Post by Hari5g900 on 2012-08-08
Kai927, try running:
```
sudo apt-get update
```
and then try
```
sudo apt-get install acetoneiso
```
also, this could be posted as a new thread

---

