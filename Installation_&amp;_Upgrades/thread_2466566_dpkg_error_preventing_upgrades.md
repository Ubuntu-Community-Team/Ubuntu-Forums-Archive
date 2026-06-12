---
title: "dpkg error preventing upgrades"
date: 2021-08-30
forum: Installation &amp; Upgrades
---

### Post by yeshua-1 on 2021-08-30
Unsure how to get around this one, but it is preventing an upgrade.
Guidance and assistance appreciated.

This is the description I get from running  dpkg --configure -asudo dpkg --configure -a
Setting up grub-efi-amd64-signed (1.167.2+2.04-1ubuntu44.2) ...
Installing for x86_64-efi platform.
grub-install: error: relocation 0x4 is not implemented yet.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-amd64-signed package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent processing triggers for shim-signed:
 shim-signed depends on grub-efi-amd64-signed | grub-efi-arm64-signed; however:
  Package grub-efi-amd64-signed is not configured yet.
  Package grub-efi-arm64-signed is not installed.

dpkg: error processing package shim-signed (--configure):
 dependency problems - leaving triggers unprocessed
Errors were encountered while processing:
 grub-efi-amd64-signed
 shim-signed

---

### Post by Bashing-om on 2021-08-30
yeshua-1- Hey ...

we have:
> 
Package grub-efi-arm64-signed is not installed.


so what happens when attempting to install the package ?
```

sudo apt update
sudo apt upgrade
sudo apt install grub-efi-arm64-signed

```

what now does the package manager advise ?

[INDENT]package manager un-happy
[INDENT][INDENT]system hurts too[/INDENT][/INDENT][/INDENT]

---

### Post by yeshua-1 on 2021-08-30
When I do that I get:

W: APT had planned for dpkg to do more than it reported back (3542 vs 3546).
   Affected packages: grub-efi-amd64-signed:amd64
ymp@ympnote:~$ sudo apt install grub-efi-arm64-signed
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package grub-efi-arm64-signed is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'grub-efi-arm64-signed' has no installation candidate

---

### Post by MAFoElffen on 2021-08-30
You haven't mentioned which Ubuntu Release you are running... That version is in Focal and Groovy.
```
apt-cache show grub-efi-amd64-signed 

```

Wait a minute... LOL 
You are AMD64, right? Like the output of your first post...
> This is the description I get from running  dpkg --configure -asudo dpkg --configure -a
```

Setting up grub-efi-[COLOR=#008000]amd64[/COLOR]-signed (1.167.2+2.04-1ubuntu44.2) ...
Installing for [COLOR=#008000]x86_64[/COLOR]-efi platform.
grub-install: error: relocation 0x4 is not implemented yet.
dpkg: error processing package grub-efi-amd64-signed (--configure):
 installed grub-efi-[COLOR=#008000]amd64[/COLOR]-signed package post-installation script subprocess returned error exit status 1
dpkg: dependency problems prevent processing triggers for shim-signed:
 shim-signed depends on grub-efi-[COLOR=#008000]amd64[/COLOR]-signed | grub-efi-[COLOR=#ff0000]arm64[/COLOR]-signed; however:
  Package grub-efi-[COLOR=#008000]amd64[/COLOR]-signed is not configured yet.
  Package grub-efi-[COLOR=#ff0000]arm64[/COLOR]-signed is not installed.
```

Why are you trying to install that for ARM64? Which would NOT be located in your repo, nor apply to your architecture...

do you not rather want to try the package noted in  post #1?
```

grub-efi-amd64-signed

```
What the above says, is that shim-signed depends on either the amd64 OR the arm64 versions of grub efi signed, which your amd64 version is not configured. The arm64 version, which is the OR in that statement, is not required, and not installed, because it is not relevant to your platform architecture.

Concentrate on "grub-efi-amd64-signed" not being configured yet.

---

### Post by yeshua-1 on 2021-08-31
Hmm, not quite sure how I got here then. Yes, my machine would be amd64. Version of Ubuntu is 20.04.3 Upgrade appears to be incomplete. Desktop does not display, and if I select it in files, a window opens but immediately vanishes.

---

### Post by yeshua-1 on 2021-09-02
Computer continued to manifest problems until I went to Synaptic and did an upgrade, this resolved the problems.

---

