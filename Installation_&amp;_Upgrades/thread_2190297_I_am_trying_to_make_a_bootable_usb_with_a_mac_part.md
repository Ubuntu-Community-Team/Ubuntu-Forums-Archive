---
title: "I am trying to make a bootable usb with a mac part 2"
date: 2013-11-26
forum: Installation &amp; Upgrades
---

### Post by gravitate on 2013-11-26
I have converted the ubuntu  ISO to IMG and then tried to put it on the memory stick using this```
[COLOR=#000000][FONT=Menlo]sudo dd if=ubuntu-12.04.3-desktop-i386.img.dmg of=/dev/rdisk1 bs=1m[/FONT][/COLOR][COLOR=#000000][FONT=Menlo]

I then got an error saying the disk is unreadable. This was after I put my pass word in for the sudo command etc and waited a few minutes. This came up in Terminal:

[code][/FONT][/COLOR][FONT=Menlo]pc3:Downloads liteaddress$ sudo dd if=ubuntu-12.04.3-desktop-i386.img.dmg of=/dev/rdisk1 bs=1m[/FONT][FONT=Menlo]Password:[/FONT]
[FONT=Menlo]707+0 records in[/FONT]
[FONT=Menlo]707+0 records out[/FONT]
[FONT=Menlo]741343232 bytes transferred in 81.837366 secs (9058738 bytes/sec)[/FONT]

[FONT=Menlo]pc3:Downloads liteaddress$[/FONT][COLOR=#000000][FONT=Menlo]
```


Did it work?[/FONT][/COLOR]

---

### Post by thatredbird on 2013-11-26
I believe the 707&#10133;0 in/out is from the DD command, so it seems to me that is took in and output the same number of blocks.

not sure what the img.dmg refers to. Seems like it would just be img, but it might be a mac thing.

you might be able to use the
hdiutil convert with greater success.

---

