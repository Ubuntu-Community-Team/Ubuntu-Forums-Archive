---
title: "Keep WinXP, delete Edgy, clean Feisty"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by noynac on 2007-04-19
Hi Folks,

I have one hard drive with 1) a WinXP partition, 2) an Ubuntu 6.10 partition, 3) an Ubuntu swap partition, and 4) a Fat32 partition for storage. I want to delete Ubuntu 6.10, replace it with a clean install of Ubuntu 7.04, and leave WinXP as it is.

Should I delete the Ubuntu 6.04 after booting to the Ubuntu 7.04 live cd?

Should I delete the Ubuntu 6.04 install using Windows?

Is any of this going to mess with the MBR?

I honestly did a search but couldn't find any answer. 

Thanks!

---

### Post by cogadh on 2007-04-19
In the past when I did this, it was best to use the Ubuntu install process to remove the old installation, i.e. when you get to the partitioning part, delete your Ubuntu partition then create a new one from the empty space. Don't delete from within Windows, that will cause problems with your GRUB boot. 

If you do this you will lose any data you have in the old Ubuntu partition.

---

