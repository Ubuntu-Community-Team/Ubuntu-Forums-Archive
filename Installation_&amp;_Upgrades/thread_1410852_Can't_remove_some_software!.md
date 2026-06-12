---
title: "Can't remove some software!"
date: 2010-02-19
forum: Installation &amp; Upgrades
---

### Post by frenc on 2010-02-19
After adding a source, I used Terminal to install some software:

```
sudo apt-get install skulltag
sudo apt-get install doomseeker-skulltag
```

Things were perfect. I wanted to remove the software so I can create a tutorial of how to install it, so I did the following:

```
sudo apt-get remove skulltag
sudo apt-get remove doomseeker-skulltag
```

It told me it was done, uninstalled, etc., yet they're still in my applications menu and are semi-functional (they appear to be broken).

How do I completely remove them? It seems I can't re-install until they're completely gone.

Sorry to register without contributing, by the way. Thanks in advance.

---

### Post by Julita on 2010-02-19
Try this:
sudo apt-get --purge remove skulltag
sudo apt-get --purge remove doomseeker-skulltag
Then, sudo apt-get autoremove

---

### Post by frenc on 2010-02-19
> **Julita said:**
> Try this:
sudo apt-get --purge remove skulltag
sudo apt-get --purge remove doomseeker-skulltag
Then, sudo apt-get autoremove

```
david@XPS:~$ sudo apt-get --purge remove skulltag
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package skulltag
david@XPS:~$ sudo apt-get --purge remove doomseeker-skulltag
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package doomseeker-skulltag
david@XPS:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  doomseeker imagemagick libflac++6 libqt4-core libqt4-test libwadseeker
  libwxbase2.8-0 libwxgtk2.8-0 python-wxgtk2.8 python-wxversion
  skulltag-client skulltag-data skulltag-data-announcer
  skulltag-data-extraskins skulltag-pk3 skulltag-server timidity
  timidity-daemon
0 upgraded, 0 newly installed, 18 to remove and 3 not upgraded.
After this operation, 89.9MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 145953 files and directories currently installed.)
Removing doomseeker ...

```

Will restart now. Thanks. I'll post results after.

Edit: They're gone. My God, thank you, Julita.

---

