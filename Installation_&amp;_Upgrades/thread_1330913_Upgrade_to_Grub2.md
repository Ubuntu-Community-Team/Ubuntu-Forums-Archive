---
title: "Upgrade to Grub2"
date: 2009-11-18
forum: Installation &amp; Upgrades
---

### Post by Abadon125 on 2009-11-18
I have Windows 7 installed on my hard drive and just installed Ubuntu 9.10 next to it and when running updates was asked to do something with Grub2.  I clicked to leave the one I currently have because I didn't want to break anything.  

Can I safely upgrade?  When I boot up my computer I believe it says I currently have Grub 1.97 something.  

Please let me know what I should do and how to do it.  I am very new to Linux and Ubuntu.
-Thanks

---

### Post by drs305 on 2009-11-18
> **Abadon125 said:**
> I have Windows 7 installed on my hard drive and just installed Ubuntu 9.10 next to it and when running updates was asked to do something with Grub2.  I clicked to leave the one I currently have because I didn't want to break anything.  

Can I safely upgrade?  When I boot up my computer I believe it says I currently have Grub 1.97 something.  

Please let me know what I should do and how to do it.  I am very new to Linux and Ubuntu.
-Thanks

If you weren't doing an update but a clean install, Grub 2 was probably asking to update itself as your system "catches up" to the most current release. If that is what happened, and you haven't tweaked the settings yet, go ahead and accept the new version. You probably won't notice a difference. If you have already made normal changes to /etc/default/grub or added a splash image via /etc/grub.d/05_debian_theme, you would just have to go back in and make them again after accepting the update.

By the way, if Grub 2 doesn't see your Windows install, it probably will after you run the update. Sometimes G2 doesn't see the Windows partition upon an initial install but will after running "update-grub". If you select yes to the upgrade, the "update-grub" will be run as part of the process.

---

### Post by Abadon125 on 2009-11-18
Well as I said it was sort of a clean install because I just installed it but it was next to a Windows partition.  The time when it asked me to update was after the installation process was completed and i was just running the update manager. 

So if I change my mind and want to install the update how would I do that?  It says that I have no updates.

Thanks again.

---

### Post by drs305 on 2009-11-18
> **Abadon125 said:**
> So if I change my mind and want to install the update how would I do that?  It says that I have no updates.
Thanks again.

You can reinstall it and that should update it to include the most recent changes:
```

sudo apt-get update
sudo apt-get install --reinstall grub-pc grub-common

```

You will see the same message you got previously (and declined).

If you are concerned you could make backup copies of the following:
/etc/grub.d folder
/etc/default/grub
/boot/grub folder

If you haven't made changes, the above probably isn't necessary.

---

### Post by Abadon125 on 2009-11-18
Worked great. Thanks!

---

