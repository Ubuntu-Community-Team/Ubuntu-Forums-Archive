---
title: "BIOS help. I Only have two options."
date: 2011-05-13
forum: Installation &amp; Upgrades
---

### Post by SunshineFolk on 2011-05-13
Ok this may be an easily answered question, but I have no idea how to google it :confused:, since there is so much information on BIOS that appears and none of it pertains to me.

I installed ubuntu 11.04 on two separate hard drives. My grub menu is on my 2nd HD which also has ubuntu. My default BIOS is to boot my 1st HD. Every time I boot up my PC, I have to hot-key my BIOS to be able to choose which HD to load, because if I dont obviously my other HD takes over.

So with that being said, when I attempt to access my BIOS (used to work fine with one HD) it gives me its own version of grub (or whatever it would be) to choose between my disc tray, 1st HD, or 2nd HD. My other option is to press esc to begin default startup (which is HD 1). So now my question is, how do I access BIOS from this menu?? There is no other option to bypass this menu to change my boot sequence. My grub is on my 2nd HD which I would like to make my default startup, so from there I can choose either one to boot. Its not really a huge problem, but I hate having to press a button to get to BIOS boot screen every single time I restart or turn my computer on. Its getting very old.   And if I dont press it then it goes straight to 1st HD...obviously...

Please help. Ive googled the hell out of this and dont really know what to type for a search. I definately use google :lol: , but it has failed me this time!! haha.

---

### Post by Quackers on 2011-05-13
Welcome to UF :-)
It sounds to me as though you are expecting to get into your bios in order to make permanent changes.
This is not done my using the "hot-key" as you call it. It is done by tapping a key at boot up. This key varies with different manufacturers and even different models.
It is often the Del key, F2, F11 or ctrl + F11. There are many, but you need to find out which one works for your computer. It may be in your computer's documentation or maybe if you visit the manufacturer's website.

In fact, there is sometimes a mention of the key to press in a splash screen as boot up begins.

---

### Post by lmarmisa on 2011-05-13
Welcome to the forums.

I would like to confirm if you have installed Ubuntu 11.04 not only in your second HD but also in your first one. 

Could you type these commands and post here the results?

```

sudo fdisk -l
sudo parted -l

```

---

