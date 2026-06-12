---
title: "Bad iso ?"
date: 2008-06-05
forum: Installation &amp; Upgrades
---

### Post by RWells on 2008-06-05
I have been trying to install Ubuntu8.04 since the lts release on three AMD sempron based machines, with Nvidia geforce mx4000 pci cards.

I down loaded three iso images using bittorent from a mirror that I cant remember now. 
All three passed the md5 checksum and all three passed the disk integrity check prior to installation.

I fought with video driver problems for over a month, after install it would boot to a black screen with no command prompt.
I would then have to reboot and select recovery mode to get to a command prompt.

Then I would have to edit xorg.conf,multiple times, still not sure what I would do to eventually force it into low graphics mode.

Then I would eventually get the nvidia drivers installed and once I even had one machine working with full 3d capabilitys with compiz-fusion,cube desktop and the works.

Then One of the updates blitzed the drivers and I was back to the low graphics mode, and never could get the nvidia driver installed after the update.

Now keep in mind this is three different machines, and three different LiveCds, created from three different iso images.

Well, My wife got madd about me always having her computer down so she could check her email and went to walmart and bought her a Acer Aspire M1100 for $500.

The Acer has Windows Vista and worked fine out of the box.

Well one day she left the house and I couldnt leave well enough alone and decided to try to install Ubutu on her new computer:(

So I went to ubuntu.com and down loaded 8.04 but not the torrent.

I down loaded from the 
[http://astromirror.uchicago.edu/ubuntu-releases/](http://astromirror.uchicago.edu/ubuntu-releases/)
mirror.

Well the install went flawless, all the hardware was recognized, including the nvidia 8800 gt video card I had added.

Well this made me happy:)

Then I  decided to try to install on one of the other three machines again, but this time I used the cd I had used on the new Acer.

Wow, Installed perfect!! no video driver issues at all.

So I decided to try the other LiveCD's I had created.

No Love, had the same video driver issues.

So now I have three cd's that passed the checksum and cd integrity test that will not install with out having video driver issues, and one cd that I never checked the md5 checksums, that installs perfect on all four machines?

Anyone care to venture what might be the problem?


Rusty

---

### Post by VMC on 2008-06-05
> **RWells said:**
> I have been trying to install Ubuntu8.04 since the lts release on three AMD sempron based machines, with Nvidia geforce mx4000 pci cards.

I down loaded three iso images using bittorent from a mirror that I cant remember now. 
All three passed the md5 checksum and all three passed the disk integrity check prior to installation.

I fought with video driver problems for over a month, after install it would boot to a black screen with no command prompt.
I would then have to reboot and select recovery mode to get to a command prompt.

Then I would have to edit xorg.conf,multiple times, still not sure what I would do to eventually force it into low graphics mode.

Then I would eventually get the nvidia drivers installed and once I even had one machine working with full 3d capabilitys with compiz-fusion,cube desktop and the works.

Then One of the updates blitzed the drivers and I was back to the low graphics mode, and never could get the nvidia driver installed after the update.

Now keep in mind this is three different machines, and three different LiveCds, created from three different iso images.

Well, My wife got madd about me always having her computer down so she could check her email and went to walmart and bought her a Acer Aspire M1100 for $500.

The Acer has Windows Vista and worked fine out of the box.

Well one day she left the house and I couldnt leave well enough alone and decided to try to install Ubutu on her new computer:(

So I went to ubuntu.com and down loaded 8.04 but not the torrent.

I down loaded from the 
[http://astromirror.uchicago.edu/ubuntu-releases/](http://astromirror.uchicago.edu/ubuntu-releases/)
mirror.

Well the install went flawless, all the hardware was recognized, including the nvidia 8800 gt video card I had added.

Well this made me happy:)

Then I  decided to try to install on one of the other three machines again, but this time I used the cd I had used on the new Acer.

Wow, Installed perfect!! no video driver issues at all.

So I decided to try the other LiveCD's I had created.

No Love, had the same video driver issues.

So now I have three cd's that passed the checksum and cd integrity test that will not install with out having video driver issues, and one cd that I never checked the md5 checksums, that installs perfect on all four machines?

Anyone care to venture what might be the problem?


Rusty

Does the md5sum or crc match on all three cd's? In other words, maybe there was and update and that's what you downloaded on the one that worked.

I would think if the cd was flawed in any way , it would have errored out.

BTW_ what happened when your wife returned and found out that you messed with her new pc :)

---

### Post by wpshooter on 2008-06-05
Are all 3 of the CD media the same brand and media type ?

I use only Sony or Imation CD-RWs.

Also, is the firmware up-to-date on ALL of your CD drives that you are using to burn these CDs ?

Good luck.

---

### Post by RWells on 2008-06-05
> **VMC said:**
> Does the md5sum or crc match on all three cd's? In other words, maybe there was and update and that's what you downloaded on the one that worked.

I would think if the cd was flawed in any way , it would have errored out.

BTW_ what happened when your wife returned and found out that you messed with her new pc :)

I will try to check the checksum on the good iso.

Luckly the Ubuntu install on the wifes comuter went well so I didnt have her madd for messing somthing up, and she likes Ubuntu, so she is using it instead of Vista.:)

---

### Post by RWells on 2008-06-05
> **wpshooter said:**
> Are all 3 of the CD media the same brand and media type ?

I use only Sony or Imation CD-RWs.

Also, is the firmware up-to-date on ALL of your CD drives that you are using to burn these CDs ?

Good luck.All 4 cd's are Imation CD-R,
Do not know about the firmware on the drives, will try to check this weekend when I have time to play.

---

