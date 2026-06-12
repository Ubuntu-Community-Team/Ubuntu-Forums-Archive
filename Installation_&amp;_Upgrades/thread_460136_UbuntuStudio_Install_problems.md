---
title: "UbuntuStudio Install problems"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by Chris Parsons on 2007-05-31
I used the following code:

```
sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'
```

and received no errors.  However with the next entry:

```
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update
```

I get the following errors:

> Get:5 [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release.gpg [189B]   
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US
Ign [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty/main Translation-en_US
Hit [http://archive.ubuntustudio.org](http://archive.ubuntustudio.org) feisty Release
Fetched 5B in 2s (2B/s)
Failed to fetch [http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release](http://archive.ubuntustudio.org/ubuntustudio/dists/feisty/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


I'm very new to Linux and Ubuntu so please bear with me.  My goal is to upgrade my current Ubuntu install to UbuntuStudio.  Could the problem be that I have the 64bit version of Ubuntu and UbuntuStudio is 32bit?

Thanks so much for your time!

---

