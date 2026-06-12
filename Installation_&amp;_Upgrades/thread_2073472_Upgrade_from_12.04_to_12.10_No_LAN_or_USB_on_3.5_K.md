---
title: "Upgrade from 12.04 to 12.10 No LAN or USB on 3.5 Kernel"
date: 2012-10-19
forum: Installation &amp; Upgrades
---

### Post by TheFuzz4 on 2012-10-19
Hey Everyone,

Thank you for your help with this.  During the upgrade process I had an error and the machine rebooted.  After getting my grub repaired I was able to finally get booted up and I finished up the installation of the packages that was left over.  Now if I boot up into the 3.5 kernel I have no Network or USB.  This is kind of a PITA since my keyboard is USB.  I have a old PS2 keyboard hooked up right now so I can test in it.  The only way that I can get my USB and LAN to work is if I boot it up using the 3.2-31 kernel.  I've never had to load any special drivers for my system so I don't think that its a driver issue.  I've ran apt-get install -f and dpkg --configure -a and both come right back to the prompt.  I've also reinstalled the 3.5-17 kernel and headers as well.  If anyone has any suggestions for this I am open to them.  Thank you all in advance for your help with this.

---

### Post by TheFuzz4 on 2012-10-19
Ok so the last thing that I didn't think about trying fixed this problem for me.

I ran

sudo apt-get dist-upgrade

After running that it installed the last packages that were left from the upgrade and we're up and running.  I hope that this will help someone else out as well.

---

