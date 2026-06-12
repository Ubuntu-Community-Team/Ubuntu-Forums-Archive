---
title: "Disabling APIC/LAPIC in 5.10?"
date: 2005-11-25
forum: Installation &amp; Upgrades
---

### Post by dmxubuntu on 2005-11-25
When trying to boot from the "main" kernel offered by grub after installing to HD, I get a "Spurious 8259A interrupt: IRQ7" error and the boot fails.

I can boot one of the other kernels, but with some degradation in fuctionnality (don't recall exactly what is not working... it's been a couple of weeks now).

Searching the web dug out some pointers. It seems the problem is with the APIC (and LAPIC) not being properly disabled by my BIOS, causing the interrupt to seem to signal spuriously and throwing the boot loader astray. I am running an Asus A7V MOBO with an AMD Thunderbird CPU (1 GH).

So I tried to give grub some inline commands to pass to the kernel to disable APIC when booting. Added "noapci" at the end of the line without success. Found another message saying there was a tag written as "pci=noacpi" for the acpi system, so I tried "pci=noapic" in case that was the syntax. No go either. Oh! And I tried tagging "apic=off". Which one of these syntaxes should be used?

So I'm stuck. Frustrating thing is that the LiveCD boots without problem. So why is the HD version different?

There must be a really simple way around this problem, but it is not documented yet. If it is, please point me in the right direction.

Tks,
Denis

---

### Post by dmxubuntu on 2005-11-28
Well, I had a couple of hours to spare. So I came back to my Ubuntu installation to try to figure out how to make it boot properly. It was a hit and miss thing, and it missed everytime, unfortunatly.

In Grub, I have four boot options: Linux, and three named kernels. I found the information for the boot option syntax in the help sreen of the LiveCD. Here is the way to turn off the apic (and lapic) system:

>Linux noapic nolapic

If you want to turn off the acpi system:

>Linux pci=noacpi

Or you can turn off only the IRQ mapping by the acpi system (notice that acpi is not apic, by the way):

>Linux acpi=noirq

You could combine all of these:

> Linux acpi=noriq noapic nolapic

I tried all combinations with "Linux" and with naming other kernels. If I turn apic and lapic off, Linux boots but doesn't recognise my network card (Realtek 8139). Haven't tried to modprobe the module. Did it many times in Slakware but Ubuntu/Debian seems a little bit unfamiliar to me. I also don't get the sound system. Maybe other things are missing. Did'nt try out every device.

I also get error messages about some missing library files. Didn't dmesg to jot down which ones yet.

Without these options, after the disks are recognized and ide0 and ide1 are identified, I get the "Spurious 8259A interrupt: IRQ7" message and a freeze. If I disable the acpi system withe the acpi=noriq option or pci=noacpi, then the boot freezes at the same point without giving the "Spurious..." message.

Rebooted with the LiveCD and everything is ok. Got the network, sound and everything works.

I'm saying to myself: Can't be a faulty apic system if the LiveCD boots ok, can it? Nor a faulty anything, except a faulting boot process or install procedure in Ubuntu, maybe.

This is the great weakness of [any] Linux: the hard setups. Once you have it going, it's great. And since more software, even games, is being made available, it is becoming more and more attractive. 

With Windows, you pay for some things that should be free and wonder what secrets lie under some of the code and face blue sreens that can't be explained. But you can be up and, if not running, at least walking with all your stuff in half a day. With Linux, you have to find the right flavor that will give you what your are looking for and will install properly on your machine. Not an easy task.

Anyway, I still have hope that I will eventually be able to install Ubuntu on my machine. Maybe I will have to wait for the next release. I don't mind. I do wish someone on the team would acknowledge the install problem though. It would help knowing the problem is being taken into account.

Cheers!

---

### Post by dmxubuntu on 2005-12-08
Well, after hours of trying all different combinations for disabling apic, lapic and apci (that makes many combinations with each kernel/method), doing it by tagging at the end of the grub command line or in the script on the hd, either I get an Ubuntu without my cards recognised (sound and network at least), or it just fails to boot with the spurious irq error message.

I still think Ubuntu is a good project. But from my trials with the LiveCD, I thought we had a Linux that would install just about anywhere with no hassle. I hope it is the case, but it is not for my machine, which is not very esoteric: Asus A7V mobo with an AMD Thunderbird at 1 GHz. 

I wish you luck with your efforts and really hope someone in the Linux community reaches the elusive goal of putting together an installer that competes with the one from Microsoft. I will keep looking for this. In the meantime, I've rolled up my sleeves and installed Gentoo, compiling everything from source. 

Cheers!

---

### Post by el3ktro on 2006-02-02
VIA chipsets are really tricky, my experience, had only problems with them. For Linux (and generally) NVIDIA is the way to o for chipsets.

Tom

---

### Post by dmx on 2006-02-03
I understand the VIA chips are tricky. Still, the LiveCD (Ubuntu) has no problems with them. Knoppix has no problem with them. Windows has no problems with them. It is hard to accept or understand that the Unbuntu disk install has problems with the same VIA chips and that there is no fix or workaround for this. :???:

---

### Post by Mustard on 2006-02-03
I'm just curious whether you installed using the apic nolapic options on the installer or whether it was a case of you adding them to grub afterwards.  I initially had some trouble with this, but found that fiddling around with BIOS settings fixed the problem.  I can't recall exactly what settings worked for me unfortunately, but I may have a peek in BIOS at some stage and see if I can remember how I went about it.

---

