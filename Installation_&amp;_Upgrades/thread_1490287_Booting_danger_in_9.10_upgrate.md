---
title: "Booting danger in 9.10 upgrate"
date: 2010-05-22
forum: Installation &amp; Upgrades
---

### Post by John_Rose1 on 2010-05-22
I am working with a triple boot Ubuntu 9.04-Vista-XP with grub in the Ubuntu partition. I used EasyBCD to configure the MBR. When installing I did not install 9.10 because the documentation (at least on the French community site) said that starting with 9.10 Ubuntu uses grub2 which is incompatibile with EasyBCD.

In the update manager I have a box to click to upgrade to 9.10. My question is: if I upgrade in this way, is there a danger that my triple boot will be broken (installation of grup2)?

If it is save to upgrade, does that mean that if I upgrade I will not loose any personal data or settings? I have my personal data in a separate home partition.

Thanks and best regards, John

---

### Post by darkod on 2010-05-22
> **John_Rose1 said:**
> I am working with a triple boot Ubuntu 9.04-Vista-XP with grub in the Ubuntu partition. I used EasyBCD to configure the MBR. When installing I did not install 9.10 because the documentation (at least on the French community site) said that starting with 9.10 Ubuntu uses grub2 which is incompatibile with EasyBCD.

In the update manager I have a box to click to upgrade to 9.10. My question is: if I upgrade in this way, is there a danger that my triple boot will be broken (installation of grup2)?

If it is save to upgrade, does that mean that if I upgrade I will not loose any personal data or settings? I have my personal data in a separate home partition.

Thanks and best regards, John

Upgrading like that should leave grub1 because it needs to be upgraded separately to grub2, which you don't have to do.
However, any upgrade can go wrong, so having a backup on external disk is always recommended, even though /home is separate.

If you really insist using EasyBCD and grub1, there is even option to make a clean install of 10.04 because it has the benefit of being LTS and you have separate /home, so a clean install would be simple. But in the last screen of the installer, hit the Advanced button and tell it not to install a bootloader (grub2).

Then you can chroot into the installation and add grub1 on the partition, as it is now.

Depending how you feel like playing with that. Personally, grub2 does a great job of booting any OS and even recovery partitions, so it depends why you want to keep EasyBCD and windows bootloader so desperately. Grub2 would make all of this so easy.

Don't forget, 9.04 stops being supported in 6 months. And the new 10.04 is LTS with support for next 3yrs.

---

### Post by John_Rose1 on 2010-05-23
Thanks so much, darkod,

I am not so technically versed, so please let me summarise what you said (with some things which seemed implicit), could you please correct/expand on as appropriate?

I understand that upgrading to 9.10 from 9.04 from within Ubuntu is different from doing an installation from a 9.10 boot CD-ROM, in that it does not replace grub1 with grub2. I guess that 9.10 instead of 10.04 is offered in this way because 10.04 has features which cannot readily be installed this way?

I started with a Vista machine, then installed Ubuntu with the idea of migrating with access to Vista for special needs, then found that Vista does not handle some of my legacy software and also intalled XP. I do not really need Vista (just have to find the time to migrate all my Windows applications to XP), but I really do need to maintain the Ubuntu-Windows boot choice for the foreseeable future [and the French documentation implied that EasyBCD works more simply and reliably with the Vista BCD than with the XP BCD].

Here I do not understand your reference to your comment "Depending how you feel like playing with that. Personally, grub2 does a great job of booting any OS and even recovery partitions, so it depends why you want to keep EasyBCD and windows bootloader so desperately. Grub2 would make all of this so easy." I used EasyBCD only because it is the solution recommended on the French Ubuntu site. If there is a (relatively staightforward) way to maintain my tiple (or double) boot using grub2 instead, then I would appreciate your pointing me to the instructions.

So, unless there is something new in reponse to the above para, I propose to undertake the following steps:
1) Back up my home directory, and click to upgrade to 9.10 with the knowledge that it in principle will not upgrade grub1 and that my triple boot will work.
2) Later, with a bit more confidence, do a clean upgrade to 10.04 following your instructions.

                                        Best regards, John

---

### Post by darkod on 2010-05-23
Yes, the upgrade 9.04->9.10 doesn't replace grub1. 9.10 is offered because you can only do upgrade to the next version, you can't jump over one.
The exception is that you can also upgrade from LTS to LTS version. 10.04 is LTS (Long Term Support) and the last LTS was 8.04.

Right now you are using windows bootloader and using EasyBCD to help you make entries in it. Usualy you would do this if you have some special setup and grub can work for you from the MBR. Or when you are nervous and new to grub, so people feel uncomfortable to let it overwrite the windows bootloader.

Grub1 and grub2 can easily boot other OSs, including XP, vista, 7, etc. Grub2 is even better in locating other OSs and does it automatically.

The windows bootloader can't detect linux by itself, and that's why you needed EasyBCD to make the entry for ubuntu. I prefer using grub installed on the MBR, but what you choose to use is up to you.

If you want to do the upgrade to 9.10, back up all your data first, because sometimes upgrades can go wrong. Also, it's always better to download the image for the version you want to upgrade to, and try it in Try Ubuntu option. If it doesn't work in live mode, don't do the upgrade before you investigate what the problem is, because most probably the upgraded ubuntu won't work too.

In your case it might be worth considering to back up the data and do a clean install of 10.04 (not upgrade). You can even make the switch to using grub2 on your MBR and let it install grub2 there. Grub2 will boot your XP and vista just fine. This is because even by upgrading to 9.10, you'll still have to upgrade to 10.04 in near future, so it just doubles the work.

Ubuntu issues LTS releases just for the purpose not to have to upgrade all the time. You don't have to upgrade even now. But the 'standard' releases are supported for 18 months while LTS for 3yrs.

So, 9.04 is already one year old and will be supported only for 6 months more. If you install 10.04 now, it will be supported for 3yrs and the next LTS is due in 2yrs. You don't have to upgrade to 10.10, 11.04, etc. If you are happy how your system is working, don't upgrade until the next LTS in two years. By then, you will probably want a newer OS anyway. :)

---

