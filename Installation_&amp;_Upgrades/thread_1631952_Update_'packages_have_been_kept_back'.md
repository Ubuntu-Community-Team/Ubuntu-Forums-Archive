---
title: "Update 'packages have been kept back'?"
date: 2010-11-27
forum: Installation &amp; Upgrades
---

### Post by candtalan on 2010-11-27
I have ubuntu 10.10 on an old dell inspiron 2500 laptop, 384MB ram,  13.9GBfree disc space apparently. The Update Manager gui shows 8 updates available, but when told to install updates, just blinks, and still awaits instruction. CL sudo apt-get update then sudo apt-get upgrade do sensible activity however, it ends with the following:

The following packages have been kept back:
  evolution-plugins linux-generic linux-headers-generic linux-image-generic

Which I do not understand. just previously I installed many updates using the CL method ok (although the gui was still not functional).

There does seem to be trouble with the gpg key for extras packages and the following seemed to sort that out
```

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
gpg: requesting key 02FDF932 from hkp server keyserver.ubuntu.com
gpg: key 02FDF932: public key "Launchpad Application Review Board PPA" imported
gpg: Total number processed: 1
gpg:               imported: 1  (RSA: 1)


```

I am out of my depth, in case it is not apparent.... and I would like to get it working.

Incidentally, the laptop was installed without a functional Internet connection from a damaged socket, though this is now fixed and working.

Any ideas please?  tia

edit:
I have just attempted to use Software Centre to install gparted, and the install 'click'  does not result in any apparent action - such as gui request for password. However, synaptic works ok and I installed gparted.

---

### Post by dino99 on 2010-11-27
in such case i first try to clean the system and maybe make room (bleachbit)

---

### Post by candtalan on 2010-11-27
> **dino99 said:**
> in such case i first try to clean the system and maybe make room (bleachbit)
Thanks, but I have do have 13GB space on the drive, it is a single partition installation. Do you mean to make space?

---

