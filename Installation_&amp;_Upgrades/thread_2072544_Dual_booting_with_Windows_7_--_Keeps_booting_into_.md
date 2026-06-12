---
title: "Dual booting with Windows 7 -- Keeps booting into Windows"
date: 2012-10-18
forum: Installation &amp; Upgrades
---

### Post by pkirkaas on 2012-10-18
I use Ubuntu every day at work. My home PC is Windows 7. I wanted to set up a dual boot with Ubuntu.

I did that. Got Grub set up. Got the choice to boot into windows or Ubuntu. Booted into Ubuntu. Configured. Rebooted, got the choice again, chose Windows.

Worked in Windows for a bit. Rebooted. No choice, no Grub, just straight into Windows. 

Booted from Ubuntu Live CD. Downloaded a grub repair tool & ran it. Rebooted. Got Grub menu, chose Ubuntu. Rebooted. Grub Menu. Chose Windows. Rebooted. No choice, straight to Windows.

So it seems like every time Windows boots, it "repairs" its MBR or something.

I've read about lots of problems dual-booting, but haven't come across any advice about this one.

Any thoughts? Weird thing is I have a pretty vanilla setup -- I would have thought if I have this problem other people would have too, but I haven't really found that.

---

### Post by darkod on 2012-10-18
It might be vendor specific (HP and Dell had software running in the background deleting grub2 few years back).
Or it might be some MS sh*t like Security Essentials or something, that considers anything except windows a threat. :)

---

### Post by rudeboyskunk on 2012-10-18
Did you install GRUB to the MBR or to the first sector of your hard disk?  After you re-install GRUB, post your grub config file if you're still having the problem.

---

### Post by Mark Phelps on 2012-10-18
I'm with darkod on this -- some PC vendors install "security" software that makes a copy of their original MBR, saves that off somewhere, and when you reboot, compares the current MBR to the saved copy -- and if they are different, restores the saved MBR.

That sounds like what your PC is doing.  Sorry, don't know the name of the software that is doing it, as it is vendor-specific.

One thing you could try is installing EasyBCD from NeoSmart technologies and using that to add an entry to the Windows boot loader for Ubuntu.  At least that way, you will get the dual-boot option back and won't have to keep rewriting the MBR.

---

