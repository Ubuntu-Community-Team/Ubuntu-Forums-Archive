---
title: "Failed boot ~40% of the time"
date: 2010-10-22
forum: Installation &amp; Upgrades
---

### Post by TheBuzzSaw on 2010-10-22
I am currently dual booting Ubuntu 10.10 and Windows 7 Pro using GRUB (whichever one was auto-installed in 10.10).

As the title suggests, about 40% of the time, after selecting an OS in the GRUB menu, it fails to boot. At first, I thought it was a bad Ubuntu install, but it happened once or twice with trying to launch Windows 7. Generally, I can just reboot, select again, and have better luck. However, I think I am reasonably concerned about this. :)

I select an item, and then I get pages upon pages of various errors, debug messages, kernel something-or-others, etc. and then it just stops. *Sometimes*, it'll fire up the ASCII-based Ubuntu loader screen (obviously not when booting Win7), but it never makes it in. I have to reboot to get it working.

Any ideas? I'm prepared to revert to 10.04 if I cannot resolve this. :(

ASUS P7P55 LX motherboard
Core i5 Quad 2.8 GHz
4 GB DDR3 RAM (Corsair)
Nvidia GTX 275 (running drivers from Nvidia, not Ubuntu)

---

### Post by Grenage on 2010-10-22
Have you, or could you, rule out the hard drive being faulty.  I'm just going in on the easy-to-test first.

---

### Post by TheBuzzSaw on 2010-10-22
Well, I cannot prove it is *not* faulty, but I did just buy it a couple months ago. It is a 1 TB Caviar Black. It would be highly unlikely... and ultra depressing if it turned out to be true... :(

---

### Post by Grenage on 2010-10-22
Well you can still access it for data 60% of the time; if it is a failure, at least you'll get your data.

If the manufacturer has a utility, that would be handy.  Failing that, some BIOS have a drive diagnostic feature.  A Linux or Windows checkdisk might be ok.

Like you say, it might not be the drive.

---

### Post by TheBuzzSaw on 2010-10-22
I'm gonna go out on a limb and assume it's not the drive. The issues only started after installing Ubuntu 10.10. When inside a particular OS, I never run into problems of any kind. It's just in and around GRUB where things go horribly wrong. I mean, I'll run a few scans anyway just to be safe, but I can't imagine my HDD going bad this soon. Does reinstalling OSes stress it in any particular way? XD

I did recently replace the motherboard. Could that affect it?

---

### Post by Grenage on 2010-10-22
> **TheBuzzSaw said:**
> I'm gonna go out on a limb and assume it's not the drive. The issues only started after installing Ubuntu 10.10. When inside a particular OS, I never run into problems of any kind. It's just in and around GRUB where things go horribly wrong. I mean, I'll run a few scans anyway just to be safe, but I can't imagine my HDD going bad this soon. Does reinstalling OSes stress it in any particular way? XD

I did recently replace the motherboard. Could that affect it?

It might do, yes; double-check all connections.  The fact that you have 'no' problems once booted, does make it less likely that it's the drive, I agree.

You could try reinstalling grub; it can't hurt!  My gut still says *hardware*, but ruling things out is still progress.

---

### Post by TheBuzzSaw on 2010-10-22
I *think* I found the problem.

Just now, I tried to boot Windows 7. For whatever reason, it made it as far as the glowy logo (where the screen is still mostly black), but it sat there forever until I did a hard reset. I was so confused! Suddenly, I noticed: my external hard drive was still plugged in. I've had problems like this in the past where the BIOS detects a USB drive, tries to mount it as a default boot hard drive, etc.

I unplugged it, rebooted, and Windows 7 booted fine. Either it was a massive coincidence, or I found the problem. I'll definitely return to this thread if it happens again (and the external is unplugged when it happens).

Thanks for brainstorming with me, Grenage. If my external was indeed the problem, your gut was right. It *was* hardware-related... just maybe not in the way we expected. ^_^

---

### Post by Grenage on 2010-10-22
I hope that it turns out to be the problem!

I'm surprised that it got as far as Grub if it was trying to boot from USB, but I'll keep my fingers crossed. :)

---

### Post by TheBuzzSaw on 2010-10-22
So far, Windows and Ubuntu both boot happily. I'm interested to collect a few weeks' worth of results. Suddenly, Ubuntu 10.10 isn't all bad. :P

---

### Post by TheBuzzSaw on 2010-10-25
It turns out there was more to the problem. Unplugging my external HDD did fix my Windows booting issues (not sure what was up with that), but I started having Ubuntu booting issues again. So, I studied my new motherboard more specifically with Google.

[http://ubuntuforums.org/showthread.php?t=1422682](http://ubuntuforums.org/showthread.php?t=1422682)

This helped me better diagnose my problem. My setup is almost identical. The first step to recovery has been in switching IDE mode to AHCI (had no idea it was set to IDE still).

---

### Post by Grenage on 2010-10-25
You should get better performance with AHCI; so if that fixes it, if will be a double win!

---

### Post by TheBuzzSaw on 2010-10-25
So far so good. I've reinstalled Windows 7 (got a new key and everything). The difference is astounding. Ubuntu reinstall is next!

---

### Post by TheBuzzSaw on 2010-10-26
Curses. It happened again.

Windows 7 is quite happy. In fact, levels now load super fast in Borderlands. I'm glad I did a clean sweep!

Ubuntu is still angry at the world. During boot, I get pages and pages of console errors. "debugfs" this, "kernel" that, etc. I can't really capture the text. I think I'll need to use a digital camera to show what is going on.

I've disabled IDE mode. I switched it to AHCI. That did help a lot of things, but these boot issues are still here.

---

### Post by TheBuzzSaw on 2010-10-28
First post has been updated with a picture.

---

### Post by Grenage on 2010-10-29
It wasn't the loose SATA cable, then?

---

### Post by TheBuzzSaw on 2010-10-29
> **Grenage said:**
> It wasn't the loose SATA cable, then?

Fixing the loose SATA cable did fix a lot of things... but Ubuntu still hates life. Windows 7 started having problems until I fixed that cable. So, now I've narrowed down to some incompatibility between Ubuntu and my mobo/CPU.

---

### Post by TheBuzzSaw on 2010-11-12
I think I fixed it for good finally.

I started noticing a pattern in all the crashes: page faults and segmentation faults. That got me thinking, "OK, that's a memory issue, not a HDD or a motherboard one." So, I ran the memtest from GRUB. It was failing 99% of tests! I started to think I had bad RAM!

So, I did a Google search for my type of RAM (Corsair XMS3). It turns out, it requires special BIOS settings. So, I set my profile to XMP. 100% pass rate in memtest now. Systems boot fine.

---

