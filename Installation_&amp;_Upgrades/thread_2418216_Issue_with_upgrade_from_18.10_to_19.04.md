---
title: "Issue with upgrade from 18.10 to 19.04"
date: 2019-05-03
forum: Installation &amp; Upgrades
---

### Post by 08quadram on 2019-05-03
I am fairly new to Ubuntu. Our family computer's hard drive failed last winter so, with the new one, I wasn't flipping for Windows again because this just more or less checks mail, surfs the web and plays games. SO, i have used ubuntu in the past and like it. Anyway, long story short, I upgraded from 18.10 to 19.04 and had a couple of errors. The computer runs fine, but I cannot install other software it seems. Trying to get flash to work, so my wife can play scrabble. I do not believe it is a hardware issue. I've rebooted the computer several times without issue. This is new after the upgrade to 19.04. There were a couple of errors while the upgrade was running. One was something about xscreensaver locked and needed unlocked or something. I do not remember the rest. It seems to function normally other than not being able to install anything further. the following I get while trying to instal:


```
Setting up grub-efi-amd64-signed (1.115+2.02+dfsg1-12ubuntu2) ...
Installing for x86_64-efi platform.
Could not prepare Boot variable: Invalid argument
grub-install: error: efibootmgr failed to register the boot entry: Input/output error.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent configuration of shim-signed:
 shim-signed depends on grub-efi-amd64-signed | grub-efi-arm64-signed; however:
  Package grub-efi-amd64-signed is not configured yet.
  Package grub-efi-arm64-signed is not installed.

dpkg: error processing package shim-signed (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 grub-efi-amd64-signed
 shim-signed
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


any help would be great.
thanks!

Mike

---

### Post by eldon-rosenberg on 2019-07-25
I have the same issue, and FYI, I found a filed bug about this with our same OS and package versions that's still open: [Bug #1826050 “package grub-efi-amd64-signed 1.115+2.02+dfsg1-12u...” : Bugs : grub2-signed package : Ubuntu.]("https://bugs.launchpad.net/ubuntu/+source/grub2-signed/+bug/1826050")  You might want to subscribe to notifications from this bug too.

I did a bit of troubleshooting, and added a comment about that to this bug in the hope that it make it more attractive / easy for the package maintainers to attempt a fix.  I believe they will only need to recompile with a later version of libefivars.

---

### Post by rsteinmetz70112 on 2019-07-25
Have you tried"

```
# sudo dpkg --configure
# sudo apt install -f
```

or

```
# sudo apt install grub-efi-amd64-signed
```

?

---

