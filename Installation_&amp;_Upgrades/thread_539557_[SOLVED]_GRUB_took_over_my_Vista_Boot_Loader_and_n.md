---
title: "[SOLVED] GRUB took over my Vista Boot Loader and now Vista won't boot"
date: 2007-08-31
forum: Installation &amp; Upgrades
---

### Post by JawsThemeSwimming428 on 2007-08-31
I have been running Ubuntu for about a year and a half with minimal issues. After issues with a new Velocity Micro ProMagix Vista machine, a KVM switch, and my Linux PC I decided to negate the KVM and install my Ubuntu HDD in my new ProMagix Vista machine. I installed the Ubuntu HDD and everything went fine, I just had to reinstall Ubuntu, no big deal. Once it was all said and done my boot manager was GRUB. However, I want to use the Vista Boot Manager for warranty purposes. I used EasyBCD 1.6 to attempt to use the Vista Boot Loader and it kind of worked. The problem was both boot loaders, GRUB and Vista were starting and I would have to select the OS twice. So I changed one of the Entries in EasyBCD and now GRUB starts and still takes me to the Vista Boot Loader, but when I select Vista it goes to the Boot Manager Screen and says Windows Vista can't start because of a recent hardware or software change. Then it gives me a file that it says is either missing or corrupt (\Windows\system32\winload.exe). I assume that is the Vista boot loader file? I do not have a Vista install disc as the manufacturer "forgot" to send me one with this nearly $2000 machine. I will have a Vista install disc sometimes next ween but is there any way to repair it before that? ...and will that even work? I am at a standstill and would appreciate anyone willing to work with me on this. If I failed to mention this, Feisty still boots but it won't recognize my Linksys Compact Wireless-G USB Adapter so I do not have Internet on it. I am taking a laptop from work home this weekend so I can communicate with the Forum. Anyone that can work with me, if there is a good time please let me know! I appreciate all help!!!!!

---

### Post by Steve1961 on 2007-08-31
I'm not sure what you can do about this problem without a disk that lets you into the vista recovery environment.  Once you have a disk you should just need to do the following:

Bootrec /rebuildbcd

---

### Post by JawsThemeSwimming428 on 2007-08-31
Thanks for the response...I guess I will have to wait. I am still open to ideas so keep them coming!

---

### Post by JawsThemeSwimming428 on 2007-08-31
My question is then, I am not sure what I did wrong. My Vista machine was pre-configured. Vista is on its own 400GB SATA HDD and it is in the first SATA position. I took my 40GB Western Digital Caviar SATA HDD and put it in the SATA slot right below the Vista drive. I booted to the Feisty Live CD and installed Feisty on the 40GB drive ( I am positive I selected the right one, it said 40GB and not 400GB) and the install went fine. I rebooted and GRUB loaded and allowed me to choose if I want Vista or Feisty. I picked Vista and everything was fine. I then tried using EasyBCD to use the Windows Boot manager instead of GRUB (because that is the way I wanted it set up), and I rebooted. Again, GRUB loaded and I selected Windows Vista, THEN it took me to the Vista Boot loader and I had to pick Vista again. I found some information on why this might be and edited the Entries in EasyBCD, rebooted, and "poof" Vista would not start. Feisty will start up, but I do not have wireless configured yet and wired is not available. How should I go about setting these up when I get the Vista Install DVD?

---

### Post by Steve1961 on 2007-08-31
> **JawsThemeSwimming428 said:**
> My question is then, I am not sure what I did wrong. My Vista machine was pre-configured. Vista is on its own 400GB SATA HDD and it is in the first SATA position. I took my 40GB Western Digital Caviar SATA HDD and put it in the SATA slot right below the Vista drive. I booted to the Feisty Live CD and installed Feisty on the 40GB drive ( I am positive I selected the right one, it said 40GB and not 400GB) and the install went fine. I rebooted and GRUB loaded and allowed me to choose if I want Vista or Feisty. I picked Vista and everything was fine. I then tried using EasyBCD to use the Windows Boot manager instead of GRUB (because that is the way I wanted it set up), and I rebooted. Again, GRUB loaded and I selected Windows Vista, THEN it took me to the Vista Boot loader and I had to pick Vista again. I found some information on why this might be and edited the Entries in EasyBCD, rebooted, and "poof" Vista would not start. Feisty will start up, but I do not have wireless configured yet and wired is not available. How should I go about setting these up when I get the Vista Install DVD?


After installing Ubuntu what you really needed to do at that stage was overwrite grub with the vista bootloader.  I thought EasyBCD had on option for reinstalling the vista bootloader, but you could also do that with an installation CD.  This should have restored the vista bootloader.  You would then need to install grub to the Ubuntu root partition, and once done, you could add it to the vista bootloader via easybcd.

---

