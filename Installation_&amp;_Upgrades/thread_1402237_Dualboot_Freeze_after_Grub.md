---
title: "Dualboot: Freeze after Grub"
date: 2010-02-08
forum: Installation &amp; Upgrades
---

### Post by Nedrah on 2010-02-08
Hey everyone,

hopefully one of you will be able to help me out here. 

I just tried a dual installation. Win7 sits on my internal HDD, Ubuntu has a partition on my external HDD. The external Hdd is set up to have ~900GB of NTFS file storage and ~100GB for / (ext4) and a seperate swap partition. I partitioned it that way from the livecd installer. I have to say that I'm basically fresh out of ideas.

I can boot Ubuntu 9.10 64bit just fine from a Usb stick. Installation also worked fine, I had the installer install Grub on the external Hdd. I am quite sure that it actually *is* on the external hdd, since unplugging it as well as changing the boot order to internal hdd first results in a straight boot to Win7. 

Anyways, booting from the external device, I get as far as the grub OS selection prompt. Windows 7s loader can be started without any problem from here. However, choosing Ubuntu (recovery or not) results in... nothing. The system plain simply freezes up (I gave it some time) and can only be reactivated by resetting it. 

So far, I tried manually editing the boot entry by pressing "e". I changed the root entry from 2,2 to 2,0 to 2,1 to 2,3 and 2,5. Afterwards I tried booting by pressing ctrl+x. The result always stays the same. No boot, frozen system. 

Pc: C2D E6750, Gf8800GT,4GB Ram. 
Pastebin of grub.cfg: [http://pastebin.com/m53a5d6eb](http://pastebin.com/m53a5d6eb)

I'd be more than thankful for any assistance you might be able to offer.

---

### Post by Nedrah on 2010-02-09
Someone?

---

### Post by oldfred on 2010-02-09
Plug in the external and run this script:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

