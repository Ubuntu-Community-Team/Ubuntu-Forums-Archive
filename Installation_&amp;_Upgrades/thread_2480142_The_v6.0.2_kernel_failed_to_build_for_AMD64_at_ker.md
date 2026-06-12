---
title: "The v6.0.2 kernel failed to build for AMD64 at kernel-ppa, please fix"
date: 2022-10-20
forum: Installation &amp; Upgrades
---

### Post by michael-goldshteyn on 2022-10-20
Direct link:

[https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.0.2/amd64/](https://kernel.ubuntu.com/~kernel-ppa/mainline/v6.0.2/amd64/)

Bottom portion of log, indicating failure:

```

btf_encoder__write_elf: failed to add .BTF section to 'sound/soc/codecs/snd-soc-tda7419.ko': 11!
Failed to encode BTF
btf_encoder__write_elf: failed to add .BTF section to 'sound/soc/codecs/snd-soc-tas571x.ko': 11!
Failed to encode BTF
make[4]: /bin/sh: Resource temporarily unavailable
make[4]: *** [/home/kernel/COD/linux/scripts/Makefile.modfinal:60: sound/soc/intel/boards/snd-skl_nau88l25_max98357a.ko] Error 127
make[4]: *** Waiting for unfinished jobs....
  LD [M]  sound/soc/intel/boards/snd-soc-kbl_rt5660.ko
/bin/sh: 1: Cannot fork
make[4]: /bin/sh: Resource temporarily unavailable
make[4]: *** [/home/kernel/COD/linux/scripts/Makefile.modfinal:60: sound/soc/intel/boards/snd-soc-intel-sof-maxim-common.ko] Error 127
make[4]: /bin/sh: Resource temporarily unavailable
make[4]: *** [/home/kernel/COD/linux/scripts/Makefile.modfinal:60: sound/soc/intel/boards/snd-soc-intel-sof-realtek-common.ko] Error 127
make[4]: /bin/sh: Resource temporarily unavailable
make[4]: *** [/home/kernel/COD/linux/scripts/Makefile.modfinal:60: sound/soc/intel/boards/snd-soc-kbl_da7219_max98357a.ko] Error 127
make[4]: /bin/sh: Resource temporarily unavailable
make[4]: *** [/home/kernel/COD/linux/scripts/Makefile.modfinal:60: sound/soc/intel/boards/snd-soc-kbl_da7219_max98927.ko] Error 127
make[4]: *** [/home/kernel/COD/linux/scripts/Makefile.modfinal:60: sound/soc/intel/boards/snd-soc-kbl_rt5660.ko] Error 2
btf_encoder__write_elf: failed to add .BTF section to 'sound/soc/codecs/snd-soc-tlv320aic3x-i2c.ko': 11!
Failed to encode BTF
/bin/sh: 1: Cannot fork
make[4]: *** [/home/kernel/COD/linux/scripts/Makefile.modfinal:60: sound/soc/codecs/snd-soc-tas6424.ko] Error 2
make[4]: *** Deleting file 'sound/soc/codecs/snd-soc-tas6424.ko'
make[4]: *** [/home/kernel/COD/linux/scripts/Makefile.modfinal:59: sound/soc/codecs/snd-soc-tda7419.ko] Error 1
make[4]: *** Deleting file 'sound/soc/codecs/snd-soc-tda7419.ko'
make[4]: *** [/home/kernel/COD/linux/scripts/Makefile.modfinal:59: sound/soc/codecs/snd-soc-tas571x.ko] Error 1
make[4]: *** Deleting file 'sound/soc/codecs/snd-soc-tas571x.ko'
make[4]: *** [/home/kernel/COD/linux/scripts/Makefile.modfinal:59: sound/soc/codecs/snd-soc-tlv320aic3x-i2c.ko] Error 1
make[4]: *** Deleting file 'sound/soc/codecs/snd-soc-tlv320aic3x-i2c.ko'
  BTF [M] sound/soc/intel/avs/snd-soc-avs.ko
Segmentation fault (core dumped)
make[4]: *** [/home/kernel/COD/linux/scripts/Makefile.modfinal:59: sound/soc/intel/avs/boards/snd-soc-avs-rt298.ko] Error 139
make[4]: *** Deleting file 'sound/soc/intel/avs/boards/snd-soc-avs-rt298.ko'
Segmentation fault (core dumped)
make[4]: *** [/home/kernel/COD/linux/scripts/Makefile.modfinal:59: sound/soc/intel/avs/boards/snd-soc-avs-rt5682.ko] Error 139
make[4]: *** Deleting file 'sound/soc/intel/avs/boards/snd-soc-avs-rt5682.ko'
make[3]: *** [/home/kernel/COD/linux/scripts/Makefile.modpost:134: __modpost] Error 2
make[2]: *** [/home/kernel/COD/linux/Makefile:1772: modules] Error 2
make[2]: Leaving directory '/home/kernel/COD/linux/debian/build/build-generic'
make[1]: *** [Makefile:222: __sub-make] Error 2
make[1]: Leaving directory '/home/kernel/COD/linux'
make: *** [debian/rules.d/2-binary-arch.mk:49: /home/kernel/COD/linux/debian/stamps/stamp-build-generic] Error 2 [COLOR=#000000]dpkg-buildpackage: error: debian/rules build subprocess returned exit status 2
[/COLOR]
```

---

### Post by Doug S on 2022-10-20
The mainline compiles have been having problems for months, and have generally suffered from an increased number of issues per unit time for a couple of years now. This latest problem "Cannot fork" seems to be somewhat of a hit and miss thing.

The time was that one could get mainline compile issues fixed in an extremely timely manor, but not anymore. See [here]("https://discourse.ubuntu.com/t/ask-us-anything-about-ubuntu-kernels/27664") and search for "mainline".

---

### Post by TenPlus1 on 2022-12-15
I really hope they manage to fix any issues as I am eager to test-drive the latest 6.1 kernel on my AMD system.

---

