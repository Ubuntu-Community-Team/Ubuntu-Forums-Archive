---
title: "Ubuntu won't boot. Please help."
date: 2007-11-02
forum: Installation &amp; Upgrades
---

### Post by BA20 on 2007-11-02
Hi all,

I have a problem since a couple of days and it keeps me bizzy. I really would like to use Ubuntu, but I just can't find the solution.

The problem is that I still can't boot. In the meantime I find that it has something to do with anything new introduced to Gutsy, since I can boot Feisty without any problems.

I tried the following boot options. I removed "splash" and replaced it every time with:
acpi=off
noacpi
acpi=force
pci=noacpi
acpi=noirq
pci=acpi
acpi_irq_balance
acpi_irq_nobalance
acpi=oldboot
acpi=ht
noapic
nolapic
irqpoll

... but nothing works. Always the same problem occurs.

In attachement soms pictures when booting.
- screen that the linux kernel boots
- the beginning of the error
- the end of the error
- the same error with the alternate cd


I would be very greatfull if anyone could help me solve this problem. I am still using Windows and I am full of good courage to change totally to Ubuntu, but this problem just doesn't do good. I really hope someone could help me. I don't want to think to the moment I just don't am interested anymore in Ubuntu because of this, I would be very sorry.

So please help me.

And please, don't send me to many links, I have seen so many but it won't help. I very sorry.


Thanks,

BA20

