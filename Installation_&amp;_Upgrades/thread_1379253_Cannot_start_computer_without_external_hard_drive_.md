---
title: "Cannot start computer without external hard drive plugged in"
date: 2010-01-12
forum: Installation &amp; Upgrades
---

### Post by sotoj159 on 2010-01-12
I finally got my new internal hdd for my laptop.  I plugged it in and installed windows 7 64 bit.  Then I partitioned my external hdd (WD mybook 640gb), and installed ubuntu 9.1 on a 200gb partition of it.  The problem is that I didn't unplug the internal hdd before I installed ubuntu.  Now the computer will not start unless I have the external hard drive plugged in.

So what should I do so that I will be able to go into windows 7 normally if the external hdd is unplugged?  I would also like to be able to use ubuntu when I plug in the external hdd.  I wouldn't mind having to go to the boot menu and choosing the external hard drive every time I wanted to use ubuntu.

The reason I partitioned the external hard drive was because it has a lot more space than my 250gb internal hdd, and I also wanted to leave space open to use as was intended, to back up stuff.

However, now that I think about it, I wouldn't mind partitioning the internal hdd and just leaving the external blank (which I should have done in the first place).

---

### Post by darkod on 2010-01-12
You can't start like this because most probably grub2 was installed on the MBR of the int hdd and its config files are on the ext hdd. That's why it's not letting you even boot windows. You should:
Unplug the ext hdd. Repair win7 bootloader to the MBR of the int hdd. Instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

After that win7 should boot fine from the int hdd.

Then plug in the ext hdd, and reinstall grub2 on the MBR of the EXT HDD (most probably it will be called /dev/sdb). The instructions are on the same link. Just make sure you use the 9.10 cd for grub2 and follow the procedure for 9.10, not for 9.04.

---

### Post by sotoj159 on 2010-01-12
> **darkod said:**
> You can't start like this because most probably grub2 was installed on the MBR of the int hdd and its config files are on the ext hdd. That's why it's not letting you even boot windows. You should:
Unplug the ext hdd. Repair win7 bootloader to the MBR of the int hdd. Instructions here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

After that win7 should boot fine from the int hdd.

Then plug in the ext hdd, and reinstall grub2 on the MBR of the EXT HDD (most probably it will be called /dev/sdb). The instructions are on the same link. Just make sure you use the 9.10 cd for grub2 and follow the procedure for 9.10, not for 9.04.

Woah!  fast reply!  I'll definitely do this.  I'll let you know how it goes; thanks!

---

### Post by recluce on 2010-01-12
If I understand everything correctly, after following these steps, you will have to change your boot sequence if you want to boot Ubuntu, since Grub2 is now on the USB drive.

---

### Post by sotoj159 on 2010-01-12
Woo!! Thank you darkod!  It worked.  :D

And recluce, yea, I do have to go to the boot menu in order to choose ubuntu, but that's fine  :D

---

### Post by raymondh on 2010-01-12
Here's a suggestion that you may try on a rainy, boring day.  

You can edit grub.cfg to include your windows install as a boot option.  That way, if the HD is plugged when you start your system, you can get a choice between ubuntu or windows.  Of course, you have to set the external as first to boot in BIOS.  If the External is unplugged, then your system boots straight into windows as BIOS will then look for the next bootable device.

[http://ubuntuforums.org/showpost.php?p=7505203&postcount=1](http://ubuntuforums.org/showpost.php?p=7505203&postcount=1)

scroll to number 6.

Glad you have your system working.  Happy ubuntu-ing.

Raymond

---

