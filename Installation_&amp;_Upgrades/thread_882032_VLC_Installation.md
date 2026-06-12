---
title: "VLC Installation"
date: 2008-08-06
forum: Installation &amp; Upgrades
---

### Post by waterrr on 2008-08-06
Hi,
I'm currently running on a Ubuntu 6.06.2 and wanted to install VLC on it, I ran these following command lines but was not successful - please help
```
echo "deb ftp://ftp.videolan.org/pub/videolan/ubuntu dapper universe" > /etc/apt/sources.list.d/vlc.list
sudo apt-get upgrade
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc libdvdcss2
```

---

### Post by dannyboy79 on 2008-08-06
first, what are the errors? also, why are you using a none trusted repository? vlc is in the universe or multiverse repo of normal http ubuntu repo's, not an ftp site.

---

### Post by limasierra on 2008-08-06
Try install one application at a time to detect what's failing. Instead of using```
sudo apt-get install vlc vlc-plugin-esd mozilla-plugin-vlc libdvdcss2
```Use```
sudo apt-get install vlc
sudo apt-get install vlc-plugin-esd
sudo apt-get install mozilla-plugin-vlc
sudo apt-get install libdvdcss2
```

---

### Post by waterrr on 2008-08-06
```
sudo apt-get install vlc 
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: aalib1 (>= 1.2)
       Depends: libdvdplay0 but it is not going to be installed
       Depends: libdvdread2 but it is not installable
       Depends: libpng2 (>= 1.0.12) but it is not installable
       Depends: libvorbis0 (>= 1.0rc3-1) but it is not installable
       Depends: libxosd0 (>= 0.7.0-1) but it is not installable
       Depends: slang1 (> 1.4.4-7.1) but it is not installable
       Depends: xlibs (> 4.1.0) but it is not installable
       Depends: ttf-thryomanes but it is not installable
E: Broken packages
admin@RRDNetwork:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  vlc: Depends: aalib1 (>= 1.2)
       Depends: libdvdplay0 but it is not going to be installed
       Depends: libdvdread2 but it is not installable
       Depends: libpng2 (>= 1.0.12) but it is not installable
       Depends: libvorbis0 (>= 1.0rc3-1) but it is not installable
       Depends: libxosd0 (>= 0.7.0-1) but it is not installable
       Depends: slang1 (> 1.4.4-7.1) but it is not installable
       Depends: xlibs (> 4.1.0) but it is not installable
       Depends: ttf-thryomanes but it is not installable
E: Broken packages

```

all the other installation errors are similar to this

---

### Post by dannyboy79 on 2008-08-06
like I said, why are you using any repo besides trusted ones. Let's see your 

/etc/apt/sources.list

this is where the problem lies I could almost gurantee it. also, if you have current broken packages installed, you'll need to get that squared away first becuase of dependencies.

---

### Post by raul_ on 2008-08-06
Is Dapper even still supported?

---

### Post by dannyboy79 on 2008-08-07
dapper drake is a LTS release. Long Term Support. I would think the repositories are still around.

---

### Post by raul_ on 2008-08-07
I thought LTS was only 2 years, but it seems it's 3. I would recommend upgrading anyway

---

### Post by dannyboy79 on 2008-08-07
my point being this whole time is that he's using an untrusted repo. You can see for yourself that the dapper repo's are still around.

[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/)

---

