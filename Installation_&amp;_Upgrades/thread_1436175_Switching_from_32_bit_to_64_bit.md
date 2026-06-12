---
title: "Switching from 32 bit to 64 bit"
date: 2010-03-22
forum: Installation &amp; Upgrades
---

### Post by amonaaron on 2010-03-22
I got a new 64 bit computer and in my infinite wisdom I installed the server edition of Ubuntu 9.10. After some help from the forums I managed to correct that issue and now I'm running the 32 bit version of Ubuntu on my new machine on a dual boot with Windows7. 


What I'm wondering is if there is a way that I could possibly switch to the 64 bit version of Ubuntu 9.10 and still be able to boot my Windows OS. I know that I could remove the 32 bit Ubuntu and start fresh, but I'm concerned that if I do that I might not be able to boot the Windows OS, due to the replacement of the Windows boot with GRUB.

Any suggestions?

Thank you in advance.

---

### Post by phillw on 2010-03-22
> **amonaaron said:**
> I got a new 64 bit computer and in my infinite wisdom I installed the server edition of Ubuntu 9.10. After some help from the forums I managed to correct that issue and now I'm running the 32 bit version of Ubuntu on my new machine on a dual boot with Windows7. 


What I'm wondering is if there is a way that I could possibly switch to the 64 bit version of Ubuntu 9.10 and still be able to boot my Windows OS. I know that I could remove the 32 bit Ubuntu and start fresh, but I'm concerned that if I do that I might not be able to boot the Windows OS, due to the replacement of the Windows boot with GRUB.

Any suggestions?

Thank you in advance.

Hi,

Re-installing ubuntu won't harm your Win area. Grub will 'see' your Win installation and add it to the list.

If you have 'stuff' on your ubuntu area, now is a good time to make a seperate /home so it is saved when ever you do a re-install / fresh upgrade.

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Regards,

Phill.

---

### Post by amonaaron on 2010-03-22
Thank you very much Phil. I didn't think it would effect my Windows boot, but I hadn't had my coffee yet so my brain wasn't functioning all that clearly :p.

Thanks again.

Cheers,

Aaron

---

