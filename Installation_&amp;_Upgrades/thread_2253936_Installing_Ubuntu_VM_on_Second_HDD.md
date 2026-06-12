---
title: "Installing Ubuntu VM on Second HDD"
date: 2014-11-23
forum: Installation &amp; Upgrades
---

### Post by rookieTest on 2014-11-23
Hi,

I have Ubuntu running using VMWare on my primary drive(SSD (Windows 8.1 is installed on this drive)), however as this drive is 500GB i'd prefer to have Ubuntu running on my second drive (HDD) which is 1TB.

What I want to know is would it be OK to install a Ubunutu VM on my second drive (HDD) without affecting booting to windows. I went to install Kali Linux on my second drive (HDD) in VMWare and due to it being the only OS on this disk I got a message saying that "no other OS was detected, if another OS exists this may cause problems with booting" (or something along those lines).

OK while writing this I just realized that obviously no other OS was detected because no other OS is on my secondary drive (HDD). But still the question tremains will having this Ubuntu VM on my HDD cause any issues with booting into the original OS (Windows). I just wanted an experienced answer before dabbling in anything to avoid problems.

Thanks :)

---

### Post by bashiergui on 2014-11-23
When you install operating systems inside VirtualBox, it is totally different than dual booting. The virtual machines will never compete with or replace your host operating system. 

You can have the VM on the second drive. That will work fine.

---

### Post by rookieTest on 2014-11-23
Perfect, thanks for your direct & quick reply :)

---

