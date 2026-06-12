---
title: "Dual Boot on different HD"
date: 2012-11-25
forum: Installation &amp; Upgrades
---

### Post by fiddler on 2012-11-25
I want to install 12.10 on a different hd. I have prepared a partition, but when I get to the point in the manual install where I click 'install', I get a box telling me I havn't chosen a root device or something similar.I don't know what it means. I'm not conversant enough to proceed. Can anyone help please?

---

### Post by QIII on 2012-11-25
Are you going to only install Ubuntu on the second drive?

Do yourself a favor and disconnect your other drive(s) to avoid the mistake of installing to it(them).  Plug it back in when you are ready to restart the machine.

When installing, choose "something else".

You should create at least a / (that's your root partition, and you get that by creating a partition and choosing / as the mount point) and a /home partition (which you get by creating a partition and selecting /home as the mount point).  You may also create a swap partition.  There are frequent lively discussions about the need for swap.  Definitely create one if you plan to hibernate.  I usually am pretty liberal with / and give it 20 - 30GiB depending on whether I expect to install a lot of software.  Make your swap 1.25 times the size of your RAM and make your /home fill the rest.  From left to right in the partitioning tool you want / then /home then swap.

When you shut down, be sure to plug the other drive back in before restarting.

On your next boot, go into your BIOS/EFI and make sure you boot from the drive you want.  If your previous drive has only Windows on it, you will want the new drive as the first in the HDD boot order and you will need to update GRUB grub to find Windows and get it in the GRUB

---

### Post by fiddler on 2012-11-25
Thanks for the speedy reply Q3. I'll have another go later and let you know how it went.

---

