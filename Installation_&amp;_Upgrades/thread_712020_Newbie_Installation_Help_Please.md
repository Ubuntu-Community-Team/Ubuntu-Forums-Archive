---
title: "Newbie Installation Help Please"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by Loudog21 on 2008-03-01
I'm trying to install Ubuntu on a Gateway 7405 labtop

I think i need the AMD 64 version of Ubuntu from the website, so thats what i downloaded and burned. 
Do you need to do anything to the install disk other than durning the iso image onto it?
Ive repartitioned the hardrive but the computer wont install from the disc, I'm fairly sure i correctly set the BIOS.
Im probably missing somthing pretty obvious...

---

### Post by Pumalite on 2008-03-01
Burn a new CD Do md5sun on the iso, burn at 4x or less in good quality CD-R media as an 'image' not 'data', check for CD integrity before install.
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Post your specs. You might need the Alternate CD

---

### Post by Loudog21 on 2008-03-01
Ok, how do i find the specs?
like I said, very new to all of this
and its an old computer so i dont remember from buying it
would that be in bios or something?

---

### Post by Pumalite on 2008-03-01
Get a Knoppix Live CD: [http://www.knopper.net/knoppix/index-en.html](http://www.knopper.net/knoppix/index-en.html)
Burn to disk and boot from it.
Go to the Terminal and post the output of:
lshw

---

### Post by Loudog21 on 2008-03-01
I told it to boot off the Knoppix cd, it thought about it, but then loaded windows...?

---

### Post by Loudog21 on 2008-03-01
Maybe I downloaded the wrong file or version?
KNOPPIX_V5.1.1CD-2007-01-04-DE.torrent

Is there any way to get specs off of xp?
windows, despite several attempts to remove it, is still on the computer

---

### Post by Pumalite on 2008-03-01
Make sure you set CD as 1st in boot order in your BIOS
Make sure you burn isos as image and not data.

---

### Post by Loudog21 on 2008-03-01
Sweet, I think that fixed it.
I downloaded the free burning software and told it to burn as an image

i think its working fine now,
thanks for the help

---

### Post by Pumalite on 2008-03-01
Good luck.

---

