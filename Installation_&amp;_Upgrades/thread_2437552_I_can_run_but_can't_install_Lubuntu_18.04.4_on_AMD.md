---
title: "I can run but can't install Lubuntu 18.04.4 on AMD Athlon MP"
date: 2020-02-25
forum: Installation &amp; Upgrades
---

### Post by b-ric-z on 2020-02-25
Hi there!

I'm trying to revive some old hardware with Lubuntu 18.04.4 32 bits, but I've hit a problem: after initiating the installation and entering the user information, the installation crashes. From /var/log/syslog:
```
Feb 25 15:50:27 lubuntu ubiquity[16187]: debconffilter_done: ubi-usersetup (current: ubi-usersetup)
Feb 25 15:50:27 lubuntu ubiquity[16187]: Step_before = stepUserInfo
Feb 25 15:50:29 lubuntu kernel: [ 1485.292845] traps: ubiquity[16187] trap invalid opcode ip:a83bc2d7 sp:bfab3fc0 error:0 in libjavascriptcoregtk-4.0.so.18.14.8[a7b78000+b5c000]
```

```
$ uname -a
Linux lubuntu 5.3.0-28-generic #30~18.04.1-Ubuntu SMP Fri Jan 17 06:11:07 UTC 2020 i686 athlon i686 GNU/Linux
```

```
$ lscpu
Arquitetura:                i686
Modo(s) operacional da CPU: 32-bit
Ordem dos bytes:            Little Endian
CPU(s):                     1
Lista de CPU(s) on-line:    0
Thread(s) per núcleo:       1
Núcleo(s) por soquete:      1
Soquete(s):                 1
ID de fornecedor:           AuthenticAMD
Família da CPU:             6
Modelo:                     8
Nome do modelo:             AMD Athlon(tm) MP
Step:                       1
CPU MHz:                    1000.028
BogoMIPS:                   2000.05
cache de L1d:               64K
cache de L1i:               64K
cache de L2:                256K
Opções:                     fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse syscall mp mmxext 3dnowext 3dnow cpuid 3dnowprefetch vmmcall
```

Of course, a program should check during runtime for supported instruction sets instead of just crashing, and if a instruction set required by the OS is missing in the processor, I would expect that the installation program should alert the user about it. In this case, I guess the invalid opcode is/should not be an OS requirement (specially because I can run Lubuntu from the installation disk), but is used (without checks) by the libjavascriptcoregtk-4.0 library.

Is there any way around this problem? May I use an older version of Lubuntu?

Any help is appreciated. Thanks!

---

### Post by mörgæs on 2020-02-25
Hi, welcome to the fora.

Your CPU has the SSE instruction set but not SSE2. This didn't use to be a problem for Lubuntu itself, only for some browsers, but now it seems to be.

An option is trying [Debian]("https://ubuntuforums.org/showthread.php?t=2130640&page=22&p=13902890&viewfull=1#post13902890"). It [should work]("https://www.debian.org/releases/stable/i386/release-notes/ch-information.en.html#webkit2gtk-on-non-sse2") but I haven't tried myself so can't promise anything.

---

### Post by Impavidus on 2020-02-25
If it's only a problem for the installer and not for Lubuntu itself (until now it appears so, as the error concerns libjavascriptcoregtk-4.0.so, which sounds like something typically used in webbrowsers, but may be used for some nice effects in the GUI installer), you could try the alternate 32-bit installer for Lubuntu 18.04, available from the Lubuntu site ([https://lubuntu.me/downloads/](https://lubuntu.me/downloads/)), or the minimal network installer ([http://cdimage.ubuntu.com/netboot/18.04/](http://cdimage.ubuntu.com/netboot/18.04/)).

---

### Post by b-ric-z on 2020-03-03
Thanks, mörgæs & Impavidus!

I used the alternate 32-bit installer and everything worked just fine! :)

---

### Post by mörgæs on 2020-03-04
Good, please mark the thread solved.

---

### Post by b-ric-z on 2020-03-06
> **mörgæs said:**
> Good, please mark the thread solved.
Done!

BTW, on your thread [Old hardware brought back to life]("https://ubuntuforums.org/showthread.php?t=2130640"), it says:

[B]
[TABLE="class: cms_table_grid, width: 1000, align: left"]
[TR]
[TD]**Hardware**[/TD]
[TD]**Age (approx.)**[/TD]
[TD]**Occurrence**[/TD]
[TD]**Examples of applications which don't work**[/TD]
[TD]**Remarks**[/TD]
[/TR]
[TR]
[TD]32 bit without SSE2[/TD]
[TD]2001-2[/TD]
[TD]Rare[/TD]
[TD]Firefox, Chromium, Chrome, Skype[/TD]
[TD][/TD]
[/TR]
[/TABLE]

[/B]
Even though my system has no SSE2 and is 32 bits, Firefox runs fine (so far at least)...

---

### Post by mörgæs on 2020-03-07
Thanks for pointing this out. Yes, Mozilla should have a tip of the hat for providing Firefox Extended Support. 

I have edited post 1 and 3. Feel free to post again in that thread if anything else is outdated.

---

