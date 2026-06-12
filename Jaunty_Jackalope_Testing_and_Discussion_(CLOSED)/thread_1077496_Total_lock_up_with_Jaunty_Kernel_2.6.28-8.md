---
title: "Total lock up with Jaunty Kernel 2.6.28-8"
date: 2009-02-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by jtappin on 2009-02-22
I've been having a problem on my "test-bed" box in that since the 2.6.28-8 kernel version, as soon as X starts, the system generally hangs up completely -- no keyboard or mouse, the only option is the reset button (occasionally the system does allow input but reboots after a few seconds).

The video card is: Nvidia GEForce FX 5200
The mouse is a USB Logitech trackman marble wheel (quite old and it's never been a problem before)
The keyboard is an HP PS/2 keyboard.
This is a 32-bit machine.

The problem occurs both with the nvidia binary drivers, and with the nv drivers.

There is no problem with 2.6.28-7 -- so I don't think it's a hardware problem.

On starting without X, there is a kernel panic as soon as I try to type anything:
```

PANIC: double fault, gdt at c180500 [255 bytes]
double fault, tss at c180b280
eip=c04ee6b6, esp = f6009fd8
eax=00000000, ebx=f600a128, ecx=00010002, edx=31ec744a
esi=f66aad34, edi=f66aad00

```
(the above is copied off the screen by hand).

Does anyone have any ideas about what the problem might be, or any actions to try before putting a bug in launchpad?


P.S. This may not be entirely an Ubuntu issue as with the current version of Arch Linux, I get a similar problem in X, but no problems on the console.

---

### Post by jpeddicord on 2009-02-22
Moved to Jaunty Jackalope Testing and Discussion.

---

### Post by jtappin on 2009-03-09
> **jtappin said:**
> 

P.S. This may not be entirely an Ubuntu issue as with the current version of Arch Linux, I get a similar problem in X, but no problems on the console.

Turns out the Arch problem was completely independent -- that was no input devices, due to hal not being started. 

Also this problem has persisted with several updates to 2.6.28-8, while 2.6.28-7 is just fine.

---

### Post by dBuster on 2009-03-09
Have you tried with all the boot options such as noapic and so forth?  I can't remember all of the options but I know when I was trying to get my new laptop going, I had all kinds of issues with kernel panics....  Got around them with the boot options until things calmed down with the kernel at that time.

---

### Post by jtappin on 2009-03-18
> **dBuster said:**
> Have you tried with all the boot options such as noapic and so forth?  I can't remember all of the options but I know when I was trying to get my new laptop going, I had all kinds of issues with kernel panics....  Got around them with the boot options until things calmed down with the kernel at that time.

I've tried a few likely ones (notably apci=off, since I saw that the ACPI loading was failing in the only working kernel 2.5.28-7) without any success.

BTW: a full list of possible boot options is at:
[http://www.kernel.org/pub/linux/kernel/people/gregkh/lkn/lkn_pdf/ch09.pdf]("http://www.kernel.org/pub/linux/kernel/people/gregkh/lkn/lkn_pdf/ch09.pdf") though I've no idea what most of them mean.

Interestingly the 16 Mar Xubuntu live-cd seems to work just fine, though no kernel since the -7 (we're up to -11) will work from HD.

---

### Post by Nullack on 2009-03-19
Upgrade to current Jaunty sauce being .11

---

### Post by jtappin on 2009-03-23
> **Nullack said:**
> Upgrade to current Jaunty sauce being .11
Still failing on HD -- One thing I need to try is a fresh install to the other partition set -- tried it the other day but ran into an unrelated problem.

---

### Post by treepleks on 2009-03-23
jtappin,

I have exactly the same problem. The machine freezes with a kernel panic, double fault. This happens since 2.6.28-8 and still happens on 2.6.28-11.

My hardware is different, I have a radeon 9800 PRO and uses the radeon open source driver. The CPU is an Athlon Barton 2500+. 1.5GB RAM.

The problem does not seem to be Xorg/DRI/AGP related. I turned off xorg by moving /etc/init.d/gdm to a different name and the machine still locks.

However, if I boot in "recovery mode" and go immediately to a "netshell", the machine is stable, apparently (tested few minutes). So the problem lies between this point and GDM starts...

I have posted a bug on launchpad. You could "confirm the bug" the bug there. Hope it will be triagged at some point.

Here is the link:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/336003]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/336003")

---

### Post by jtappin on 2009-03-24
> **jtappin said:**
> Still failing on HD -- One thing I need to try is a fresh install to the other partition set -- tried it the other day but ran into an unrelated problem.

A fresh install of Xubuntu on a different set of partitions works AOK with both the -9 kernel that was on the (week or so old) CD and the -11 installed in the first upgrade. I wonder whether it's a legacy configuration issue from Intrepid that fails after the 2.6.28-7 release or something Kubuntu-specific?

I did see a note in the bug report about network-manager being implicated, but I've not had a chance to test that.

---

### Post by TheUnderTaker on 2009-03-24
are you guys using ext4 by chance? My netbook was locking up too i switched back to ext3. there is a bug that ext4 is causing some systems too lockup.

---

### Post by jtappin on 2009-03-25
> **TheUnderTaker said:**
> are you guys using ext4 by chance? My netbook was locking up too i switched back to ext3. there is a bug that ext4 is causing some systems too lockup.

No -- good ol' ext3 all the way on my machine.

---

### Post by jtappin on 2009-03-30
> **jtappin said:**
> A fresh install of Xubuntu on a different set of partitions works AOK with both the -9 kernel that was on the (week or so old) CD and the -11 installed in the first upgrade. I wonder whether it's a legacy configuration issue from Intrepid that fails after the 2.6.28-7 release or something Kubuntu-specific?


Looks like the culprit is [FONT="Courier New"]powernowd[/FONT]. Which is not installed by default on the current versions, but was still there in the upgraded system.

With the -7 kernel packages it was failing to load and thus not causing problems, but with -8 onwards it was loading and then causing the panic. 

The problem may well be specific to nForce2 chipsets.

---

