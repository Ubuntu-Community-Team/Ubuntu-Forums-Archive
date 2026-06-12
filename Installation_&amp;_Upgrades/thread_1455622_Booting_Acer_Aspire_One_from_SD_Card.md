---
title: "Booting Acer Aspire One from SD Card"
date: 2010-04-16
forum: Installation &amp; Upgrades
---

### Post by uncleBern on 2010-04-16
Hi (Newby here) - but don't let that stop you helping please... :)

I'm trying make my Acer Aspire One (with the early terrible slow SSD) work without me just getting crazy at the slow speeds. 

To solve this I want to run from Linux on my SD card. - but since Acer won't boot from the SD I'll have to have keep Linux on the HD so will boot into Grub and then I can select the Version on the SD to load.
*This is based on a few posts of people who have done this - but they are all last year or so and so use older OS which runs Grub - rather than Grub2 .*

I've tryed using Ubuntu UNR and Mint. - the installs work fine, but what I have at the moment is:
Mint workin on SSD and its Grub shows the Mint version on my SD card.

But when I select that I just get:[FONT=Courier New]
[/FONT][INDENT][FONT=Courier New]error: no such device: 1d72305e-b3d7-488e-b319-c01712b2d49e  [/FONT]
[/INDENT]I thought maybe the solution would be that SD version should have no Grub - but doesn't make a difference. 
I've tried a few different installs, UNR Mint, partitioning & boot options, I've had a poke around in grub config but cant find what should be changed.
I'm sure this is possible, and I'm certainly not the 1st to try to do it.

ref: 

[LIST]
[*][http://www.ubuntusolutions.org/2009/05/how-to-make-the-acer-aspire-one-faster.html](http://www.ubuntusolutions.org/2009/05/how-to-make-the-acer-aspire-one-faster.html)
[*][http://www.osnews.com/story/20743/Eeebuntu_2_0_SD_Card_Installation_on_the_Aspire_One](http://www.osnews.com/story/20743/Eeebuntu_2_0_SD_Card_Installation_on_the_Aspire_One)
[/LIST]

Incidentally I had before tried to solve the slowness by running swap on the SD, but still too slow.

---

