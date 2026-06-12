---
title: "PXE Install says &quot;No CD-ROM Found&quot;"
date: 2011-09-06
forum: Installation &amp; Upgrades
---

### Post by wiz561 on 2011-09-06
Hi,

I'm setting up a PXE install server on a NFS share.  I took the server ISO and used it in the instructions here...

[https://help.ubuntu.com/community/PXEInstallMultiDistro](https://help.ubuntu.com/community/PXEInstallMultiDistro)

It's booting up fine and finding all the files.  I'm getting stuck on the point where it says "Detect and mount CD-ROM".  I'm sure it's just a simple stanza option you have to add, but I can't seem to get past this point.  

If anybody has any suggestions, I'd greatly appreciate it!

---

### Post by haqking on 2011-09-06
> **wiz561 said:**
> Hi,

I'm setting up a PXE install server on a NFS share.  I took the server ISO and used it in the instructions here...

[https://help.ubuntu.com/community/PXEInstallMultiDistro](https://help.ubuntu.com/community/PXEInstallMultiDistro)

It's booting up fine and finding all the files.  I'm getting stuck on the point where it says "Detect and mount CD-ROM".  I'm sure it's just a simple stanza option you have to add, but I can't seem to get past this point.  

If anybody has any suggestions, I'd greatly appreciate it!


mount it manually [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

usually

*sudo mount /media/cdrom0/*

or whatever the name or location of device is

---

### Post by wiz561 on 2011-09-06
Thanks for the response.

This message always happens when I try to do an install off a usb stick.  Usually how I solve it is copy the ISO to the stick and mount it as /media/cdrom, then point the installation to the CD-ROM ISO.

I'm guessing there's a better way to do this, so that it will automatically move on.  I was hoping for a better solution, but mounting the ISO will work...

Thanks!

---

