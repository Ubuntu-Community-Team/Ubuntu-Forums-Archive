---
title: "random reboots"
date: 2006-12-03
forum: Installation &amp; Upgrades
---

### Post by JeremyA on 2006-12-03
I've recently installed both Windows XP (ja, I know, sorry) and Ubuntu Edgy Eft on an Asus Vintage AH-1 barebones system.  I'm running an athlon64 3200+ for CPU, and 2 GB of DDR400 RAM.  My primary drive is a SATA drive, and I have an IDE DVD burner installed.

Here's my problem:  Edgy reboots randomly.  Sometimes, it'll reboot  while gnome is firing up.
sometimes, it'll reboot when I try to start synaptic.  Sometimes, when firefox starts.

It's highly peculiar, and I can't duplicate this random rebooting under windows, so I suspect it's a software problem, not a hardware problem--though, it could be that windows is just masking the hardware problem.

nothing is showing up in /var/log/messages, or any other logfile for that matter, and I can seem to find no issues whatsoever. 

I've tried booting with noapic and nolapic flags, but they have no effect on this problem. 

I've tried the system with different RAM, and the problem still occurs.  I am up to latest rev for BIOS updates.  CPU and motherboard temperature are well within normal tolerances.

Any tips or suggestions are much appreciated.  I can shift over to doing my work under Windoze for a few days, but it's a painful, painful migration.

Jeremy

---

### Post by JeremyA on 2006-12-04
I've tried booting with the following options:
noapic nolapic acpi=off

and it took _longer_ until I got a random reboot, but it still happened.  The mouse froze, the keyboard was dead, and *bam* it cycled on me.

this is ugly, to say the least.

---

### Post by dbott67 on 2006-12-04
What kind of video card do you have & what driver are you using?

```
dbott@edgy:~$ **sudo lshw -C video**
  *-display:0
       description: VGA compatible controller
       product: [COLOR="Red"]RV350 AP [Radeon 9600][/COLOR]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@01:00.0
       version: 00
       size: 256MB
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list
       configuration: [COLOR="Red"]driver=fglrx_pci[/COLOR]
       resources: iomemory:e0000000-efffffff ioport:d800-d8ff iomemory:bf800000-bf80ffff irq:217
  *-display:1 UNCLAIMED
       description: Display controller
       product: RV350 AP [Radeon 9600] (Secondary)
       vendor: ATI Technologies Inc
       physical id: 0.1
       bus info: pci@01:00.1
       version: 00
       size: 256MB
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       resources: iomemory:c0000000-cfffffff iomemory:bf000000-bf00ffff
```

You can also type:
```
dbott@edgy:~$ **cat /etc/X11/xorg.conf | grep Driver**
        Driver          "kbd"
        Driver          "mouse"
  Driver        "wacom"
  Driver        "wacom"
  Driver        "wacom"
        Driver          "fglrx"
```

A buggy video driver can cause freezing & re-booting.  If you've got an ATI, you could try downloading the latest fglrx drivers from here:

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

-Dave

---

### Post by JeremyA on 2006-12-14
unfortunately, even installing the latest nvidia drivers did not solve my problem.  

the video card is a PCI-express Nvidia Geforce 6200A.

I had the AGP version of this same card in my previous workstation with no issues, so perhaps this is related to the fact that this card is PCI-E.

---

### Post by JeremyA on 2006-12-18
I've been fiddling with various kernel boot options, in an attempt to make the system stable.

The following options all failed, with various results:

acpi=off  pci=biosirq                  --rebooted
pci=routeirq                              --rebooted
noapic  pci=routeirq                   --hard hang, no reboot
noapic nolapic pci=routeirq         --rebooted
noapic nolapic acpi=off pci=routeirq  --rebooted (but stayed up nearly fifteen minutes!)
noapic nolapic acpi=off pci=biosirq    --rebooted
pci=nommconf                          --rebooted

I then restored the BIOS defaults, and rebooted

noapic nolapic                           --rebooted
pci=nommconf noapic nolapic     --rebooted

My current test, which was stable for 2 hours last night:

noapic nolapic acpi=off pci=nommconf

this may be the magic key.  I will keep testing.
Oh, I also verified that the system and VGA BIOS are at the latest revisions

---

### Post by dbott67 on 2006-12-18
Hi Jeremy,

Does the problem still happen if you boot into Windows XP? (or off the Live CD of Edgy/Dapper/Breezy/Knoppix/Whatever)?

My next step would be to try to isolate the problem down to the OS or hardware.  If the system does not re-boot under XP (or some Live CD), perhaps the issue is with Edgy.

-Dave

---

### Post by JeremyA on 2006-12-19
The system is rock solid under Windows XP Pro.  I don't get to say that much!

The hardware appears to check out just fine, so I'm blaming something in Edgy's kernel at this point.

I've taken to monitoring the CPU, RAM, and network load, in addition to disk activity.  I've also been watching the CPU speed move from 1 Ghz to 1.8 Ghz to 2.0 Ghz and back down.  That never seems to affect the systems.  I can find no patterns regarding system activity and the reboots.  It would appear to happen slightly more often during heavy system loads, but I cannot put any numbers behind that assertion.

](*,)

---

### Post by dbott67 on 2006-12-19
How did you install Edgy?  Did you download the "Live CD" and install it or upgrade from Dapper?

If you downloaded the Live CD (of either Edgy or Dapper), try booting off the Live CD and see if it reboots.

-Dave

---

### Post by JeremyA on 2006-12-22
Since the LiveCD was doing the random reboot thing as well, I decided to recompile the kernel.

2.6.19.1 takes longer to reboot randomly.  I'm currently running with only the noapic and nolapic flags, and the latest version of the nvidia drivers.  In my copious free time, I'll try it without any flags at all.  I let the machine sit overnight, checking mail every ten minutes, and it didn't reboot a single time.  Now I've got 7 and a half hours of uptime--which is a kind of record for this particular workstation.

Unfortunately, while trying to install alien, the system rebooted again.

This is my only machine with a marvell gigabit ethernet card.  I'm going to see about getting the latest drivers for that beastie, and see if that improves it.  There always seems to be _some_ type of network activity going on when this thing blows up.

---

### Post by JeremyA on 2007-01-06
In utter frustration, I tried something truly foolhardy:

I upgraded everything to feisty fawn.

Sonuvagun, it worked.  I've worked on this for 1.5 hours without a single random reboot.  I also booted with full apic and lapic functionality, and am having no issues at all.

Something got fixed between edgy and feisty, and whatever it is, it fixed my problems.

I consider this problem closed.

---

### Post by MetalMusicAddict on 2007-01-06
Funny thing is for me in Feisty Im getting random shutdowns on boot.

---

### Post by JeremyA on 2007-01-07
figures.  Are you running on Asus hardware as well?

---

### Post by riven0 on 2007-01-07
Is it possible your CPU is overheating? I know this was a problem with the Macbooks last year and it was discovered that overheating was the problem... due to a faulty heatsink, of course, but all the same...

---

### Post by JeremyA on 2007-01-07
In my case, that was definitely not an issue.  I could find no pattern for the hangs or reboots.   I wonder if it was some combination of PCI-Express, athlon64 and 32-bit ubuntu.

---

