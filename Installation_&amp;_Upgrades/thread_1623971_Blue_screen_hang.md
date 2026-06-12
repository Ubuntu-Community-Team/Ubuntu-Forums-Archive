---
title: "Blue screen hang"
date: 2010-11-17
forum: Installation &amp; Upgrades
---

### Post by xirochanh on 2010-11-17
I'm installing Ubuntu server 10 on my PC and got this problem.
After choosing language, network configuration, naming host, select time zone, then the blue screen just hang there.
It seems like a box to indicate that it's detecting hard drive, then disappears, maybe it can not detect hard drive?? if yes what should I do?

my PC spec is:
- Main: ASUS P5Q-PRO
- VGA: ASUS EAH3450
- CPU: Intel Core 2 Quad Q9550 2.83 Ghz
- HDD: Sata

I tried with both x86 & 64 bit version, also tried to unplug USB mouse, still doesn't work
Please help,
thank you

---

### Post by sikander3786 on 2010-11-17
Hi and Welcome to the forums :)

Did you check the disk for defects? Also check the integrity of image used to burn the disc.

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by xirochanh on 2010-11-17
Yes, I did, they're all ok.

---

### Post by xirochanh on 2010-11-18
Exactly, it hang at step 'Detect disks'

---

### Post by sikander3786 on 2010-11-18
If there are more than 1 Sata controllers on the board, move your HDD to the other Sata contoller (different coloured group of sata ports).

If that doesn't help, check in your Bios for Raid settings and disable them if present. Or from Bios, set your HDD mode to ahci compatible.

---

### Post by xirochanh on 2010-12-21
> **sikander3786 said:**
> If there are more than 1 Sata controllers on the board, move your HDD to the other Sata contoller (different coloured group of sata ports).

If that doesn't help, check in your Bios for Raid settings and disable them if present. Or from Bios, set your HDD mode to ahci compatible.

I do as your suggestion but installation sill couldn't detect the hdd.
I also follow the solution for P5Q-E, which tell me to **"Configure SATA as ..**." to **[AHCI], ** change USB setting "**BIOS EHCI Hand-Off**" to **[Disabled]****, [B]& enable **[/B]**ACPI 2.0**[B].

Again, my mainboard is ASUS P5Q-PRO. any suggestion, please
[/B]

---

### Post by sikander3786 on 2010-12-22
> **xirochanh said:**
> I do as your suggestion but installation sill couldn't detect the hdd.
I also follow the solution for P5Q-E, which tell me to **"Configure SATA as ..**." to **[AHCI], ** change USB setting "**BIOS EHCI Hand-Off**" to **[Disabled]****, [B]& enable **[/B]**ACPI 2.0**[B].

Again, my mainboard is ASUS P5Q-PRO. any suggestion, please
[/B]
From a boot Live CD/USB's Terminal, post the output of this command.

```
sudo fdisk -lu
```

---

### Post by theasprint on 2010-12-22
Hi,

Just a wild guess:

Do you want to try the Alternate .iso file?
The Alternate provides more support for low-end graphics and unsupported PCs.

Perhaps your laptop is not really compatible? I know there's a laptop incompatibility list but I have not checked there. 

*I don't know you're using a laptop or a desktop. Sorry.

---

### Post by xirochanh on 2010-12-22
I haven't tried the alternate distribution or the live CD, gonna do it.
I just learned from some suggestion that I should disable Marvel IDE. I did, then no more CD-Rom, I burnt the iso file to usb pen drive, then tried, and got black screen after hitting enter to choose option "install ubuntu". I tried removing quiet splash from boot option, nothing better happened.

I'm using PC, not laptop, spec as in the first post

Thanks

---

### Post by Nuvenus Chovendus on 2010-12-22
Wonder, I managed to solve the problem here.

You guys are great
Hugs :D
[Nuvenus Chovendus]("http://blogseopark.blogspot.com/2010/12/nuvenus-chovendus-desafio-seo.html")

Happy happy happy :guitar:

---

### Post by xirochanh on 2010-12-22
poor me, I might got problem with hardware.

Firstly, choose option "run ubuntu from this USB", black screen with white information lines running for a while, then freeze.
I reload default settings for the BIOS, try again, and can pass the black screen & white lines, but freeze that the pink screen with UBUNTU at the center.

Even the live USB couldn't I enjoy, how can I install ubuntu to hard disk.

Don't know what to do, next, replace the PC??

---

### Post by xirochanh on 2010-12-22
on the UBUNTU loading screen, I hit Ctrl-Alt-F1 to see what happen behind the scene, what I see is the following lines repeated:
....................
Buffer I/O error on device fd0, logical block 0
end_request: I/O error, dev fd0, sector 0
...................
surely, I don't have floppy disk, what's next?

---

### Post by xirochanh on 2010-12-22
> **sikander3786 said:**
> From a boot Live CD/USB's Terminal, post the output of this command.

```
sudo fdisk -lu
```

The PC I'm installing ubuntu has no internet connection, so I can not show you the capture of output, but basically it recognize my hard disk, partitions, usb:

/dev/sda1
/dev/sda2
/dev/sdb
/dev/sdb1

as I mentioned previously, I got some error with the fd0 recognize, now I disabled floppy in BIOS, no such problem happens, I can go directly to ubuntu on live USB, and I believe that the installation runs well for desktop version. However, I'd like to install the server edition, and got the blue freezing screen like I said

---

### Post by sikander3786 on 2010-12-22
Ok. Try the F6 boot options. There are 6 of them and you might need to try all of them, one-by-one. I think nomodeset of acpi=off or noapic might work for you.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

---

### Post by xirochanh on 2010-12-22
> **sikander3786 said:**
> Ok. Try the F6 boot options. There are 6 of them and you might need to try all of them, one-by-one. I think nomodeset of acpi=off or noapic might work for you.

[https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options](https://help.ubuntu.com/community/LiveCDBootOptions#Main%20Page%20Options)

None of these options can help. The thing making me mad is: there's just a black blue screen with no message, at least some exception or information must be shown to give me some clue:frown:

---

### Post by sikander3786 on 2010-12-23
> **xirochanh said:**
> None of these options can help. The thing making me mad is: there's just a black blue screen with no message, at least some exception or information must be shown to give me some clue:frown:
Feeling stumped at this one...

Are you sure the Hardware is just ok? I mean it might be a faulty RAM or some other thing causing the problems. I am saying that because I've never seen the error with Ubuntu which is appearing at your PC. Might be worth to run a memtest from Ubuntu boot menu.

---

### Post by xirochanh on 2010-12-28
> **sikander3786 said:**
> Feeling stumped at this one...

Are you sure the Hardware is just ok? I mean it might be a faulty RAM or some other thing causing the problems. I am saying that because I've never seen the error with Ubuntu which is appearing at your PC. Might be worth to run a memtest from Ubuntu boot menu.

I gave up server edition, installed desktop edition just smoothly. So, can say that hardware must be ok.

Thanks a lot for your help

---

