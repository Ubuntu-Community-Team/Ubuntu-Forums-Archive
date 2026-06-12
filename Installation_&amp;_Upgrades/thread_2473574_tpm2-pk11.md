---
title: "tpm2-pk11?"
date: 2022-04-07
forum: Installation &amp; Upgrades
---

### Post by tmcca on 2022-04-07
I cant find where to install this package? So I can use SSH keys with TPM?

tpm2_ptool init is what I need?

Anyone?

---

### Post by oldos2er on 2022-04-07
Which version of Ubuntu? On jammy the package name is simple-tpm-pk11, in the universe repository.

---

### Post by tmcca on 2022-04-07
It looks like I have focal when I ran lsb_release -a codename is focal

simple-tpm is for tpm 1.0? isn't it? I need tpm2.0 which I thought was[COLOR=#3D596E][FONT=SFMono-Regular] libtpm2-pkcs11-1[/FONT][/COLOR]

Trousers is for sure for TPM1. I have TPM version 2

---

### Post by oldos2er on 2022-04-07
Here are all the tpm2 packages for focal: [https://packages.ubuntu.com/search?keywords=tpm2&searchon=names&suite=focal&section=all](https://packages.ubuntu.com/search?keywords=tpm2&searchon=names&suite=focal&section=all)
Not sure which one, if any, are what you need. 

> simple-tpm is for tpm 1.0? Yes I believe so.

---

### Post by tmcca on 2022-04-07
I think need to update distro to Jammy

---

### Post by oldos2er on 2022-04-07
I don't recommend doing that unless you're willing to beta test.

---

### Post by tmcca on 2022-04-07
[https://packages.ubuntu.com/search?suite=jammy&searchon=names&keywords=tpm2](https://packages.ubuntu.com/search?suite=jammy&searchon=names&keywords=tpm2)

I need the package[h=3]Package libtpm2-pkcs11-1[/h]
This is not in focal correct? Is there way to just add that package?

---

### Post by oldos2er on 2022-04-07
There's not really a supported way to do that that I'm aware of.

---

