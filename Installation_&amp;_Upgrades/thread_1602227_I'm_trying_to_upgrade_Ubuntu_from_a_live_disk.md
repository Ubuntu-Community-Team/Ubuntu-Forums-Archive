---
title: "I'm trying to upgrade Ubuntu from a live disk"
date: 2010-10-21
forum: Installation &amp; Upgrades
---

### Post by Externalist on 2010-10-21
My ubuntu desktop died yesterday. I rebooted my computer in like 1 month and after grub, the screen is all black and it stays there... forever. :(
So I decided to see if the problem persists or not when I completely upgrade my ubuntu to the latest version. So I downloaded the latest ubuntu iso from the site, burned it, and booted from CD and I see several selections to choose from the menu list. The second one was "Install Ubuntu". What I'm worried about is I don't know whether selecting 'Install Ubuntu' will erase all my previous data, or there will be an option to upgrade Ubuntu without erasing all the data.
Is it safe to install from the live disk? Will my data be safe? Is there any way to upgrade my Ubuntu on the HD to the latest Ubuntu from a live disk?
Thanks!

---

### Post by vader95 on 2010-10-21
Are you on ubuntu 10.04?

What I would do is boot into the live CD and mount the Ubuntu partition.  Then, copy all the files you need onto another partition or external hard drive.  I would then do a fresh install, and make a separate partition for /home, so you would have /, /home, and maybe swap.

From what I understand is you cannot upgrade from the live CD, but you can from the alternate CD, however, I think you have to be on the desktop to upgrade.

vader95

---

### Post by TBABill on 2010-10-21
+1. If you install from the LiveCD you will be overwriting your partition unless you install to a separate one. This will not be an upgrade, but a fresh install. If you have critical documents you want to save, make sure, as stated above, that you do so before beginning that process. You can also just copy them to a thumb drive or external drive if you do not want another partition on that current drive, plus if you make a mistake creating a new partition you could destroy the data currently there.

---

### Post by Externalist on 2010-10-21
Well... I tracked down the problem and it seems to be the hard drive failure, so upgrading will be no good. :(
I'm gonna have to buy a new hard drive now. Thanks for the help!

---

