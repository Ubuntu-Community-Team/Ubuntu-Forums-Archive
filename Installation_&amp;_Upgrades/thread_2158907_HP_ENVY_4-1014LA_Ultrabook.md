---
title: "HP ENVY 4-1014LA Ultrabook"
date: 2013-07-01
forum: Installation &amp; Upgrades
---

### Post by Sergio_ on 2013-07-01
[FONT=arial]Hi!
 I have an hp envy 4-1040la, specs:
 
2° Generation  Intel® Core™ i3-2377M 1,5Ghz
3 MB de caché L3
4GB de SDRAM DDR3 (1 DIMM)
Graphics Card Intel® HD 3000
Display 14,0 HD(8) BrightView backlight LED (1366 x 768)
HDD 500 GB (5400 rpm)
mSATA 32 GB[COLOR=#333333]
[/COLOR]
and I want to install lastest ubuntu on it. I have been searching and I found that only the hp envy 4 sleekbook is supported, wich one is very simillar to mine
[http://www.ubuntu.com/certification/hardware/201209-11790/](http://www.ubuntu.com/certification/hardware/201209-11790/)
(the full list of all supported hp is here-> [http://www.ubuntu.com/certification/desktop/make/HP/?page=1&category=Desktop&category=Laptop&category=Netbook](http://www.ubuntu.com/certification/desktop/make/HP/?page=1&category=Desktop&category=Laptop&category=Netbook))

I also found these info [http://www.linlap.com/hp_envy_4](http://www.linlap.com/hp_envy_4) wich is very similar to mine, but it says that the card reader and multitouch are not working. I dont care about the card reader too much, but the sensitivity of the touchad was one of the reason because I bought these laptop...does anyone have installed on it, or have more info about it?[/FONT]

---

### Post by fantab on 2013-07-01
Does this HP has Windows7 or Windows8 as a pre-installed OS? Does it boot with EFI (UEFI)?

HP generally has its HDD partitioned into 4 primary partitions. Which is limiting on 'msdos' or Legacy BIOS. This can be generally true if you have Windows7 and or old laptop. If its brand new and boots Windos8 then there is good possiblity that HDD has GPT and boot in UEFI. If the second senario is true then the earlier mentioned limitation of only 4 Primary partitions is not applicable anymore.

If you can provide us some confirmation about your HP then we can help you install Ubuntu as either dual-boot with Windows or only Ubuntu.

Installing Ubuntu won't be an issue. What graphics card do you have on board?

---

### Post by Sergio_ on 2013-07-01
It has Windows 7 home premium pre-installed as OS. How do I know if it boots with EFI (UEFI)? I bought the HP on september 2012, Its kind of new.

The graphic card is not dedicated, is a [COLOR=#000000][FONT=Arial]Intel HD graphics 3000 with up to 1696MB total graphics memory[/FONT][/COLOR]

---

### Post by Sergio_ on 2013-07-01
NEW! I have tried an ubuntu live version from a pendrive, everything works almost fine (didn´t try the SDReader) except for that the deactivating/activating PAD button in the upper left corner didn´t work, but the worth of all....I didn´t have the 3fingers backwards and forward option. It´s very useful (without mentioning that you can also configure 4 and 5 fingers actions, which ubuntu also didn´t have). Does any one knows a solution?

PD: maybe i should make another thread or find in the forum?

---

### Post by fantab on 2013-07-02
The output of command below should tell us if you have UEFI boot:

```
sudo parted -l
```

I think the touchpad features are handled by 'Synaptics Driver', it can be configured to our liking. Since I don't have Ubuntu using any touchpad I cannot give your more details. 
For more info on Synaptics driver (the link provides info related to another distro but the basics are same):  [https://wiki.archlinux.org/index.php/Synaptics](https://wiki.archlinux.org/index.php/Synaptics)

---

