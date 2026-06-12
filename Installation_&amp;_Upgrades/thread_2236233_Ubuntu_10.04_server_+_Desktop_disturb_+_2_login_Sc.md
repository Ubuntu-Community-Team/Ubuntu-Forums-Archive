---
title: "Ubuntu 10.04 server + Desktop disturb + 2 login Screen + Not updating from CLI"
date: 2014-07-25
forum: Installation &amp; Upgrades
---

### Post by aristatechnologies2 on 2014-07-25
Dear Sir,

We have installed ubuntu 10.04 server with gnome desktop since Sept./Oct 2009 and we have enabled Terminal Service.

So more than 30 thin pc/clients were working on that server.

Now today we got strange problem, the server and thin pcs are getting Dual Login Screen or Disturb screen.
so they cannot log to their work.

Also when we tried updating ubuntu than it gaves an error as below
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release.gpg [189B]
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid/multiverse Translation-en_IN
Get:2 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release.gpg [198B]
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) lucid-updates/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid Release
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates Release [58.3kB]
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/main Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/restricted Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/universe Sources
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid/multiverse Sources
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Packages [764kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/main Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/universe Translation-en_IN
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) lucid-security/multiverse Translation-en_IN
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release [57.3kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Packages [569kB]
Get:8 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Packages [4,624B]
Get:9 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/main Sources [336kB]
Get:10 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/restricted Sources [2,196B]
Get:11 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Packages [349kB]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)
Get:12 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/universe Sources [110kB]
Get:13 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Packages [2,829B]
Ign [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/) lucid/main Translation-en_IN
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
Ign [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/) lucid/main Translation-en_IN
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release.gpg
Ign [http://ppa.launchpad.net/webupd8team/gnome3/ubuntu/](http://ppa.launchpad.net/webupd8team/gnome3/ubuntu/) lucid/main Translation-en_IN
Get:14 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/main Sources [243kB]
Get:15 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Packages [11.5kB]
Get:16 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) lucid-updates/multiverse Sources [5,817B]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid Release
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Ign [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
Get:17 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/restricted Sources [1,267B]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages
  404  Not Found
Get:18 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Packages [204kB]
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) lucid/main Packages 
  404  Not Found
Get:19 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/universe Sources [46.7kB]
Get:20 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Packages [5,373B]
Get:21 [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security/multiverse Sources [2,347B]
Fetched 2,773kB in 27s (102kB/s)
W: Failed to fetch [http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/lucid/Release.gpg](http://ppa.launchpad.net/gdm2setup/gdm2setup/ubuntu/dists/lucid/Release.gpg)  Something wicked happened resolving 'ppa.launchpad.net:http' (-5 - No address associated with hostname)


W: Failed to fetch [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found


W: Failed to fetch [http://ppa.launchpad.net/webupd8team/gnome3/ubuntu/dists/lucid/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/webupd8team/gnome3/ubuntu/dists/lucid/main/binary-amd64/Packages.gz)  404  Not Found


E: Some index files failed to download, they have been ignored, or old ones used instead.


**Friends:** 
the problem arise is it dont allow to update the GDM library. or anything related to GUI login. 
b/c. of that I think it has disturb the LTSP thing also.

Any suggestion in this regard will be highly appreciatable.

it's quiet urgent and very very important.

Thank in advance.

Good day,

note: if you need more info please let me know here.

---

### Post by bapoumba on 2014-07-25
10.04 has reached end of life for the Desktop over a year ago : [http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)
The ppa you were using are gone for 10.04 and give 404s. For ex, the gnome one works for 14.04, the current LTS release : [http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/trusty/main/binary-amd64/Packages.gz](http://ppa.launchpad.net/gnome3-team/gnome3/ubuntu/dists/trusty/main/binary-amd64/Packages.gz)

So I would highly recommend you backup and install a supported release.

---

### Post by Bucky Ball on 2014-07-25
Don't think the server edition has reached end-of-life, though, bapoumba. That's what OP is using. ;)

---

### Post by bapoumba on 2014-07-25
Yes BB, but why the gnome ppas and the GDM/login problems ?

---

### Post by Bucky Ball on 2014-07-25
True ... good chance of breakage there, as you mention.

```
W: Failed to fetch http://ppa.launchpad.net/gnome3-team...64/Packages.gz 404 Not Found


W: Failed to fetch http://ppa.launchpad.net/webupd8team...64/Packages.gz 404 Not Found
```

---

