---
title: "Install Ubuntu on new win8 laptop"
date: 2013-12-26
forum: Installation &amp; Upgrades
---

### Post by patriq on 2013-12-26
Good day Ubuntu team,

First I thank you for any and all assistance and wish all those reading this happy holidays.

I have recently purchased a new laptop: an Asus notebook; asus x102b,

and much to my discomfort as a user it came pre-loaded with ms win8, an operating system I can not bare to use. It is my intention to somehow circumvent win8 and load directly into an Ubuntu environment on startup, however I fear completely formatting and re-installing with a new OS will void the warranty and I must admit I am hesitant to proceed without a second opinion having heard from the saleperson that the hard drive among other components have been rigged to prevent the installation of any OS other than the pre-installed win8.

As a solution I was hoping I may partition my hard drive, allocating 10 to 20gb to win8 and dedicate the remainder of the hard drive to Ubuntu. Is this possible?

Could this setup be configured so that my computer loads directly into Ubuntu on startup with full admidnistrative rights to my machine and without the slightest indication that win8 is tucked away into a partition never to be logged into again? 
-if yes, how may this be accomplished?

Finally, I have only ever installed Ubuntu using an Iso file bunt on dvd and my new computer has no optical drive, thus I pressume I will have to install Ubuntu using a usb-install, something I've never done thus I come to you for your thoughts and advice.

Is this a good solution? May I ask for your opinion please?

Best,

patriq

---

### Post by oldfred on 2013-12-26
Do not know about your specific model. Some work pretty easily, others not so much. Worst case is to install Ubuntu in BIOS boot mode which works with gpt partitioned drives. You cannot easily dual boot from grub menu, but have to chose which system to boot from UEFI menu and may have to turn on UEFI or turn off CSM/BIOS/Legacy boot mode. Some auto switch as it knows how each is installed. But UEFI and BIOS are not compatible and once you start booting one system you cannot switch to the other boot mode.

Windows really wants 30% free space to work, so do not shrink too much. At 10% free it slows to a crawl.

Best to turn off secure boot. You must in Windows turn off its fast boot or always on hibernation. Resize Windows using its internal disk tools and reboot so it runs chkdsk. If chkdsk needed flag or hibernation flag are set, Ubuntu will not see Windows and a install may overwrite it totally. Always best to fully backup Windows and efi partition, even if you may not use it much. You may want to sell computer later and buyer may want Windows.

Lots of details in link in my signature. 

What video card/chip, and is it an ultrabook with the small SSD? That adds to difficulty but you can still install.

Flash drive installs are just like DVD except they are a bit faster. Instructions on flash drive install are on page to download Ubuntu. Best to use newest 13.10 as it is a new computer. Older versions of Ubuntu do not have as up-to-date UEFI nor Intel support.

---

