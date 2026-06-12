---
title: "Install Ubuntu on particular partition of particular harddrive."
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by finny388 on 2008-01-01
I am sorry if this has been covered somewhere else but I've searched and can't find my exact situation.

I am new to Unix, Linux and Ubuntu but I like what I've seen. I don't want to go another round with Microsoft with Vista.

Simply: I want to dual boot XP and Ubuntu (7.10 unless there is reason to use diff ver)

My setup:

Drive A (Mstr):
Part1: Windows
Part2: Files

Drive B (Slave):
Part1(10GB): Windows
Part2: Files

all are NTFS

Currently I boot w Drive A Part 1. Drive B Part1 is a relic and can be wiped out, and used for Linux.

But I don't want to disturb Drive B Part 2.

I want to have:
Drive A (Mstr):
Part1: Windows (untouched)
Part2: Files (untouched)

Drive B (Slave):
Part1(10GB): Ubunto (EST3)
Part2: Files (untouched)


Steps I've taken:
1. Boot w Live CD
2. Install
2a. I delete Drive B Part 1 partition
2b. Create new in EST3 format.
Problem:
2c. Click Fwd and I get something like Cannot find root file - go back and fix it.

Questions:
I want the dual boot to trigger from Drive A Part 1 so I guess I'd edit boot.ini to point to Ubuntu?
Do I want the new linux partition to be Primary or Logical?
What can I do about this root error?

Thanks for any help and I can't wait to make this switch!

Cheers

---

### Post by logos34 on 2008-01-01
> **finny388 said:**
> Steps I've taken:
1. Boot w Live CD
2. Install
2a. I delete Drive B Part 1 partition
2b. Create new in EST3 format.
Problem:
2c. Click Fwd and I get something like Cannot find root file - go back and fix it.

Questions:
I want the dual boot to trigger from Drive A Part 1 so I guess I'd edit boot.ini to point to Ubuntu?
Do I want the new linux partition to be Primary or Logical?
What can I do about this root error?s

It appears you forgot to set the mountpoint.  You want a primary ext3 root mounting at '/'.

---

### Post by finny388 on 2008-01-02
Thanks logos34, it seemed to install smoothly.
I didn't install bootloader b/c I thought WinXP would handle that.
I removed the CD for reboot knowing it was now going to reboot to WinXP. I let it go to see if Windows was fine. It was.

[B]Another reboot, assign Drive B (my new Ubuntu drive) to boot in BIOS, and I get black screen w "PRESS A KEY TO REBOOT".

And it just loops doing that.[/B]

Was it b/c I didn't install bootloader?
Because I booted into WinXP before closing the installation deal of Ubuntu?

Amazingly google has nothing on this error for ubuntu.

Please help! Also, I am reading that GRUB is the best bootloader around.

I don't care which drive handles booting. Windows will for the time being be the default OS. I just want to boot into Ubuntu as time permits to try it out.

What is my best approach now?

Thanks

---

### Post by logos34 on 2008-01-02
hmm...Grub installs by default to the Bios boot drive (in this case your master/xp), so grub should have popped upon reboot. Set the xp drive back to boot drive in Bios and try tapping Esc key on reboot to bring up the grub menu screen--maybe 'hiddenmenu' option is enabled.  If not there, then try[ reinstalling grub from the live cd]("http://ubuntuforums.org/showthread.php?t=224351").  (except install it to the windows drive mbr, so do 'setup (hd**0**)')

edit: when you say you didn't install bootloader, did you explicitly tell it NOT to install grub? ('advanced button', etc)

---

### Post by finny388 on 2008-01-02
yes
I went into Advanced and unchecked the install of bootloader.

Is GRUB another name for Bootloader?

When I get home tonight I will try to install grub to my main disk (hd0) and let you know what happens.

But grub = bootloader correct?

Thanks so much logos34

---

### Post by logos34 on 2008-01-02
> **finny388 said:**
> yes
I went into Advanced and unchecked the install of bootloader.

In that case you don't have any grub files at all in boot.  Better to just reinstall (at around 30 min it'll take less time than fixing it).  Just let it install grub to default location, '(hd0)'--the MBR on your XP drive.  It'll overwrite your windows bootloader, but you can easily restore that later if necessary by using the Super Grub Disk or your XP install CD (--> fixmbr).

Yes, grub is synonymous with bootloader

---

### Post by zvacet on 2008-01-02
**GRUB=Grand Unified Bootloader**

---

### Post by finny388 on 2008-01-03
That was so simple!

Thanks logos34,

Finny

---

### Post by logos34 on 2008-01-03
> **finny388 said:**
> That was so simple!

Thanks logos34,

Finny

So, you fixed it or what?

---

