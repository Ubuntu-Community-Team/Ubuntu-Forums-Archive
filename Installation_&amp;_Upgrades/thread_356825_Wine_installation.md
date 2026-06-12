---
title: "Wine installation"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by gollybegully on 2007-02-08
ok so i enable extra repositories using this guide [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
 then I followed this guide to try and install wine [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

when i put in sudo apt-get install wine I get this message:
Package wine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package wine has no installation candidate

---

### Post by gollybegully on 2007-02-08
if anybody knows an alternate to wine I'd be happy to try that as well

---

### Post by divague on 2007-02-08
[http://www.codeweavers.com/products/cxoffice/](http://www.codeweavers.com/products/cxoffice/)

and for games
[http://www.transgaming.com](http://www.transgaming.com)

---

### Post by gollybegully on 2007-02-08
> **divague said:**
> [http://www.codeweavers.com/products/cxoffice/](http://www.codeweavers.com/products/cxoffice/)

and for games
[http://www.transgaming.com](http://www.transgaming.com)

sounds pretty good....but I dont wanna pay for it if theres free apps available

---

### Post by machoo02 on 2007-02-08
Well, you could run Windows within a virtual environment.  But otherwise there really isn't a free alternative to wine for getting windows applicatons running in linux.

BTW, I'm not sure if the guide is the best way to add the wine repositories.  you could try adding them manually:```
gksudo gedit /etc/apt/sources.list
```Paste the following lines to the bottom of your sources.  ```
## Latest WINE packages from WineHQ
deb http://wine.budgetdedicated.com/apt edgy main

```Be sure to replace edgy with dapper if that is what you are running.  Save and close, then ```
sudo apt-get update
sudo apt-get install wine
```

See if that works.

---

### Post by gollybegully on 2007-02-09
I added those two lines at the bottom of the file, but after trying to update apt I still get 

Failed to fetch [http://wine.budgetdedicated.com/apt/dists/edgy/Release](http://wine.budgetdedicated.com/apt/dists/edgy/Release)  Unable to find expected entry  main/binary-amd64/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

  your directions were fairly simple but is it possible I'm not using the gedit properly?....or perhaps its trying to get that 64 bit version that causing problems?

---

### Post by gollybegully on 2007-02-09
Come on there's gotta be another way to download it

---

### Post by gollybegully on 2007-02-09
I DID IT!

apparently they dont make wine for 64 bit architecture so you have to put in this hack 

[http://wiki.winehq.org/UbuntuAMD64](http://wiki.winehq.org/UbuntuAMD64)

and make sure you have he various ia32-libs packages installed already

---

