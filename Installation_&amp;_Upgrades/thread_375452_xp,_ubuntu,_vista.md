---
title: "xp, ubuntu, vista"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by Sumint620 on 2007-03-03
I've got a problem here. I have Windows XP installed on my primary hard drive. I put a second drive in earlier this year and installed Ubuntu on it. What I would like to do now is keep my XP hard drive and Ubuntu drive and install Windows Vista on either the same drive as Ubuntu or a new hard drive that i'm ordering. Is there anyway to do this without loosing any data from XP or Ubuntu? Thanks

---

### Post by ffxr on 2007-03-03
you can do this.. you might need to edit your windows boot.ini and linux grub files (/boot/grub/menu.lst) 

vista might take over the boot sector completely but i think u can recover your grub boot by using the live or alternate cd and repairing the boot .. u wont lose any data.. (as long your careful not format or delete parititions; it might just take a wee bit of fiddling to get the boot sequence sorted again)

sorry i cant be more specific.. m sure there is other threads on this or similar issues.

---

### Post by Sumint620 on 2007-03-04
ok. i think i have another problem though. what i would really like is for grub to look like this:
Ubuntu 6.10
Other OSes:
Windows XP*
Windows Vista

*default startup

is there any way to make windows vista appear in grub? i ask this because my mom uses windows xp and probably wouldn't be comfortable in vista. I want to use vista and ubuntu.
thanks

---

### Post by ffxr on 2007-03-06
yeah you can edit your grub so that the windows boot loader is the default by changing the default 0 line in your  /boot/grub/menu.lst to the number of the windows option, just count number of OS' titles in the lst and put that number in..

you can chnage the default os that is booted by windows via an edit of boot.ini or via the windows gui -> right click my computer -> properties _> advanced its in there somewhere i think..

post back if you need further elaboration.

---

### Post by Sumint620 on 2007-03-06
ok well i think there is a problem. i was told that because vista uses a different boot thingamajig, that it wont show in GRUB. what happens is it shows windows xp and then it proceedes to the windows boot loader with "microsoft windows" (vista) and "older version of windows" (xp) (i want to skip the boot loader and put vista in grub)

i did find a website that shows how to do this but it is only a tutorial for one hard drive. i know you can do it with more than one (in my case 3, one for xp, vista, and ubuntu) but i'm not quite sure how. if somebody could "translate" the tutorial into being used with 3 hard drives that would be great.

*wrong link, i'll find it soon*
[http://hevnikov.com/blog/2006/12/24/triple-boot-qa-2/](http://hevnikov.com/blog/2006/12/24/triple-boot-qa-2/) <--- right link!!

thanks

---

### Post by confused57 on 2007-03-06
> **Sumint620 said:**
> I've got a problem here. I have Windows XP installed on my primary hard drive. I put a second drive in earlier this year and installed Ubuntu on it. What I would like to do now is keep my XP hard drive and Ubuntu drive and install Windows Vista on either the same drive as Ubuntu or a new hard drive that i'm ordering. Is there anyway to do this without loosing any data from XP or Ubuntu? Thanks

Are your 2 current drives IDE and the 3rd on you're planning on installing also IDE?
I'm assuming on your current setup with 2 hard drives that grub is installed to your Windows XP drive.
I can make some suggestions, but I can't guarantee they will work, if you can let me know about your drives & current setup.

---

### Post by Sumint620 on 2007-03-07
yes, right now my setup is two IDE drives with GRUB on the windows drive. my new drive will be SATA 3.0gb/s

---

### Post by confused57 on 2007-03-07
> **Sumint620 said:**
> yes, right now my setup is two IDE drives with GRUB on the windows drive. my new drive will be SATA 3.0gb/s
I can't guarantee my suggestions will work, but what I would do is disconnect your 2 IDE drives when you install the SATA drive prior to installing Vista...this way you'll be relatively certain that you won't lose anything on in Windows or Ubuntu.  You should always then be able to boot Vista from bios, if you're not able to boot it from grub.

After you get Vista installed & updated, then you could reconnect your IDE drives, then I'd go into bios and set the hard drive boot order, Windows IDE first, Ubuntu IDE second, and the Vista SATA third.  Then you should be able to add an entry to grub to boot Vista, something similar to this:

```
title              Windows XP
rootnoverify       (hd2,0)
savedefault
makeactive
map                (hd0) (hd2)
map                (hd2) (hd0)
chainloader        +1
```

You might want to search around for other options, or maybe someone else will reply with another possibility.

---

### Post by Sumint620 on 2007-03-07
that seems like a logical solution. did you check out the link i sent by any chance? it is along the same lines, you "hide" the XP drive while installing vista. what would be nice is if somebody could translate that site in my post a few up into three hard drives (not partitions on one drive) with xp on the first (already installed), ubuntu on the second (already installed), and vista on the third (needs to be installed). thanks.

---

### Post by confused57 on 2007-03-07
> **Sumint620 said:**
> that seems like a logical solution. did you check out the link i sent by any chance? it is along the same lines, you "hide" the XP drive while installing vista. what would be nice is if somebody could translate that site in my post a few up into three hard drives (not partitions on one drive) with xp on the first (already installed), ubuntu on the second (already installed), and vista on the third (needs to be installed). thanks.

Here's another link explaining how to hide one Windows OS from another when installed on the same hard drive:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_system_Entries)

I think this just applies to 2 Windows OS installed on 2 different partitions on the same hard drive and triple booting with Linux using grub...I don't think it would apply to multiple drives.

Another reason I suggested disconnecting your IDE drives is that I'm not sure which drive Vista would install it's boot code mbr, it may install to your Windows mbr...I don't know for sure.

---

### Post by Sumint620 on 2007-03-08
ok. i found this software (think it might just be for Vista so Vista will need to be already installed I think) called EasyBCD. anybody know anything about this?

---

