---
title: "extremely slow system using linux-image-server or amd64"
date: 2007-12-15
forum: Installation &amp; Upgrades
---

### Post by e2npau on 2007-12-15
Hello,

Yesterday my new computer arrived - and I was happy as a child in a candy store.

Reality struck rather quickly.

My system is a Q6600 intel core 2 quad on a gigabyte ga-p35-ds4 mobo with 8 Gb of ram. Since I wanted to use all of my memory I first tried to install 7.10 amd64 but I didn't get very far. All it would show was a black screen. 

By using 7.10-alternate-amd64 and removing quiet from the bootopts I got a little further - it was actually running - only extremely slow - after about an hour I had finished the disk partitioning and I got bored and rebooted.

If I'm using 7.10-desktop-i386 or 7.10-alternate-i386 everything works fine my systems gets installed and boots up quickly - but with only 3.6 Gb of ram.

If I install linux-image-server on my i386 system I get the exact same results as if I were using the amd64-distro - an extremely slow system - the raid5 speed check reports 33 Mb/s instead of 10071 Mb/s.

I have tried booting with more or less every possible combination of "clock=pit , clock=pmtmr, nosmp, noapic, nolapic, acpi=off, apm=off, hpet=disable" and it doesn't make any difference. Nor have any bios settings I've tried out made any difference either - such as enable/disable nx or vmx.

I would really like to be able to use all of my ram ... If someone has any ideas I would be very happe to hear them.

  /N

---

### Post by e2npau on 2007-12-15
more information:

Since linux-image-2.6.22-14-generic is working great apart from me missing 4 Gb of ram i made a custom kernel by using /boot/config-2.6.22-14-generic and make-kpkg only changing higmem support from 4 Gb to 64 Gb.

And that kernel also ran extremely slow.

The problem seem to be pinned down - but I have no clue what can be done.

Anybody knows? Please!

---

### Post by e2npau on 2007-12-16
I might add that I let memtest86+ run overnight with no errors.

  /N

---

### Post by roaldz on 2007-12-16
Very weird problem. Try an older ubuntu amd64 cd (6.06?). See if that boots. Only thing I can think off..

---

### Post by e2npau on 2007-12-16
After a lot of googling on this one - here's what I have found.

It is most probably a buggy bios - probably will need to upgrade/downgrade bios or aply the patch below and build meself a new kernel.

[http://lkml.org/lkml/2007/6/6/333](http://lkml.org/lkml/2007/6/6/333)

Other links that's interesting in this context.

kubuntu amd64 user with the same problem:
[http://mail.wlug.org/pipermail/wlug/2007-August/006260.html](http://mail.wlug.org/pipermail/wlug/2007-August/006260.html)

Gentoo:
[http://groups.google.com/group/linux.gentoo.user/browse_frm/thread/830f835cc37dacb6/d9ef4d926c80149%23d9ef4d926c80149](http://groups.google.com/group/linux.gentoo.user/browse_frm/thread/830f835cc37dacb6/d9ef4d926c80149%23d9ef4d926c80149)

/N

---

### Post by roaldz on 2007-12-16
What if you take a 32bit kernel that works, and recompile it to have 64bit support..? I dont have experience on that one, but you could fuzz it out... Right?

---

### Post by e2npau on 2007-12-17
A bios upgrade solved the problem.

The reason I didn't do that as the first thing was that I already had a recent bios - from august this year and the readme file for the new bioses only stated "Support Intel 45nm Yorkfield CPU" and my computer wasn't equipped with a floppy drive.

However using the cd-method from [http://gentoo-wiki.com/HOWTO_Create_a_DOS_boot_disk](http://gentoo-wiki.com/HOWTO_Create_a_DOS_boot_disk) I was able to make a bootable cd-rom and flash the bios - and now everything is working with at full speed with all the ram.

Now I only need a reinstall from i386 to x86_64. :)

---

