---
title: "i have quite a problem here, now i cant install ANYTHING!"
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by Aesir09 on 2007-08-13
A few days ago i tried to install virtualbox, and there was only a i386 version when i am running a i686 (the package was choking up so i just closed it). So now, When i try to install something....


```
dom@ubuntu:~$ sudo apt-get install kubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
dom@ubuntu:~$ sudo apt-get remove virtualbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
dom@ubuntu:~$ 

```


there is also an error/update logo by the clock on the panel, when i click on it i get this message:

[IMG]http://img339.imageshack.us/img339/7320/screenshotupdatemanagergd0.png[/IMG]

---

### Post by merlinus on 2007-08-13
Try this:

```

sudo dpkg --configure -a

```

-merlin

---

### Post by forestpixie on 2007-08-13
I had exactly that problem with virtualbox [here]("http://ubuntuforums.org/showthread.php?t=444863") and [here]("http://ubuntuforums.org/showthread.php?t=445014") 

got it sorted with this command 
```

sudo dpkg --remove --force-remove-reinstreq virtualbox
```

---

