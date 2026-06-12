---
title: "How can I reinstall linux-image"
date: 2007-01-31
forum: Installation &amp; Upgrades
---

### Post by duns0014 on 2007-01-31
I need to reinstall the linux-image package so that I can get the ndiswrapper module in /lib/modules back on my machine, I deleted it kind of by accident.  However, when I looked at the install cd, I couldn't find the linux-image package, even though synaptic says it's installed.  How can I get it?

---

### Post by jpkotta on 2007-01-31
linux-image is a virtual package that points to the latest linux-image-<version> package, and this is the package that has ndiswrapper.ko.  

```
[jpkotta@galois ~](0)$ dpkg -S ndiswrapper
ndiswrapper-utils: /etc/ndiswrapper
ndiswrapper-utils: /usr/share/doc/ndiswrapper-utils/AUTHORS
ndiswrapper-utils: /usr/share/man/man8/ndiswrapper.8.gz
ndiswrapper-utils: /usr/share/doc/ndiswrapper-utils/copyright
ndiswrapper-utils: /usr/sbin/ndiswrapper-buginfo
ndiswrapper-utils: /usr/share/doc/ndiswrapper-utils/README.Debian
linux-image-2.6.15-26-server: /lib/modules/2.6.15-26-server/kernel/drivers/net/ndiswrapper
ndiswrapper-utils: /usr/share/doc/ndiswrapper-utils/changelog.Debian.gz
linux-image-2.6.15-27-server: /lib/modules/2.6.15-27-server/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
ndiswrapper-utils: /usr/share/doc/ndiswrapper-utils
ndiswrapper-utils: /usr/share/doc/ndiswrapper-utils/changelog.gz
ndiswrapper-utils: /usr/sbin/ndiswrapper
linux-image-2.6.15-27-server: /lib/modules/2.6.15-27-server/kernel/drivers/net/ndiswrapper
linux-image-2.6.15-26-server: /lib/modules/2.6.15-26-server/kernel/drivers/net/ndiswrapper/ndiswrapper.ko
ndiswrapper-utils: /usr/share/doc/ndiswrapper-utils/README

```

Try a reinstall of linux-image-<version>
```
sudo aptitude reinstall linux-image-2.6....
```
You can find the version you're currently running with ```
uname -a
```

---

### Post by duns0014 on 2007-01-31
Ok, but why isn't this on my install cd?  How could it have gotten installed?

---

### Post by az on 2007-01-31
> **duns0014 said:**
> Ok, but why isn't this on my install cd?  How could it have gotten installed?

Did you boot the cd or did you just look at the filesystem?  Because when you boot the cd, the installed system image gets mounted.  Otherwise, the whole thing is just one big file.

---

### Post by duns0014 on 2007-01-31
I looked at the filesystem.  I understand the basics of filesystems in unix, but didn't totally get what you're saying there.  I put the cd in, clicked on the icon on my desktop, and browsed the pool directory.  I also did a search for it and couldn't find it on the cd.

---

### Post by az on 2007-01-31
> **duns0014 said:**
> I looked at the filesystem.  I understand the basics of filesystems in unix, but didn't totally get what you're saying there.  I put the cd in, clicked on the icon on my desktop, and browsed the pool directory.  I also did a search for it and couldn't find it on the cd.

The live cd is not like the alternate cd.  The packages are not there as packages.  They are already installed in an image on the cd.  The small repository you are browsing from the live cd is there to provide a few tools (build-essential, linux-headers, etc) for people to compile extra driver once they have installed.

To browse the actual filesystem that you run when you run the live cd, you would have to mount the image (it's in the casper directory, filesystem.squashfs) as a loop filesystem.

---

### Post by duns0014 on 2007-01-31
Oh, thanks.  I'll try that.

---

### Post by **martha** on 2007-02-02
Look, I have lost my 3d acceleration by mistake (tried to install a dri driver :(  to improve the default acceleration given by ubuntu) and I think that reinstalling the linux-image package could recover that. Is that correct?

Moreover, if I do that, is there any risk to lose other configurations? I'm worried about the resolution (which I've solved with 915resolution package), the sound and the wireless (both were a little hard to configure and I wouldn't like to (mainly because I don't remember how to) reconfigure them).

Do I risk loosing any data?

Thanks a lot for any help.
M.

---

### Post by duns0014 on 2007-02-04
I fixed my problem.

Martha, I'm no expert but you may just have to redo the depmod -a and then modprobe <driver>.  If you actually deleted the file under /lib/modules, I'd try reinstalling linux-image.  If it's not the exact same version, you may have to copy it over to the version that matches your kernel.  You might lose some module settings, but probably not.

As an aside, where can I get more info on how linux loads modules, which modules it decides to load, and how I can customize this without reinstalling or compiling a kernel?  I've already read the modprobe and depmod man pages.

---

