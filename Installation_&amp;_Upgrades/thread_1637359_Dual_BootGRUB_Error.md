---
title: "Dual Boot/GRUB Error"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by DGorilla on 2010-12-04
I deleted the partition that contained my GRUB files on laptop that previously was dual boot Vista and Linux Mint. I intended to remove Linux Mint and install Ubuntu in that space, but I didn't realize this would destroy GRUB and not allow me to boot into Vista. I can get into Ubuntu via Live CD but cannot install from the CD due to either a CD or HDD problem. I think my next step is to attempt a USB stick install but thought it wise to ask for help before making a bad problem worse.

---

### Post by dino99 on 2010-12-04
[http://community.linuxmint.com/tutorial/view/245](http://community.linuxmint.com/tutorial/view/245)

---

### Post by efflandt on 2010-12-04
Unless you ended up with bad iso download or burn, replacing Mint should be a simple matter of manually selecting whatever partition(s) you used for Mint, setting mount points for them, and checking to format / (install automatically finds any swap).  That should replace whatever old grub in your mbr and you should then be able to dual boot.

If you want to be able to boot Vista until you get around to doing that, you can do **bootrec /FixMbr** from Vista recovery disk, or web search "fix windows mbr from linux".

---

### Post by DGorilla on 2010-12-04
Thank you both. I apparently did have a bad ISO or CD, because the USB install worked with no problems. Obviously, the Ubuntu installation fixed GRUB.

---

