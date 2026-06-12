---
title: "dualboot - boot ubuntu as primary default using xp bootloader - howto?"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by Lexje on 2010-02-09
Hi forum,

Google can't seem to find any help on this one, so here goes:

HP/Compaq mini 311c with XP-home preinstalled.
Ubuntu Karmic installed on /dev/sda6
swap = /dev/sda5

I've done
```
dd if=/dev/sda6 of=grub.bin bs=512 count=1
```
and copied grub.bin to c:\grub.bin

Then I've added a line to boot.ini with c:\grub.bin

So far so good.
Dual booting works alright so no problem there.

The previous makes XP the default boot option.
[COLOR="Blue"]**Now what I'd want is to have Ubuntu as default boot option.**[/COLOR] And keep using the windows bootloader.

I've tried to fumble with boot.ini in many ways, but I can't get this to work.

At the moment it is even so that it 'seems' as if the machine is looping through 2 boot.ini files, each with different timeout settings. (I've indeed been playing with these)

I know for sure there is no other boot.ini file on the system, so I wonder if NTLDR or something else writes / copies part or all of boot.ini to maybe the MBR?

Thanks for all your suggestions!

Erwin

---

### Post by darkod on 2010-02-09
I don't remember any more for XP how are the options and menus exactly called, but look around for similar titles if I miss it.
Try right-clicking My Computer, select Properties. In the new window there should be a tab Advanced. Inside there should be section Startup and Recovery and a button Settings for it.
That is what you need to find. I think clicking on Settings should open the options which OS to be booted first (provided it can see Ubuntu which is chainloaded) and the timeout. That should be the best way to control the boot.

---

