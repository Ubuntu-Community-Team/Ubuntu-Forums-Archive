---
title: "apt-get update breaks"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by ditikos on 2007-02-27
Hello, I am using Xubuntu 6.10 and when I try to apt-get update (to get the new updates) from the greek repository, it shows me the following errors:

```
Err http://gr.archive.ubuntu.com edgy Release.gpg
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Err http://gr.archive.ubuntu.com edgy/main Translation-en_US
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Err http://gr.archive.ubuntu.com edgy/restricted Translation-en_US
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Err http://gr.archive.ubuntu.com edgy/universe Translation-en_US
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Err http://gr.archive.ubuntu.com edgy/multiverse Translation-en_US
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Err http://gr.archive.ubuntu.com edgy-updates Release.gpg
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Get:1 http://security.ubuntu.com edgy-security Release.gpg [191B]
Ign http://security.ubuntu.com edgy-security/main Translation-en_US
Ign http://security.ubuntu.com edgy-security/restricted Translation-en_US
Err http://gr.archive.ubuntu.com edgy-updates/main Translation-en_US
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Get:2 http://ubuntu.beryl-project.org edgy Release.gpg [191B]
Ign http://ubuntu.beryl-project.org edgy/main Translation-en_US
Err http://gr.archive.ubuntu.com edgy-updates/restricted Translation-en_US
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Ign http://security.ubuntu.com edgy-security/universe Translation-en_US
Ign http://security.ubuntu.com edgy-security/multiverse Translation-en_US
Err http://gr.archive.ubuntu.com edgy-updates/universe Translation-en_US
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Hit http://security.ubuntu.com edgy-security Release
Err http://gr.archive.ubuntu.com edgy-updates/multiverse Translation-en_US
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Ign http://gr.archive.ubuntu.com edgy Release
Get:3 http://ubuntu.beryl-project.org edgy Release [2961B]
Ign http://scratchbox.org ./ Release.gpg
Ign http://scratchbox.org ./ Translation-en_US
Ign http://gr.archive.ubuntu.com edgy-updates Release
Ign http://gr.archive.ubuntu.com edgy/main Packages
Hit http://security.ubuntu.com edgy-security/main Packages
Ign http://gr.archive.ubuntu.com edgy/restricted Packages
Get:4 http://ubuntu.beryl-project.org edgy/main Packages [11.1kB]
Ign http://gr.archive.ubuntu.com edgy/universe Packages
Ign http://scratchbox.org ./ Release
Ign http://download.skype.com stable Release.gpg
Hit http://security.ubuntu.com edgy-security/restricted Packages
Hit http://security.ubuntu.com edgy-security/universe Packages
Hit http://security.ubuntu.com edgy-security/multiverse Packages
Ign http://gr.archive.ubuntu.com edgy/multiverse Packages
Ign http://gr.archive.ubuntu.com edgy/main Sources
Ign http://gr.archive.ubuntu.com edgy/restricted Sources
Ign http://gr.archive.ubuntu.com edgy/universe Sources
Ign http://gr.archive.ubuntu.com edgy/multiverse Sources
Hit http://security.ubuntu.com edgy-security/main Sources
Hit http://security.ubuntu.com edgy-security/restricted Sources
Hit http://security.ubuntu.com edgy-security/universe Sources
Hit http://security.ubuntu.com edgy-security/multiverse Sources
Ign http://scratchbox.org ./ Packages
Ign http://gr.archive.ubuntu.com edgy-updates/main Packages
Ign http://download.skype.com stable/non-free Translation-en_US
Ign http://gr.archive.ubuntu.com edgy-updates/restricted Packages
Ign http://gr.archive.ubuntu.com edgy-updates/universe Packages
Ign http://gr.archive.ubuntu.com edgy-updates/multiverse Packages
Get:5 http://ubuntu.beryl-project.org edgy/main Sources [7396B]
Ign http://gr.archive.ubuntu.com edgy-updates/main Sources
Hit http://scratchbox.org ./ Packages
Ign http://gr.archive.ubuntu.com edgy-updates/restricted Sources
Ign http://gr.archive.ubuntu.com edgy-updates/universe Sources
Ign http://gr.archive.ubuntu.com edgy-updates/multiverse Sources
Ign http://download.skype.com stable Release
Err http://gr.archive.ubuntu.com edgy/main Packages
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Err http://gr.archive.ubuntu.com edgy/restricted Packages
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Err http://gr.archive.ubuntu.com edgy/universe Packages
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Err http://gr.archive.ubuntu.com edgy/multiverse Packages
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Err http://gr.archive.ubuntu.com edgy/main Sources
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Err http://gr.archive.ubuntu.com edgy/restricted Sources
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Err http://gr.archive.ubuntu.com edgy/universe Sources
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Err http://gr.archive.ubuntu.com edgy/multiverse Sources
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Err http://gr.archive.ubuntu.com edgy-updates/main Packages
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Err http://gr.archive.ubuntu.com edgy-updates/restricted Packages
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Err http://gr.archive.ubuntu.com edgy-updates/universe Packages
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Err http://gr.archive.ubuntu.com edgy-updates/multiverse Packages
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Err http://gr.archive.ubuntu.com edgy-updates/main Sources
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Err http://gr.archive.ubuntu.com edgy-updates/restricted Sources
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Ign http://download.skype.com stable/non-free Packages
Err http://gr.archive.ubuntu.com edgy-updates/universe Sources
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Err http://gr.archive.ubuntu.com edgy-updates/multiverse Sources
  Cannot initiate the connection to gr.archive.ubuntu.com:80 (2001:648:2000:de::211). - connect (101 Network is unreachable) [IP: 2001:648:2000:de::211 80]
Hit http://download.skype.com stable/non-free Packages
Fetched 21.6kB in 1s (13.6kB/s)
Reading package lists...
```

Is it a generic problem? It started doing it today. It says that network is unreachable, but when I ping the server it responds ok.

---

### Post by lhtown on 2007-02-27
Well, the unfortunate fact is that the 100% uptime server hasn't yet been devised. It appears that the server is down.

You can try changing the repositories to another one to see if that works or just wait a while and try again later.

---

