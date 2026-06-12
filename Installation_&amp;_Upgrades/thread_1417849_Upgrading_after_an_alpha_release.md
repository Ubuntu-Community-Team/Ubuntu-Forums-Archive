---
title: "Upgrading after an alpha release?"
date: 2010-02-27
forum: Installation &amp; Upgrades
---

### Post by Jugney on 2010-02-27
Hi all,

I'm hearing some juicy things about the alpha 3 release of Lucid Lynx, and am getting a bit of an itchy trigger finger...I'd like to transition my system over now, but want to make sure it'll be a smooth upgrade to the stable release when that comes out. Will I need to reinstall to go from alpha to stable, or will it be taken care of by the Update Manager?

Thanks,
Jugney

---

### Post by presence1960 on 2010-02-27
> **Jugney said:**
> Hi all,

I'm hearing some juicy things about the alpha 3 release of Lucid Lynx, and am getting a bit of an itchy trigger finger...I'd like to transition my system over now, but want to make sure it'll be a smooth upgrade to the stable release when that comes out. Will I need to reinstall to go from alpha to stable, or will it be taken care of by the Update Manager?

Thanks,
Jugney

Remember it is still in alpha stage. Not yet quite ready for prime time. I would not transition over yet. Maybe create another partition for it and install to that partition. This way if the alpha goes south on you , you will still have a reliable version to boot into.

That's what I have done. I also did not install GRUB from the alpha CD. Choose to install no bootloader and kept karmic's bootloader in MBR. After the lucid install I booted into karmic and ran ```
sudo update-grub
```to add lucid to the grub menu.

---

### Post by Jugney on 2010-02-27
Cool beans. I have another partition I will install to.

Just for my knowledge, however, does it work to just do the updates to get from alpha to beta to rc to stable? Or not?

---

### Post by Jugney on 2010-02-27
PS - How do I install Lucid alpha without having it touch GRUB?

---

### Post by presence1960 on 2010-02-27
> **Jugney said:**
> PS - How do I install Lucid alpha without having it touch GRUB?

At the Ready to Install window click the Advanced button and set it to not install bootloader option. 

I have never done a dist-upgrade whether from old version to new version or alpha to beta or final release. I always do clean installs. Back up data and use [this]("http://ubuntuforums.org/showpost.php?p=7157175&postcount=5") little how to from lovinglinux to install all my packages on the new install

---

### Post by Mark Phelps on 2010-02-28
It's not at all uncommon for one alpha to dramatically change (replace, delete) something used in a previous alpha.  So, while they might be upgradeable, there's no guarantee that they all will be.

You would do better waiting for the beta.  It's upgradeable to the final release.

---

