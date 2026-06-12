---
title: "PS3 Ubuntu 7.04 to 7.10 Help"
date: 2008-02-04
forum: Installation &amp; Upgrades
---

### Post by TheGingerNinja on 2008-02-04
Hi all, I'm just wondering if any of you can help with two errors I have trying to upgrade from 7.04 to 7.10. I'm not sure if the two are related but I don't know too much about Ubuntu.

Problem 1) I've been following the instructions and apparently I have to run the following two lines in the terminal.

$ sudo apt-get remove linux-image-powerpc64-smp linux-powerpc64-smp linux-restricted-modules-powerpc64-smp

$ sudo apt-get install linux-cell 

The first one works fine but the second returns an error stating "Couldn't find package linux-cell." Does anyone know what I'm doing wrong?

2) I ignored this error (usually not wise) and tried to directly upgrade through the Update manager and clicked through the first few boxes and then opens the upgrade window. The progress bar fetches a number of different packages but then returns the error 

"Failed to fetch [http://elisa.fluendo.com/packages/dists/feisty/Release](http://elisa.fluendo.com/packages/dists/feisty/Release) Unable to find expected entry main/binary-powerpc/Packages in Meta-index file (malformed Release file?)"

 Any ideas?

Thanks for all your help.

---

### Post by zvacet on 2008-02-04
```
gsudo gedit /etc/apt/sources.list
```

Put # sign in front of any third party repos including that one.Save and close.

```
sudo apt-get update
```

Now try to upgrade.

---

### Post by TheGingerNinja on 2008-02-12
Thanks, I've managed to complete the update but now when I try to load 7.10 from the kboot screen the PS3 just turns itself off with no error messages.

Short of downloading a 7.10 iso and burning it can you think of anything I could try?

Cheers
Andrew

---

