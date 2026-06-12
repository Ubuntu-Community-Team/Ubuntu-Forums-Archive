---
title: "Problem installing ALSA driver"
date: 2008-09-26
forum: Installation &amp; Upgrades
---

### Post by R2D2! on 2008-09-26
I've downloaded alsa-driver-1.0.17; and when I try to &#305;nstall &#305;t, the follow&#305;ng code appears:

```
ilhuitemoc@ilhuitemoc-laptop:~/Aplicaciones/alsa-driver-1.0.17$ sudo make
[...]
In file included from /home/ilhuitemoc/Aplicaciones/alsa-driver-1.0.17/soc/soc-dapm.c:2:
/home/ilhuitemoc/Aplicaciones/alsa-driver-1.0.17/soc/../alsa-kernel/soc/soc-dapm.c: En la función ‘dapm_pop_time_store’:
/home/ilhuitemoc/Aplicaciones/alsa-driver-1.0.17/soc/../alsa-kernel/soc/soc-dapm.c:834: error: declaración implícita de la función ‘strict_strtoul’
make[3]: *** [/home/ilhuitemoc/Aplicaciones/alsa-driver-1.0.17/soc/soc-dapm.o] Error 1
make[2]: *** [/home/ilhuitemoc/Aplicaciones/alsa-driver-1.0.17/soc] Error 2
make[1]: *** [_module_/home/ilhuitemoc/Aplicaciones/alsa-driver-1.0.17] Error 2
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.24-19-generic'
make: *** [compile] Error 2
ilhuitemoc@ilhuitemoc-laptop:~/Aplicaciones/alsa-driver-1.0.17$ 

```

How can I f&#305;x the Error?

—Arturo Ilhu&#305;temoc

---

