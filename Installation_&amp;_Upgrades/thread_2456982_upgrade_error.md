---
title: "upgrade error"
date: 2021-01-23
forum: Installation &amp; Upgrades
---

### Post by Seth-666 on 2021-01-23
Good morning, can anyone pls help me? 

i have this error ... basicly as i can see when i am trying to upgrade "dist..." its saying 

" ```
fter this operation, 501 MB of additional disk space will be used.Do you want to continue? [Y/n] y
Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 311486 files and directories currently installed.)
Preparing to unpack .../pop-gnome-initial-setup_3.36.1~1608149692~20.04~0358b40_amd64.deb ...
Unpacking pop-gnome-initial-setup (3.36.1~1608149692~20.04~0358b40) ...
dpkg: error processing archive /var/cache/apt/archives/pop-gnome-initial-setup_3.36.1~1608149692~20.04~0358b40_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/gnome-initial-setup/vendor.conf', which is also in package gnome-initial-setup 3.36.2-0ubuntu2
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/pop-gnome-initial-setup_3.36.1~1608149692~20.04~0358b40_amd64.deb

``` "

i trying to install it with synaptic myself ... no luck ....

---

### Post by Impavidus on 2021-01-23
It means that you've got two packages on your system that can't be there both. One is pop-gnome-initial-setup, the other is gnome-initial-setup. One of them has t be removed.

Which release of Ubuntu have you got and where did you get those packages from, if not from the official repos? If you get all packages from the official repos, these problems are supposed not to happen.

---

### Post by Seth-666 on 2021-01-25
hi there,  it is , Ubuntu 20.04.1 LTS . only from the official repo i am updating my OS 
and how can i fix this pls ... ? 
Sorry for the late replay i am working many hours ... this days . 

Thank you

---

### Post by ActionParsnip on 2021-01-25
Are you running PopOS ?

---

### Post by #&amp;thj^% on 2021-01-25
I'll always start with this.
To reconfigure dpkg database, simply run:

```
sudo dpkg --configure -a
```

This command will try to fix the corrupted dpkg database and then reconfigure all broken packages. This command usually fixes the dpkg returned an error code (1) problem. If it is not solved for any reason, follow the subsequent solutions.
If the first method didn't work, run the following command to perform force install:

```
sudo apt install -f
```

Or,

```
sudo apt install --fix-broken
```

Here, -f (or --fix-broken) option will attempt to correct the Ubuntu system with broken dependencies.

When you install a package, it will be downloaded and saved in the cache folder "/var/cache/apt/archives/".

To fix this error, remove the cached package using this command:

```
sudo rm /var/cache/apt/archives/pop-gnome-initial-setup_3.36.1~1608149692~20.04~0358b40_amd64.deb
```

Replace eog_3.36.2-0ubuntu1_amd64.deb with your package.

Clean the package cache folder:

```
sudo apt clean
```

```
sudo apt autoremove
```

Update the source lists:

```
sudo apt-get update
```

Upgrade your system:

```
sudo apt upgrade
```

Finally, get the fresh package from official repositories and reinstall it like below:

```
sudo apt-get install <Your Package>
```
This solution works for me. Good Luck.

---

### Post by Seth-666 on 2021-01-27
unfortunately before posting here i made good research and tried all above . but i tried them again exact like you said early , and still no luck ... 

```
Preparing to unpack .../pop-gnome-initial-setup_3.36.1~1608149692~20.04~0358b40_
amd64.deb ...
Unpacking pop-gnome-initial-setup (3.36.1~1608149692~20.04~0358b40) ...
dpkg: error processing archive /var/cache/apt/archives/pop-gnome-initial-setup_3
.36.1~1608149692~20.04~0358b40_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/gnome-initial-setup/vendor.conf', which is also i
n package gnome-initial-setup 3.36.2-0ubuntu2
dpkg-deb: error: paste subprocess was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/pop-gnome-initial-setup_3.36.1~1608149692~20.04~0358b40
_amd64.deb
E: Sub-proce

```

i will just reinstall the hole system ... thank you

---

### Post by Seth-666 on 2021-01-27
CLOSE topic please , thank you

---

