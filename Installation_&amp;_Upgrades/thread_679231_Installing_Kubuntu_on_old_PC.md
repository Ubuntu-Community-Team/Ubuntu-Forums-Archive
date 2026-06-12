---
title: "Installing Kubuntu on old PC"
date: 2008-01-26
forum: Installation &amp; Upgrades
---

### Post by colecampbell666 on 2008-01-26
The HDD on my old PC is 160 Gb, but Windoze XP only reads it as 32 Gb. Ubuntu/Kubuntu read the drive as 160 Gb, so I wiped it to try and get the full HDD. I installed Xp, and then Kubuntu and I get an error 18. I deleted XP, and formatted the PC. I installed Kubuntu again. Error 18. After a few more cycles of this, I realised that even in Kubuntu, the HDD only read as 32 Gb sometimes. If I partition it, and then restart, it will read the full size. If I partition it to 160 Gb, in the format utility, Active@ KillDisk Free, says that there is a 160 Gb partition on a 32 Gb HDD. If I try to format the partition in lieu of the whole HDD, it only formats 32 Gb. After a few tries of doing the same thing, I got Kubuntu to work, but when I updated it, it screwed it up. After reformatting it, confident that the problem was fixed, it stopped working again. Anyone able to shed light on my problem?

And a query: I'm getting more RAM, 2 Gb PC133 SDRAM, the max supported by my PC, and I want to know if my CPU will cause bottleneck issues. Here are my current PC specs:

Pentium 4 @1.5 Ghz, 512 Kb cache 400 Mhz FSB
GigaByte 8IDML -C Motherboard
512 Mb PC133 SDRAM
ATI Radeon 9550 Pro 256 Mb @ AGP4X
Maxtor DiamondMax 6Y160P0 160 Gb 7200RPM (master)
Maxtor DiamondMax 2B020H1 20 Gb 5400RPM (slave)

Will my CPU cause bottlenecks currently, or when I get the new RAM, and if it does, is [this](http://processorfinder.intel.com/details.aspx?sSpec=SL7E4) a good replacement?

---

### Post by CheShA on 2008-01-26
The only configuration problem I could think is that maybe there is a jumper on the drive which is set to restrict it to 32GB and it is not being interpreted properly by your BIOS, or that your BIOS is reporting the capacity incorrectly.  If there's no such jumper on your hard drive, then maybe flashing your BIOS could fix it, but most likely of all is that your HDD is knackered and you should replace it - try swapping it out for another large capacity drive first to make sure your BIOS can handle drives that big before you splash out though.

Edit: looking at the specs for your your board of course it should support drives this big.

---

### Post by CheShA on 2008-01-26
Oh, and I wouldn't expect your CPU to cause a bottleneck, you should get fair performance out of that with Kubuntu and 2GiB RAM.  Unless you're doing somethign specificcally memory intensive (usually gaming), beyond a certain level, CPU figures don't actually mean a heck of a lot in the real world IMHO, it's not often you'll see your CPU max out if you're just doing day to day stuff so why bother upgrading?  OK so Unzipping a big file or applying a complex effect in Gimp will go a little quicker, but loading firefox, watchign movies, etc etc you won't notice a worthwhile difference. Linux allows you the luxury of long lived hardware, instead of forcing upgrades with continual bloat like Winblows has a habit of doing.

Edit: of course, if you can get that CPU for cheap then ethere's no reason why not to upgrade ;)

---

### Post by colecampbell666 on 2008-01-26
My HDD used to report in as 160 Gb (it's 3 years old) And I do plan to use my PC for gaming. (HL2, Source  powered games) I can get both the CPU and the RAM for 50$ (each), so is it worth it?

---

### Post by louieb on 2008-01-26
Your is the situation where a separate /boot partition at the start of the drive is  a cure. Make it about 100-125 MB. GRUB error 18  is the only reason I would use a separate  /boot partition.

[Illustrated Dual Boot Site]("http://users.bigpond.net.au/hermanzone/")

Another cure may be a BIOS upgrade. check  the motherboards manufactures web site to see if one is available.

---

### Post by colecampbell666 on 2008-01-27
Which instructions on the aforementioned page should I use?

I'm saving up for a new PC, is it really worth getting a new CPU for this one, or should I save my 50$?

---

### Post by zvacet on 2008-01-27
[This](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

