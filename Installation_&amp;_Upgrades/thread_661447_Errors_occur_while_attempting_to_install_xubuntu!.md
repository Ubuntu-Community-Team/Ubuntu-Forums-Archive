---
title: "Errors occur while attempting to install xubuntu!"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by Hoss212 on 2008-01-07
Hello, I am trying to install 7.10 on my old laptop, it can be seen from the link below...

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00011680&lc=en&cc=us&dlc=en&product=95218&lang=en](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00011680&lc=en&cc=us&dlc=en&product=95218&lang=en)

It currently has Windows XP Professional on it. But, I am trying to obviously install xubuntu 7.10. Now I boot it up and it's not at the xubuntu start menu... the menu is

- Start or install xubuntu
- Start xubuntu in safe graphics mode
- Install with driver update CD
- OEM install (for manufactures)
- Check CD for defects
- Memory test
- Boot from first hard disk

...and then accross the bottom F1 = Help, F2 = Language, F3 = Keymap, F4 = VGA, F5 = Accessibility, F6 = Other Options.

Well if I try to install which is what im trying to do, the first error I encounter is this...

BIOS age (1998) fails cutoff (200), acpi=force must be enabled... Or 'similar'

Then it loads with bar bouncing bar and forth... (This goes on for about 10 minutes...)

Then I get all of these Buffer I/O errors and SQUASHFS errors...

Then I'm stuck right here, it just keeps going on forever and all I can do is turn off. All help is extremely appreciated! :confused:

---

### Post by Partyboi2 on 2008-01-08
You can try adding acpi=force to the boot options
At main menu
Press F6 (other options)
at the end of the line add
```
acpi=force
```then press enter
If that works then you will need to add it to grub menu when you have installed. (can tell you how to do that if it works)
If that does not work I would suggest trying the alternate cd as its a text base installer and works well with older machines
[http://mirror.internode.on.net/pub/ubuntu/xubuntu/7.10/release/](http://mirror.internode.on.net/pub/ubuntu/xubuntu/7.10/release/)
[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

---

### Post by Hoss212 on 2008-01-08
> **Partyboi2 said:**
> You can try adding acpi=force to the boot options
At main menu
Press F6 (other options)
at the end of the line add
```
acpi=force
```then press enter
If that works then you will need to add it to grub menu when you have installed. (can tell you how to do that if it works)
If that does not work I would suggest trying the alternate cd as its a text base installer and works well with older machines
[http://mirror.internode.on.net/pub/ubuntu/xubuntu/7.10/release/](http://mirror.internode.on.net/pub/ubuntu/xubuntu/7.10/release/)
[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

Nope didn't work... shall I try the alternate install? because I tried Desktop...

---

### Post by Gina on 2008-01-08
Yes, you'll need the Alternate install - too little memory to run the Desktop in.

I too am trying to install Ubuntu on an old laptop - with a higher spec than yours (mentioned in another thread).  Nothing later than Dapper (6.06) would install even using the Alternate CD.  Xubuntu didn't fare any better than Ubuntu to my surprise.

---

### Post by Hoss212 on 2008-01-08
> **Gina said:**
> Yes, you'll need the Alternate install - too little memory to run the Desktop in.

I too am trying to install Ubuntu on an old laptop - with a higher spec than yours (mentioned in another thread).  Nothing later than Dapper (6.06) would install even using the Alternate CD.  Xubuntu didn't fare any better than Ubuntu to my surprise.

Well if this thing could run XP, I'm SURE it will be able to run this... Thanks mate, download alternate install now! :)

---

