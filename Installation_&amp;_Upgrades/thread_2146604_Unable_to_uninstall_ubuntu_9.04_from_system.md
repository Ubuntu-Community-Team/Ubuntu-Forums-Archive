---
title: "Unable to uninstall ubuntu 9.04 from system"
date: 2013-05-19
forum: Installation &amp; Upgrades
---

### Post by 24adithya on 2013-05-19
Hi,

I have installed Ubuntu 9.04 as dual boot along with Windows 7 in my laptop. There is only one drive currently (C:). It asked me to install grub loader so i obliged and installed everything. Now, I am trying to remove/uninstall Ubuntu from my laptop. Here are few strange things which i have observed.

1)I put the wubi CD to uninstall and it did uninstall but whenever i restart my laptop, i get the dual boot option which is fine since, i haven't modified the boot.ini file. The stranger part is if the ubuntu boot is selected, Ubuntu starts ! I am able to login and do stuff.
2)Now, i put the wubi CD again but i don't get any option of uninstalling it now! Nor is there an option of removing the grub loader. 
3)I tried finding it in 'Programs and Features' but it doesn't appear there as well.
4)There are some steps mentioned related to [uninstalling ubuntu which are risky]("https://wiki.ubuntu.com/WubiGuide"), as i don't have a backup disk yet ! Plus, i don't want to lose any data as my entire 640GB of disk is almost full !

Please suggest what should i do and how do i go about it

---

### Post by ajgreeny on 2013-05-19
Is this a wubi dual boot or not; you have confused me?

If you installed ubuntu from a running Windows 7 OS, then it is definitely wubi and you should be able to uninstall ubuntu through the Windows 7 Control-Centre -> Add/Remove utility, the same as any other windows application.

As far as I'm aware there is no uninstall available from the live CD, but I could be wrong, never having used wubi.

---

### Post by 24adithya on 2013-05-19
> **ajgreeny said:**
> Is this a wubi dual boot or not; you have confused me?

If you installed ubuntu from a running Windows 7 OS, then it is definitely wubi and you should be able to uninstall ubuntu through the Windows 7 Control-Centre -> Add/Remove utility, the same as any other windows application.

As far as I'm aware there is no uninstall available from the live CD, but I could be wrong, never having used wubi.

It is wubi dual boot,  but it asked me to install a grub loader in order to install Ubuntu alongside Win 7 for dual boot option which i did. I don't get the option for Removing Ubuntu in Add/Remove Utility :(.

---

### Post by ajgreeny on 2013-05-19
I am still confused but I'm afraid I don't know enough about wubi to help you more, so I will have to bow out here and let other more knowledgeable people help you.

---

### Post by jamesisin on 2013-05-19
Did you begin with Wubi and then use that installation to create an actual HDD installation of Ubuntu?  If you boot into Windows do you see your Linux partitions listed in Disk Manager?

---

### Post by 24adithya on 2013-05-20
> **jamesisin said:**
> Did you begin with Wubi and then use that installation to create an actual HDD installation of Ubuntu?  If you boot into Windows do you see your Linux partitions listed in Disk Manager?

I have attached the image..it doesn't show anything as linux or ubuntu partition but i suspect the partition which is size 2.32 gb might be that!

---

### Post by jamesisin on 2013-05-20
If those other partitions (at the right and unlabeled) are not ones you have created for something else, you could delete them.  And for crying out loud, back up your data.

---

