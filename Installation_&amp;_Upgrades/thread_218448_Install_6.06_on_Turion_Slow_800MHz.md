---
title: "Install 6.06 on Turion Slow 800MHz??"
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by itsdaveperdue on 2006-07-18
Hi Folks,

I'm trying to install the latest 64-bit Ubuntu on my laptop.  It's got an AMD Turion ML-37 (2.0GHz).  Problem is booting from the CD it's only 800Mhz.  I can't get it to go faster. I tried stopping powernowd, but I think it's not there.  I also tried manually pushing up the freq by using cpu-freq 200000 and some other stuff.

I've also tried passing an acpi=off argument to the kernel during the install, but then it doesn't boot at all.

Please HELP!

Dave](*,)

---

### Post by itsdaveperdue on 2006-07-19
Well it turns out the problem is not with the install cd...after installing my system is still running really slow and scaling is not working.  I've moved this to the 64-bit forums.

[http://www.ubuntuforums.org/showthread.php?t=218999]("http://www.ubuntuforums.org/showthread.php?t=218999")

---

### Post by hizaguchi on 2006-07-25
Not a 64 bit problem.  It happens in 32 bit Ubuntu too.

---

### Post by itsdaveperdue on 2006-08-17
Add "noapic nolapic" to the boot options and it works great.

---

