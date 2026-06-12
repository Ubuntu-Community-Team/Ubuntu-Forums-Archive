---
title: "Installation problem on Compaq Laptop (Turon X2): Ubunut AMD64 desktop"
date: 2007-05-09
forum: Installation &amp; Upgrades
---

### Post by vozhyk on 2007-05-09
Hi, everyone,

I have a problem to install Ubuntu 7.04 (AMD64) on my new Compaq laptop (F504)

The installation halt just after "*Configuring network interfaces.... [OK]"

Any ideas?

Many thanks,

v.

SPECIFICATION:

# AMD Turion 64 X2 Dual Core TL-50
# 1600 MHz HyperTransport
# 512 KB Cache
# 1 GB RAM
# 80 GB Hard Drive
# 128 MB nVidia GeForce Go 6150 Graphics

---

### Post by dan171717 on 2007-05-09
is it crashing during live cd boot or install or after install?? if it is during istall then go into system/adminstaton then network and disable the networkadaptor then try

---

### Post by vozhyk on 2007-05-09
> **dan171717 said:**
> is it crashing during live cd boot or install or after install??

I guess it's crashing during live cd boot.
(If I'm not mistaken, Ubuntu Desktop loaded LiveCD first and  after need to click for installation).

> **dan171717 said:**
>  if it is during istall then go into system/adminstaton then network and disable the networkadaptor then try

What do you mean by "system/administration"? Bios?

Many thanks,
v.

---

### Post by vozhyk on 2007-05-09
> **Thumper723 said:**
> I had the same issue with a Presario V6310US

On the boot screen, press F6 "boot options.

Type in at the end of the current script pci=noacpi

It is some sort of power management issue. That is how a much more educated user explained it to me..

It installed fine, I just have some bugs.. Sometimes when I log in, its OK. Other times, I get a cursor and blank desktop, no icons.

It worked for me :)

v.

---

### Post by jcaveman on 2007-05-10
My HP DV6119US is functionally identical to your Presario.  The HP/Compaq notebooks have a broken bios and you need to load the liveCD with the following boot parameters:

noapic irqpoll noirqdebug

The noapic bypasses the problem the notebook has with apic that causes your lockup.  Unfortunately, noapic also partially disables the appropriate handling of IRQs, so you need to add in the irqpoll noirqdebug parameters to get USB working correctly.

---

### Post by vozhyk on 2007-05-11
> **jcaveman said:**
> My HP DV6119US is functionally identical to your Presario.  The HP/Compaq notebooks have a broken bios and you need to load the liveCD with the following boot parameters:

noapic irqpoll noirqdebug

The noapic bypasses the problem the notebook has with apic that causes your lockup.  Unfortunately, noapic also partially disables the appropriate handling of IRQs, so you need to add in the irqpoll noirqdebug parameters to get USB working correctly.

Many thanks.
Installing with the parameters really helped.

v.

---

### Post by zipperback on 2007-05-14
Did you get your laptop fully functional now with your install?

I was about to buy the same laptop you are using, but I wanted to make sure it all works before I buy it.

Does your sound, usb, etc all work correctly?

Thanks.

---

### Post by vozhyk on 2007-05-15
> **zipperback said:**
> Did you get your laptop fully functional now with your install?

I was about to buy the same laptop you are using, but I wanted to make sure it all works before I buy it.

Does your sound, usb, etc all work correctly?

Thanks.

My answer would be Almost.

I had to reinstall with all parameters ("noapic irqpoll noirqdebug"),
as it was quicker to fix sound and usb.
It works fine now.
Automatix installed Nvidia drivers without problems too.

The only issues left are with  with integrated mic and wireless card.

v.

---

### Post by kaleido on 2007-05-20
For people using the x64 version of Ubuntu 7.04 on this type of laptops, can you all check something for me?
Please run [FONT="Arial Black"]top[/FONT], and check how much % of the cpu is id (idle), and how much is in hi (hardware interrupt)?

When I tried the 64 bit version, and used the above mentioned boot flags, my computer was spending like 60-90% of the cpu on hi (hardware interrupts).  Even when I'm not running any apps.

With the 32 bit Ubuntu, my cpu is now 90% idle in top most of the time.
(Note, after installing the binary Nvidia driver, I don't need to pass any boot flags, and everything works fine.)

P.S. I have Compaq v6000z.

---

### Post by RagingOcelot on 2007-09-09
I'd love to figure out how to get rid of the hardware interrupt issue I'm also experiencing.  It shows up on my 64-bit Feisty install as a constantly very high (90-100%) percentage all the time.  Sure doesn't seem like it slows the computer down much, though.

---

### Post by kaleido on 2007-09-12
> **jcaveman said:**
> My HP DV6119US is functionally identical to your Presario.  The HP/Compaq notebooks have a broken bios and you need to load the liveCD with the following boot parameters:

noapic irqpoll noirqdebug

The noapic bypasses the problem the notebook has with apic that causes your lockup.  Unfortunately, noapic also partially disables the appropriate handling of IRQs, so you need to add in the irqpoll noirqdebug parameters to get USB working correctly.

I don't buy the broken bios view.
I tried Fedora and Sabayon (a version of Gentoo), both run fine without passing any boot parameters.

I think this Compaq V6000z laptop bios is perfectly fine, it is Ubuntu that is broken.

---

### Post by sanfin on 2007-10-05
[FONT="Verdana"]Hi everyone!
I don't know if it's my first time to post in this forum anyway I must say THANK YOU to vozhyk that with his advices help me a lot to install Ubuntu on my HP TX1250!
I've been trying several times to install it and always crash down or I wasn't able to boot it!
Happy open source software to everyone!
UBUNTU is better! ;)
/paolo[/FONT]

---

