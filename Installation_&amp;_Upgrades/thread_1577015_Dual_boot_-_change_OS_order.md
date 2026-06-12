---
title: "Dual boot - change OS order"
date: 2010-09-18
forum: Installation &amp; Upgrades
---

### Post by eXtremer on 2010-09-18
Hi all.
I have two questions:

1. I had Win XP, I've installed Ubuntu on another Partition, now Ubuntu starts first, can I change XP to be the first one to load ? And how to do it ?

2. When I have to choose from 2 installed systems on the screen I see, Ubuntu, Testmem and Windows XP, can I rename Windows XP title to something else ? And how to do it ?

Thank you in advance.

---

### Post by Rubi1200 on 2010-09-18
See here for details:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Sections 5, 6, and possibly 7 are the most relevant.

---

### Post by efflandt on 2010-09-18
One of the simplest things you can do to default to whichever was booted last, and assuming a new enough Ubuntu with grub2, is to edit /etc/default/grub.

Change GRUB_DEFAULT=0 to GRUB_DEFAULT=saved, and add GRUB_SAVEDEFAULT=true

Those settings are slightly different to always default to the same specific entry.  See [https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202")

If you actually want to change the order of menu entries, then you need to look at /etc/grub.d/.  I have not tampered with that other than grub menu colors.

---

### Post by eXtremer on 2010-09-20
> **efflandt said:**
> One of the simplest things you can do to default to whichever was booted last, and assuming a new enough Ubuntu with grub2, is to edit /etc/default/grub.

Change GRUB_DEFAULT=0 to GRUB_DEFAULT=saved, and add GRUB_SAVEDEFAULT=true

Those settings are slightly different to always default to the same specific entry.  See [https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202](https://help.ubuntu.com/community/Grub2#Configuring%20GRUB%202)

If you actually want to change the order of menu entries, then you need to look at /etc/grub.d/.  I have not tampered with that other than grub menu colors.

I cannot save GRUB file I think it's the same thing as the boot.ini in Windows you wont be able to save because the file is "active" - in use, then how to save it ?

---

### Post by dirghrabadia on 2010-09-20
This might be of some help:
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602) :)

---

### Post by wilee-nilee on 2010-09-20
What is the Ubuntu install distro, I'm curious if it's grub-legacy or grub2 we are dealing with.

---

### Post by dirghrabadia on 2010-09-20
> **wilee-nilee said:**
> What is the Ubuntu install distro, I'm curious if it's grub-legacy or grub2 we are dealing with.

+1. 

I didn't realize that OP hadn't mentioned that.

---

### Post by karthick87 on 2010-09-20
I am using grub2,so how can i change the boot order..?

---

### Post by wilee-nilee on 2010-09-20
> **dirghrabadia said:**
> +1. 

I didn't realize that OP hadn't mentioned that.

It is easy to miss that and wubi installs and other nice holes to fall in.;)

---

### Post by eXtremer on 2010-09-20
> **wilee-nilee said:**
> What is the Ubuntu install distro, I'm  curious if it's grub-legacy or grub2 we are dealing with.

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

---

### Post by wilee-nilee on 2010-09-20
> **eXtremer said:**
> DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

You can modify the grub file as described, or just install startup manager it will let you set the default boot, and the time out. Be careful to leave that time out above 0, as you never know when you might want to bet into the recovery in Ubuntu.

---

### Post by eXtremer on 2010-09-20
> **wilee-nilee said:**
> You can modify the grub file as described, or just install startup manager it will let you set the default boot, and the time out. Be careful to leave that time out above 0, as you never know when you might want to bet into the recovery in Ubuntu.

Thanks wilee-nilee ;)

---

