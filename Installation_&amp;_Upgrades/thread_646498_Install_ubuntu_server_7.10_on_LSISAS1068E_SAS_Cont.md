---
title: "Install ubuntu server 7.10 on LSISAS1068E SAS Controller"
date: 2007-12-21
forum: Installation &amp; Upgrades
---

### Post by qiutian on 2007-12-21
Trying to setup a new web server with unbuntu 7.10 on a Supermicro X7DVL-3. This motherboard has a LSISAS1068E 8-port SAS RAID Controller.

I have got two 15k SAS hardisk established a raid 0 array, i now can see the new array is online, but  ubuntu cannot load the driver for it correctly.

I've tried to load megaraid megaraid_sas manually from the list but nothing happend.

Also read a lot posts from the forum, only this post which says someone made it work by downgrade their firmware to a lower version looks similar.

[http://ubuntuforums.org/showthread.php?t=437424&highlight=megaraid](http://ubuntuforums.org/showthread.php?t=437424&highlight=megaraid)

Anyone knows whether this also works in my case?

I went to the LSISA's website:
[http://www.lsi.com/storage_home/products_home/standard_product_ics/sas_ics/lsisas1068e/index.html?remote=1&locale=EN](http://www.lsi.com/storage_home/products_home/standard_product_ics/sas_ics/lsisas1068e/index.html?remote=1&locale=EN)

but cannot find any firmware from there?

Do those Suse and RH drivers on that page works for ubuntu? no?

Any help will be appreciated. :)

---

### Post by qiutian on 2007-12-21
any idea?

---

### Post by AndyVe on 2008-01-08
rick @ Linux Mafia [suggests]("http://linuxmafia.com/faq/Hardware/sas.html") mptsas

I can't get it to run though on my 8204XLP card.

---

### Post by buihuy on 2008-01-12
Any luck with this?  I have the same supermicro mobo and I've tried many diff linux distros.

---

### Post by KotZer on 2008-01-14
Hello all.. I have the same problem..
The right module for this card is **megasr** and unfortunately a part of it is proprietary. In the LSI driver page they give away this compiled module that is available only for suse and RHEL... Unfortunately any debian-based distro cannot run this module..

However, gentoo wiki has a guide for the compilation of this drive in any kernel..
[http://gentoo-wiki.com/HARDWARE_LSI_8208ELP_RAID5_Controller](http://gentoo-wiki.com/HARDWARE_LSI_8208ELP_RAID5_Controller)

It seems that it is working with linux kernels 2.6.19 and below, so it is not appropriate for gutsy.. 

I wasn't able to make it work on the installation phase of gutsy server cd... Debian has the same problem..


I will try to boot with dapper live cd compile it from there , and then start the installation probing the compiled module (megasr.ko)..

Has anyone tried this ? Damn, why do they make it so difficult with those closed-sources drivers?

---

### Post by qiutian on 2008-01-15
> **KotZer said:**
> Hello all.. I have the same problem..
The right module for this card is **megasr** and unfortunately a part of it is proprietary. In the LSI driver page they give away this compiled module that is available only for suse and RHEL... Unfortunately any debian-based distro cannot run this module..

However, gentoo wiki has a guide for the compilation of this drive in any kernel..
[http://gentoo-wiki.com/HARDWARE_LSI_8208ELP_RAID5_Controller](http://gentoo-wiki.com/HARDWARE_LSI_8208ELP_RAID5_Controller)

It seems that it is working with linux kernels 2.6.19 and below, so it is not appropriate for gutsy.. 

I wasn't able to make it work on the installation phase of gutsy server cd... Debian has the same problem..


I will try to boot with dapper live cd compile it from there , and then start the installation probing the compiled module (megasr.ko)..

Has anyone tried this ? Damn, why do they make it so difficult with those closed-sources drivers?

any luck by doing this?

Does that means i am able to compile the driver into the kernal accroding to gentoo's guide if i run it from Ubuntu 6.06 LTS CD?

---

### Post by KotZer on 2008-01-29
> **qiutian said:**
> any luck by doing this?

Does that means i am able to compile the driver into the kernal accroding to gentoo's guide if i run it from Ubuntu 6.06 LTS CD?

Theoretically yes, if you have the same version of kernel, bit i didnt have the time to try it..

Instead, I managed to install CentOS using the provided drivers disk without any problem.. It is not what i wanted (i hate rpm) but this is the curse of linux distros and new hardware (with closed drivers :mad:)

---

### Post by tjdub on 2008-03-20
I was able to get this piece of crap controller to work with 6.06.2 LTS:

[http://tjw.org/ubuntu-megasr/](http://tjw.org/ubuntu-megasr/)

---

