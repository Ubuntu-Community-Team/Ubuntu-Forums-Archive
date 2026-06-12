---
title: "recent apt-get update/dist-update caused issue for nvidia/vbox"
date: 2010-05-08
forum: Installation &amp; Upgrades
---

### Post by yangeryanger on 2010-05-08
got the following message:

```
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-21-generic
 *  nvidia (96.43.13)...                                                        nvidia (96.43.13): Installing module.
.......(bad exit status: 10)
  Build failed.  Installation skipped.
                                                                         [fail]
 *  vboxdrv (3.1.6)...                                                          vboxdrv (3.1.6): Installing module.
.......(bad exit status: 10)
  Build failed.  Installation skipped.
                                                                         [fail]
 *  vboxnetadp (3.1.6)...                                                       vboxnetadp (3.1.6): Installing module.
.......(bad exit status: 10)
  Build failed.  Installation skipped.
                                                                         [fail]
 *  vboxnetflt (3.1.6)...                                                       vboxnetflt (3.1.6): Installing module.
.......(bad exit status: 10)
  Build failed.  Installation skipped.
                                                                         [fail]
run-parts: executing /etc/kernel/postinst.d/nvidia-common

Setting up linux-image-generic (2.6.31.21.34) ...
Setting up linux-generic (2.6.31.21.34) ...
Setting up linux-headers-2.6.31-21 (2.6.31-21.59) ...
Setting up linux-headers-2.6.31-21-generic (2.6.31-21.59) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms
 * Running DKMS auto installation service for kernel 2.6.31-21-generic
 *  nvidia (96.43.13)...                                                        nvidia (96.43.13): Installing module.
.......(bad exit status: 10)
  Build failed.  Installation skipped.
                                                                         [fail]
 *  vboxdrv (3.1.6)...                                                          vboxdrv (3.1.6): Installing module.
.......(bad exit status: 10)
  Build failed.  Installation skipped.
                                                                         [fail]
 *  vboxnetadp (3.1.6)...                                                       vboxnetadp (3.1.6): Installing module.
.......(bad exit status: 10)
  Build failed.  Installation skipped.
                                                                         [fail]
 *  vboxnetflt (3.1.6)...                                                       vboxnetflt (3.1.6): Installing module.
.......(bad exit status: 10)
  Build failed.  Installation skipped.
                                                                         [fail]
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common

Setting up linux-headers-generic (2.6.31.21.34) ...


```

any advise? I'm assuming the newest linux kernel can't support vbox and nvidia drivers yet?

---

