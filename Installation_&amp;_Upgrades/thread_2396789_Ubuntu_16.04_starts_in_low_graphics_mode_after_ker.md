---
title: "Ubuntu 16.04 starts in low graphics mode after kernel upgrade to 4.17.x"
date: 2018-07-20
forum: Installation &amp; Upgrades
---

### Post by atom-101 on 2018-07-20
I have just upgraded my PC build to coffee lake with an i7 8700k. I installed Ubuntu 16.04 from my live pen drive that has been around for quite a while.  The kernel version installed was 4.4.130. Everything was fully functional,  except not having any sound. 
I figured it would be some driver problem due to how old the kernel is, so I upgraded to 4.17.8. The upgrade gave some Intel graphic driver missing errors.  I downloaded the required binaries from their site(all the missing bins were skylake, kabylake or broxton, nothing related to coffee lake) 
Next I had to install libssl 1.1.0 which was not natively available for 16.04. After finally completing the installation of 4.17.8 I rebooted only to be greeted by a black screen with a message saying, system started in low graphics mode and that I would have to manually configure graphics drivers. 
I still had my 4.4 kernel which boots just fine. I used it to remove 4.17.8 and installed 4.17.0 in hopes that it would be more stable and not as much bleeding edge as 4.17.8, but nothing changed. 
Please guide me to correctly set up Intel UHD 630 graphics for kernel version 4.17.x

---

### Post by Impavidus on 2018-07-20
It would be much easier to try 4.15 first, as that's officially supported by Ubuntu. Just install the HWE stack: [https://wiki.ubuntu.com/Kernel/LTSEnablementStack](https://wiki.ubuntu.com/Kernel/LTSEnablementStack)

Alternatively, as you mention this is a fresh install, why not try 18.04? It also comes with 4.15.

---

### Post by atom-101 on 2018-07-21
Thanks. That worked and as expected, I now have sound over hdmi. As for 18.04, I thought I would install from what I already have(that is 16.04) and do a dist-upgrade. 
So here comes the next problem that I am having. Trying to do a dist upgrade gives me unmet dependencies in the following packages
```

The following packages have unmet dependencies:
 fontconfig : Depends: fontconfig-config but it is not going to be installed
 libfontconfig1 : Depends: fontconfig-config (= 2.11.94-0ubuntu1.1) but it is not going to be installed
 libgtk2.0-0 : Depends: libcairo2 (>= 1.6.4-6.1) but it is not going to be installed
               Depends: libpangocairo-1.0-0 (>= 1.28.3) but it is not going to be installed
               Depends: libpangoft2-1.0-0 (>= 1.28.3) but it is not going to be installed
               Recommends: libgtk2.0-bin
 libsm6 : Depends: libuuid1 (>= 2.16) but it is not going to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

```

On trying to install the unmet dependencies, I get the following  
```

fontconfig-config is already the newest version (2.11.94-0ubuntu1.1).
fontconfig-config set to manually installed.

```
```

libcairo2 is already the newest version (1.14.6-1).
libcairo2 set to manually installed.

```
```
ibpangocairo-1.0-0 is already the newest version (1.38.1-1).
libpangocairo-1.0-0 set to manually installed. 
```
```
libpangoft2-1.0-0 is already the newest version (1.38.1-1).
libpangoft2-1.0-0 set to manually installed.
```
```
libuuid1 is already the newest version (2.27.1-6ubuntu3.4).
```

As you can see, all requirements are satisfied, so why do I get unmet dependencies?

PS: Ubuntu software updater is now notifying me that Linux version 4.17.8 is available and is asking me to upgrade. If it is not officially supported, then why am I being asked to upgrade to it?

---

### Post by Impavidus on 2018-07-21
If you want 18.04, install 18.04. Don't install 16.04 followed by an upgrade to 18.04, as the upgrade takes a long time and may go wrong. I always had success with release upgrades, but that's not the case for everyone. If you've nothing to lose, fresh installs are much better.

You probably use some non-official repositories that provide kernel 4.17 and may cause other problems. You can try to disable non-official repositories and fix the package manager with```
sudo apt install -f
```and hope it works.

Or you can download the 18.04 installer and get a clean 18.04 system in less than an hour. You initial attempts to solve your problem may have done more harm than good. Without understanding what you did exactly, it may be hard to clean up.

---

### Post by atom-101 on 2018-07-22
That didn't work. 
I got myself 18.04 using an ISO. It works fine now. Thanks for all your help.

---

