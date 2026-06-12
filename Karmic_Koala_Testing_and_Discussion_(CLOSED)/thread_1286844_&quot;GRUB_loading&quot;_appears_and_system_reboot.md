---
title: "&quot;GRUB loading&quot; appears and system reboots"
date: 2009-10-09
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jward3010 on 2009-10-09
I have no idea how this happened, I didn't do anything to instigate it. Last night everything was fine and today GRUB never loads fully, and system reboots constantly. This is with Karmic BETA 64-bit and Grub 1.97-beta3 (I think it's 3).

What happens:
1. I power up my laptop.
2. The BIOS screen passes and "GRUB Loading" appears.
3. The system restarts instantly, I never see a GRUB menu and timeout screen.
4. The system constantly reboots in a loop.

What can I do to check / repair GRUB?

---

### Post by budluva04 on 2009-10-09
fire up a live cd and recover grub?

[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD")

---

### Post by jward3010 on 2009-10-09
Much appreciated and thanks also for the hasty reply. I'll check that out this second.

---

### Post by jward3010 on 2009-10-09
Great, I'm back. Thanks for that guide, I was having trouble finding it.

I think this is important to point out for the sake of development. It looks as though the volume was corrupted and I'm wondering if that is spelling any problems for ext4. The reason I say this is because I never did a dirty shutdown of Ubuntu to cause corruption, now maybe it's a disk thing but the laptop is only 2 weeks old. Here's the flow of things:

1. Started up - Got to "GRUB Loading" and a sudden restart - loop, loop etc.
2. Booted liveUSB, read above reply, ran guide above, rebooted and got GRUB menu back (only thing missing was Vista option). THANKS!
3. Booted into Ubuntu option but it couldn't boot as "fsck found errors" on the partition. "Run a manual fsck" or "Ctrl-D to try again". First tried "Ctrl-D" no luck, didn't do anything for ages. REBOOT.
4. After reboot, ubuntu option again > "fsck found errors!" still. I ran manual check, it said it "changed files". Rebooted.
5. Boots into Ubuntu without problems.

I know there are known "ext4" corruption issues, is this related, does it sound similar. I mean, I did nothing to cause errors as far as I'm concerned. I always use the laptop on a solid desk, no forced shutdowns, no crazy data throughput, no system stressing - It's only really used for internet at the mo.

---

### Post by ranch hand on 2009-10-09
I don't believe that yours is an ext4 problem.  I have been running ext4 with 9.04 since the RC came out with no problem.

I have hod, however, a couple of times when os-prober has done some "interesting" things to my system.  One was kind of like yours except another drive was involved.  That drive was all grub-legacy and only left on by the stupidity of the guy on the keyboard.

I had to do a CD rescue of my grub-legacy to stop getting the message that the device was not identifiable.

---

### Post by Jonie on 2009-10-09
To throw in my penny, I would check the disk for errors anyway. Speaking from my experience, hdd failure curve has a peak at the begining of lifetime, too. Install smartmontools and check health status of the drive, grep the dmesg for errors relating to sda. This might not be the case either, the new kernel could be in a way incompatible with the mainboard, disabling hpet support might for example resolve the problem.
To put it in a nutshell, the filesystem corruption may be totally unrelated to the new GRUB and ext4.

---

### Post by jward3010 on 2009-10-10
Thanks both of you for your tips, in regards to doing a full check, should I do that with live cd and what command should I use, any particular switches to use for fsck. I'm pure lucky typing fsck on it's own checked the drive.

---

### Post by jward3010 on 2009-10-10
> **ranch hand said:**
> I had to do a CD rescue of my grub-legacy to stop getting the message that the device was not identifiable.

How did grub exactly have this problem, not identifying the device?

And does anyone have any idea as to why the volume became corrupted after purely normal operations? I wouldn't have been completely surprised if I did a hard shutdown while there was data writing going on but the previous shutdown was completely safe as far as I knew.

---

### Post by sandyverden on 2009-10-10
your laptop is bad....
wkwkwkwkwk

---

### Post by Jonie on 2009-10-10
> And does anyone have any idea as to why the volume became corrupted after purely normal operations? I wouldn't have been completely surprised if I did a hard shutdown while there was data writing going on but the previous shutdown was completely safe as far as I knew.

The effects look just like if the hard disk was failing:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/217920")

---

