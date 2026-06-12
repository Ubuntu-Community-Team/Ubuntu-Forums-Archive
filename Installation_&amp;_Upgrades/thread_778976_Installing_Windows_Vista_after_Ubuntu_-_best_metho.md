---
title: "Installing Windows Vista after Ubuntu - best method/guide ?"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by aroddo on 2008-05-02
I have an obsolete Windows XP on a primary partition (sda1) (which is also the /boot partition), Ubuntu on another primary partition (sda3) and an active Windows XP on a logical drive (sda6) in an extended partition(sda2).

all three systems boot fine, although the logical windows partition works only via windows bootloader and not directly through Grub.

Now I want to install Vista 64 on sda1 so i can migrate essential windows applications to it (essential meaning itunes and games ;) ) and polish my vista skills, while Ubuntu will be used for all the rest.

I'm pretty sure that vista will do it's best to destroy everything non-windowsish, so I'd like to ask for best-practice guides or advice on what to do and what to expect.

Normally I'd expect that after the windows installation all I have to do would be reinstalling grub, but with vista i'm not so sure ... my last experience caused me to take a 1 year vacation from that shitty jealous installer, so I'm extra cautious before trying again.

Thanks in advance.

---

### Post by aroddo on 2008-05-03
don't tell me you all failed miserably ...

---

### Post by wildteen88 on 2008-05-03
Vista shouldn't touch your ubuntu installation. Once Vista is installed you'll need to reinstall grub.

You could keep the Vista bootloader and install EasyBCD to boot into grub. Grub will need to be installed to your ubuntu partition though.

---

### Post by aroddo on 2008-05-05
which bootloader is - or should be - running first ?
Grub -> BCD
       - or -
BCD -> Grub

 because of that.I haven an old windows in a logical drive that I can only boot by with a windows bootloader My old boot sequence went:
grub -> Windows bootloader -> win xp/win xp64
grub -> ubuntu

if vista plays along then i'd be fine with that sequence.

---

### Post by NEUR0M4NCER on 2008-05-05
This website was recommended to me in another similar thread, it worked flawlessly for me, and many others.

It tells you exactly how to dual-boot XP, Vista & Linux, with detailed instructions for any variation of install. Awesome - well worth the read.

[The definitive dual-booting guide: Linux, Vista and XP step-by-step](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

This should tell you everything you need to know.

Regards

---

### Post by Computer Guru on 2008-05-05
Another pictorial for dual-booting Ubuntu and Vista (same concept and steps as the APCMag link, but more straight-forward):
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

It should work..

---

### Post by aroddo on 2008-05-06
Thank you for your links.

They cleared up something I was wondering all the time.

I used the neogrub method which relies on easyBCD. It put's it's menu.lst on the same drive as vista and contains (after editing it) the menu-items usually found in your normal grub menu.lst.

you can even put in an entry for the windows bootloader so you can switch from one bootloader to another.

Anyway, I have to recognize microsoft efforts: They overdid themselves again in trying to **** it up for everyone using alternative operating systems. 
And boy - Vista is BLOATED ! After installation it takes up 18 gb of space ! I see myself resizing partitions again soon ...

cheers!

---