PS: here are some messages I posted:
- [http://ubuntuforums.org/showthread.php?p=3691187](http://ubuntuforums.org/showthread.php?p=3691187)
- [https://answers.launchpad.net/ubuntu/+question/16854](https://answers.launchpad.net/ubuntu/+question/16854)
- [https://bugs.launchpad.net/ubuntu/+bug/159541](https://bugs.launchpad.net/ubuntu/+bug/159541)

---

### Post by It_Was_Luck on 2007-11-02
This is the live CD I can see, when your at the main menu select "Check CD for Defects" and see if that picks up anything.

---

### Post by Pumalite on 2007-11-02
Start with the basics: download new iso if md5sum not correct, burn new CD at 4x, check for CD corruption before install, try your CD in a different computer. If all that fails, then go with the Alternate CD.

---

### Post by BA20 on 2007-11-02
I did what you said: I tried the Live CD on another computer and I did the cd-check for defects. The Live CD works on the other computer, It works very fine there. The CD check (which I also dit on that computer, it doesn't on mine) did not return any error: it just said: "no errors found". So if I am right, I think the CD must be OK. But that's not so OK because we still don't know the problem...

Do you know what the errors on the screen prints mean?

---

### Post by Pumalite on 2007-11-02
It seems you already tried the Alternate CD. I'm stumped, sorry. Someone that knows better will chime in.

---

### Post by Pumalite on 2007-11-02
OTOH, there are some boot parameters that you might try. I'm not very good at this, but I have a Guide and a collection of links:

[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317

I hope it helps.

---

### Post by BA20 on 2007-11-03
I really appreciate your help, but I don't know where to start. I have tried so many boot options (see my first post on this thread), I retried the ones you send, but always the same errors. **Is there someone who has an idea which options could be the solution, looking at my erros?**

In the meantime I did an md5sum of the CD and of each file, but still no errors there.

---

### Post by joao82 on 2007-11-03
have you tried unplugging all the modems, printers, external drives, etc?
try booting with only the keyboard and monitor. no idea if it's related, but it's not hard to do.

---

### Post by BA20 on 2007-11-03
I just tried to do what you said. I unplugged everything exept for the keyboard, the screen and the power supply, but I still get the same error. So I also tried without the screen, without the keyboard and without both, so that I only have to power supply, bot none of that works.

I really hope that there could be solution.

---

### Post by BA20 on 2007-11-03
Is there someone else who has an idea? I really love to install Ubuntu, but I can't find how.

Thank you.

---

### Post by lguedes on 2007-11-03
I have the same problem, and it is caused, I think, by an incompatibility between the latest kernel and my Seagate hard disk (ST320413A)

Don't know how to fix

---

### Post by BA20 on 2007-11-03
That's very interesting! I have the same hard disk: ST320413A. Maybe that's where the problem comes from. Does anyone has an idea?

---

### Post by mivo on 2007-11-03
Does your computer have a floppy drive? It seems to be looking for one, so it might be enabled in the BIOS (even though you might not even have one). Try going into the BIOS (f2, f10, ESC, depends on your BIOS) and check if the floppy is enabled. Disable it if this applies.

---

### Post by BA20 on 2007-11-03
Hi mivo, you are right about the floppy drive! I have one and indeed it had something to do with it, because when I desabled the floppy drive, the error was slightly different: it wasn't looking anymore for the floppy drive... but there is still that "modprobe abnormal exit". Do you know what that means?

Thanks for the idea about the floppy drive, we are getting closer and closer. Maybe I just have to try to unplug the hard drive and see what happens when I boot. Unless you or someone else has another idea, so I don't need to go in my computer...

---

### Post by BA20 on 2007-11-03
I forgot to attach the new screenprint.

---

### Post by mivo on 2007-11-03
This resembles [this bug]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/93648"), but that one was fixed months ago. (Don't use the kernel linked in there.)

Are you sure your kernel options are taken? Do you press ESC in the Grub countdown, then "e"dit and "b"oot? Does your machine restart completely or does it continue to boot from where you were? (i.e. no other Grub countdown)

---

### Post by BA20 on 2007-11-03
Indeed it ressembles the bug you link to. What should I do, except for trying the linked kernel?

Concerning Grub: I don't think I am using Grub. It is just the Live CD. I choose "Start or install Ubuntu". (see a picture in my first post) Which boot options do you think I should try?

Thanks

---

### Post by mivo on 2007-11-03
Have you tried a different Linux distro? At this point this is what I would probably try. I have been impressed with the Fedora 8 RC3 which had worked on my hardware out of the box when Gutsy would not (it also automatically told me to use irqpoll). This would at least tell us (and you) whether the problem is Ubuntu-specific or of a more general Linux nature -- and could help to narrow down the search. Just the Live CD will do: [http://torrent.fedoraproject.org/](http://torrent.fedoraproject.org/)  (I would not recommend Fedora 7, it did not work well on my hardware.) This sounds better than opening your computer and removing hardware. :)

Sorry this is so frustrating. I went through similar pains this past week.

---

### Post by BA20 on 2007-11-03
I will immediatley try Fedora. It really sounds impressive that Fedora told you to use irqpoll, so it saw the problem. This sounds indeed better than opening my computer. In fact, removing the hard disk does not solve my problem because where else do I install Linux :)

So thank you for the tip, beacuse as you say, it really can be frustrating when nothing works.

---

### Post by mivo on 2007-11-03
Yes, when it found a problem with IRQ 19, it said something like "Maybe you should try the irqpoll option?". This was actually the one tip that helped me fix my Gutsy issues (on this brand-new computer). When Fedora worked, I knew it was not my computer, which not only made me feel significantly better, but also made working on the problem more hopeful: I knew that my hardware was not somehow unfit to run Linux. It is all Linux, so if one distro works, you should be able to get any other to work as well (though not necessarily easily).

---

### Post by BA20 on 2007-11-05
Yesterday I tried the Fedora 8 Live CD. I still get errors there. Please see the first attached picture to this post. It had something to do with my sr1-device. Could this be my Seagate harddisk? So if it is, could we conclude that there is a problem between my harddisk en the newest linux kernel? And the question that interests me the most: does anywone know how to slove this problem? In other words: **does anyone know how I could boot my computer with my harddisk?**

In the second picture you can see that there is a a problem with irqbalance. So I tried irqpoll (as in Mivo's problem), but nothing changed. To be complete: I got the errors, but Fedora still started. I would like to do the same with Ubuntu...

---

### Post by mivo on 2007-11-05
I wish I had any more ideas. I experienced the same situation that Fedora did boot into the OS even after the error messages, but Ubuntu would hang itself and only work once I knew what the problem was and could modify the boot options (in my case this was irqpoll and nosplash, but this does not seem to apply here). If nobody here has any suggestions that you have not already tried, I think you could also try asking on the Fedora forums -- they have a large community with a fairly high technical knowledge level, too.

I'm curious what is causing your troubles. (And I admire your patience.)

---

### Post by lguedes on 2007-11-12
Hi,

Found how to install Gutsy on the Seagate ST320413A disk, you must add all_generic_ide to the kernel startup options.

Press F6 on the live cd start menu and add "all_generic_ide" (no quotes) to the line that appears so you can install, then on reboot press Esc and do the same and see:

[http://ubuntuforums.org/showthread.php?t=584601]("http://ubuntuforums.org/showthread.php?t=584601")

to make it permanent.

Hope it helps

Luís

---

### Post by BA20 on 2007-11-14
Hi Luís!

Thank you very much! It did solve my problem. I was able to install Ubuntu 7.10 and it boots as it should now. So great!

BA20

---

