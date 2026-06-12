---
title: "Strange Behaviour After Upgrade"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by andrewlee_foo on 2007-10-21
I found that my PC acting strange after u upgrade my feisty to gutsy.

my hard disk keep on read/write all the time although i din run anything.

i tried to reboot my PC and leave it there after i login, hen i can see the hard disk led keeps on blinking. anyone have the same problem like mine?

---

### Post by andrewlee_foo on 2007-10-21
can someone answer me?
my mouse cursor is also keep on shaking it self.
it even moved down itself sometimes after the upgrade.

---

### Post by homerhomer on 2007-10-21
go to system - administration - system tools

This tool will show you your system resources.  click on processes and sort them by cpu and memory

hopefully this helps out locate some strangness

let me know what you see

what would also be a good idea to look through your device messages for errors

go to a command terminal ( applications -accessories - terminal )

and paste the following
 dmesg > $HOME/Desktop/devicemessage.txt


this will create a text file on your desktop called  devicemessage.txt

look through it for errors
let me know, how it goes

---

### Post by dimeotane on 2007-10-21
yes, having something similar here since upgrading.  Hard drive is pulsing once a second like the tick of a clock reading or writing to the drive.
Theres several seconds wait time when trying to open a terminal window.
Delays in firefox when opening a new page to load.  Google takes several seconds to come up.

---

