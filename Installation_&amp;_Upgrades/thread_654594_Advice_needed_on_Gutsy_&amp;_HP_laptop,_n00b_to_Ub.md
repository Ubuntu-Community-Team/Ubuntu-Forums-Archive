---
title: "Advice needed on Gutsy &amp; HP laptop, n00b to Ubuntu"
date: 2007-12-31
forum: Installation &amp; Upgrades
---

### Post by Decman on 2007-12-31
I had an old HP laptop unused which I planned to install Linux onto so I could learn all about the OS:)

I downloaded Gutsy,burned a CD and booted from the DVD-ROM drive and everything worked OK. I installed on the HD and the problem started! I had a black screen for quite some time & then another screen which might have been a log-in screen but I couldn't read anything. I then read the advice on the forum about Gutsy & HP laptops, I know I should have read it first:) Anyway should I revert to Feisty which seems to be more compatible with HP laptops or should I perserve with Gutsy? If I am to perserve with Gutsy I need help on trying to get it to work properly. I am a complete n00by to Linux although years ago I did use DOS!

The laptop is a HP Omnibook VT6200, 512Mb RAM, 30GB HD, graphics card Radeon Mobility M6 LY.

Thanks.

---

### Post by logos34 on 2007-12-31
try this:
[https://help.ubuntu.com/community/WikiGuide/AtiX700Mobility?highlight=%28Mobility%29](https://help.ubuntu.com/community/WikiGuide/AtiX700Mobility?highlight=%28Mobility%29)
(in step 1 I believe it should be ctrl+alt+F**1**)

OR

boot into recovery mode and type:

sudo dpkg-reconfigure xserver-xorg

select 'vesa' driver.  You can mostly accept the defaults on the rest.  Reboot, and once logged into dektop enable ati restricted driver as above.

---

### Post by Decman on 2008-01-01
> **logos34 said:**
> try this:
[https://help.ubuntu.com/community/WikiGuide/AtiX700Mobility?highlight=%28Mobility%29](https://help.ubuntu.com/community/WikiGuide/AtiX700Mobility?highlight=%28Mobility%29)
(in step 1 I believe it should be ctrl+alt+F**1**)

OR

boot into recovery mode and type:

sudo dpkg-reconfigure xserver-xorg

select 'vesa' driver.  You can mostly accept the defaults on the rest.  Reboot, and once logged into dektop enable ati restricted driver as above.

Thanks for the help, I've tried the second suggestion but I still haven't solved the issue I think. I'll investigate further tomorrow and thanks again.

---

### Post by Decman on 2008-01-02
I can now log-in and everthing seems to work OK. I launched Restricted Drivers Manager but the message I got back said my h/w didn't need any restricted drivers. Any advice on how to get the correct driver for the ATI Radeon card?

Thanks for the help/

---

### Post by torgrot on 2008-01-02
Which Radeon do you have?  They have discontiued support for some of the older cards.  If yours is one of them then there isn't a restricted driver for it.

torgrot

---

### Post by Decman on 2008-01-02
Torgrot the card is a Radeon Mobility M6 LY,thanks for any help.

---

