---
title: "Migrating from 32bit to 64bit"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by moody_mark on 2010-03-15
Hi, Ive been using Ubuntu 32bit on my work Dell E6400 for nearly a year now with no problems. It is capable of running Ubuntu 64bit and Ive tried out the live CD which seems ok. I have a spare 40GB HDD and a USB caddy so Id like to install Ubuntu 64bit onto that and start working with that as a trial. Once im happy I can get all the usual things I need for my work (like vpnc) working then I'll wipe the main internal HDD and install Ubuntu 64bit.

Apart from backing up my home directory, id like to backup a list of my installed packages as a list of reference so I know what to add into my new install. Is there a "apt" command to do this and list the packages in a way where if I install those packages, I'll not hit any dependancy problems by installing one before another?

---

### Post by wojox on 2010-03-15
Run and post back:

```
sudo lshw | grep cpu
```

---

### Post by moody_mark on 2010-03-15
output:

```
     *-cpu                
          bus info: cpu@0
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni dtes64 monitor ds_cpl vmx smx est tm2 ssse3 cx16 xtpr pdcm sse4_1 lahf_lm tpr_shadow vnmi flexpriority cpufreq
        *-logicalcpu:0
        *-logicalcpu:1
```

---

### Post by wojox on 2010-03-15
**x86-64** yup, it will work. :p

---

### Post by wojox on 2010-03-15
I've never tried this from 32 to 64 bit but look here: [http://stringofthoughts.wordpress.com/2009/04/29/package-installation-after-renew-install-ubuntu/](http://stringofthoughts.wordpress.com/2009/04/29/package-installation-after-renew-install-ubuntu/)

---

### Post by moody_mark on 2010-03-15
To quote the post above

> To backup

```
sudo dpkg –get-selections > myPackages
```

To re-instate

```
sudo dpkg –set-selections < myPackages && sudo apt-get dselect-upgrade
```

This is a good tip, If using this technique is the order of the list important, will a dependency fail if the order is wrong? Also I wonder if when re-installing to 64-bit, would those packages be valid? Perhaps theres some other that are the 64-bit equivalent?

---

### Post by bsharp on 2010-03-15
> **moody_mark said:**
> Also I wonder if when re-installing to 64-bit, would those packages be valid? Perhaps theres some other that are the 64-bit equivalent?

That's a good point. However, Ubuntu has had 64-bit support since the beginning. I've been using it as long as I've been using Ubuntu (6.06). I haven't had any 64-bit related problems since *at least* 7.10, so unless you're using some very obscure packages, you will be fine. By now, even if you are using very obscure packages, you'll still probably be fine.

The only package I know of off the top of my head that wouldn't install would be w32codecs, to get it just install w64codecs. Any other problem packages would likely have a slightly different name.

Edit:You can also create/restore a list of installed packages through Synaptic.

---

