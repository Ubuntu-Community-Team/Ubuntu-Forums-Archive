---
title: "address space collision"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by whoop on 2009-10-02
Anybody else noticing this after upgrade from jaunty to karmic (maybe this only happens on 32 bit machines)
I get this right after grub (grub 1, haven't upgraded this machine to grub2 yet) in xubuntu karmic 32bit:
[	0.359961] pci 0000:02:01.0: BAR 6: address space collision on of device [0x fbf00000-0xfbf1ffff] 

I am not the only one: [https://bugs.launchpad.net/ubuntu/+bug/424142](https://bugs.launchpad.net/ubuntu/+bug/424142)
But it doesn't seem like allot of people are experiencing this.

---

### Post by Peter09 on 2009-10-02
Yes - I've seen this error message as well.

---

### Post by FuturePilot on 2009-10-02
I get the same message.

---

### Post by whoop on 2009-10-02
Getting this on 64bit as well ?

---

### Post by FuturePilot on 2009-10-02
I had Karmic 64bit on another computer and I didn't see this message, but I'm guessing that's because it's something hardware specific. I can't test it on this one because it's not 64bit capable.

---

### Post by Hideaki on 2009-10-02
I get a very similar message.

---

### Post by mc4man on 2009-10-02
see it on a machine with ide hdd(s), don't see on machine with sata hdd(s).
(the sata machine gets the usb messages instead.

Doesn't seem to affect anything (that I've noticed

---

### Post by Hairy_Palms on 2009-10-02
i see it on my system with only sata HDD but its optical drive is IDE so maybe IDE devices are the common factor, but it doesnt seem to affect anything here either.

---

### Post by daetsy on 2009-10-02
I also see it. All my drives are SATA.

---

### Post by Hairy_Palms on 2009-10-03
> I also see it. All my drives are SATA.
there goes my theory :(

---

### Post by ljrmorgan on 2009-10-03
I also have this on an AMD64 system. My HD is SATA, DVD drives are IDE and I also have an external USB Hard Drive plugged in. I've got a wireless card, TV Tuner and sound card (all PCI).

---

### Post by froggyswamp on 2009-10-03
Here's the bug report:

[https://bugs.launchpad.net/ubuntu/+bug/424142](https://bugs.launchpad.net/ubuntu/+bug/424142)

I think if more people confirm it then the Ubuntu devs will be more willing to fix it sooner.

---

### Post by pburdick on 2009-10-03
I am experiencing the bug too on my Compaq 6715b. It's a bug with the way the kernel 2.6.31 handles PCI resources. Linus Torvalds describes the problem [[COLOR="Navy"]here[/COLOR]]("http://patchwork.kernel.org/patch/39988/"). There appears to be a fix in the works, but not for kernel 2.6.31.

---

### Post by addeboy on 2009-10-03
Also it happens to me, on Ubuntu 9.10 beta amd64. I think that's the reason why one of my hdd's attached to a PCI-SATA card disappears (it remains mounted, but I get an input/output error when I try a ls on it's mount point).

---

### Post by 4partee on 2009-10-06
I have two fails:

GA-MA785GM-US2H (rev. 1.0) desktop motherboard and,

MSI Wind U100 netbook.

---

### Post by brucealdridge on 2009-10-12
i was having this issue, unable to boot karmic beta (64bit) it gave the error, then hung after 'Checking battery state' 

machine has onboard vga and a pci-e vga card.
turned off the onboard vga in bios (options weren't straight forward, it was vga mode 'uma' (i think) or 'disabled', booted no problems

-bruce

---

### Post by 4partee on 2009-10-17
> **brucealdridge said:**
> i was having this issue, unable to boot karmic beta (64bit) it gave the error, then hung after 'Checking battery state' 

machine has onboard vga and a pci-e vga card.
turned off the onboard vga in bios (options weren't straight forward, it was vga mode 'uma' (i think) or 'disabled', booted no problems

-bruce

Thanks bruce;

I need the on-board video.

I did change the UMA frame buffer size from auto to 512m and still got the address space collision message.  The install did start this time, however, the partitioner step did not recognize both HDDs. 

I'll just leave it there for now.

John

---

