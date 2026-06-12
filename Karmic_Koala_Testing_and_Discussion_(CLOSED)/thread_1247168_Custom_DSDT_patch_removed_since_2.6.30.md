---
title: "Custom DSDT patch removed since 2.6.30"
date: 2009-08-22
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by 67GTA on 2009-08-22
Just to let anyone know that it concerns, the patch that allows loading a custom DSDT patch is not being included anymore since 2.6.30. The 2.6.31 kernel in Karmic and beyond will not support custom DSDT files anymore. This seems to be from Linus, and floated downstream. To date, Ubuntu, Arch, and Opensuse have axed the patch. I'm not sure about Debian yet. I'm sure others will follow. You will have to compile your own kernel to include custom DSDT files from now on. I had a discussion with the Ubuntu kernel devs, and was told to file bugs against "linux" so buggy DSDT code could be addressed at the kernel level. The idea was that custom DSDT files shouldn't be needed anymore. Good luck.

---

### Post by Polygon on 2009-08-23
yeah this is what i was  afraid of......

now its like 10X harder to get a custom dsdt to load, and 90% of people won't even bother and will just give up on linux rather then deal with learning how to compile the kernel just to get a custom dsdt to load. Heck, even I am confused out of my mind on how to compile a kernel.

are you going to take care of submitting bugs for all of the fixed dsdts or should we file bugs (and at which tracker? the kernel bug tracker?) for each dsdt file that we have?

---

### Post by eldragon on 2009-08-23
i think, and dont quote me on this, the issue is the patch wasnt working anymore, and thus, it was dropped. this is what i recall from the archlinux dev list.

if it never made it to the kernel, then its probably more a hack than a patch.

---

### Post by 67GTA on 2009-08-24
The various distros that use newer kernels like Arch, Opensuse, Ubuntu, etc., apply the patch themselves. It doesn't come from the main kernel devs. Linus and other main kernel devs decided not to support it anymore, so there were problems getting it compiled into the kernels since 2.6.30. I filed bugs for my DSDT problems, but am skeptical about them being fixed. I will have to stay at 9.04 unless they are fixed, because my HP laptop overheats. I wonder who I would contact at HP about this, and if they would care? They would probably say that the laptop doesn't support Linux:(

---

### Post by 67GTA on 2009-08-25
For the fearless, I have used kernelcheck to build 2.6.30 on Jaunty with the dsdt patch. I guess I'll install a test partition for 9.10 and try it with 2.6.31 when the patch is released. If it works okay, I might update my DSDT thread with this info. Kernelcheck is about as easy as it gets for newbie kernel compiling. I'm just afraid of all the "my computer won't boot" replies afterwards:(

[http://gaugusch.at/kernel.shtml](http://gaugusch.at/kernel.shtml)

[http://kcheck.sourceforge.net/](http://kcheck.sourceforge.net/)

---

### Post by crimsun on 2009-08-25
> **eldragon said:**
> i think, and dont quote me on this, the issue is the patch wasnt working anymore, and thus, it was dropped. this is what i recall from the archlinux dev list.

That is precisely the kernel team lead's stance, and I concur with it.

That said, if someone wants to show some love for the patch, I'm happy to help (attempt to) sponsor it (back) into ubuntu-karmic.git.

---

### Post by AutoStatic on 2009-09-21
I'm willing to show some love! It would be very unconvenient if I have to recompile every single new kernel for my little netbook which suffers from an erroneous DSDT.

---

### Post by 67GTA on 2009-09-21
I have had a discussion with the kernel devs about it. They refuse to touch it. I've gotten two different answers. One is that the main kernel devs no longer want to use the patch, and everyone else is following suit. The idea was to make people file kernel bugs instead of covering them up with custom dsdt's. The other answer was that the patch had errors with 2.6.30 and 2.6.31, so it was dropped. Either way, my problem can't be fixed by any kernel dev. I've gotten a WONTFIX on two bug reports.  My laptop overheats because the CPU temps aren't seen.

[https://wiki.edubuntu.org/LaptopTestingTeam/HPdv5z](https://wiki.edubuntu.org/LaptopTestingTeam/HPdv5z)



I am planning to move to Opensuse when 11.2 goes final. They have fixed the patch and committed it. 

[https://bugzilla.novell.com/show_bug.cgi?id=533555](https://bugzilla.novell.com/show_bug.cgi?id=533555)

It is useless to bother as far as Ubuntu is concerned. I'm not sure about Debian.

---

### Post by AutoStatic on 2009-09-25
SuSE was my first ever Linux experience, haven't checked it for a looooong time. But if it supports adding custom DSDT's to your initrd image than I'm willing to give it a try.

---

### Post by 67GTA on 2009-09-25
I am waiting for milestone 8 so I can test the custom dsdt patch. The commit should be in the kernel by then. I like Opensuse, but never cared for their Gnome desktop. I use KDE. If you are used to Ubuntu's implementation of Gnome, Opensuse is hard to get used to.

---

### Post by Prikolchik on 2009-10-23
I was looking for a way to fix my buggy DSDT and stumbled upon [this patch]("http://patchwork.kernel.org/patch/52801/mbox/"). Is this something that could add DSDT patch back?

---

### Post by lemmyg on 2009-10-23
Hi,
your problem has to do with the DSDT bios toshiba?

If so, you have to update the bios phoenix 3.8 or greater to resolve the problem with acpi.
with kernel 2.6.22 or greater, the Toshiba laptop acpi works properly.  

I have a laptop toshiba pro p100-103 working in hardy correctly.


	
Good luck.

---

### Post by krantix on 2009-10-23
somehow with karmic my nvidia card is not working again, i.e. it's overheating. only option is to boot with acpi=off

---

### Post by krantix on 2009-10-24
apparently karmic kernel won't load ANY custom DSDT without a patch... this is insane. I can't run the laptop always with acpi=off to avoid overheating!!! really disappointed by kernel maintainers.

---

### Post by lemmyg on 2009-10-24
hi,
are your laptop toshiba with bios phoenix? 

you can look this:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/136469)

---

### Post by krantix on 2009-10-24
I have a perfectly patched DSDT that would avoid overheating on my p100 toshiba, but the new kernel won't load it. Is there any way around? I've upgraded the bios to 4.7 but still only way to survive is with acpi=off (card gets as hot as 120 degrees!)

---

### Post by lemmyg on 2009-10-25
hi,
you can report it in launchpad.

---

### Post by krantix on 2009-10-25
> **lemmyg said:**
> hi,
you can report it in launchpad.

done. it was marked as invalid due to the new kernel policy of refusing DSDTs....

---

