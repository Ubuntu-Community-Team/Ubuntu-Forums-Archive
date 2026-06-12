---
title: "Ubuntu 12.04 has stoped showing the recovery mode balck screen"
date: 2012-10-06
forum: Installation &amp; Upgrades
---

### Post by hoboy on 2012-10-06
I use ubuntu 12.04 but for some reasons it has stopped showing the recovery screen,before showing the desktop the screen is blank.
Then it continuous to login to the Desktop.

---

### Post by darkod on 2012-10-06
Recovery screen? It doesn't show any recovery screen as far as I know.

Do you mean the grub2 bootloader boot menu?

---

### Post by hoboy on 2012-10-06
> **darkod said:**
> Recovery screen? It doesn't show any recovery screen as far as I know.

Do you mean the grub2 bootloader boot menu?

Yes that is what I mean 
tks

---

### Post by darkod on 2012-10-06
If you have only ubuntu the boot menu doesn't show since there is only one OS, no point for OS selection screen.

You can make it show by holding Shift when it is booting, if you need to enter the recovery mode or similar.

If you have more OSs and you think the menu should be there, first try running:
sudo update-grub

That will scan all disks for boot files of other OSs and add them to the boot menu. If it doesn't, that means there is something wrong with the boot files, etc.

---

