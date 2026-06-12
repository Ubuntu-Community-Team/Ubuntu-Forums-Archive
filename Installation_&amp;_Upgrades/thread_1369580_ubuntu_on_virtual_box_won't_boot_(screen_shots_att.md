---
title: "ubuntu on virtual box won't boot (screen shots attached)"
date: 2010-01-01
forum: Installation &amp; Upgrades
---

### Post by new lin on 2010-01-01
Aftre upgading VirtualBox to 3.1.2 I faced this problem and ubuntu will not boot 
 
what is the prolem & how to resolve my system

---

### Post by gsmanners on 2010-01-01
Some kind of weird new bug? Anyway, if that was a real system you could just recover grub's config with a live CD. If you still have the live CD around or an image of it, you could try that:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by new lin on 2010-01-01
Thanks for your reply 

What do you mean by real system ?

It's a single OS on a virtual machine (Sun Virtual Box running within MS Vista)

---

### Post by gsmanners on 2010-01-02
*If* it was a real system. Since it's a virtual system, you'll need to mount the Live CD using VirtualBox's configuration, but otherwise it's the same idea.

---

### Post by new lin on 2010-01-03
Thanks again
 
I did, but mount command asks about file system!

---

### Post by CharlesA on 2010-01-03
> **new lin said:**
> Thanks again
 
I did, but mount command asks about file system!

If the ISO is mounted in VirtualBox, then it should behave exactly like a cd in a cdrom. Being mounted at /media/cdrom.

---

### Post by new lin on 2010-01-03
> **CharlesA said:**
> If the ISO is mounted in VirtualBox, then it should behave exactly like a cd in a cdrom. Being mounted at /media/cdrom.
 
 
that.s right !
 
but trying to execute commands adviced to resolve the problem by mounting the root mount asks for file system 
 
I tried to execute this :
 
mount /dev/sda1 /media/root!

---

