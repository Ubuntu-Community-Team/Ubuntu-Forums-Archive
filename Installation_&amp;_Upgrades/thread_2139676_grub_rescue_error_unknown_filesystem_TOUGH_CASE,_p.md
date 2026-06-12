---
title: "grub rescue: error unknown filesystem TOUGH CASE, please help ..."
date: 2013-04-27
forum: Installation &amp; Upgrades
---

### Post by timer0x01 on 2013-04-27
[FONT=arial]Hello,[/FONT]

[FONT=arial]After laptop system crush (which was caused by hard restart), my ubuntu linux is not booting, it is showing now:[/FONT]

[FONT=arial]error: uknown filesystem[/FONT]
[FONT=arial]grub rescue>[/FONT]

[FONT=arial]Solutions that I tried:[/FONT]

[FONT=arial]1st solution)[/FONT][FONT=arial]I've read a lot about similar problems and I've tried to work with grub rescue from console:
> 
grub rescue>ls
(hd0) (hd0,msdos5) (hd0) (hd0,msdos1)
grub rescue>ls (hd0,msdos5)
error: uknown filesystem
grub rescue>ls (hd0,msdos1)
error: uknown filesystem


So, I can't list/find my linux filesystem ,,,

2nd solution)
After all, I decide to try Boot Repair, I've installed it on UBUNTU live USB, but there is no "Recommended repair" button and there is no "Advanced options". There is only one button which is "Create a BootInfo summary" - I've created one, the link is [http://paste.ubuntu.com/5609223/](http://paste.ubuntu.com/5609223/).
I tried BootRepair on latest UBUNTU and on Linux Secure Remix, they both are LIVE editions baked on USB - the same result, Boot Repair not working.
Also OS-Uninstaller on Linux Secure Remix states that there is not found/installed OS.

This is the log from Boot Repair:
[http://paste.ubuntu.com/5609223/](http://paste.ubuntu.com/5609223/)

I tried the same Linux Secure Remix on a different PC and at least there is button "Recommended repair". So I think the problem is in my HDD or MBR .. I don't know..


I am out of options... :( Please, HELP!

THANK YOU!!!
[/FONT]

---

### Post by gordintoronto on 2013-04-27
It seems likely that you will need to reinstall.

---

### Post by timer0x01 on 2013-04-28
The problem is solved here: [http://askubuntu.com/questions/286837/grub-rescue-error-unknown-filesystem-tough-unique-case](http://askubuntu.com/questions/286837/grub-rescue-error-unknown-filesystem-tough-unique-case)

---

