---
title: "no boot menu on 9.10 on dual boot"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by paul_anders on 2009-12-01
hi
 i just installed ubuntu 9.10 on my machine. windows xp was previously installed.
the ubuntu installion was fine and ended. on machine restart the machine
boot straight into windows xp. there are no boot menu where i can choose the operating system. on ubuntu 9.04 i had a menu.

how can i get a menu on 9.10 or does this new ubuntu a stand alone ?

thanks
PA

---

### Post by darkod on 2009-12-01
I guess you installed it on different hdd. You xp hdd is still first in BIOS in boot order and it goes straight into XP. Set the ubuntu drive as first choice and it should be fine.

---

### Post by paul_anders on 2009-12-01
yes i do have bunty on a different drive... 
how do i get the boot menu back up though


thanks
PA

---

### Post by darkod on 2009-12-01
Did you set that drive as first choice in BIOS?
Enter BIOS on your machine and look around in Boot options or Advanced options.

Be careful, one type of selection is talking about DEVICES, like 1st cd-rom, 2nd hdd, etc.
That means that looking for bootloader first any CD in the drive will be checked, then the hdd. In this setting you don't need to change anything.
But for cases like yours where you have more than one hdd, there is also separate setting which sets the order in which the hdds are checked for bootloader. In that setting your ubuntu drive has to be first, not your xp drive.

---

### Post by paul_anders on 2009-12-01
thats strange i never had to do that before...
yes my windows is on drive o and the linux was installed to drive 1 but i think your solution will mess things up more.

usually when i install bunty on another driver it usually see windows and take care of it in a boot menu. 

if i was to go in the bios and set drive 1 to boot then id expect that bunty still wouldnt create a boot menu. but now boot into linux itself. thats if grub is in a good working order

thanks
PA

---

### Post by darkod on 2009-12-01
There is grub2 installed of the MBR (Master Boot Record) of drive 1, as you call it. It will not mess up anything. The grub menu is there.
But you have to instruct the computer where to look for the bootloader (in this case grub2), and that is done with the mentioned BIOS settings. Right now it's checking drive 0 for bootloader first, windows xp bootloader is there and it's booting windows directly. Windows bootloader does not try to add other OS to the menu, unlike grub.

---

### Post by paul_anders on 2009-12-01
ok well that sounds logical to me... sorry im not trying to fight against you but im just stuck with the way that always worked for me LOL (a typical stubborn human)

ok ill give that bios to boot from the 2nd hdd in about 30mins

ill sure let you know what happens

thanks
PA

---

### Post by paul_anders on 2009-12-01
this bunty 9.10 is such a hassle.
my second drive is sata drive and not in the bios. this is so much crap
as i try to set the sata drive to active.

why cant 9.10 work like all the previous versions where they automatically take care of windows and the menu regardless of what drive the operating systems are on.

plus i cant really afford to muck around with my windows drive as i got too much work on it and dont feel like loosing 37gig of work any day soon.

so i was thinking to get 9.04 back on then upgrade, but to me thats just crazy as how long can i keep upgrading for.

is their a way where i can install a clean bunty 9.10 to my sata drive (hdd 1) and have it recognize windows on a primary drive (hdd 0) and show the menu while booting or is this impossible to do in this version of bunty ?

thanks
PA

---

### Post by darkod on 2009-12-01
If BIOS is not showing your second drive that has NOTHING to do with ubuntu. Please don't confuse those things also because these threads will come up in search engines for months to come.
If BIOS doesn't recognize a hard drive it's like it doesn't even exist. How did you manage to install anything on it then? Very confusing...
Once more, grub is there, and the menu is there. Sort out your machine so BIOS can see ALL of your drives.
Alternatively, if somehow that drive is recognized but can't be boot option, you can instruct grub to install on the windows drive. But don't know if that's something you want to do.
And Idon't think 9.04 can make much difference. BIOS is one thing, ubuntu as OS another.

---

### Post by oldfred on 2009-12-01
New grub2 has a minor bug that causes it to boot slow if you install grub on one drive but have your Ubuntu install on another drive. It is best to switch drive order in BIOS or if old pata the master/slave settings. Some older motherboards do have issues with mixed sata/pata configurations and grub/ubuntu do not see them in the same order. I had some of these problems with my old system a year or so ago before I updated my hardware and am now all Sata.

---

### Post by paul_anders on 2009-12-13
thanks for the replies
i managed to install grub2 and got both bunty 9.10 and windows
back in the boot menu.

alls fine now thanks
PA

---

