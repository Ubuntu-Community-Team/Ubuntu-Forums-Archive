---
title: "Safely Remove Old Kernels ?"
date: 2005-03-29
forum: Installation &amp; Upgrades
---

### Post by EternalNewbie on 2005-03-29
Hi,
     I have been faithfully updating Warty and now find myself with 6 kernel images from these updates. These are starting to take up some serious space.
     What is the canonical ( pun intended ) way to get rid of the old kernel images. I have seen several suggestions searching these forums, but I am a bit worried about the symlink situation and Grub configuration.

                                                          Happy Ubuntu User,
                                                                      John Duncan

---

### Post by ubuntu_demon on 2005-03-29
[QUOTE=EternalNewbie]Hi,
     I have been faithfully updating Warty and now find myself with 6 kernel images from these updates. These are starting to take up some serious space.
     What is the canonical ( pun intended ) way to get rid of the old kernel images. I have seen several suggestions searching these forums, but I am a bit worried about the symlink situation and Grub configuration.

                                                          Happy Ubuntu User,
                                                                      John Duncan[/QUOTE]
 apt-get remove kernelname

use grubconf for editting your grubconfiguration if needed

---

