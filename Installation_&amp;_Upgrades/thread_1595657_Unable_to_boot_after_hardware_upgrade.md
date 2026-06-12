---
title: "Unable to boot after hardware upgrade"
date: 2010-10-13
forum: Installation &amp; Upgrades
---

### Post by FelixII on 2010-10-13
Hi,

yesterday I upgraded my hardware, my specs are as following:

AMD Phenom II X4 965 (new)
Asrock K10N78D Mainboard (new)
1 TB Harddrive (Western Digital WD10EARS) (new)
Palit Geforce 460 GTX
3 GB DDR2-800 RAM

First I installed Windows 7 which worked without any problems. After that I wanted to install Ubuntu 10.10. (32 bit) The installation worked fine and the first boot also worked without any problems. Since then I get strange errors nearly everytime I try to boot up. I'm posting a "screenshot" as an attachment which shows the bottom end of the output before the system stops to work (Alt+Print+B is still working). I also get the same error when trying to boot up from a Live USB-Stick. It's quite random, around 25% of my tries are successful and the system boots up normally.

Things I already tried:

- Testing my RAM (no errors)
- Booting with just one RAM block (same error, also tried a different one)
- Installing 10.04/BIOS Reset/Installing from CD  (same problem)

So what do you think? A hardware defect? Then I wonder why Win7 works fine...

I would like to post a complete boot log, how can I do that?

Any help is welcome :)

Felix

---

### Post by FelixII on 2010-10-14
Anyone?

Thanks in advance.

---

### Post by mister_p_1998 on 2010-10-14
Which version of Ubuntu 32? are you installing the AMD or Intel version?
Steve

---

### Post by FelixII on 2010-10-14
Hi,

my image is called "ubuntu-10.10-desktop-i386.iso".

---

### Post by mister_p_1998 on 2010-10-14
I think you need to install the AMD version:

[http://releases.ubuntu.com/lucid/ubuntu-10.04.1-desktop-amd64.iso](http://releases.ubuntu.com/lucid/ubuntu-10.04.1-desktop-amd64.iso)

Steve

---

### Post by FelixII on 2010-10-14
I also tried the AMD version a few hours ago, same error. I gave it up and built my old components back in. I will return the hardware to the vendor tomorrow and go for a Intel CPU. 

Greetings and thanks for your help :-)

Felix

---

### Post by cascade9 on 2010-10-14
Bit late now, as you've put the old stuf back in, but I would have tried the 'noapic' or 'acip=off' options. 

I'd guess that its a chipset/motherboard issue. nvidia, nice video cards, some of the chipsets are dodgy. You could try a AMD 770/790X/790FX/870/890FX chipset motherbaord, I havent heard on any major issues with them.

---

### Post by FelixII on 2010-10-14
I also tried acpi=off because it solved some problems with my old mainboard but it didn't have any effect.

Since I can't determine if the mainboard or the CPU is causing the problem, I'll have to return both.

---

