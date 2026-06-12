---
title: "Installation Problems"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by djzalzer on 2008-07-30
Hello, Ubuntu community.

So I just bought a new hard disk and I wanted to dual boot Ubuntu and... another operating system on it (Windows is on a separate disk).  Here's my problem.

Disk 1 has windows on it, boots fine.  I can access my Ubuntu partition via this disk.  My ubuntu partition is on disk 2, half of it is formatted with ntsc.

Disk 2 has nothing on it (except a partition for ubuntu).  When I boot with Ubuntu disk in the drive and this disk in the drive, nothing happens (my nvidia boot manager keeps telling me to check my cords :[)

I CAN run a live disk, but only if Disk 1 is connected (I had to use the boot menu adder thing on the ubuntu disk when it's opened with windows)

I only can connect 2 IDE devices at one time.  (DVD drive and 1 or 2, or 1 and 2.)

So how can I install Ubuntu?

PS "Get SATA" or "Get new mobo" is not an option, as my funds are rather low and will be for about a month)

EDIT

Here are my specs:
AMD Athlon 64 x2 3800+ (iirc)
2gb ram
1-40gig hard disk
1-320gig hard disk (for ubuntu :])
DVD drive, but just there to fill the hole (who needs CDs anyway?).  DVD drive plugged in = one hard disk has to come out.

---

### Post by kspncr on 2008-07-30
Are you sure that when you try to run the live cd your DVD drive is first in the boot order? I think if you keep taking out and replacing hardware like you are, the BIOS might change the boot order by itself (I'm fairly certain this has happened to me once). Check your boot order with your DVD drive and hard drive 2 hooked up.

---

### Post by djzalzer on 2008-07-30
Hi, & thanks for your speedy reply.

The problem is, the BIOS acts like I have plugged nothing at all into the ide ports!  It sees no dvd drive and no hard disk.

Both of the jumpers are set to 'cable select.'

The boot order remains unchanged.

---

### Post by overdrank on 2008-07-30
> **djzalzer said:**
> Hi, & thanks for your speedy reply.

The problem is, the BIOS acts like I have plugged nothing at all into the ide ports!  It sees no dvd drive and no hard disk.

Both of the jumpers are set to 'cable select.'

The boot order remains unchanged.

Hi and I am a little confused. ( believe me that is not hard :) ) But you are saying you can only hook one hard drive and the DVD drive at a time. Does you mother board have only one IDE channel? I have never had hard drives work with cable select. I have always set them accordingly as master and slave.

---

### Post by kspncr on 2008-07-30
> **overdrank said:**
> I have never had hard drives work with cable select. I have always set them accordingly as master and slave.

Yeah, that's a good point. Generally, cable select is good for a second hard drive for storage purposes. Try setting the jumper to master and see if that helps.

---

### Post by djzalzer on 2008-07-30
Yep, with master and slave everything works fine.  Whenever I switch OSes, I have to mess with a jumper, but it's a small sacrifice for the pleasure of using this exceptional operating system! :]

---

### Post by kspncr on 2008-07-31
Pretty soon, I'm sure you'll find yourself booting Windows less and less...until, eventually...well, I don't have to say what comes next;)

And I'm sure having to swap hardware around every time helps kill motivation to boot Windows.

Glad everything works for you, have fun

---

