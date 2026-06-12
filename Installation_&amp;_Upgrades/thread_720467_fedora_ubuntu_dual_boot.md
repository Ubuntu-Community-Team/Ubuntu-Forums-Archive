---
title: "fedora ubuntu dual boot"
date: 2008-03-10
forum: Installation &amp; Upgrades
---

### Post by buccaneere on 2008-03-10
All guides for Ubuntu dual boot seem to be for Windows/Ubuntu.

Any guides for dual-linux install?

I have Ubuntu practical guide 1140 pages, and Fed RHEL bible 1090 pages, and they do not answer dual linux boot q's...

Thanks............

---

### Post by ajgreeny on 2008-03-10
I have had both these and windows on my machine in the past without major problems.  The only comments I would make are that fedora was hopeless at seeing other linux installations on the machine when it's installed, so it might be better to install fedora first then Ubuntu which will certainly find the fedora and add it to menu.lst.  Also I recall problems of fedora being installed by default on a logical partition, which gave a number of problems when I tried to mount the partition in Ubuntu.  It could be overcome, I know, but I eventually installed fedora on to a primary partition and no difficulties were seen with that.

PS.  I still prefer Ubuntu to anything else I've tried

---

### Post by kellemes on 2008-03-10
> **buccaneere said:**
> All guides for Ubuntu dual boot seem to be for Windows/Ubuntu.

Any guides for dual-linux install?

I have Ubuntu practical guide 1140 pages, and Fed RHEL bible 1090 pages, and they do not answer dual linux boot q's...

Thanks............

Think about what distro you want to use to manage your system.. Assuming it's ubuntu.. (the other way around works just the same)
Install Ubuntu, let it install Grub in the MBR
Install Fedora on it's own partitions, the only partition you can share is Swap.
Let Fedora install grub in the MBR.. therefor overwriting Ubuntu's Grub-install.

Download/burn/boot [Super Grub Disk]("http://supergrub.forjamari.linex.org/") and use  it to "fix" your Ubuntu Grub-install, so.. reinstall Grub based on the /boot/grub/menu.lst from the boot-partition/directory of your Ubuntu installation.
This will give you back your Grub boot menu as setup by Ubuntu.. this will be without Fedora-entry.

Now.. edit /boot/grub/menu.lst and include an entry that points to the /boot/grub/menu.lst created by Fedora, **this way you create a nested boot-menu**. In other words.. you'll include the Fedora bootmenu into your Ubuntu bootmenu.

This way changes made to the bootmenu by Fedora (for example when the kernel gets upgraded) are automatically included in your bootmenu, you simply let Fedora handle it's own Grub-install and Ubuntu it's own Grub-install.

Example of an entry.

```
# Fedora
title Fedora version blabla
configfile   (hd2,8)/grub/menu.lst
```

---

### Post by buccaneere on 2008-03-10
> **kellemes said:**
> Think about what distro you want to use to manage your system.. Assuming it's ubuntu.. (the other way around works just the same)
Install Ubuntu, let it install Grub in the MBR
Install Fedora on it's own partitions, the only partition you can share is Swap.
Let Fedora install grub in the MBR.. therefor overwriting Ubuntu's Grub-install.

Download/burn/boot [Super Grub Disk]("http://supergrub.forjamari.linex.org/") and use  it to "fix" your Ubuntu Grub-install, so.. reinstall Grub based on the /boot/grub/menu.lst from the boot-partition/directory of your Ubuntu installation.
This will give you back your Grub boot menu as setup by Ubuntu.. this will be without Fedora-entry.

Now.. edit /boot/grub/menu.lst and include an entry that points to the /boot/grub/menu.lst created by Fedora, **this way you create a nested boot-menu**. In other words.. you'll include the Fedora bootmenu into your Ubuntu bootmenu.

This way changes made to the bootmenu by Fedora (for example when the kernel gets upgraded) are automatically included in your bootmenu, you simply let Fedora handle it's own Grub-install and Ubuntu it's own Grub-install.

Example of an entry.

```
# Fedora
title Fedora version blabla
configfile   (hd2,8)/grub/menu.lst
```

Good call.

That's what I had goin' on - the Ubuntu Grub loader gettin' overwritten, and no "Ubuntu choice' in the boot list.

Got one loaded (a desktop) right now, but the HP dv9000 is bein' obnoxious about it...

---

