---
title: "What's wrong with our PC?"
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by Julia A on 2008-04-19
Hi
I've been advised to try this forum to see whether anybody can identify what might be wrong with our PC (I used Ubuntu 7.10 desktop version when Windows failed to install.  I don't have any previous experience of Linux):

Our PC, with a Q6600 processor, Foxconn motherboard, and running Windows  XP MCE, recently refused to load Windows (just kept freezing at startup). Since our warranty was unfortunately invalid (it was an Evesham PC, purchased last year, and Evesham have gone bankrupt), I decided to try to identify the problem. After trying all the simple options, I reinstalled Windows, but then was told I had to reactivate Windows. I tried to do this by phone, quoting the number generated, but was told that it was invalid because the PC wasn't recognised. It was this that made me wonder whether the motherboard had died.]
:(

Anyway, I then decided to try to install Linux Ubuntu (from a CD). The initial installation screen came up ok. However, I then had a whole screen full of error messages (examples: "Failed to accept xfer mode", "Device not accepting address 3, error 110" "Ata5.00 revalidation failed errno=-5", "ata6.01 exception e-mask 0x0 SAct oxo SERR 0X0 action 0X2 frozen")

I have had a look on various forums to see what might be the problem, but the technical details are a bit beyond me. The PC beeps when it starts up, and there are also green lights for the DVD writers. I've opened the case and the fans on the motherboard, on the PSU, and an external one on the case are all functioning.

Grateful for any thoughts.

---

### Post by overdrank on 2008-04-19
> **Julia A said:**
> Hi
I've been advised to try this forum to see whether anybody can identify what might be wrong with our PC (I used Ubuntu 7.10 desktop version when Windows failed to install.  I don't have any previous experience of Linux):

Our PC, with a Q6600 processor, Foxconn motherboard, and running Windows  XP MCE, recently refused to load Windows (just kept freezing at startup). Since our warranty was unfortunately invalid (it was an Evesham PC, purchased last year, and Evesham have gone bankrupt), I decided to try to identify the problem. After trying all the simple options, I reinstalled Windows, but then was told I had to reactivate Windows. I tried to do this by phone, quoting the number generated, but was told that it was invalid because the PC wasn't recognised. It was this that made me wonder whether the motherboard had died.]
:(

Anyway, I then decided to try to install Linux Ubuntu (from a CD). The initial installation screen came up ok. However, I then had a whole screen full of error messages (examples: "Failed to accept xfer mode", "Device not accepting address 3, error 110" "Ata5.00 revalidation failed errno=-5", "ata6.01 exception e-mask 0x0 SAct oxo SERR 0X0 action 0X2 frozen")

I have had a look on various forums to see what might be the problem, but the technical details are a bit beyond me. The PC beeps when it starts up, and there are also green lights for the DVD writers. I've opened the case and the fans on the motherboard, on the PSU, and an external one on the case are all functioning.

Grateful for any thoughts.

HI and welcome, if I am understanding your right, you did install windows but could not activate it correct? Then this would mean that your motherboard is not dead. The errors with the live cd are unknown to me but have you checked the disc for errors and you may want to do a checksum on the cd 
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by Whiffle on 2008-04-19
I'd be suspect of the hard drive.

---

### Post by Pumalite on 2008-04-19
I think it's a bad burn, but would try the Alternate CD.
You can check your HDD with TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by Tomatz on 2008-04-19
Its either your HDD or ram (most probably your ram as the live cd loads into ram not your hdd as you have no swap).

To test the ram you can do a memtest from the ubuntu live cd (the bootscreen). Run it for a few hours to be sure.

To test the hdd download the following and burn the .iso to cd to do a hdd health test:

[http://www.download3k.com/System-Utilities/File-Disk-Management/Download-IBM-Hitachi-Drive-Fitness-Test.html](http://www.download3k.com/System-Utilities/File-Disk-Management/Download-IBM-Hitachi-Drive-Fitness-Test.html)

---

### Post by pietjanjaap on 2008-04-19
Check de cd for bad sectors, boot from the cd and choose to check the cd.

---

