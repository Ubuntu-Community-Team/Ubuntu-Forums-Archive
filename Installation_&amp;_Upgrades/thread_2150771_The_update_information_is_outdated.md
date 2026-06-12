---
title: "The update information is outdated"
date: 2013-06-02
forum: Installation &amp; Upgrades
---

### Post by Edenhard on 2013-06-02
There will be a warning on the top bar saying that 'the update information is outdated... '

If 'sudo apt-get update',  get the following errors:

*W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://archive.canonical.com](http://archive.canonical.com) raring Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>*
*W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/raring/Release](http://archive.canonical.com/ubuntu/dists/raring/Release)  *

[I]W: Some index files failed to download. They have been ignored, or old ones used instead.


[/I]How can I deal with it? Thanks!

---

### Post by ibjsb4 on 2013-06-02
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo rm -r /var/lib/apt/lists/*
sudo mkdir /var/lib/apt/lists/partial
sudo apt-get update
```

There are also other methods for fixing this.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GPG+error+BADSIG&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GPG+error+BADSIG&sa=Search&cof=FORID:9)

---

