---
title: "nothing helps to fix broken package manager."
date: 2013-02-10
forum: Installation &amp; Upgrades
---

### Post by U202E on 2013-02-10
If I want to remove/install update a package apt gives this error
```
libdrm-dev : Requires: libdrm-nouveau1a (= 2.4.42+git1302070925.20c560~gd~p) but 2.4.39-0ubuntu1 is installed.
```and If I use sudo apt-get -f install it 'works' untill it gives this error:
```
dpkg: fout bij afhandelen van /var/cache/apt/archives/libdrm-nouveau1a_2.4.42+git1302070925.20c560~gd~p_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libdrm_nouveau.so.2.0.0', which is also in package libdrm-nouveau2 2.4.39-0ubuntu1
Fouten gevonden tijdens behandelen van:
 /var/cache/apt/archives/libdrm-nouveau1a_2.4.42+git1302070925.20c560~gd~p_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```^^"fouten" is dutch for "errors", for some reason apt is not 100% translated to the nl-NL locale.

I tried everything I was able to find on the internet! -but nothing helped.
And yes I have added some PPAs, but this 'broken' package is build succesfully according to [https://launchpad.net/~oibaf/+archive/graphics-drivers/+packages](https://launchpad.net/~oibaf/+archive/graphics-drivers/+packages)
^^the .deb file from /var/cache/apt/archives/ is included as an attachment, it looks like a normal archive with no errors...

what's the (best) working fix I haven't found?
^^most apt/dpkg commands don't work, especially the ones I need; removing any PPA won't help. (even with the --force option)
most probably I have to manually edit something to make apt work again...
^^something like reverse enginering the .deb file or so.

info about my laptop:
ubuntu 12.04 64-bit (I am considering an upgrade, to quantal, raring or just keep using precise)
to install the mesa  9.0.2 with gallium I added the mesa9 and the optimized-drivers PPAs, probably it was a mistake to add the new ppa before removing the other one, now I have only the optim-drv one left.
the ppa:  oibaf / Updated and Optimized Graphics Drivers

---

### Post by schragge on 2013-02-10
Try to remove *libdrm-nouveau2* first

---

### Post by U202E on 2013-02-10
> **schragge said:**
> Try to remove *libdrm-nouveau2* first
I can't use dpkg...
do you think deleting this with nautilus will help?
/usr/share/x86_64-linux-gnu/libdrm_nouveau.so.2.0.0

^there is a libdrm_nouveau.so pointing at this file.

---

### Post by dino99 on 2013-02-10
sudo rm /var/cache/apt/archives/*

then try again

note: have you some ppa or extra repo activated ?

---

### Post by schragge on 2013-02-10
> **U202E said:**
> I can't use dpkg... Even with --force-* options? Something like
```
sudo dpkg --force-remove-reinstreq -r libdrm-nouveau2
```Or at least,
```

echo libdrm-nouveau2 deinstall|sudo dpkg --set-selections
sudo apt-get upgrade

```> **U202E said:**
> do you think deleting this with nautilus will help?
/usr/share/x86_64-linux-gnu/libdrm_nouveau.so.2.0.0

^there is a libdrm_nouveau.so pointing at this file.I wouldn't try it before all other options are exhausted.

---

### Post by U202E on 2013-02-10
> **dino99 said:**
> sudo rm /var/cache/apt/archives/*

^^thanks for your reply, but it just removes a cache file; It doesn't help.
(Rm gave me an error because it can't delete an folder)
the deb file looks good, I can just open it with archive manager and view it's content.

> note: have you some ppa or extra repo activated ?
as I mentioned before: yes, I added the optimized-drv and mesa9 ppa, then removed ppa:mesa9.

---

### Post by U202E on 2013-02-10
> **schragge said:**
> Even with --force-* options? Something like
```
sudo dpkg --force-remove-reinstreq -r libdrm-nouveau2
```Or at least,
```

echo libdrm-nouveau2 deinstall|sudo dpkg --set-selections
sudo apt-get upgrade

```I wouldn't try it before all other options are exhausted.
thanks for the options, I have tried all your commands and nothing helped.
when saying not able to use dpkg I meaned even with force...

and removing the /usr/lib...    well I tried it it: I didn't remove it but I just moved it to desktop, and because nothing happened I moved it back.

do you think upgrading to quantal will fix this? or will it make things worse?

---

### Post by schragge on 2013-02-10
What does *sudo dpkg -C* show?

---

### Post by U202E on 2013-02-10
> **schragge said:**
> What does *sudo dpkg -C* show?
It looks like at least someone can help me...

this is the result:
 ```
De volgende pakketten zijn uitgepakt maar nog niet geconfigureerd.  Ze
moeten geconfigureerd worden met dpkg --configure of de menu optie
Configureren in dselect om ze te laten werken:
 libosmesa6-dev       Mesa Off-screen rendering extension -- development files
 libgl1-mesa-dev      free implementation of the OpenGL API -- GLX development 
 mesa-common-dev      Developer documentation for Mesa
 libdrm-dev           Userspace interface to kernel DRM services -- development
```
in case you're not dutch, it says ' these packages are unpacked but not configured, they have to be configured with --configure'

---

### Post by schragge on 2013-02-10
First, try to configure them one by one
```

sudo dpkg --configure libosmesa6-dev
sudo dpkg --configure libgl1-mesa-dev
sudo dpkg --configure mesa-common-dev
sudo dpkg --configure libdrm-dev

```
Then look again at the output of 'sudo dpkg -C'

---

### Post by U202E on 2013-02-10
> **schragge said:**
> First, try to configure them one by one
```

sudo dpkg --configure libosmesa6-dev
sudo dpkg --configure libgl1-mesa-dev
sudo dpkg --configure mesa-common-dev
sudo dpkg --configure libdrm-dev

```Then look again at the output of 'sudo dpkg -C'

yeah, I can't configure them because dpkg says there are unmet dependencies.
:confused:, that didn't work.

it's like the chicken-and-egg -effect: because of the error I can't fix the error.

---

### Post by schragge on 2013-02-10
Ok, please post the output of
```

dpkg -l libdrm-nouveau2
apt-cache rdepends libdrm-nouveau2

```

---

### Post by U202E on 2013-02-10
> **schragge said:**
> Ok, please post the output of
```

dpkg -l libdrm-nouveau2
apt-cache rdepends libdrm-nouveau2

```
here you have it:
```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Naam           Versie         Omschrijving
+++-==============-==============-============================================
ri  libdrm-nouveau 2.4.39-0ubuntu Userspace interface to nouveau-specific kern

``````
apt-cache rdepends libdrm-nouveau2
libdrm-nouveau2
Reverse Depends:
  libdrm-nouveau2:i386
  libdrm-nouveau2:i386
  libdrm-nouveau2:i386
  libdrm-nouveau2:i386
  xserver-xorg-video-nouveau-lts-quantal
  libgl1-mesa-dri-lts-quantal
  libgbm1-lts-quantal
  libegl1-mesa-drivers-lts-quantal
  libdrm-nouveau2-dbg
  libdrm-dev
```
quite surpricing to me that it says   xserver....quantal, I am using precise.

---

### Post by schragge on 2013-02-10
Wait a minute, why do the packages from quantal show up in reverse dependencies of libdrm-nouveau2:
> **U202E said:**
> here you have it:
```

...
  xserver-xorg-video-nouveau-lts-quantal
  libgl1-mesa-dri-lts-quantal
  libgbm1-lts-quantal
  libegl1-mesa-drivers-lts-quantal
...

``` What repositories have been enabled in your */etc/apt/sources.list*? Please post the output of
```

grep '^[^#]' /etc/apt/sources.list

```

---

### Post by schragge on 2013-02-10
> **schragge said:**
> Wait a minute, why do the packages from quantal show up in reverse dependencies of libdrm-nouveau2Answering to myself: they are from precise-updates.

Ok, then try (you can hit <TAB> several times to complete the file name)
```

sudo apt-get -d upgrade libdrm-nouveau1a
dpkg --force-overwrite -i /var/cache/apt/archives/libdrm-nouveau1a_2.4.42+git1302070925.20c560~gd~p_amd64.deb
sudo apt-get -f upgrade

```

---

### Post by U202E on 2013-02-11
> **schragge said:**
> Wait a minute, why do the packages from quantal show up in reverse dependencies of libdrm-nouveau2:
 What repositories have been enabled in your */etc/apt/sources.list*? Please post the output of
```

grep '^[^#]' /etc/apt/sources.list

```
^^that surprised me as well.
```
:~$ grep '^[^#]' /etc/apt/sources.list
deb http://archive.ubuntu.com/ubuntu precise main restricted
deb-src http://archive.ubuntu.com/ubuntu precise main restricted
deb http://archive.ubuntu.com/ubuntu precise-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-updates main restricted
deb http://archive.ubuntu.com/ubuntu precise universe
deb-src http://archive.ubuntu.com/ubuntu precise universe
deb http://archive.ubuntu.com/ubuntu precise-updates universe
deb-src http://archive.ubuntu.com/ubuntu precise-updates universe
deb http://archive.ubuntu.com/ubuntu precise multiverse
deb-src http://archive.ubuntu.com/ubuntu precise multiverse
deb http://archive.ubuntu.com/ubuntu precise-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-updates multiverse
deb http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu precise-security main restricted
deb-src http://archive.ubuntu.com/ubuntu precise-security main restricted
deb http://archive.ubuntu.com/ubuntu precise-security universe
deb-src http://archive.ubuntu.com/ubuntu precise-security universe
deb http://archive.ubuntu.com/ubuntu precise-security multiverse
deb-src http://archive.ubuntu.com/ubuntu precise-security multiverse
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
deb http://archive.ubuntu.com/ubuntu precise-proposed restricted main multiverse universe
```
^^looks clear, no quantal. perhaps it's an error with a package: made for quantal but distributed as precise.

---

### Post by dino99 on 2013-02-11
> **U202E said:**
> 

as I mentioned before: yes, I added the optimized-drv and mesa9 ppa, then removed ppa:mesa9.

so ppa-purge might be your friend (if you use it about that other optimized-drv)

---

### Post by U202E on 2013-02-11
> **dino99 said:**
> so ppa-purge might be your friend (if you use it about that other optimized-drv)
it isn't, I considered it but then I thought "why install unnecessary packages?" add-apt-repository ppa:user:blahblah-ppah works just as well.

As far as I know ppa-purge can't fix this error.

---

### Post by schragge on 2013-02-11
> **U202E said:**
> ^^that surprised me as well. I've already found out, see [post=12502722]here[/post]. BTW, have you tried *dpkg --force-overwrite* as I suggested there?

---

### Post by U202E on 2013-02-11
> **schragge said:**
> I've already found out, see [post=12502722]here[/post]. BTW, have you tried *dpkg --force-overwrite* as I suggested there?
At least I have tried sudo dpkg --remove --force-remove-reinstreq.
ok lets copy that code into the teminal...
**[SIZE=3]thank you!!!!!![/SIZE]**

looks like the force-overwrite did help.
while typing this firefox says I have to restart my browser because there is an updated version->if firefox is updated apt works again!
the error box dissapeared.

all updates installed without any error, now it doesn't feel like windows anymore :D

---

