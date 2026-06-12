---
title: "Where can I find and install remastersys?"
date: 2008-08-29
forum: Installation &amp; Upgrades
---

### Post by colobix on 2008-08-29
HI. where do I install remastersys from?
I found an archive file but that doesn't help me much when I dont know where to place the files so I need a deb file or terminal code please.
Thank you:)

---

### Post by VMC on 2008-08-29
Synaptic Pacjage Manager, then do a search for 'remastersys". Or open Terminal and type:
```
apt-get install remastersys
```

Edit:I think the above is what your asking. Or do you have a remastered cdrom disk and don't know how to use it?

---

### Post by linux_tech on 2008-08-30
Download and install the latest version of Remastersys from: [http://remastersys.klikit-linux.com/repository/remastersys](http://remastersys.klikit-linux.com/repository/remastersys)
other programs to create a customized Live CD/DVD of Ubuntu (a remaster), such as remastersys, the Ubuntu Customization Kit and Reconstructor

---

### Post by danlaptic on 2010-09-28
> **linux_tech said:**
> Download and install the latest version of Remastersys from: [http://remastersys.klikit-linux.com/repository/remastersys](http://remastersys.klikit-linux.com/repository/remastersys)
other programs to create a customized Live CD/DVD of Ubuntu (a remaster), such as remastersys, the Ubuntu Customization Kit and Reconstructor

The above link is now dead.  A recent lifehacker article found here:

[http://lifehacker.com/5645072/make-your-own-customized-ubuntu-live-cd-or-usb-drive](http://lifehacker.com/5645072/make-your-own-customized-ubuntu-live-cd-or-usb-drive)

Gives directions for installing on newer Ubuntu releases (I'm running 10.04) but step 2 causes step 3 to return the following error:

E: Malformed line 55 in source list /etc/apt/sources.list (dist)

I'm interested in using this software but can't find installation documentation on the developers website([http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)), and other documentation seems to be out of date.

*EDIT*
Please see related thread:
[http://ubuntuforums.org/showthread.php?t=1578881](http://ubuntuforums.org/showthread.php?t=1578881)

Add this line to /etc/apt/sources.list For Karmic, Lucid and Newer with grub2 - version 2.0.13-1 and up:

# Remastersys
deb [http://www.geekconnection.org/remastersys/repository](http://www.geekconnection.org/remastersys/repository) karmic/

---

