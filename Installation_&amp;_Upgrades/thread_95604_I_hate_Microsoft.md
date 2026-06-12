---
title: "I hate Microsoft"
date: 2005-11-26
forum: Installation &amp; Upgrades
---

### Post by aznboi on 2005-11-26
yea so on my laptop, there is one HD. But it is split up into two partitions. It used to be Windows and Ubuntu, but seeing as how i didnt really need windows anymore, i erased partition one and had a free partition. My cousin gave me a Windows XP Home SP2 CD, but I already had a Windows XP Pro SP2 cd... but i decided to install that cd onto the free partition anyway.... y i did it stumps me 2:confused: ... i think it just cuz i was bored.... anyway halfway through setup i was like screw it i hate Msoft, so i turned it off and wnated to go to Ubuntu to use gparted to wipe that partition again...but..... windows had already "fixed" my MBR for me and grub wasnt showing up!:???: so now i cant get into my ubuntu....but i am installing SuSE 9.3 on it so grub can come back and hopefully recognize my Ubuntu... I think it might be eaiser to use a Live cd and i do have the latest version of koppix on a dvd.. but cant do it now since im waiting for SuSE to finish.... well yea if i do get Ubuntu booted back, how can i restore its GRUB? cuz i plan on wiping partition one again so i can have some free space for my Ubuntu...

---

### Post by Xian on 2005-11-26
[QUOTE=aznboi]well yea if i do get Ubuntu booted back, how can i restore its GRUB? cuz i plan on wiping partition one again so i can have some free space for my Ubuntu...[/QUOTE]
Boot into Ubuntu, then issue this command:

$ sudo grub-install /dev/hdx

where 'x' is your HD letter

---

### Post by taurus on 2005-11-26
SuSE should pick up your Ubuntu and has an entry for you.  Otherwise, you can always add that to SuSE's /boot/grub/menu.lst.  Then, pick Ubuntu from the menu and after it finishes booting, you just install GRUB on MBR (from Ubuntu) again...

---

### Post by aznboi on 2005-11-26
[QUOTE=Xian]Boot into Ubuntu, then issue this command:

$ sudo grub-install /dev/hdx

where 'x' is your HD letter[/QUOTE]

thnx once SuSE finishes installing (15 or so minutes...) ill boot into Ubuntu and try that. Thnx

[quote="taurus"]SuSE should pick up your Ubuntu and has an entry for you. Otherwise, you can always add that to SuSE's /boot/grub/menu.lst. Then, pick Ubuntu from the menu and after it finishes booting, you just install GRUB on MBR (from Ubuntu) again...[/quote]
Yea i think i did see it was detected by SuSE when they asked about the bootloader...thnk goodness. SuSE is great and all, but i like Ubuntu:D

EDIT
O yea and sry for all the people with a real problem... i moved all ur posts down one... lol

---

