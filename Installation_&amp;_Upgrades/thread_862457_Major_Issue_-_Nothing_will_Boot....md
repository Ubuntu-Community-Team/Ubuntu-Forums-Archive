---
title: "Major Issue - Nothing will Boot..."
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by endlessnameless on 2008-07-17
Sincere apologies if this is in the wrong forum... 

I'm not sure where to put this, but I'm currently running an AMD64 version of Ubuntu 8.04 that my brother gave me. Having realised that this is the wrong version, I've made a live CD of the proper...but now it wont boot when I tell the computer to boot from the HDD. I've tried several different Live CD's at this stage, and none of them will boot. I even inserted an XP cd, and that wont boot either...

Would reformatting the drive make a difference? 
How would I do that inside Ubuntu? I've backed up everything onto a separate laptop already, so thats checked off the list...

---

### Post by wpshooter on 2008-07-17
Do you have the CD drive listed as the FIRST boot device in the BIOS ?

---

### Post by achim_59 on 2008-07-17
Reformatting the hard disk **should** work but it won't solve the problem as such. You seem a savvy sort of person, so I won't bother to ask you whether you set the boot preferences to boot from a CD/DVD drive. It seems to me as though your BIOS is fragged. In that case reformatting probably won't work, either.

What happens when you try to enter the CMOS setup?

Achim

---

### Post by endlessnameless on 2008-07-18
Appreciate the replies, people. 

The method I'm using is this: power on computer, press f12, met with menu displaying options on whither to boot from the hard drive or CD/DVD Drive, and naturally I choose CD Drive. 

All that occurs is that I'm met with the grub menu and Linux loads up as normal. 

Having backed up everything, I'm in a position where I can reformat and take a gamble...but of course, if I loose...my computer is useless...

My optical drive is working perfectly by the way...I mean, the xp installation application will load up fine in WINE...so thats definitely not an issue...

---

### Post by endlessnameless on 2008-07-18
> **wpshooter said:**
> Do you have the CD drive listed as the FIRST boot device in the BIOS ?

No, HDD is listed as the first, but I have the option to choose when the menu is displayed. Unfortunately enough, no such luck for I...

---

### Post by wpshooter on 2008-07-18
> **endlessnameless said:**
> No, HDD is listed as the first, but I have the option to choose when the menu is displayed. Unfortunately enough, no such luck for I...

Put the CD drive as the first boot device in the BIOS.

---

### Post by apche93 on 2008-07-18
I dont understand what the problem is...

If you can get to the live cd, and uve backed up all ur files, then why dont u just install Ubuntu?

> ..but now it wont boot when I tell the computer to boot from the HDD..

Exactly what is the message that pops up when u turn ur computer on?


Please make sure that you have no external USB devices connected when your computer boots.  If you have USB devices like flash drive or external hd (and it doesnt have bootable material), please unplug them.  IF you dont u would get a message like "NTLDR is missing" "Crtl+alt+del".

---

### Post by achim_59 on 2008-07-21
I'm in the same boat as apche93. I thought I at least understood what the problem was about but now I'm thinking I've missed something. Did you solve your problem?

> All that occurs is that I'm met with the grub menu and Linux loads up as normal. 

As for the boot options: I recall that my Aspire Laptop used to give me boot options after I pressed F12 or something... didn't really work consistently so I went back into setup and changed the boot sequence to CD/ floppy/HDD. This seems to be the best option and works fine even when you don't have a floppy drive (which most newer Laptops and PC'S don't). I've never booted from a flash drive, so I won't comment on that.

Cheers,

Achim

---

