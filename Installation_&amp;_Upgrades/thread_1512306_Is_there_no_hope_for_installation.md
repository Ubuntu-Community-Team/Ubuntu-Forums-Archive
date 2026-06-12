---
title: "Is there no hope for installation?"
date: 2010-06-18
forum: Installation &amp; Upgrades
---

### Post by mp3c on 2010-06-18
I have an old Dell Latitude Laptop, and was willing to install Xubuntu.

The ISO I used was xubuntu-10.04-alternate-i386.iso

I've tried some methods and failed:

[LIST][INDENT][/INDENT]
[*]Wubi     (requires more memory than I have.) 


[*]unetbootin     [INDENT][/INDENT](will not install bootloader)


[*]CD     [INDENT][/INDENT](All my CDs are over x24, and my drive only takes those)


[*]USB     [INDENT][/INDENT](Used Plop Boot Mgr. and I hit Install Xubuntu - Freezes for hours. I used USB 1.1)
[/LIST]

I wasn't able to use a floppy drive; I lost it sometime ago.

Any help,
mp3c

---

### Post by wilee-nilee on 2010-06-18
What is the computer model exactly and the specs.

---

### Post by fjordsurfer on 2010-06-18
what's the problem?

If the Xubuntu Live-CD doesn't boot, just take the Ubuntu Live-CD. After installing in a terminal type:

sudo aptitude update && sudo aptitude install xubuntu-desktop

This isn't elegant, but it works.

fjordsurfer

---

### Post by wilee-nilee on 2010-06-18
> **fjordsurfer said:**
> what's the problem?

If the Xubuntu Live-CD doesn't boot, just take the Ubuntu Live-CD. After installing in a terminal type:

sudo aptitude update && sudo aptitude install xubuntu-desktop

This isn't elegant, but it works.

fjordsurfer

It's not the live cd, it's the alternative and a wubi install.

---

### Post by mp3c on 2010-06-18
> **wilee-nilee said:**
> What is the computer model exactly and the specs.
Thanks Wilee, it's a 
[LIST]
[*]Dell Latitude C600
[*]Mobile Pentium (R) III-850/700 Mhz
[*]SYS Memory 128
[*]24x CD-ROM (Dell TM LBL P/N: 5044D AD2
[*]Video CTRL - ATI M3
[*]Audio CTRL - ESS Maestro 3

---

### Post by mp3c on 2010-06-18
> **wilee-nilee said:**
> What is the computer model exactly and the specs.


Thanks Wilee, it's a 
[LIST]
[*]Dell Latitude C600
[*]Mobile Pentium (R) III-850/700 Mhz
[*]SYS Memory 128
[*]24x CD-ROM (Dell TM LBL P/N: 5044D AD2
[*]Video CTRL - ATI M3
[*]Audio CTRL - ESS Maestro 3
[*]Jolicloud in MBR (removed actual OS)
[*]Plop Boot Manager in MBR
[*]Windows XP Professional SP2 in MBR
[/LIST]

---

### Post by stumay on 2010-06-18
> **mp3c said:**
> Thanks Wilee, it's a 
[LIST]
[*]Dell Latitude C600
[*]Mobile Pentium (R) III-850/700 Mhz
[*]SYS Memory 128
[*]24x CD-ROM (Dell TM LBL P/N: 5044D AD2
[*]Video CTRL - ATI M3
[*]Audio CTRL - ESS Maestro 3
[*]Jolicloud in MBR (removed actual OS)
[*]Plop Boot Manager in MBR
[*]Windows XP Professional SP2 in MBR
[/LIST]


INstall Windows 98 Millenimum

For Ubuntu I believe it said you need Minimum of 256MEGS OF RAM  anything below that is a no go.  Personally I wouldn't even think of installing an OS without at least 1GiG of Ram.  Sell the Laptop after installing Windows 98, that's what the other guys would say, but didn't because they're nice.  I telling you this to save more embarrassment.

Get a Netbook for 299.00

---

### Post by mp3c on 2010-06-18
> **stumay said:**
> INstall Windows 98 Millenimum

For Ubuntu I believe it said you need Minimum of 256MEGS OF RAM  anything below that is a no go.  Personally I wouldn't even think of installing an OS without at least 1GiG of Ram.  Sell the Laptop after installing Windows 98, that's what the other guys would say, but didn't because they're nice.  I telling you this to save more embarrassment.

Get a Netbook for 299.00
LOL...
Nothin' serious... I was just curios if I could breathe new lide again...

---

### Post by wilee-nilee on 2010-06-18
> **mp3c said:**
> Thanks Wilee, it's a 
[LIST]
[*]Dell Latitude C600
[*]Mobile Pentium (R) III-850/700 Mhz
[*]SYS Memory 128
[*]24x CD-ROM (Dell TM LBL P/N: 5044D AD2
[*]Video CTRL - ATI M3
[*]Audio CTRL - ESS Maestro 3
[*]Jolicloud in MBR (removed actual OS)
[*]Plop Boot Manager in MBR
[*]Windows XP Professional SP2 in MBR
[/LIST]

There are small distro that would run great with that setup puppuylucid would, damn small linux and others.

---

### Post by mp3c on 2010-07-16
> **wilee-nilee said:**
> There are small distro that would run great with that setup puppuylucid would, damn small linux and others.

Thanks for reffering, works great!

---

### Post by Alver on 2010-07-16
> **stumay said:**
> INstall Windows 98 Millenimum

For Ubuntu I believe it said you need Minimum of 256MEGS OF RAM  anything below that is a no go.  Personally I wouldn't even think of installing an OS without at least 1GiG of Ram.  Sell the Laptop after installing Windows 98, that's what the other guys would say, but didn't because they're nice.  I telling you this to save more embarrassment.

Get a Netbook for 299.00
Some months ago I installed Xubuntu 9.10 on an ageiing Toshiba Satellite 2410-303 with 512 MB ram it runs very well. I also have an older Medion desktop with 512 MB ram where I installed Ubuntu 9.10 in dual boot with W xp. All functions well there too. A couple of weeks ago I upgraded my Ubuntu 9.10 to 10.04 without the slighthest hick-up. 512 MB ram is certainly minimal but you can still get a good working system.

---

### Post by alphasoup on 2010-10-30
The C600 is a great laptop, get at least 512MB of memory and enjoy.
A lot of C600 were used years ago so inexpensive "refurbished" memory stick may be available to fill it up.

I am typing this from an even older latitude CP 500-650 MHz with 512MB now running Ubuntu 10.4.1 kernel 2.6.32-25-386.
You can even watch videos on utube if you can accept a couple fps rate, the audio is great (once you install firmware)...
Keep using a good laptop as long as it works since won't get much money by selling it, this old Dell has worked with RH 6.0 - through 8.0, Mandriva 2005-2007 and finally Ubuntu from 8.4 - 10.4.1 and each time
it seems to have improved from new software releases:
Chrome, firefox, thunderbird, seamonkey and open office do very well.

---

