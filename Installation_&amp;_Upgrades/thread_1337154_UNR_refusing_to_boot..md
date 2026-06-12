---
title: "UNR refusing to boot."
date: 2009-11-25
forum: Installation &amp; Upgrades
---

### Post by t0mppa on 2009-11-25
After installing UNR as a dual-boot with Windows 7 on my new netbook, I cannot boot into it. The install went through without producing any errors and grub shows UNR and Windows there just fine. Picking UNR from GRUB simply causes the computer to restart instead of loading up the UNR though. Picking Windows from GRUB works just fine.

So, any ideas as to what's causing this? The installer didn't make the partition I put / on bootable?

---

### Post by dund on 2009-11-25
i'm having a similar problem. i'm using a new asus netbook i plan on giving my 5 year old for christmas. 

where i differ is i'm using win xp and my system will boot into the command line of grub. if someone could tell me the command to go forward into the gui would be great. otherwise i'll assume our problems are similar unless told otherwise. if so i'll gladly start a new thread.

thanks guys!

---

### Post by t0mppa on 2009-11-26
Well, getting to the command line of GRUB naturally works, if you get GRUB to load. I can get that far too, but didn't mention it, since it seemed rather obvious.

If you mean getting to the command line after loading up the kernel, just not into the GUI, then our cases differ quite a bit and you're probably just having problems with your graphics card drivers.

If we're on the same boat however, I wrote up a [bug report on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/488416"), so you could just chip in to let the powers that be notice it's not just me who's experiencing this.

---

### Post by dund on 2009-11-27
i don't think it's the drivers honestly. mine booted fine the first time and tested the file system. the test came back fine as far as i saw and upon reboot unr just doesn't boot.

i appreciate that link and i posted to it too hoping it'll be noticed.

i guess now it's time to just sit back and have some popcorn... :popcorn: ... and wait.

---

