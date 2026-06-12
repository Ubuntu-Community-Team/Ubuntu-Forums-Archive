---
title: "Dual boot problems"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by wman2 on 2011-01-12
Hi guys.

So my laptop was preinstalled with Windows Vista.  I tried to install Ubuntu as a dual boot a while ago, and Ubuntu booted fine, but Windows wouldn't load (there were also a few corrupt entries in the boot loader too).  So, with all hope of keeping Windows gone (didn't come with recovery partition), I clean installed Ubuntu.  This has been working fine ever since, and I use Windows XP on a virtual machine, but it is slow and not ideal.

Also, on another computer, it came with XP.  I installed Linux Mint, again with the hope of booting it alongside XP.  But when I tried to boot XP from the loader, the screen just turned black and nothing happened, so I am using Mint on that one still.

So, you see,  I have not had a good experience with dual-booting and I was wondering if these are known problems, or I'm doing something wrong, or something else?  Because I'd like to install XP on laptop, but am afraid it will mess things up (I've spent a long time getting Ubuntu just how I like it).

Any help appreciated - cheers. 

EDIT: How do I get the gibberish to remove from post? I've tried deleting it:


[CENTER][COLOR=#000000] 
[/COLOR][/CENTER]
[LEFT][COLOR=#CCCCCC][FONT=Trebuchet MS][/FONT][/COLOR][/LEFT]
[CENTER][COLOR=#000000]AfrikaansAlbanianArabicBelarusianBulgarianCatalanChineseCroatianCzechDanishDetect languageDutchEnglishEstonianFilipinoFinnishFrenchGalicianGermanGreekHaitian Creole ALPHAHebrewHindiHungarianIcelandicIndonesianIrishItalianJapaneseKoreanLatvianLithuanianMacedonianMalayMalteseNorwegianPersianPolishPortugueseRomanianRussianSerbianSlovakSlovenianSpanishSwahiliSwedishThaiTurkishUkrainianVietnameseWelshYiddish[COLOR=lightgrey]**&#8644;**[/COLOR]AfrikaansAlbanianArabicBelarusianBulgarianCatalanChineseCroatianCzechDanishDutchEnglishEstonianFilipinoFinnishFrenchGalicianGermanGreekHaitian Creole ALPHAHebrewHindiHungarianIcelandicIndonesianIrishItalianJapaneseKoreanLatvianLithuanianMacedonianMalayMalteseNorwegianPersianPolishPortugueseRomanianRussianSerbianSlovakSlovenianSpanishSwahiliSwedishThaiTurkishUkrainianVietnameseWelshYiddish[LEFT]Detect language » Hungarian[/LEFT]


[/COLOR][/CENTER]

---

### Post by garvinrick4 on 2011-01-12
```

# I can see no problem if you install grub to sda when installing to internal drive used to boot from. 
If you install Windows after Ubuntu you have to install grub to mbr because windows will overwrite 
existing grub in mbr (master boot record) with its own. 
[Grub 2 Basics - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1195275") 
In this link above shows you how to install grub with live Cd.

# Now below is a link for reinstalling Windows grub as to boot Windows, then you can 
reinstall Ubuntu's grub from link above so as to boot both.
[Grub/XP/Vista Bootloader - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=1014708")

## Anytime you make a change in grub you run this in terminal:
[CODE]sudo update-grub
```# Above will put any new entries in 
grub-config files which then makes a menuentry
in Ubuntu's grub to choose to boot into.

# grub-legacy is old version of grub. 
# grub2 is new version which has been installed in Ubuntu since version 9.10
# Just remember to put grub of choice into mbr of drive Ubuntu being installed on.
 Such as sda or sdb or sdc

# Drives can be found by running this in terminal:
```
sudo fdisk -l
``` (Lower case L)
[/code]# To get rid of gibberish in post hit edit and highlight and delete:

---

### Post by oldfred on 2011-01-12
I always partition in advance and then use manual install to use those partitions. I never wanted to trust an automatic installer and its decisions and the newest version with Maverick is so confusing that many users are overwriting the windows install.

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Dual drive internal or external
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)

---

