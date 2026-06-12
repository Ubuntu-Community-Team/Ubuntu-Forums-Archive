---
title: "error: no such device: 5a5ecb88-7c3d-468c-a351-e9edc6d4a154."
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by bouchedorée on 2012-05-01
Hy everyone, i am using a Acer Aspire One 721 and just tried to update from 11.10 to 12.04, the installation blocked and I was forced to shut down. I rebooted from USB and made a clean install of 12.04 and all went ok. After installation I installed additional drivers for my acer but while installing the graphic driver, the system crashed. When I rebooted I got a black screen with only the cursor blinking. No way to get in the recovery mode. I tried to boot from USB and wanted to maybe re install ubuntu 12.04 but got a Grub error. Not finding a solution in the Internet I thought I install fedora on the whole disk and this way eliminate all other systems installed. Fedora worked fine and I tried to install ubuntu 12.04 again from USB but got following error:  
 

 error: no such device: 5a5ecb88-7c3d-468c-a351-e9edc6d4a154.
 Grub rescue> _
 

 I also tried installing ubuntu 10.10 that I had on an old CD and got a similar error.... did not have problems installing other linux os like puppy or fedora.

 

 Is there any wai to get ubuntu working again??
 Since I tried the first upgrade to 12.04 the system continues crashing randomly also when not using... any help would be great. Thx

---

### Post by bouchedorée on 2012-05-01
I'm not new to linux but not really into it yet so be slow wiht me!!

Acer Aspire One 721, AMD Athlon II Neo Processor k125 (1.7 Ghz), 2 GB DDR3 Memory, 320 GB HDI storage.

---

### Post by bouchedorée on 2012-05-01
also fedora seems not to srat eny more after reboot. I get following error message:

error: ELF header smaller than expected.
Entering rescue mode...
grub rescue> _

---

### Post by darkod on 2012-05-01
First of all, does 12.04 work fine in live mode from the cd? Does it load and work correctly?

If it does, you can do the install again, BUT ONLY ONCE, and if grub2 gives an error to boot you might need to update grub2 on the MBR only. DO NOT reinstall again. Only once.

---

### Post by bouchedorée on 2012-05-02
When trying to boot from cd i get the error:   

**error: no such device: 5a5ecb88-7c3d-468c-a351-e9edc6d4a154.**

when booting from hard disk i get: 

[B]GRUB loading.
Welcome to GRUB
error: ELF header smaller than expected.
Entering rescue mode...
grub rescue> _[/B]

I think i have tried to install it more than once... could that be the problem? I only get this two errors, no matter what i do. Except for other os like fedora or puppy, they load fine from cd and work without problems. Only Ubuntu wont work from live cd, 12.04 does not and neither do other versions (i tried 10.10).

Thanks a lot for the help, i'm quite a newbie but love ubuntu!!

---

### Post by darkod on 2012-05-02
Booting from cd shouldn't give you errors about UUID, only booting from hdd can do that. Are you sure you have the cd created correctly and you are booting from it?

---

### Post by bouchedorée on 2012-05-02
**You where right**, there is a problem with the ubuntu 12.04 USB that i created and used for the first install... dont understand why it is not working anymore, it worked fine at the first install... **i get the same error on other pc when booting from USB**. I'm now downloading ubntu-12.04-desktop-i386.iso again and will create a other bootable USB. I'll install it and let you know if all goes fine!! 

**Thanks a lot in the mean time!!**! Stupid mistake I made assuming the USB should work... thx

---

