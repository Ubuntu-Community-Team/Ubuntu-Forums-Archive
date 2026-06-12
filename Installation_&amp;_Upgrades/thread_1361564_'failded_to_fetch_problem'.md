---
title: "'failded to fetch problem'"
date: 2009-12-22
forum: Installation &amp; Upgrades
---

### Post by 24dhruv on 2009-12-22
i have got a ubuntu jaunty 64bit os

whenever i try to run 'update manager' or 'synaptic package manager it gives me errors'
like failed to fetch ...........
i was using server from India then changed it to main servers still comes the same thing.
following are the screenshots for visualize the errors.
[http://lh4.ggpht.com/_37vfcYJMDx0/Sy9Os7apK2I/AAAAAAAAADw/7zTY0nSZJnM/s800/Screenshot1.jpg](http://lh4.ggpht.com/_37vfcYJMDx0/Sy9Os7apK2I/AAAAAAAAADw/7zTY0nSZJnM/s800/Screenshot1.jpg)
[http://lh5.ggpht.com/_37vfcYJMDx0/Sy9OtMrdooI/AAAAAAAAAD0/KZSpf7uUp5g/s144/Screenshot2.jpg](http://lh5.ggpht.com/_37vfcYJMDx0/Sy9OtMrdooI/AAAAAAAAAD0/KZSpf7uUp5g/s144/Screenshot2.jpg)

---

### Post by MelDJ on 2009-12-22
they all seem to be language packs. so i assume that this is normal as it doesn't need/wasn't told to download the language packs

---

### Post by 24dhruv on 2009-12-22
@^^
i don't think so because none of them gets success and i have tried to install an app from synaptic and also tried the following commands

sudo apt-get update
sudo apt-get update -o Acquire::http::No-Cache=True
sudo apt-get update -o Acquire::BrokenProxy=true

but they all fails

though i can surf internet from firefox

i have tried [www.appnr.com](www.appnr.com) but it also fails

---

### Post by MelDJ on 2009-12-22
could you post the output of sudo apt-get update?

---

### Post by 24dhruv on 2009-12-22
here it is ::


```
dhr@dhr-laptop:~$ sudo apt-get update
[sudo] password for dhr: 
Err http://archive.ubuntu.com jaunty Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com jaunty/main Translation-en_IN
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com jaunty/restricted Translation-en_IN
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com jaunty/universe Translation-en_IN
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com jaunty/multiverse Translation-en_IN
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com jaunty-updates Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com jaunty-updates/main Translation-en_IN
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com jaunty-updates/restricted Translation-en_IN
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com jaunty-updates/universe Translation-en_IN
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com jaunty-updates/multiverse Translation-en_IN
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com jaunty-security Release.gpg
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com jaunty-security/main Translation-en_IN
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com jaunty-security/restricted Translation-en_IN
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com jaunty-security/universe Translation-en_IN
  Could not resolve 'archive.ubuntu.com'
Err http://archive.ubuntu.com jaunty-security/multiverse Translation-en_IN
  Could not resolve 'archive.ubuntu.com'
Reading package lists... Done
W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/main/i18n/Translation-en_IN.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/restricted/i18n/Translation-en_IN.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/universe/i18n/Translation-en_IN.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty/multiverse/i18n/Translation-en_IN.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/main/i18n/Translation-en_IN.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/restricted/i18n/Translation-en_IN.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/universe/i18n/Translation-en_IN.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-updates/multiverse/i18n/Translation-en_IN.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/Release.gpg  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/main/i18n/Translation-en_IN.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/restricted/i18n/Translation-en_IN.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/universe/i18n/Translation-en_IN.bz2  Could not resolve 'archive.ubuntu.com'

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/jaunty-security/multiverse/i18n/Translation-en_IN.bz2  Could not resolve 'archive.ubuntu.com'

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems
dhr@dhr-laptop:~$ 

```

---

### Post by MelDJ on 2009-12-22
in admin-software sources, let ubuntu pick the best server. then see what happens. it could be that the server is down

---

### Post by 24dhruv on 2009-12-22
:confused::)
it says no suitable download server was found
please cehck your internet connection

is it causing due to my connection to the internet it is through a proxy server in wireless environment

---

### Post by MelDJ on 2009-12-22
> **24dhruv said:**
> :confused::)
it says no suitable download server was found
please cehck your internet connection

is it causing due to my connection to the internet it is through a proxy server in wireless environment

it could be that.

---

