---
title: "VMware on Ubuntu Gutsy"
date: 2008-01-13
forum: Installation &amp; Upgrades
---

### Post by enrique.vidal on 2008-01-13
Morning,

Yesterday I needed to run a virtual OpenBSD machine to do some testing, however I tried with qemu with kqemu but the machine wouldn't load so I tried Virtual box, it loaded and everything with lots of bugs and the image it self would not boot, so I jumped to Vmware Player.

I create my image use easyvmx and then installed vmware-player from someone elses repository however, the installation when wrong and now it wont let me remove it nor complete the installation, the odd thing is that the problem seemed to be getting fixed gradually.

What I mean is after the first reboot and second reinstall try (as suggested by apt-get)

```
sudo apt-get install --reinstall vmware-player
```

Another part of the package was installed but still came back with an erro code 2.

After the second reboot gutsy recognizes the VMware propietary driver, this time I tried with Synaptic update Manager and another part of the installation went through, but I dont seem to be able to get any further.

Any recomendatios as what do in this case? (besides only installing debs from the Ubuntu repositories).

Any help is greatly appreciated (And believe me I learned the lesson).

Thanks in Advance

---

### Post by zvacet on 2008-01-13
```
sudo apt-get --purge remove vmware-player
```

When you remove it install vmware-server from synaptic including kernel modules and kernel source.Here is serial number** 98841-YYAF2-2C721-48M8H**

---

### Post by enrique.vidal on 2008-01-13
That is the first thing I tried but it didn't work either.

---

### Post by zvacet on 2008-01-13
```
sudo dpkg --remove --force-remove-reinstreq vmware-player
```

---

