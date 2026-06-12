---
title: "[SOLVED] 7.10 won't boot on M2A-MVP Asus mainboard"
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by sblanzio on 2007-10-21
Just to let you know..

Ubuntu 7.10 seems impossible to boot on M2A-MVP Asus mainboard.

Feisty gave some trobules too but you could boot with "acpi=off" option.

Now this doesn't work anymore.

Thanks god i haven't upgraded.

Bug filed. [https://bugs.launchpad.net/ubuntu/+bug/155349](https://bugs.launchpad.net/ubuntu/+bug/155349)

if you find a way to overcome this please answer both here and on launchpad.

thnx
bye

---

### Post by Desd on 2007-10-21
I seem to have a similar problem. I did upgrade, but it would not work. Blamed my stupidity in interrupting the upgrade and start again. Slowly by slowly I've tried to solve the problem, ending up in wipping my hdd with dban and fixing my mbr with supergrub, but still:

Both Ubuntu and Kubuntu will not boot. The start up ends somewhere at the progressbar. Nothing happens. I thus do get the install menu with the six or so choices and pressing "start and install (K)Ubuntu" will produce the progressbar to run, but at a certain point the progress bar gets stuck just like my PC... 

The CD's will work on my wife's laptop, so there is no problem there.

Running on a Asus F3M 3400+ sempron. 7.04 worked flawlessly...
Greetings,


Desd

---

### Post by the_real_bubba on 2007-10-21
Arrgh! this really sucks!  I finally got the second HD for a machine I bought a month ago, then I spent all day trying to get this to work and I figured it was not working because I didn't understand SATA master/slave HD configs.  Now I can't take back my computer and ask for my money back just because it won't run Ubuntu...

I can run the AMD64 7.10 live CD, and the install seems to go fine, but after the grub OS selection, I get a persistent black screen of nothingness...

---

### Post by sblanzio on 2007-10-22
did you try grub kernel options like "acpi=off", "pci=noacpi", "noapic", "nolapic", "irqpoll" ? Pay attention there's difference between "apic" and "acpi"

bye!

---

### Post by the_real_bubba on 2007-10-22
Hmmmm, so I can boot into rescue mode from the installed HD kernel...

Now, with acpi=off, pci=noacpi, noapic, nolapic, irqpoll I can boot, but no monitor or graphics card detection (and if I enter my monitor and video card, it just forgets what I entered and boots into ridiculously low resolution mode anyway.

Also, grub edits at boot time are ignored (good thing I can make new grub stanzas via rescue mode.

Installing linux hasn't been this much work since Slackware. :(

Thanks for the help sblanzio, I'll keep plugging away hopefully I can get a usable system before the sun rises.

---

### Post by the_real_bubba on 2007-10-22
OK, now I think it's not the mobo, I think it's the videocard, or something.  The crucial grub tweak is to remove the "quiet".  It's the "ubuntu is running in low-graphics mode" graphical dialog that I think is creating the hang.  I don't think this is visible with the "quiet" grub option.  For some reason, the Samsung Syncmaster 940bw and ATI Sapphire HD 2600 XT are not detected, the max graphics resolution is 800x600 and the dialog announcing this during boot was invisible.  Without "quiet" there's a very long and ugly boot, followed by a low res computing experience...  It's late & I'm cranky. I'll see what else I can fund tomorrow evening.

---

### Post by sblanzio on 2007-10-22
If I can suggest you... unless you can't do but install gutsy, go back to feisty and wait for something better from developers.

---

### Post by sblanzio on 2007-10-22
I have to apologyse with developers and all of you, but my troubles depended on my mistakes.

During my tests with Gutsy live cd, I used to hard-reboot when it hanged after booting. I did like this because I already tried several times with fiesty, and when my cd drive stopped spinning because of acpi trobules, this meant it just freezed.
Now, I accidentally found out that if I leave it loading more, after a couple of minutes my cd drive starts spinning again and, even if very slowly, the gnome session begins. So I investigated booting without kernel options like "quite" or "splash", and I found out that gutsy stopped because it was looking for a floppy drive that I don't have, but that is indeed set on Bios.
So I removed the floppy drive from bios and now my gutsy cd live loads perfectly. Just, I must say, it's really slow to load.

More, this means that Gutsy live cd, differently from Feisty, can boot without acpi=off, and in fact, if I halt my system from gnome, surprise surprise... the system halts!

So, this is not at all a backward step with acpi, but a forward one! Now my mainboard is acpi supported by ubuntu! (at least on live cd... ;) )

So, at least on my side, this problem is "solved".
Next week I will format and install gutsy, then I'll let you know if I'll find any trouble about booting.

thanks everybody and, again, my apologyses.

bye!
sblanzio

---

### Post by the_real_bubba on 2007-10-22
I'm with sblanzio here, the "quiet" grub option is hiding the proximate mechanism of failure, but seems there's something deeply broken about 7.10 on this mobo.  It runs _very_ slowly, in addition to the video problems reported here.

---

