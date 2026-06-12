---
title: "NTLDR missing after vanilla ubuntu install"
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by lee797 on 2008-01-01
I have just installed Gutsy on to my new Dell Inspiron. It was my first action and formatted over Windows Vista (intentionally). On reboot I get the famous NTLDR missing. I can work around it by booting through the gutsy install disk, but I would rather not have to. Can anyone advise me how I can remedy this problem? NB This is not a dual boot, but a plain ubuntu install so I should have no need for NTLDR.

---

### Post by Pumalite on 2008-01-01
First, fix the MBR in your Vista. Use your CD or Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
Second, to install Ubuntu, you first have to allocate space for it from WITHIN Vista with the Vista partitioner. Then install Ubuntu.
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

