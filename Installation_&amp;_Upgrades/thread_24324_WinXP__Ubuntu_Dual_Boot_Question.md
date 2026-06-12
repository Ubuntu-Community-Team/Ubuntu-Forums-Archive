---
title: "WinXP / Ubuntu Dual Boot Question"
date: 2005-04-06
forum: Installation &amp; Upgrades
---

### Post by jkndrkn on 2005-04-06
My hda is 20gb.  I have an older install of winxp filling up the first 6gb of my hard disk. I plan on shrinking this partition to leave about 1gb of space.  Is this enough space to allow windows to function comfortably?

I plan on installing ubuntu on hda right after winxp. I want to avoid installing grub over my MBR, and I take it that the only other option you have is to install it to the same partition that ubuntu occupies?

If this is the case, must the ubuntu partition begin before the 1024 limit?

If I were to decide to let grub overwrite the MBR, could I conceivably install ubuntu beyond the 1024 limit or even to another hard disk hdb or hdc?

My previous experience with grub left me with an Error 17 message and a an unbootable system.

If I were to use Boot Magic and forego installing grub or lilo, could I install ubuntu beyond 1024 or on hdb or hdc? How reliable is Boot Magic in identifying ubuntu installs?

What do you suggest?

Thanks in advance..

---

### Post by CrashTECH on 2005-04-06
[QUOTE=jkndrkn]My hda is 20gb.  I have an older install of winxp filling up the first 6gb of my hard disk. I plan on shrinking this partition to leave about 1gb of space.  Is this enough space to allow windows to function comfortably?

I plan on installing ubuntu on hda right after winxp. I want to avoid installing grub over my MBR, and I take it that the only other option you have is to install it to the same partition that ubuntu occupies?

If this is the case, must the ubuntu partition begin before the 1024 limit?

If I were to decide to let grub overwrite the MBR, could I conceivably install ubuntu beyond the 1024 limit or even to another hard disk hdb or hdc?

My previous experience with grub left me with an Error 17 message and a an unbootable system.

If I were to use Boot Magic and forego installing grub or lilo, could I install ubuntu beyond 1024 or on hdb or hdc? How reliable is Boot Magic in identifying ubuntu installs?

What do you suggest?

Thanks in advance..[/QUOTE]
 I wouldnt shrink it that much... I have a 60 gb drive in my laptop... and I left 35+ some change for my XP install.... How much time do you plan on spending in XP? Keep that in mind too... I am going to spend about 60% of my time in XP and the rest in Ubuntu.

Unless you dont plan on having any software installed in XP then you might be able to leave out enough features/options in XP to have it be that small... (but why have it then?)

I would probalby leave XP with at least the 6 gb you have, maybe 8 or 9. I would also just install Grub with its defaults. Setting up dual booting for me was a cinche.

I used Partition Magic to divide up my drive (originally 57+ some change GB). I left about 20 for Ubuntu even though I really dont need that much space right now. my swap partition is 1992 MB I gave 102MB for boot, although I did not install grub to that, I let it install on the MBR. Then dumped the rest for /

Then again, I went through 3 different distros on the extra space before I settled with Ubuntu and I nuked everything that wasnt on my windows partition and started fresh for each install.

---

### Post by jkndrkn on 2005-04-06
[QUOTE=CrashTECH]Unless you dont plan on having any software installed in XP then you might be able to leave out enough features/options in XP to have it be that small... (but why have it then?)[/QUOTE]

Answer: hda contains winxp. Winxp applications and media files reside on hdb and hdc, respectively.

Additional question: Where did you place the boot partition? Before or after the windows partition. Is it within the 1024 limit? Does it have to be? Will grub detect ubuntu if ubuntu is beyond cylinder 1024?

Thanks for your replies. I think i'll be able to manage it this time.

---

