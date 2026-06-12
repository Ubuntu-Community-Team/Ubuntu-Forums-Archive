---
title: "Thinking of giving it another shot"
date: 2008-11-13
forum: Installation &amp; Upgrades
---

### Post by badogg on 2008-11-13
Hey everyone, I think I am going to have some time here shortly to give Ubuntu another go-round.  Since my last try, I have done some substantial upgrades and would like some input to see if anyone has any thoughts about weather you see anything that is going to make this a deal-breaker so I don't waste any time trying to get it to work.  So much appreciated for taking a few to read through this and provide any input.

My hardware:
Asus Maximus II Formula Motherboard (ICH10r)
QVL Supported G.Skill PC28500 RAM - 4GB
BFGTech Nvidia 8800gts 640mb Video Card
Creative X-Fi Fatality Platinum Sound Card
2 Raid Arrays (both on the ICH10r controller, not using that stupid 'speeding hdd' garbage):
Boot Volume: Raid 5, 3x WD 250gb SATAII
Storage Volume: Raid0, 2x Seagate 500gb SATAII

I currently have Windows Vista Ultimate 64bit installed on the Raid5 array, and it is running beautifully.  I would like to install Ubuntu 8.10 to multi-boot.  My main concerns are trying to install it on the Raid5 and also along side Vista.  Hardware wise, I think my only concern is the Soundblaster X-Fi card - not sure if there is a working drive or not for it.

So again, I really appreciate any insight or any additional thoughts about this.

Thanks a ton!!

---

### Post by inobe on 2008-11-13
i grabbed this searching wiki

[https://wiki.ubuntu.com/DmraidSupport](https://wiki.ubuntu.com/DmraidSupport)

however this article says it is not supported.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

software raid is supposedly supported out of the box, i would think hardware raid being easier to setup, it would just be the matter of partitioning and formating.

i suggest installing ubuntu onto a spare sata and bios booting !

good luck

edit: alternative installer cd, that appears to be one method of configuring raid

[http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

that link was found here, check method 1

[https://help.ubuntu.com/community/FakeRaidHowto#Method%201](https://help.ubuntu.com/community/FakeRaidHowto#Method%201)

---

