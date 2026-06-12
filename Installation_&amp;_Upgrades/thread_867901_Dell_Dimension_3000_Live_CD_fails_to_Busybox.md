---
title: "Dell Dimension 3000: Live CD fails to Busybox"
date: 2008-07-23
forum: Installation &amp; Upgrades
---

### Post by R.C. on 2008-07-23
I am a relative Linux Noob.

I have a Dell Dimension 3000 with 1GB RAM and a 40GB HD partitioned for Dual Boot; GRUB can currently load either Win XP Home, or Ubuntu 8.04, from the boot menu.

I would like to try some other Desktop Linux distros. I've created Live CDs of Linux Mint and Kubuntu, and plan later to do the same for PCLinuxOS, Freespire, and maybe Simply MEPIS. All the CDs are burned at 2x speed, and checked: They're fine.

But when I try to boot from the Live CD, it fails with the Busybox prompt, both on the Kubuntu and Mint CDs.

I have tried hitting F6 to add different boot options. I have tried adding the following options (sometimes in combination, sometimes alone) after the two dashes:

pnpbios=off
acpi=off
irqpoll
floppy=off
all_generic_ide

I also tried hitting F4, which (I think) allowed me to set the video to some kind of compatibility mode or something; I don't recall the exact wording.

ANYHOW, none of that has worked: I always wind up at the Busybox prompt, which is utterly useless since I'm too much of a newbie to know what to do with it.

When I first installed Ubuntu it was Feisty Fawn, and over time I upgraded it to 8.04 via update downloads. But I remember the original Feisty Fawn live CDs working FLAWLESSLY.

SO, I have LOTS OF QUESTIONS:

So, what's wrong with the new Live CD's? Why don't they "just work" like the old ones?

Is there any workaround? Or any easier way to completely replace my Ubuntu installation with Mint, Kubuntu, PCLinuxOS, Freespire, et cetera, so I can see how each one behaves "out of the box?"

Is there any way to troubleshoot EXACTLY what's going wrong with the process? Some kind of logfile or something?

Are there some BIOS settings I need to change?

Finally, it looks like I'm far from alone in having this problem; is there an official bugfix release expected?

---

### Post by Pumalite on 2008-07-23
Did you do md5sum on the isos prior to burnning? Clean the lens in your burner

---

### Post by R.C. on 2008-07-23
> **Pumalite said:**
> Did you do md5sum on the isos prior to burnning? Clean the lens in your burner

Pumalite:

While I appreciate the effort; this is why I wrote the original question in such detail: To avoid unnecessary time spent on fixes I'd already tried. Yes, I ran md5sum (actually a command line program called "fsum" from a Windows command prompt) to check the ISOs. No problem, the CDs are as they ought to be.

Any other thoughts?

Anyone else?

---

### Post by R.C. on 2008-07-23
Nobody?

Helloooo? (What with the large number of people who've apparently had this problem before, I hoped someone had figured out a workable solution!)

---

### Post by tech0007 on 2008-07-23
i dont know why the livecd's not working for you.  try the alternate cd instead.

---

### Post by R.C. on 2008-07-23
New Information!

I figured out how to turn off the "quiet" and "splash" options during boot using F6.

This allows me to see everything happening, and see exactly where the Live CD is failing.

The failure happens right at/after this line shows up:

[71.897398] sd 2:0:0:0 Attached scsi generic sd type0

...which I don't understand, since I don't have any SCSI drives or devices in this computer.

Does this help anyone know what's causing the problem?

Let me know. Thanks.

---

### Post by oceallaighm on 2008-07-24
Hi, I don't know if this is of any help.

Link to an earlier posting of mine.

[http://ubuntuforums.org/showthread.php?t=836160](http://ubuntuforums.org/showthread.php?t=836160)

---

### Post by R.C. on 2008-07-24
PROBLEM STILL UNRESOLVED:

I have new information:

However, I have tried booting live CDs from many other distros. Here are the results:

PCLinuxOS 2007: Success

Freespire 2.0.8: Success

Puppy Linux 4.0: Success

Linux Mint 5, Kubuntu 8.04, Xubuntu 8.04: Fails to Busybox with no error message, but with the following messages immediately prior:

"sdb: sdb1 sdb2 sdb3
sd 0:0:0:0 [sdb] Attached SCSI disk
sd 0:0:0:0 Attached SCSI generic sg1 type0"
...and then the Busybox prompt

SimplyMEPIS 7.0: Fails; after booting from CD, it suddenly says it can't find the CD

openSUSE 11.0: After booting from CD, fails with the following message:

"uhc1-hcd
Waiting for CD device to appear....."

FOLKS, all this looks like a problem with the CD drive. What I don't understand is: It's *booting* from the CD drive! It obviously is working up to a point...and then it stops working.

What do I do?

---

### Post by R.C. on 2008-07-24
*bump*

Please read new info (preceding post) re: CD issue

---

### Post by ribico on 2008-07-24
I had the same problem on a desktop..
I was able to boot using all_generic_ide kernel option at boot as suggested by avtolle at the following link

[http://ubuntuforums.org/showthread.php?t=866882&highlight=busybox](http://ubuntuforums.org/showthread.php?t=866882&highlight=busybox)

hope it helps.

ciao

---

### Post by R.C. on 2008-07-24
Already tried all_generic_ide, to no avail. Also a bunch of other boot options (I listed them in an earlier note, above).

Any other ideas?

BTW, a lot of the boot messages suggest that these Live CDs are *initially* able to "see" my CD drive, but then something goes wrong and they lose the ability to "see" the CD drive, causing a failure.

Would replacing the CD-ROM fix this? Or is it more likely to be a controller-on-the-board thing which can't be fixed by just replacing the drive?

---

