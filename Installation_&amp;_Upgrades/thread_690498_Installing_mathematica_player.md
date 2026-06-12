---
title: "Installing mathematica player"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by ftpvk on 2008-02-07
I download the mathematica player for Linux,  but when I try to install it

it says, that gedit could not find the symbol encoding?? 

than it says to select a coding from the menu (UTF-8, ISO...) and try again

(translation from Lithuanian ubuntu) 

Any suggestions what to do?

---

### Post by Partyboi2 on 2008-02-08
open a terminal (Applications>Accessories>Terminal)
make sure you are in the correct directory of the downloaded file
```
ls
```
make sure you can see > MathematicaPlayer.sh
If not then change to the correct directory where the file is.
then
```
sudo sh MathematicaPlayer.sh
```
answer the questions to install.

---

### Post by ftpvk on 2008-02-09
thanks, your instructions worked but I get a message that I am missing some dc++ libraries? something like that

---

### Post by zvacet on 2008-02-09
Look for exact name of these packages and 

```
sudo apt-get install** packagename**
```

or you can try to find them in synaptic and install.After that run command Partyboi2 post to you.

---

### Post by ftpvk on 2008-02-10
ok, thanks that worked

---

