---
title: "How to Upgrade a Specific Package"
date: 2015-11-22
forum: Installation &amp; Upgrades
---

### Post by convert_mrta on 2015-11-22
Hello,  I've running 14.04, and want to keep running it until a new LTS version comes out.   But, I've discovered that I have a very old version of gparted installed (0.18.0), and I would like install the latest package (0.24)

Running a sudo apt-get update does nothing, since .18 is the version included in 14.04, so no update is made.    So, how can I get the update manager to give me packages which are more up-to-date than the packages included in 14.04?

I don't see a repository for gparted on gparted.org that I can add to my software sources.

Thanks very much.

---

### Post by Dennis N on 2015-11-22
> So, how can I get the update manager to give me packages which are more up-to-date than the packages included in 14.04?
You have to resort to other methods: Outside of compiling your own software, PPAs or even .deb files are other ways.
> I don't see a repository for gparted on gparted.org that I can add to my software sources.
I had the same problem with this old gparted version in Ubuntu MATE 14.04, so found a .deb package for the newer version and installed it with gdebi package installer. So far, it has functioned properly, and includes support for GPT partition names. You have to make a judgment on the trustworthyness of the source.

[http://www.ubuntuupdates.org/package/getdeb_apps/trusty/apps/getdeb/gparted](http://www.ubuntuupdates.org/package/getdeb_apps/trusty/apps/getdeb/gparted)

Version currently installed on my system:
```
dmn@Zotac:~$ apt-cache policy gparted
gparted:
  Installed: [COLOR="#FF0000"]0.24.0-1~getdeb1
[/COLOR]  Candidate: 0.24.0-1~getdeb1
  Version table:
 *** 0.24.0-1~getdeb1 0
        100 /var/lib/dpkg/status
     0.18.0-1 0
        500 http://us.archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages

```

---

