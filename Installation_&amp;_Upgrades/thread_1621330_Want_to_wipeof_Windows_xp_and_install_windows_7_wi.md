---
title: "Want to wipeof Windows xp and install windows 7 within Ubuntu"
date: 2010-11-14
forum: Installation &amp; Upgrades
---

### Post by h3llboy on 2010-11-14
Hello Everyone,

I have installed Ubuntu within xp abt 6 months before and till now im running dual boot with grub loader. I guess its Ubuntu became the primary OS but not sure.

I need to figure out 2 things.
1) Which one is the primary OS. Since the grub loader is showing first, is it ubuntu? or since i have installed ubuntu alongside xp, is it XP? which one gets affected if i format/remove c: drive.
2) And second  i would like to format xp and install windows 7 without losing my data, hard drives etc. Is it possible? i want to just format my windows xp installed c: and want my ubuntu remain untouched, coz I have made many manual configurations and installed many softwares and made my ubuntu more stable than windows, so that i will continue to use ubuntu grub loader henceforth for ubuntu and windows 7.

Any help would be greatly appreciated. Because i love ubuntu and i dont want to lose my ubuntu back.

Thanks in advance.
-goGul.

---

### Post by searchfgold6789 on 2010-11-14
> 
1) Which one is the primary OS. Since the grub loader is showing first, is it ubuntu? or since i have installed ubuntu alongside xp, is it XP? which one gets affected if i format/remove c: drive.XP, I guess, because if you remove XP then you remove Ubuntu because Ubuntu is installed as a program within XP.> 
2) And second  i would like to format xp and install windows 7 without losing my data, hard drives etc. Is it possible? i want to just format my windows xp installed c: and want my ubuntu remain untouched, coz I have made many manual configurations and installed many softwares and made my ubuntu more stable than windows, so that i will continue to use ubuntu grub loader henceforth for ubuntu and windows 7.

If you have XP SP2 with .NET framework 2.0 or higher, which is probably true for the average XP user, then you will be able to upgrade to Windows 7 (you have to buy software for this) and keep some of your settings, and probably most of your programs, and be able to view hard disks and media that XP was able to recognize. But keep in mind that it is nowhere close to being an Ubuntu upgrade, where with a click of a button the system makes minute changes one by one and saves all your settings, etc. You will need to make a few sacrifices.
To see what the upgrade will be able to do for you, you can download the [_**Windows 7 Upgrade Advisor**_]("http://download.microsoft.com/download/9/5/D/95D3883A-00A2-4A8A-A979-48D5AB9B1112/Windows7UpgradeAdvisorSetup.exe").

---

### Post by h3llboy on 2010-11-14
So,

The moment i insert my windows 7 cd (Im not gonna upgrade since i have the cd ) and clicked format, im gonna lose windows xp and ubuntu completely. Am i right?

If that is the case, then i need to install ubuntu again after completing windows installation. This makes me sad. Fine. Thanks for the quick reply. I owe to you :).

P.S: I have installed ubuntu not as program ( Wubi installer). Its in separate partition boots grub. 

-goGul

---

### Post by Mark Phelps on 2010-11-14
> **searchfgold6789 said:**
> ... upgrade to Windows 7 (you have to buy software for this) and keep some of your settings, and probably some of your programs ...

You will only be able to keep your programs if you purchase the Wint upgrade utility from LapLink software.  MS does NOT support upgrading from XP to Win7.  All it will do is keep your settings and your data.  It will not keep your programs.

---

### Post by cybergnome on 2010-11-15
I would add to remember that you don't have to lose the Ubuntu install if you back up the partition and restore if back, after the Win 7 install.

---

### Post by h3llboy on 2010-11-15
> **cybergnome said:**
> I would add to remember that you don't have to lose the Ubuntu install if you back up the partition and restore if back, after the Win 7 install.

Really? How can i do that so? For instance, Let's say, my partition is like this.
c: NTFS Primary some 20GB where windows sits
D: NTFS Secondary some 50Gb
E: NTFS blah blah blah
and
an EXT partittion where my ubuntu sits.

If i boot the system with ma windows 7 cd and getting a screen like above, if i format ma c and do install, will my ubuntu be safe? or any other thing i need to do? 

Since im a newbie in these dual boot things and all i need help as i already lost my 250GB data pnce while playing like this without knowing the complete thing.

Thanks.

---

