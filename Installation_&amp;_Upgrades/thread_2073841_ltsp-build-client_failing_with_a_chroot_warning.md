---
title: "ltsp-build-client failing with a chroot warning"
date: 2012-10-20
forum: Installation &amp; Upgrades
---

### Post by pullipuli on 2012-10-20
Hi,

I am trying to build an edubuntu fat client(i386) from a 12.04 64bit. I am using a mirror because the internet repositories are failing.

```
> sudo ltsp-build-client --fat-client --fat-client-desktop edubuntu-desktop --arch i386 --skipimage --mirror file:///media/iso --accept-unsigned-packages
I: Retrieving Release
I: Retrieving Release.gpg
I: Checking Release signature
I: Valid Release signature (key id C5986B4F1257FFA86632CBA746181433FBB75451)
I: Retrieving Packages
I: Validating Packages
I: Resolving dependencies of required packages...
I: Resolving dependencies of base packages...
I: Chosen extractor for .deb packages: dpkg-deb
W: Failure trying to run: chroot /opt/ltsp/i386 mount -t proc proc /proc
error: LTSP client installation ended abnormally
>

```


and :confused:
```

> ls -l /opt/ltsp/i386/
drwxr-xr-x 2 root root 4096 Oct 20 22:41 debootstrap
drwxr-xr-x 2 root root 4096 May  2 16:45 dev
drwxr-xr-x 3 root root 4096 Oct 20 22:41 etc
drwxr-xr-x 4 root root 4096 Oct 20 22:41 var

```


- Thanks.

---

### Post by pullipuli on 2012-10-20
Hi,

 I tried updating --mirror and --extra-mirror with some good mirrors from ubuntu.com, but it only eats all bandwidth and dies after a long series of GET, saying different reasons "Unable to get package", "Unable to verify", "Hash Sum mismatch" etc.. 

Is there any option to restart the build process from where it failed? instead of restarting the whole thing over and over again?

the build is not starting second time unless you remove the ltsp folder, which contains the whole download !!


Thanks.

---

