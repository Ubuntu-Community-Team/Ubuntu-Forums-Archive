---
title: "Troubles upgrading to Feisty 7.04"
date: 2007-05-02
forum: Installation &amp; Upgrades
---

### Post by eGrant on 2007-05-02
Hey there, I checked out and didn't find any questions similar to my own. I was trying to upgrade my Dapper Drake 6.06 LTS to the new Feisty 7.04, but apparently there were some troubles installing NVIDIA drivers - there were 6 broken packages that were not installed and I couldn't find a way to install them. And now I have no graphic interface (some xorg problem). If I try to 'apt-get upgrade' or 'apt-get dist-upgrade' (or 'aptitude'...) I get a long list of installed packages which must be uninstalled in order to get the NVIDIA drivers to work, but I have no idea how to do that. I'm basically stuck like this now. Oh, and '-f' didn't help at all either.
Any ideas anyone?

---

### Post by zvacet on 2007-05-02
You can not upgrade from Dapper to Feisty directly.That is what give you troubles.You have two ways to go:
1.Dapper>Edgy>Feisty upgrade but I think that is too much to download
2.download Feisty CD (alternate will be my choice,but you do as you wish) and make clean install

---

### Post by Steve H on 2007-05-02
Have you got a working desktop? I may be worthwhile just downloading the drivers from [_Nvidia.com_]("http://www.nvidia.com/content/drivers/drivers.asp"), that worked for me when I had similar problems with upgrading from Edgy to Feisty. It killed my X server and I only had command line to sort it all.

 If you don't have a working X desktop yet try running

```
sudo dpkg-reconfigure xserver-xorg
```

That should at least give you a desktop to use to get to Nvidia, and get the latest drivers. If none of that works let me know, I still have a few tricks up my sleeve that we can try (but I'm at work and can't remember where I put them!!:) )

---

### Post by eGrant on 2007-05-03
Hey, thanks for the help. I wasn't able to restore my original Ubuntu, so I installed a fresh one. I just hope that there aren't many other geniuses like myself who are trying to upgrade as I did :p

---

