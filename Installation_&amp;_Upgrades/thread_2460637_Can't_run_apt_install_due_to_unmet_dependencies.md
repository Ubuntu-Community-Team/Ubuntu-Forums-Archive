---
title: "Can't run apt install due to unmet dependencies"
date: 2021-04-15
forum: Installation &amp; Upgrades
---

### Post by wullig on 2021-04-15
I'm trying to update some packages but I keep getting the message "unmet dependencies".


What I do


    [HTML]sudo apt update // All good here
    sudo apt install --only-upgrade certbot[/HTML]


With the apt install I get the following messages (I translated the messages so they will not be correct word by word):




    [HTML]It's useful to run "apt-get -f install" to fix the following issues:
    The following packages have unmet dependencies:
         certbot : Depends: python3-certbot (= 0.31.0-2~deb10u1+ubuntu16.04.1+certbot+3) but it's not going to be installed
         linux-headers-4.4.0-179-generic : Depends: linux-headers-4.4.0-179 but it's not going to be installed
         linux-image-4.4.0-179-generic : Depends: linux-modules-4.4.0-179-generic but it's not going to be installed[/HTML]


The kernel right now is:


    [HTML]uname -a
    Linux 4.4.0-178-generic #208-Ubuntu SMP Sun Apr 5 23:45:10 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
[/HTML]

So I try to run `apt-get -f install`




    [HTML]After this operation, 131MB will be occupiede on disk
    Continue? Y/n
    E: Sub-process /usr/bin/dpkg exited unexpectedly[/HTML]




So I read it might have to do with free space in `/boot`, which indeed has A LOT of old kernels, but following all the guides I can't remove.


With `sudo apt-get autoremove --purge` I get again the unmet dependencies warning as before and suggest to run `apt-get -f install`.


If I try to remove a old kernel with `dpkg` the process get killed almost immediately:


    [HTML]sudo dpkg --force-all -P linux-image-4.4.0-71-generic
    Reading database 95%
    Killed[/HTML]


With `sudo dpkg --configure -a` I get 


So I'm quite stuck and tried almost everything out there

---

### Post by Impavidus on 2021-04-15
The complete output of```
LANG=C sudo apt install -f
```may help.

The LANG=C part will switch translations off, changing all output to English. Although, as it's all standard messages, I can typically handle it as long as it's in some germanic or romance language.

---

### Post by wullig on 2021-04-15
Ah good thing to know! Thanks.

This is the output:

```
root@xxx:/boot# sudo apt install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  linux-headers-4.4.0-179 linux-modules-4.4.0-179-generic
The following NEW packages will be installed:
  linux-headers-4.4.0-179 linux-modules-4.4.0-179-generic
0 upgraded, 2 newly installed, 0 to remove and 286 not upgraded.
6 not fully installed or removed.
Need to get 0 B/22.1 MB of archives.
After this operation, 131 MB of additional disk space will be used.
Do you want to continue? [Y/n]
E: Sub-process /usr/bin/dpkg exited unexpectedly
```

And just before the last line the text ```
Reading database ... 90%
``` appears and then replaced by ```
E: Sub-process /usr/bin/dpkg exited unexpectedly
```

---

### Post by wullig on 2021-04-15
Ah damn, solved it.

I didn't have enough RAM, since the server has only 512MB.

Made a swap file by following this guide: [https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04](https://www.digitalocean.com/community/tutorials/how-to-add-swap-space-on-ubuntu-16-04)

After that all commands were running correctly.

---

### Post by Impavidus on 2021-04-16
Well, I didn't expect that error. Good it's solved now. 512MB is tiny these days.

---

### Post by ActionParsnip on 2021-04-16
RAM is super cheap too, is an upgrade possible? If so then it'll really really help

---

### Post by wullig on 2021-04-16
It is an old server hosted on DigitalOcean with the basic plan.

I actually double checked and I can upgrade for the same price to 1GB ram and 5GB of extra storage. Just done that!

---

### Post by ActionParsnip on 2021-04-21
I see. Also note that if you are root you don't need to use sudo. You already have full system access

---

