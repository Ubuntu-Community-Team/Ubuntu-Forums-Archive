---
title: "bad MD5Sum - cant smart upgrade."
date: 2005-07-13
forum: Installation &amp; Upgrades
---

### Post by pabc on 2005-07-13
I'm trying to upgrade firefox from 1.0.2 to 1.04 using synaptic and as a result it appears I need to install libcairo1(0.3.0-1) amoungst other things but I continually get a bad MD5Sum and the option to continue regardless which I don't.

'Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/libc/libcairo/libcairo1_0.3.0-1_i386.deb)  MD5Sum mismatch'

I've cleared my cache and retried but still a bad download. 

I've also tried to 'apt-get install libcairo1' but still no the MD5Sum error.

I've had a look and can find the 0.4.0-1 deb on the web. should I just put that on and hope Synaptic realises a new version is already installed? or should I just ignore that package in Synaptic. Better yet, where can I find older .debs then I can figure out how to install the .deb and rerun the synaptic smart upgrade.

Any help would be appreciated. This all feels so different as my only experience of linux before yesterday was a few weeks on KDE/FC3.

P

---

### Post by Leif on 2005-07-13
The us site is having problems. Replace us.archive's in your sources with just archive for the moment.

---

### Post by pabc on 2005-07-13
[QUOTE=Leif]The us site is having problems. Replace us.archive's in your sources with just archive for the moment.[/QUOTE]

Thanks. I had considered that. I had a lot of problems with yum when dags repo went nutty.

For info, I have now found the libcairo1_0.3.0-1_i386.deb.
Could I have done;
[COLOR=Blue]ipkg install libcairo1_0.3.0-1_i386.deb[/COLOR]
then done a synaptic smart install.?

What I'm really asking is does synaptic detect packages installed by ipkg and/or apt-get?

P

---

### Post by Leif on 2005-07-13
Yes, things installed using dpkg and apt-get will show up in synaptic (I believe synaptic is an apt-get frontend itself), and will get upgraded when new versions become available.

---

