---
title: "Grub2 / Dual boot system"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by Bonez56 on 2010-11-23
Hi all,

Been using Linux for many many years but Grub2 is annoying the heck out of me at the moment.

My home desktop PC is set up as follows:

/dev/sda – 40GB 10k Raptor with Ubuntu 10.10 installed
/dev/sdb – 500GB HDD formatted to ext4
/dev/sdc – 500GB HDD split up as follows:

/dev/sdc1 – 80gb NTFS partition with Win7 installed
/dev/sdc1 – Remaining drive space NTFS but nothing on it yet

Grub2 refuses to detect that Windows is installed on the 3rd HDD. I've googled and spent hours trying all sorts of things to get it to detect it and add it to my boot menu.

If I disconnect all drives except the Windows drive it boots up straight into Win7, so it's healthy and happy. (as healthy and happy as Windows can be, I need it for work purposes only!)

Does anyone have any tips on what would be the best method to force grub to realise that Windows is sitting there?

As far as I understand, the Win7 partition should be (hd2,1) – does that sound right to you?

I haven't tried booting off an Ubuntu CD and re-installing grub, since I can get into Linux and all the guides seem to be about how to restore grub after a Windows install eats it....

Any help would be appreciated, and free popcorn if you help me fix it :popcorn:

---

### Post by wilee-nilee on 2010-11-23
For now use the per-sesion key prompt like going to the bios to boot W7 mine is f12. This is a post bios boot from menu. You would hit the key as soon as you power on.

To be honest this may be a hard fix hard to say but the per-session boot can tide you over for now.

---

### Post by Quackers on 2010-11-23
hmmmm popcorn :-)
Have you run ```
sudo update-grub
``` in a terminal?

---

### Post by wilee-nilee on 2010-11-23
> **Quackers said:**
> hmmmm popcorn :-)
Have you run ```
sudo update-grub
``` in a terminal?

Doh, good eye; that always helps to try.

---

### Post by Quackers on 2010-11-23
Lol, that popcorn got me going :-)
It may well be that the OP has done that already. We'll find out soon!

Please send popcorn overnight! :-)

---

### Post by wilee-nilee on 2010-11-23
> **Quackers said:**
> Lol, that popcorn got me going :-)
It may well be that the OP has done that already. We'll find out soon!

Please send popcorn overnight! :-)

I always go straight to where the problem might be without considering the first steps.

---

