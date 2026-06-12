---
title: "Upgrade problem with xfonts-intl-european"
date: 2006-11-04
forum: Installation &amp; Upgrades
---

### Post by aum11 on 2006-11-04
Have had problems since the upgrade to edgy.  Have been blocked by an inability to complete the deleting ofxorg-driver-fglrx.  Got around this by forcing the install to the earlier version required by Edgy.

However now there is a continual problem with the error message from synaptic:

E: xfonts-intl-european: subprocess post-installation script returned error exit status 2

Help is very much needed.  Thanks.

---

### Post by aum11 on 2006-11-04
Have since tried to reinstall the package or delete the package but always it fails with the same message.

How to get past this please?

---

### Post by al:x on 2006-11-05
Hello,

I have the same problem and was wandering whether you could solve it?

Thanks in advance.

---

### Post by aum11 on 2006-11-05
Good news and bad news.

I tried everything I knew to fix the problems that arose from the upgrade but eventually got to the place where it wouldn't even reboot.  This has occupied me for toooooooooo long!!

So I grasped the nettle and installed the new 6.10 from CD just this morning.

I have been pleasantly suprised by how much of the old system is recognised by the new install...for instance the way the panel was setup is the same.

OF course, this has worked out well because I have a separate partition for /home, and this is not touched by the reinstall.

It is probably time for a fresh start in any case as this system has been upgraded ever since warty.

Good luck.

---

### Post by al:x on 2006-11-06
Hello,

for me it became very late yesterday but finally I succeeded with the upgrade.

Guided by a Newsgroup posting I was able to manually remove the package, afterwards the upgrade worked out well. No further problems so far.

In case anybody else got the problem, here is how you uninstall manually:

```

sudo rm /var/lib/dpkg/info/xfonts-intl-european.post*
sudo update-fonts-dir misc
sudo /etc/init.d/xfs force-reload
sudo apt-get remove xfonts-intl-european
```

At least it worked for me ;-)

---

