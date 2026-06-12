---
title: "BIOS age fails cutoff, trying to install"
date: 2007-03-14
forum: Installation &amp; Upgrades
---

### Post by rjfioravanti on 2007-03-14
Hi everyone

I am trying to install xubuntu on some laptops, I download the herd 5 feisty cd

The menu boots up fine, but when I click start or install, i get stuck at the following error

[code]
ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
invalid compressed format (err=2)
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block

This happens right after it tries to load the linux kernel

It is happening on P3 IBM Thinkpads, model 600x

How can I get around this?

---

### Post by jjalocha on 2007-03-14
Have you tried installing a stable (Edgy Eft) version before? Did that work?

---

### Post by rjfioravanti on 2007-03-14
I have not tried edgy, I started using feisty at home a while ago and ive had no problems so I didnt think it would make a difference

---

### Post by rjfioravanti on 2007-03-15
I figured out so far that I may be able to proceed just by adding the correct boot option, does anybody know what these may be?

---

### Post by rjfioravanti on 2007-03-15
if I add the boot options: 

acpi=off apm=on

then I get rid of my first error message, which feels like progress =)

now I am just getting the following errors on boot (from live cd)


invalid compressed format (err=2)
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block

---

### Post by rjfioravanti on 2007-03-15
I updated the bios by downloading an update from the IBM website, and then I was able to load the live cd using no boot options

we will see how the install goes

---

### Post by Pitt Stains on 2007-10-27
I know this is an old thread, but....

I have an old NEC PowerMate 2000, onto which I've installed Xubuntu 7.10.  However, I can't get it to boot (or rather, I think it boots, but instead of getting a login screen, I get a black screen).

Anyway, I am getting the same BIOS age notice, and I located this BIOS update from the NEC website: [ftp://ftp.necam.com/pub/Catalog/3921/PM2KC-BIOS-13.exe](ftp://ftp.necam.com/pub/Catalog/3921/PM2KC-BIOS-13.exe).  The problem is the website says the update is for Windows XP or NT 4, and the file is an exe.  Is there anyway to run this from the CLI (which I can access), or do I have to install Windows just to do this update?  In which case... ARG!

Thanks!
Pitt

---

### Post by soleille on 2008-03-10
This is seriously weird - I have had the same problem and upgraded the BIOS (well- had someone upgrade it, this looked way over my head) on my T20

It IS upgraded now (a good 10 versions above the one I had) - however, *all* versions have the *same* BIOS date somewhere in 1999 - so it still fails cutoff age.

While this means Ubuntu doesn't usually start up at the first try, the third or so mostly does it - and weirdly enough, if I've booted windows, restart and then boot Ubuntu, it comes up on the first try without fail.



Will the suggestion of  " boot action acpi=off apm=on" get rid of the startup problem? With no acpi I still won't be able to hibernate etc right? Can something else be messed up if I add this?

If this is a good idea, can I have a aimed-at-idiot walkthrough through setting this boot option please? (when, where and how exactly do i do it?)

Thank in advance :o)

---

