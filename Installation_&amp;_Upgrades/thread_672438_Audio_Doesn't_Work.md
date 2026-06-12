---
title: "Audio Doesn't Work"
date: 2008-01-19
forum: Installation &amp; Upgrades
---

### Post by techgy on 2008-01-19
Ok. I admit that I'm now lost.
Having just started using Xubuntu I have managed to the wireless internet going but little else. 

I'd like to be able to play mp3 audio as well as a video or two. However, neither will work.
I've tried to follow the install directions given by others to install software (RealPlayer) for instance, but I've failed miserably.

I have downloaded the Linux install file for RealPlayer10GOLD.bin and have it in a folder. Where do I go from here?

:confused:

---

### Post by kellemes on 2008-01-19
For restricted formats (including mp3) see.. [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
For realplayer see.. [https://help.ubuntu.com/community/RealplayerInstallationMethods](https://help.ubuntu.com/community/RealplayerInstallationMethods)

---

### Post by techgy on 2008-01-19
I'm using Xubuntu v7.10  

The commands you referenced didn't work.

The file I'm trying to install is RealPlayer10GOLD.bin which I have stored in a folder by itself.

Also, the "deb" command isn't found when I try to use it. (Terminal)

---

### Post by kellemes on 2008-01-19
> **techgy said:**
> I'm using Xubuntu v7.10  

The commands you referenced didn't work.

The file I'm trying to install is RealPlayer10GOLD.bin which I have stored in a folder by itself.


The second link explains how to install RealPlayer10GOLD.bin
Can you explain why this is not working?

---

### Post by techgy on 2008-01-19
First of all the instructions to install RealPlayer10GOLD.bin are for Xubuntu versions that I don't have. I'm running v7.10

When I did attempt the install using

sudo aptitude install RealPlayer10GOLD.bin

I received a message saying that the file couldn't be found.

I gave the above command from within the folder that the file was stored.

---

### Post by kellemes on 2008-01-19
> **techgy said:**
> First of all the instructions to install RealPlayer10GOLD.bin are for Xubuntu versions that I don't have. I'm running v7.10

When I did attempt the install using

sudo aptitude install RealPlayer10GOLD.bin

I received a message saying that the file couldn't be found.

I gave the above command from within the folder that the file was stored.

You can't use apt-get since you're not using the repositories to install a package, in this case you're using a separate installer-package provided by RealPlayer. So this needs to be done differently..

From the folder where this file is do the following..
```

sudo chmod +x RealPlayer10GOLD.bin
sudo ./RealPlayer10GOLD.bin

```
The installer should now come up..

---

### Post by techgy on 2008-01-19
Upon trying the commands you suggested I receive an error message telling me that a libray is missing.

libstdc++.so.5

---

### Post by kellemes on 2008-01-20
> **techgy said:**
> Upon trying the commands you suggested I receive an error message telling me that a libray is missing.

libstdc++.so.5


This will fix it..
```
sudo apt-get install libstdc++5
```

---

### Post by techgy on 2008-01-20
Thanks everyone! Problem resolved !!!

Appreciated the help! Perhaps some day when I've figured this all out, I can return the favor. 

:)

---

