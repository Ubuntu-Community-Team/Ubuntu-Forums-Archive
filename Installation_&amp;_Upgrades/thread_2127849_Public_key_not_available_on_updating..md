---
title: "Public key not available on updating."
date: 2013-03-21
forum: Installation &amp; Upgrades
---

### Post by hencelence on 2013-03-21
Hey guys,
when I try to update my Ubuntu 12.10 it gives me this output:
```
sudo apt-get update
[sudo] password for lenz: 
Hit http://dl.google.com stable Release.gpg
Hit http://dl.google.com stable Release                                        
Hit http://de.archive.ubuntu.com quantal Release.gpg                           
Get:1 http://repository.spotify.com stable Release.gpg [489 B]                 
Get:2 http://extras.ubuntu.com quantal Release.gpg [72 B]                      
...
Ign http://de.archive.ubuntu.com quantal-updates/universe Translation-en_US
Fetched 1,036 kB in 4s (230 kB/s)
Reading package lists... Done
W: GPG error: http://repository.spotify.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 082CCEDF94558F59
W: GPG error: http://ppa.launchpad.net quantal Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 4F172854044A3B98
W: GPG error: http://ppa.launchpad.net quantal Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 83FBA1751378B444
W: GPG error: http://ppa.launchpad.net quantal Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 6AF0E1940624A220
W: Duplicate sources.list entry http://dl.google.com/linux/earth/deb/ stable/main i386 Packages (/var/lib/apt/lists/dl.google.com_linux_earth_deb_dists_stable_main_binary-i386_Packages)
W: Duplicate sources.list entry http://repo.steampowered.com/steam/ precise/steam i386 Packages (/var/lib/apt/lists/repo.steampowered.com_steam_dists_precise_steam_binary-i386_Packages)

```

There seem to be two errors: 1) Pubkey missing for some sources
2) Duplicate sources for some software.

I tried to fix it by using the graphic application "software sources".
Should I edit my sources.list?


Thanks for your help.

---

### Post by ibjsb4 on 2013-03-21
The first link shows how to fix a single GPG error NO_PUBKEY and the second link shows how to fix multiple pubkey errors.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GPG+error+NO_PUBKEY&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GPG+error+NO_PUBKEY&sa=Search&cof=FORID:9)

Look for those duplicate sources in /var/lib/apt/lists.

---

