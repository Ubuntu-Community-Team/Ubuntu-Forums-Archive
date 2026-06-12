---
title: "installing php 7 on 14.04 - Cannot add PPA: 'ppa:ondrej/php-7.0'"
date: 2019-11-02
forum: Installation &amp; Upgrades
---

### Post by marchello_lippi2 on 2019-11-02
Hi all, 
I'm trying to install php 7 on 14.04, but can't add ppa.
```
$ sudo add-apt-repository ppa:ondrej/php-7.0Cannot add PPA: 'ppa:ondrej/php-7.0'.
Please check that the PPA name or format is correct.
```
Please advise.

---

### Post by SeijiSensei on 2019-11-02
14.04 is [no longer supported]("https://wiki.ubuntu.com/Releases"). I don't see any 14.04 builds in the list on this page: [https://launchpad.net/~ondrej/+archive/ubuntu/php](https://launchpad.net/~ondrej/+archive/ubuntu/php)

Time to upgrade to 18.04.

---

### Post by TheFu on 2019-11-02
+1 - move to 18.04 which is supported into 2023. It is the current LTS release.

If you stay with Canonical server packages, then you can pay for support for 10 yrs.  That won't address any PPA support.  That is something that you'll need to handle yourself or pay the team to accomplish.  Hobbyists maintaining a PPA are more likely to want to be on the most recent LTS for server software or the most recent distro for desktop stuff.

Best to stick with the core stuff that Canonical supports.  For fun, run this:
```
sudo ubuntu-support-status
```

---

### Post by marchello_lippi2 on 2019-11-07
Thanks SeijiSensei, TheFu. It worked for me on 18.04.3 LTS. Though it's vps and I had to create everything from scratch, because vps provider claimed that upgrade would not go well. I have two other vps with 14.04 and would try to upgrade them from console. Anyway... it is ok now on vps that I needed the most. Thanks.

---

