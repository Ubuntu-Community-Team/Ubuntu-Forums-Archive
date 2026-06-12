---
title: "win10 (gpt partition table ) ubuntu 16.04 install partitions"
date: 2018-09-02
forum: Installation &amp; Upgrades
---

### Post by klein5366 on 2018-09-02
good day 
i'm getting ready to duel boot win10 with um 16.04 on an hp 15 p390nr 
i have ran try ubuntu and it runs good .

i have never worked with gpt partition table before.
see attachment :
i have some questions about partitioning and gpt partition table 
i'm planning on shrinking sda3 with win10, creating an unused space
then 
i would like to back up the gpt partition table with the live session and save it maybe zip it. 
so in the future i can restore the original gpt partition table,  if i find i have to reinstall win10. 

in the unused space i need two partitions, one for ubuntu and a 16gb linus-swap.

old school with an mbr you could create an extended partition and install partitions with in that,
how can i create two more partitions with my unused space i created ?

would it be better to create those partitions with win 10 ?

and use gparted to format them ?

---

### Post by oldfred on 2018-09-02
With gpt(GUID) partitioning the limit is 128 partitions. And users can modify that for even more. 
And all partitions are the same or in effect all primary.

Only use Windows to shrink NTFS partition and reboot immediately so it can run chkdsk.
Make sure Windows fast start up is off.
Usually better to have UEFI fast boot off also when reconfiguring. Fast boot assumes no changes and immediately jumps to booting. But then it boots so quick you do not normally have time to press keys to get into UEFI or UEFI boot menu.

See link in my signature for lots of info on UEFI & UEFI boot. Links to more info if you do not understand something. Only 9 "easy" steps to install Ubuntu. Do not skip backup step.

Even if not same model, or version of Ubuntu, issues are often common across models. Usually bigger  difference if AMD or Intel based. So look for other similar HP models.
       HP UEFI boot order change with efibootmgr does not stick, but change in HP's UEFI does work
[https://ubuntuforums.org/showthread.php?t=2390309](https://ubuntuforums.org/showthread.php?t=2390309)
HP 11m reinstall Windows & dual boot with Ubuntu 16.04
[https://ubuntuforums.org/showthread.php?t=2389104](https://ubuntuforums.org/showthread.php?t=2389104)
Probook G4 470 Ubuntu works fine with UEFI and secure boot. 
[https://ubuntuforums.org/showthread.php?t=2381663](https://ubuntuforums.org/showthread.php?t=2381663) 
            HP - escape + F9 for boot menu, F10 for bios setup

---

