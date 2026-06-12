---
title: "Lock Package Version in Kubuntu"
date: 2011-07-26
forum: Installation &amp; Upgrades
---

### Post by pcwiz11 on 2011-07-26
I am currently testing Kubuntu 10.04.3 LTS in Kubuntu using Wubi. I have heard that it's best to lock the 'grub-pc' and 'grub-common' packages to prevent them being updated when using Wubi as it can destroy the installation.

I managed to do this easily through Synaptic on normal Ubuntu but cannot find an option to do this in KPackageKit on Kubuntu. 

How can I lock the versions of these packages in KPackageKit?:confused:

---

### Post by Ichtyandr on 2011-07-27
I know it does not answer your question, but I just switched to Synaptic on Kubuntu and never looked back. there is no package manager comparable in features.

---

### Post by bcbc on 2011-07-27
> **pcwiz11 said:**
> I am currently testing Kubuntu 10.04.3 LTS in Kubuntu using Wubi. I have heard that it's best to lock the 'grub-pc' and 'grub-common' packages to prevent them being updated when using Wubi as it can destroy the installation.

I managed to do this easily through Synaptic on normal Ubuntu but cannot find an option to do this in KPackageKit on Kubuntu. 

How can I lock the versions of these packages in KPackageKit?:confused:

This is no longer necessary. The 10.04.3 update includes Wubi/Grub2 fixes that were developed prior to the Natty release. 

So the grub reboot and grub rescue prompt days of Wubi are a thing of the past...

FYI here's a way to lock packages from command line [http://ubuntuforums.org/showpost.php?p=10687475&postcount=373](http://ubuntuforums.org/showpost.php?p=10687475&postcount=373)

---

### Post by pcwiz11 on 2011-07-28
> **Ichtyandr said:**
> I know it does not answer your question, but I just switched to Synaptic on Kubuntu and never looked back. there is no package manager comparable in features.

Thanks for your help, Ichtyandr. I like Synaptic and think that I will do as you have and install it instead of KPackageKit.

---

### Post by pcwiz11 on 2011-07-28
> **bcbc said:**
> This is no longer necessary. The 10.04.3 update includes Wubi/Grub2 fixes that were developed prior to the Natty release. 

So the grub reboot and grub rescue prompt days of Wubi are a thing of the past...

FYI here's a way to lock packages from command line [http://ubuntuforums.org/showpost.php?p=10687475&postcount=373](http://ubuntuforums.org/showpost.php?p=10687475&postcount=373)

Thanks for your help bcbc. I didn't know that this is no longer necessary as of 10.04.3 LTS. Also thanks for the link to the method to lock packages via the terminal as I'm sure it will be useful at some stage.

---

### Post by pcwiz11 on 2011-07-28
> **bcbc said:**
> This is no longer necessary. The 10.04.3 update includes Wubi/Grub2 fixes that were developed prior to the Natty release. 

So the grub reboot and grub rescue prompt days of Wubi are a thing of the past...

FYI here's a way to lock packages from command line [http://ubuntuforums.org/showpost.php?p=10687475&postcount=373](http://ubuntuforums.org/showpost.php?p=10687475&postcount=373)

One more question, is it still necessary to lock 'grub-pc' and 'grub-common' in Ubuntu 10.10 and 11.04?

---

### Post by bcbc on 2011-07-28
> **pcwiz11 said:**
> One more question, is it still necessary to lock 'grub-pc' and 'grub-common' in Ubuntu 10.10 and 11.04?
No it's not necessary.

It's never been necessary in 11.04. In 10.10 it was only those who upgraded that were affected (or if you reinstalled grub or updated the wubildr). 10.10 was fixed in June: [https://launchpad.net/ubuntu/maverick/+source/grub2/1.98+20100804-5ubuntu3.3](https://launchpad.net/ubuntu/maverick/+source/grub2/1.98+20100804-5ubuntu3.3)

---

### Post by pcwiz11 on 2011-07-28
> **bcbc said:**
> No it's not necessary.

It's never been necessary in 11.04. In 10.10 it was only those who upgraded that were affected (or if you reinstalled grub or updated the wubildr). 10.10 was fixed in June: [https://launchpad.net/ubuntu/maverick/+source/grub2/1.98+20100804-5ubuntu3.3](https://launchpad.net/ubuntu/maverick/+source/grub2/1.98+20100804-5ubuntu3.3)

Excellent, thanks bcbc.

---

