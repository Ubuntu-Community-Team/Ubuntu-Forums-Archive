---
title: "Completely remove Mint 17 partion"
date: 2014-08-08
forum: Installation &amp; Upgrades
---

### Post by LaJuan on 2014-08-08
Hi,

I have been running Ubuntu for years now and wanted to give mint a trial. I didn't like feel of it. I logged into mint and used terminal to purge/remove mint but, it still shows up in my boot menu. How do I completely remove the mint 17 partion so I can free up that hard drive space?

Dell Precision 390 8GB, Ubuntu 14.04

---

### Post by grahammechanical on 2014-08-08
I am confused as to what you want to do. Is it remove the listing of Mint from the Grub boot menu now that you have removed Mint from the hard disk? Is it remove/resize the partitions? Is it remove Linux Mint 17 from the hard disk?

I am confused as to what you have done and what you still need to do. My advice would be to do things in this order,

1) load into Ubuntu and run
```
sudo update-grub
sudo grub-install /dev/sda
```

assuming that you only have one hard disk. Those two commands will put the Grub of Ubuntu back in charge of the Grub boot menu.

2) Use Gparted from a Ubuntu live session to delete the Linux Mint 17 partition and then resize another partition to take up the unallocated space that has been created.

3) Load into Ubuntu and run again
```
sudo update-grub
sudo grub-install /dev/sda
```

That will remove the listing of Linux Mint from the Grub boot menu. More importantly, you will still be able to load into Ubuntu. If the Grub configuration files in Linux Mint are in control of the Grub menu, then removing Linux Mint will break the Grub boot menu and you will not be able to load into Ubuntu.

An alternative to this is to keep that Linux Mint partition and simply install another version or flavour of Ubuntu onto it.

Regards.

---

### Post by LaJuan on 2014-08-08
Thanks!!!!!!!! The one key thing I was missing to completely removed Mint 17 was GPart and I'm in the process as we speak!!!!! Thanks again for all your experience AND support!!!!!!!!:guitar:

---

