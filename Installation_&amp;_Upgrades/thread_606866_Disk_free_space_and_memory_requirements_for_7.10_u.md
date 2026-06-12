---
title: "Disk free space and memory requirements for 7.10 upgrade"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by mxg01 on 2007-11-08
I've not been able to find anything about what's required. 

I plan to do an online upgrade as I can't burn CDs. I understand the disk space requirement is variable and depends on what's installed. Is there anyway to do a rough calculation or does the install process tell me if I have enough space?

Will 256MB be enough memory?

Thanks in advance.

---

### Post by aysiu on 2007-11-08
If you already have 7.04 installed, upgrading to 7.10 will probably not take up any more space. And if 256 MB of RAM was enough for 7.04, it'll also be enough for 7.10.

---

### Post by mxg01 on 2007-11-08
Thanks for the reply. I was worried about the number of packages that require downloading as it downloads them all then installs. Maybe I'm just being over cautious but if I break the computer my wife will be cross with me. Experience tells me to avoid that.

---

### Post by atlfalcons866 on 2007-11-08
gutsy requires 320MB

---

### Post by aysiu on 2007-11-08
Well how much free space do you have? I think you should have at least 1 GB of free space just in case.

You may want to do a ```
sudo apt-get clean
``` before doing the upgrade, too.

---

### Post by aysiu on 2007-11-08
> **atlfalcons866 said:**
> gutsy requires 320MB
320 MB more space than Feisty? That may be the case. I don't know.

or 320 MB of RAM? Definitely not the case. For a month, I was running Gutsy just fine on my laptop with 256 MB of RAM.

---

### Post by atlfalcons866 on 2007-11-08
[http://cdimage.ubuntu.com/daily/20071016.1/](http://cdimage.ubuntu.com/daily/20071016.1/)

is says right there. Maybe its just for the live cd

---

### Post by mxg01 on 2007-11-08
I have around 700MB free on / at the moment. /home is on another partition. I'll do a clean later and see what happens. I'd thought that should be enough for new and upgraded packages plus some working space.

Thanks.

---

### Post by aysiu on 2007-11-08
> **atlfalcons866 said:**
> [http://cdimage.ubuntu.com/daily/20071016.1/](http://cdimage.ubuntu.com/daily/20071016.1/)

is says right there. Maybe its just for the live cd
[quote=the page you linked to]**Alternate install CD**

The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * creating pre-configured OEM systems;
    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installs on systems with **less than about 320MB of RAM** (although note that low-memory systems may not be able to run a full desktop environment reasonably). [/quote] You linked to the Alternate CD, which is not the live CD, and that works well for systems with *less* than 320 MB of RAM. So 320 MB of RAM is not a minimum requirement.

---

