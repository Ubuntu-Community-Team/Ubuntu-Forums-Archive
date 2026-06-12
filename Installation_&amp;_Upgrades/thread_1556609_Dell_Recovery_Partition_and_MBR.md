---
title: "Dell Recovery Partition and MBR"
date: 2010-08-19
forum: Installation &amp; Upgrades
---

### Post by Dylnuge on 2010-08-19
Hello,

I'm planning on installing Ubuntu as a dual boot alongside Windows 7 on my Dell computer. I know Dell has a separate partition for recovery, and on my old computer installing GRUB overrode the Dell MBR (of course) and made it impossible to open the recovery partition.

This is primarily an issue because since Dell computers no longer ship with OS CDs, I need a way to recover system files if they are lost when I resize the main partition.

Is there a way to let GRUB know how to load the recovery partition?

Thanks,
Dylan

---

### Post by pricetech on 2010-08-19
> **Dylnuge said:**
> This is primarily an issue because since Dell computers no longer ship with OS CDs,

What ?!?!?!?!

Contact support and DEMAND installation media, unless you were given the option and declined when you bought the computer.

I've only had one order from Dell that didn't include media and they sent it to me when I contacted them and threw a fit.

---

### Post by efflandt on 2010-08-19
There should be a Dell Datasafe app in Win 7 that should allow you to create 2 Recovery DVD's with data in the RECOVERY partition, which you should do (or should have done) before you attempt anything that could possibly mess up your system.  They can allow you to restore your drive like it was from the factory if all else fails.  Then you should probably back up your System as it is now using normal Win 7 backup.  Backing up your own data is a separate procedure.

I don't really know if they use a special MBR, because mine just had the RECOVERY partition marked as the boot partition.  So it probably just chain loads from there normally.  But I put grub on a primary partition instead of the MBR.  Do both the RECOVERY and Win 7 partitions show up in your grub menu?

---

