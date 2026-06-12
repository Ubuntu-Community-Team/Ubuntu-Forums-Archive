---
title: "Unable to install package ubuntu-defaults-ja"
date: 2020-06-25
forum: Installation &amp; Upgrades
---

### Post by usernotfound on 2020-06-25
Hello,

When I try to install ubuntu-defaults-ja, a dependency error causes I am unable to install it.

The version is 16.04 LTS.

root@HP-ProBook-450-G2:/home/user01# sudo apt-get install ubuntu-defaults-ja
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 ubuntu-defaults-ja : Depends: fonts-noto-cjk-extra but it is not installable
E: Unable to correct problems, you have held broken packages.

---

### Post by Bashing-om on 2020-06-25
usernotfound; Hello - Welcome to the forum :)

The package:
> 
ubuntu-defaults-ja


Does not appear to be an official ubuntu package.
Where did you get it from ?
Show us:
```

apt policy ubuntu-defaults-ja fonts-noto-cjk-extra

```
"fonts-noto-cjk-extra" is an official ubuntu package.
Are we looking at a PPA maintainer's error ?

[INDENT]gots to be a causation
[/INDENT]

---

### Post by ActionParsnip on 2020-06-26
If you are root, you don't need to use "sudo". You already have absolute system power. Are you logging in to the system as root? (I hope not)

---

### Post by ActionParsnip on 2020-06-26
[https://launchpad.net/ubuntu/+ppas?name_filter=ubuntu%2Ddefaults%2Dja](https://launchpad.net/ubuntu/+ppas?name_filter=ubuntu%2Ddefaults%2Dja)

Shows PPAs with the package. Have you used one of these?

---

### Post by tokyobadger on 2020-06-26
This package seems to be (a core) part of the Ubuntu Japan Team's (not an approved Localization Team) Ubuntu Japanese Remix. They give 3 reasons for why a remix is necessary:
1. The Live Session does not properly support Japanese and is therefore not an ideal introduction to Ubuntu/Linux
2. Some of the modifications required to provide a better Japanese UX adversely impact other language environments so can't be included in the regular Ubuntu images
3. The Ubuntu Japan Team are able to provide faster bug-fixes related to the Japanese UX

The default font used for Japanese text Takao is replaced with Noto in this remix.

On [this page ]("https://www.ubuntulinux.jp/products/JA-Localized")  (in Japanese) they describe how to add the ppa's required to convert an existing regular Ubuntu install - the commands required are provided in English and most of the Japanese text is well handled by Google Translate (if necessary).

OP says they are currently using 16.04. This project has images for 20.04 so could also be an opportunity to upgrade with a fresh install after trying the Live Session.

---

