---
title: "GRUB ATE MY XP !!! ...well ...cocked up my boot order ;-))"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by welshchap on 2010-04-30
Well not exactly ... its stil there just no option to boot from it !

This is despite telling grub to LEAVE my grub menu alone! it seems not to have done so!

Time to consult the ubuntu wiki .....ah its not in menu.lst anymore then ? ok we can cope with this ....

so I went to /etc/default/gru....ah ! NO /GRUB FOLDER ??? :confused:

so my families XP install is in /dev/sda1 as NTFS 

can someone point me to the correct file to edit to get my XP boot options back please?

I take it to get XP to boot as default (it IS the family PC first) i have to edit a file prefixed 10_ ? 

Many thanks in advance 

Welsh Chap

---

### Post by Cabe13 on 2010-04-30
it's not a folder in /etc/default/ ...it's a file called grub. you can edit the boot order there and then run sudo update-grub.

---

### Post by kansasnoob on 2010-04-30
It's rather impossible to follow what's up here. Please post the results of the Boot Info script as described here:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by welshchap on 2010-04-30
Sorry for the confusion chaps 

its solved now anyway 

so for the historic record:

Was running Karmic 9.10 desktop - fully up to date 

updated to Lucid LTS upon notification of availability

lucid upgrade program during execution said to me 
"what do you want to do ? leave grub as it is ? 
go with the package maintainers default?" 

I selected "leave as it is"

upgrade finished prompted to reboot

rebooted 

upon startup , no XP option in GRUB menu 

<<5 seconds of cold sweat>>  >;-o

boot successfully into ubuntu lucid ( whew!) 

load ubuntu wiki in firefox 

read that grub is now grub 2 and that "things ain't where they used to be"

looked where the wiki said to find the grub config files (/etc/default/grub)

no such folder !!

posted query to forum (before first coffee of the day) 

<<drank coffee....woke up>> ;)

went back into terminal 

poked around in /boot/grub

surprised to find the old menu.lst

cat 'ed menu.lst - found that ubuntu is still reading the old files the same way ?? thought grub2 was different ??...whatever...

cp'd menu.lst menu.arrgh (safety backup) 

nano menu.lst

added in the appropriate section (below all the commented out lines and above the first of the lucid kernel boot option lines) 4 new lines

```

title ye olde micro$0ft nonsense (XP)
root		(hd0,0)
makeactive
chainloader	+1

```

wrote out to menu.lst

just in case , did a grub-update

init 6 to reboot 

hey presto - default boot of windows xp restored and before the family got home (relief!!)

sorry for any pre-coffee confusion caused on my part. relieved to say I was able to fix it myself without further ado.


regards  / thanks 

Welsh Chap

---

