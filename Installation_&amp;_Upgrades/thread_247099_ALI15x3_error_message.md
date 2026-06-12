---
title: "ALI15x3 error message"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by Tantalus90 on 2006-08-30
It zings past at speed and I seem unable to pause it but it seems to show a message that the bios is out of date, upgrade the bios or run 

force_addr=0xaddr

not keen on updating bios as it has been working fine (?) for years MB is an asus A7A266 (ddr) with ali chips and an Athlon 1333.

How and when do i run this command ? 

Is this really an ali bios problem or is it a problem with the kernel ?

Thanks in advance 
Tant

---

### Post by Tantalus90 on 2006-08-30
bump

anyone ?

Tant

---

### Post by Tantalus90 on 2006-08-31
sigh

---

### Post by Tantalus90 on 2006-09-06
awwwwww, I really would like an answer too 

Tant

---

### Post by seraph47 on 2006-11-04
ive gotten this problem after i just did an install of 6.10

---

### Post by seraph47 on 2006-11-04
heres the full error message:

```
Decompressing Linux...done.
Booting the kernel.
[   89.170377] ali15x3_smbus 0000:00:1e.1: ALI15X3_smb region uninitialized - upgrade BIOS or use force_addr=0xaddr
[   89.170638] ali15x3_smbus 0000:00:1e.1: ALI5X3 not detected, module not inserted.
```

---

### Post by caterminator on 2006-12-19
I'm having that message as well. Something like update Bios or try force_addr=oxaddr.
The difference is that it happens to me before I can even install linux. When I first try the installation (Ubuntu 6.10) a couple of errors appear. Than the screen goes blank before I can even read it all. And thats it for my install :(
I have an Fujitsu Siemens Amilo A 7600 Laptop and already run the latest BIOS 1.1

---

### Post by PsyDev on 2006-12-21
I have the exact same problem. I have a laptop (Toshiba Satellite 1805-S273) and when i tried installing Ubuntu 6.10, I got this error message. Ubuntu install stalled and I had to reboot.

I did the CD integrity and it was ok.

In the safemode install, I got the same error message.


In both times I saw a beige background while the cd continued to load. Then the screen went back to a black screen with no blinking cursor. Then about 2 or 3 minutes later, the cd-rom stops spinning and I am left with a blank, black screen where nothing seems to be happening.

---

### Post by Kevanx on 2007-03-01
I'm having the exact same issue with a Toshiba satellite 1800 model as well - trying to install for the first time.

It looks like this problem is specific to the 6.10 release. Can someone confirm? If so, could we submit a bug report for implementation in feisty fawn? Sorry if this post makes me look ignorant - I'm New .

---

### Post by cborga1985 on 2007-04-02
Anybody have an answer to this? The message displays but the computer continues to boot after a few seconds. Kind of annoying though because it slows down the booting process.

---

### Post by cborga1985 on 2007-04-04
hello?

---

### Post by in_flu_ence on 2007-04-06
I have a similar problem. It runs ok in my system (64bit Kubuntu 6.10). Just that there are hang-ups once in a while if I didn't unplug my USB drive and I didn't switch off my computer by switching off the main power. Pressing the shutdown button in my desktop doesn't seem to cut off the power completely and seem to cause the hang up.

Any similar experience?

---

### Post by Kevanx on 2007-05-06
I only had the problem when running off the LiveCD. Installation solved it, so I'm afraid I can't help you.

---

### Post by in_flu_ence on 2007-05-07
feisty seems to fix my problem too as of now since I don't see those random crashing when my USB drive is inserted at boot up.

---

### Post by cborga1985 on 2007-05-20
I still see the message in Feisty but it doesn't seem to have any effect.

---

### Post by RavanH on 2007-09-18
Looks like an 'old' issue but for me it is still there... Even in the latest Gutsy development :(

Really nobody with any ideas?

--ravan

---

### Post by k0elw on 2007-10-15
> **PsyDev said:**
> I have the exact same problem. I have a laptop (Toshiba Satellite 1805-S273) and when i tried installing Ubuntu 6.10, I got this error message. Ubuntu install stalled and I had to reboot.

I did the CD integrity and it was ok.

In the safemode install, I got the same error message.


In both times I saw a beige background while the cd continued to load. Then the screen went back to a black screen with no blinking cursor. Then about 2 or 3 minutes later, the cd-rom stops spinning and I am left with a blank, black screen where nothing seems to be happening.

Similar story here with a Compaq Presario 1675, won't install, won't boot live CD.
Ubuntu 6.04 & 7.04.  CD integrity checks ok.

---

