---
title: "Upgrade to 11.04 on Acer Aspire one AOA110 results in black screen"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by Geemacmcm on 2012-05-03
I am a relative beginner here, hopefully I will describe relevant information.

I had been successsfully running version 10.? on my Acer Aspire One AOA110 netbook and have upgraded to version 11.04, however on restarting after the install it does not completely boot up.  It gets to the login box and on entering the password the screen goes blank/black.

I have looked through the sticky post and can report the following
that Grub does load, 
after editing nosplash --verbose text, I don't think the linux kernel boots
Through the Grub menu I can run the failsafeX mode and get the software running, but there are messages about running in Low Graphics mode, as "card and input device settings could not be detected correctly."

In response to the command lspci | grep VGA the following is returned:-
00:02:0 VGA compatible controller: Intel Compatible Mobile 945GME Express Integrated Graphics Controller (rev03).

sudo hwinfo --moditor reports resolution of 1024x600 therefore:-

I tried editing GRUB and inserting the line
GRUB_GFXMODE=1024x600
running the grub update, and rebooting, without success.

Assistance will be greatly appreciated, if more information is needed to resolve this black screen, please let me know.
Thanks

---

