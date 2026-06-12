---
title: "Black screen during startup &amp; shutdown!"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by UbNewbie on 2006-11-18
Hi all,

Yesterday had tried to upgrade my Dapper Drake Desltop to Edgy, but is failed! The upgrade process didn't restore the correct hard disk partition labels!

so I started a new and fresh installation of the Edgy! So far so good at least it start normally now also using my dual boot option to Windows machine.

The problem I have right now is that I don't see any messages or images during the startup and shutdown process! The screen stays black!

Somebody has the same experience? Any advise?

Thanks in advance.

Regards,

Ubnewbie

---

### Post by gborzi on 2006-11-18
I have had the same problem in dapper, when I compiled a custom kernel. The problem was due to the missing vesafb module in the initrd image for the custom compiled kernel. I fixed it by adding this list of modules > capability
vesafb
fbcon
unix to /etc/mkinitramfs/modules and recreating the initrd image with a > sudo dpkg-reconfigure <kernel package name>I think that on edgy this list must be added to /etc/initramfs-tools/modules. However, it is quite strange that it doesn't work with the precompiled kernel.

---

### Post by UbNewbie on 2006-11-18
Hi,

the problem is that I haven't that problem with Dapper. And indeed you are right regarding the vesafb becuase I saw this thread that explain that  a little bit deeper.. [http://www.ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters](http://www.ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters)

so I have change my grub option and now I see a little bit more. But still need to fine tuning it.

Thanks..

regards,

Ubnewbie

---

