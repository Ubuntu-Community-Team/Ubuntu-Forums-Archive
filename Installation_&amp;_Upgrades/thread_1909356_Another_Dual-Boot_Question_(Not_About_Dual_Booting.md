---
title: "Another Dual-Boot Question (Not About Dual Booting)"
date: 2012-01-15
forum: Installation &amp; Upgrades
---

### Post by Hostage777 on 2012-01-15
Alright, so I am trying to get Windoze installed on an MSI notebook which previously was running exclusively Ubuntu 11.04. I had no problem getting GRUB configured and getting Windows installed to an ntfs partition (despite the inanity of the MSi recovery disk). The laptop contains ubuntu on an ext4 and a swap partition as well. Unfortunately, whenever I boot to windows, I get to a screen that says "starting services" and then receive a dialog which reads "Windows cannot complete the installation. To complete the installation, restart". When I hit okay, it restarts, and then loops back to the same place.

I realize this is technically a question about windows, but I trust this community and I'm hoping someone else has had a similar experience. All the win community support is ****.

Any help with this asinine software would be greatly appreciated!

---

### Post by darkod on 2012-01-15
1. Are you installing onto a primary ntfs partition?

2. Are you creating the partition with the win7 installer or it's created in advance?

3. The win7 install would install windows bootloader on the MBR so it's very strange you still have grub on the MBR.

---

### Post by kc1di on 2012-01-15
Windows likes to think it's the only system on the computer and thus will take over the MBR you'll will most likely have to install windows completely allow it to set the Master Boot Record to windows. it will not see your Ubuntu install.  Then you will have to re install Grub to the mbr after. Here is a page that maybe of help

[http://www.dangibbs.co.uk/journal/repair-restore-grub-2-with-ubuntu-10-04-live-cd]("http://www.dangibbs.co.uk/journal/repair-restore-grub-2-with-ubuntu-10-04-live-cd")

and another: [http://askubuntu.com/questions/80434/installing-windows-vista-after-installed-ubuntu-11-10-oneiric]("http://askubuntu.com/questions/80434/installing-windows-vista-after-installed-ubuntu-11-10-oneiric")

---

