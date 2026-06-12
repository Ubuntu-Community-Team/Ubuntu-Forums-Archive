---
title: "How to install aMule on Ubuntu 20.04"
date: 2020-04-26
forum: Installation &amp; Upgrades
---

### Post by astermask on 2020-04-26
How to install aMule on Ubuntu 20.04

As people already know, aMule is no longer supported in the official Ubuntu repositories since version 20.04 LTS.
However it is possible to install aMule MANUALLY in a very simple way !! :D
aMule needs a few libraries that can be easily installed with APT. For the rest, just download the appropriate .deb files and you're done.

Here is a simple detailed guide:

[LIST=1]
[*]Download from this site [https://packages.ubuntu.com/bionic/amd64/libwxgtk3.0-0v5/download](https://packages.ubuntu.com/bionic/amd64/libwxgtk3.0-0v5/download)
this library:
[B]libwxgtk3.0-0v5_3.0.4+dfsg-12_amd64.deb

[/B]
[*]Download from [http://archive.ubuntu.com/ubuntu/pool/universe/a/amule/](http://archive.ubuntu.com/ubuntu/pool/universe/a/amule/)
these DEB files:
[B]amule_2.3.2-6_amd64.deb
amule-common_2.3.2-6_all.deb
amule-utils_2.3.2-6_amd64.deb[/B]

If necessary, according to your needs, also download one or more of the following optional packages:
[B]amule-daemon_2.3.2-6_amd64.deb
amule-gnome-support_2.3.2-6_all.deb
amule-utils-gui_2.3.2-6_amd64.deb

[/B]
[*]Go to the download folder and run the following commands to install the necessary libraries and DEB files:
(To avoid missing dependency errors, do it in the following order)
```
sudo apt install -y libboost-system1.67.0 libcrypto++6 libwxbase3.0-0v5 libgeoip1 libupnp13
sudo dpkg -i libwxgtk3.0-0v5_3.0.4+dfsg-12_amd64.deb
sudo dpkg -i amule-common_2.3.2-6_all.deb
sudo dpkg -i amule_2.3.2-6_amd64.deb
sudo dpkg -i amule-utils_2.3.2-6_amd64.deb
```
[*]Similarly, optional packages can be installed with dpkg.

I hope I helped you.  ):P
[/LIST]

Notes:
September 30th, 2020 - Updated the link to download libwxgtk3.0-0v5 library

---

### Post by dardiv92 on 2020-04-29
I still use amule a lot and i was disappointed when I couldn't find it in the software center. Thank you so much, this guide is very useful. :p

---

### Post by stuarte83 on 2020-09-29
Hi astermask,

I tried following your guide to installing aMule on Ubuntu 20.04 but failed at the first "hurdle". (I am using Kubuntu 20.04.1, continuously updated.) When I tried to use the first link th you supplied, i.e. [https://packages.ubuntu.com/eoan/amd64/libwxgtk3.0-0v5/download](https://packages.ubuntu.com/eoan/amd64/libwxgtk3.0-0v5/download)  the Ubuntu packages site responded with the following :-

    [h=1]Error[/h]  two or more packages specified (libwxgtk3.0-0v5 eoan)
 


My question is, is there another way to get the libwxgtk3.0-0v5 eoan package without using the first link that you have supplied ?

I have successfully downloaded the following from the second link that you supplied.
[B]amule_2.3.2-6_amd64.deb
amule-common_2.3.2-6_all.deb
amule-utils_2.3.2-6_amd64.deb
[/B]
**[B]amule-daemon_2.3.2-6_amd64.deb**[/B]
[B][B][B]amule-utils-gui_2.3.2-6_amd64.deb

I have not yet actioned the instructions that you supplied in the code box.

Best regards,

Stuart

[/B][/B][/B]

---

### Post by astermask on 2020-09-30
> **stuarte83 said:**
> Hi astermask,

I tried following your guide to installing aMule on Ubuntu 20.04 but failed at the first "hurdle". (I am using Kubuntu 20.04.1, continuously updated.) When I tried to use the first link th you supplied, i.e. [https://packages.ubuntu.com/eoan/amd64/libwxgtk3.0-0v5/download](https://packages.ubuntu.com/eoan/amd64/libwxgtk3.0-0v5/download)  the Ubuntu packages site responded with the following :-

I just updated the link! :D  Now it's all ok.

---

### Post by stuarte83 on 2020-10-03
Hi astermask,

Thank you for updating the link.

Best regards,

Stuart

---

### Post by ActionParsnip on 2020-10-03
aMule hasn't been updated in 4 years. I don't suggest you use it and use something that is actually maintained. I suspect the software will be full of new security issues and bugs that won't be resolved

---

### Post by astermask on 2020-10-19
> **ActionParsnip said:**
> aMule hasn't been updated in 4 years. I don't suggest you use it and use something that is actually maintained. I suspect the software will be full of new security issues and bugs that won't be resolved
aMule is supported again by the OFFICIAL repositories of ubuntu 20.10!
In Ubuntu 20.10 you can install amule simply with: 
```
sudo apt install amule
```
This guide is still useful for anyone who wants to install aMule on Ubuntu 20.04 LTS  ;)

---

### Post by jatauli on 2021-06-26
The "2.3.2-6" files are not there anymore. Will it work the same with the "2.3.2-2" files? or "2.3.3-1"?
I'm still using ubuntu 20.04 and I don't feel like messing it up again, it's been a rough week.
Thanks

---

### Post by hajuestark on 2021-07-11
> **jatauli said:**
> The "2.3.2-6" files are not there anymore. Will it work the same with the "2.3.2-2" files? or "2.3.3-1"?
I'm still using ubuntu 20.04 and I don't feel like messing it up again, it's been a rough week.
Thanks

Had the same Problem. I have just upgraded a Ubuntu 19.10 Installation to Ubuntu 20.04LTS and wanted to install amule -- but I wondered -- there where no packets for it. 
I have tried to install amule with the updated 'astermask' links, but had errors with unmatched dependencies and had to deinstall the hole amule packets. "2.3.3-1" packets did not work for me. :(
But now I tried the other tip from this forum:[ UBUNTU 20.04 HOW CAN I INSTALL aMULE??]("https://ubuntuforums.org/showthread.php?t=2458778")
[**[COLOR=#000000]CelticWarrior[/COLOR]**]("https://ubuntuforums.org/member.php?u=1826209") gave a link to a [Spanish tutorial]("https://www.muylinux.com/2020/12/02/amule-ubuntu-20-04-lts/") which suggest to install the amule packets of Ubuntu 20.10. And I succeeded with this advice. [SIZE=2]:popcorn:[/SIZE]

---

