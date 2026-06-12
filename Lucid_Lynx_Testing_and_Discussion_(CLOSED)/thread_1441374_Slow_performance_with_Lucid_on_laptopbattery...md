---
title: "Slow performance with Lucid on laptop/battery.."
date: 2010-03-28
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by azredwing on 2010-03-28
I'm trying out Lucid (x86_64). I've got a few issues that I'm not sure are due to the beta or due to my laptop. 

Lucid boots really quickly, but after getting to the main desktop, everything is just... slow and unresponsive. Opening any program (like, for instance, a terminal window) takes forever and many times the window greys out as if it's locked. (Running sudo apt-get update && sudo apt-get upgrade locks the terminal window up and I get asked if I want to force-close it.) Clicking shut-down (after clicking the menu button and waiting for the menu to appear) seems to not do anything until about 20 seconds later, and by then 4 of them pop up because I keep trying to click shut-down.

I can't really explain in further detail what is going on, other than it all seems very sluggish and unresponsive. Oddly, this behavior only seems to exist when the laptop isn't plugged in. I'm not sure what to make of this. 

I'm running a Thinkpad T61 - I also just installed a 64GB SSD HDD (Patriot PS-100). I'm unsure if the new HDD is the culprit or this performance issue is in Lucid itself.

EDIT: **Solution!**

It turns out that there's an issue with libata and the SSD (dmesg logs are in the thread). Changing my BIOS SATA controller setting from "AHCI" to "Compatibility" resolved the issue. This did not occur with my SSD in Karmic, i.e., I ran the SSD fine with AHCI mode. Go figure.

---

### Post by azredwing on 2010-03-29
I can now definitively say that this problem exists only when the laptop is not plugged in upon boot. If I plug it in after it boots, the sluggishness remains. Unplugging the laptop results in the same slow performance as before. So as it stands, I have to keep the laptop plugged in in order for the OS to be responsive.

---

### Post by hugmenot on 2010-03-29
Are you using any naive power saving methods?

In particular make sure that you aren&#8217;t using the &#8250;powersave&#8249; cpu scaling governor. You should be using &#8250;ondemand&#8249;

What does this show:
```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```

---

### Post by azredwing on 2010-03-29
> **hugmenot said:**
> Are you using any naive power saving methods?

In particular make sure that you aren&#8217;t using the &#8250;powersave&#8249; cpu scaling governor. You should be using &#8250;ondemand&#8249;

What does this show:
```
cat /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
```

I'm running a dual-core processor. Running the above on both CPUs returns [FONT="Courier New"]ondemand[/FONT] and not [FONT="Courier New"]powersave[/FONT].

---

### Post by azredwing on 2010-03-29
sorry for the bump - but I feel like this could be a big deal if it's not just me but other Lucid laptop users. Does nobody else have this issue?

---

### Post by miegiel on 2010-03-29
> **azredwing said:**
> sorry for the bump - but I feel like this could be a big deal if it's not just me but other Lucid laptop users. Does nobody else have this issue?

No problems here (32bit lucid 2.6.32-18-generic-pae). Not exactly the same hardware, but it's close.
```
user@machine:~$ sudo lshw -short
H/W path               Device     Class       Description
=========================================================
                                  system      Aspire 3810T
/0                                bus         Aspire 3810T
/0/0                              memory      1MiB BIOS
/0/f                              memory      4GiB System Memory
/0/f/0                            memory      2GiB SODIMM Synchronous 800 MHz (1.2 ns)
/0/f/1                            memory      2GiB SODIMM Synchronous 800 MHz (1.2 ns)
/0/17                             processor   Intel(R) Core(TM)2 Duo CPU     U9400  @ 1.40GHz
/0/17/18                          memory      3MiB L2 cache
/0/17/1a                          memory      32KiB L1 cache
/0/17/1.1                         processor   Logical CPU
/0/17/1.2                         processor   Logical CPU
/0/19                             memory      32KiB L1 cache
/0/100                            bridge      Mobile 4 Series Chipset Memory Controller Hub
/0/100/2                          display     Mobile 4 Series Chipset Integrated Graphics Controller
/0/100/2.1                        display     Mobile 4 Series Chipset Integrated Graphics Controller
/0/100/1a                         bus         82801I (ICH9 Family) USB UHCI Controller #4
/0/100/1a.1                       bus         82801I (ICH9 Family) USB UHCI Controller #5
/0/100/1a.7                       bus         82801I (ICH9 Family) USB2 EHCI Controller #2
/0/100/1b                         multimedia  82801I (ICH9 Family) HD Audio Controller
/0/100/1c                         bridge      82801I (ICH9 Family) PCI Express Port 1
/0/100/1c/0            wlan0      network     Wireless WiFi Link 5100
/0/100/1c.2                       bridge      82801I (ICH9 Family) PCI Express Port 3
/0/100/1c.2/0          eth0       network     AR8131 Gigabit Ethernet
/0/100/1d                         bus         82801I (ICH9 Family) USB UHCI Controller #1
/0/100/1d.1                       bus         82801I (ICH9 Family) USB UHCI Controller #2
/0/100/1d.2                       bus         82801I (ICH9 Family) USB UHCI Controller #3
/0/100/1d.3                       bus         82801I (ICH9 Family) USB UHCI Controller #6
/0/100/1d.7                       bus         82801I (ICH9 Family) USB2 EHCI Controller #1
/0/100/1e                         bridge      82801 Mobile PCI Bridge
/0/100/1f                         bridge      ICH9M-E LPC Interface Controller
/0/100/1f.2            scsi1      storage     ICH9M/M-E SATA AHCI Controller
/0/100/1f.2/0.0.0      /dev/sda   disk        320GB WDC WD3200BJKT-0
/0/100/1f.2/0.0.0/1    /dev/sda1  volume      64GiB Windows NTFS volume
/0/100/1f.2/0.0.0/2    /dev/sda2  volume      234GiB Extended partition
/0/100/1f.2/0.0.0/2/5  /dev/sda5  volume      4094MiB Linux swap / Solaris partition
/0/100/1f.2/0.0.0/2/6  /dev/sda6  volume      12GiB Linux filesystem partition
/0/100/1f.2/0.0.0/2/7  /dev/sda7  volume      12GiB Linux filesystem partition
/0/100/1f.2/0.0.0/2/8  /dev/sda8  volume      206GiB Linux filesystem partition
/0/100/1f.3                       bus         82801I (ICH9 Family) SMBus Controller
/0/100/1f.6                       generic     82801I (ICH9 Family) Thermal Subsystem
```

---

### Post by azredwing on 2010-03-29
Thanks for the input, **miegiel**. I see you're not using an SSD - perhaps this narrows down my issue to an SSD. I'm weary of replacing my good Karmic install on my non-SSD drive for sake of testing this, however. I'd like to get others with SSD laptops to corroborate what I suspect.
 
```

$  sudo lshw -short
H/W path             Device     Class       Description
=======================================================
                                system      7658CTO
/0                              bus         7658CTO
/0/0                            memory      128KiB BIOS
/0/6                            processor   Intel(R) Core(TM)2 Duo CPU     T7700
/0/6/a                          memory      64KiB L1 cache
/0/6/c                          memory      4MiB L2 cache
/0/b                            memory      64KiB L1 cache
/0/2b                           memory      4GiB System Memory
/0/2b/0                         memory      2GiB SODIMM DDR2 Synchronous 667 MHz
/0/2b/1                         memory      2GiB SODIMM DDR2 Synchronous 667 MHz
/0/100                          bridge      Mobile PM965/GM965/GL960 Memory Cont
/0/100/2                        display     Mobile GM965/GL960 Integrated Graphi
/0/100/2.1                      display     Mobile GM965/GL960 Integrated Graphi
/0/100/19            eth0       network     82566MM Gigabit Network Connection
/0/100/1a                       bus         82801H (ICH8 Family) USB UHCI Contro
/0/100/1a.1                     bus         82801H (ICH8 Family) USB UHCI Contro
/0/100/1a.7                     bus         82801H (ICH8 Family) USB2 EHCI Contr
/0/100/1b                       multimedia  82801H (ICH8 Family) HD Audio Contro
/0/100/1c                       bridge      82801H (ICH8 Family) PCI Express Por
/0/100/1c.1                     bridge      82801H (ICH8 Family) PCI Express Por
/0/100/1c.1/0        wlan0      network     PRO/Wireless 3945ABG [Golan] Network
/0/100/1c.2                     bridge      82801H (ICH8 Family) PCI Express Por
/0/100/1c.3                     bridge      82801H (ICH8 Family) PCI Express Por
/0/100/1c.4                     bridge      82801H (ICH8 Family) PCI Express Por
/0/100/1d                       bus         82801H (ICH8 Family) USB UHCI Contro
/0/100/1d.1                     bus         82801H (ICH8 Family) USB UHCI Contro
/0/100/1d.2                     bus         82801H (ICH8 Family) USB UHCI Contro
/0/100/1d.7                     bus         82801H (ICH8 Family) USB2 EHCI Contr
/0/100/1e                       bridge      82801 Mobile PCI Bridge
/0/100/1e/0                     bridge      RL5c476 II
/0/100/1e/0.1                   bus         R5C832 IEEE 1394 Controller
/0/100/1f                       bridge      82801HBM (ICH8M-E) LPC Interface Con
/0/100/1f.1          scsi0      storage     82801HBM/HEM (ICH8M/ICH8M-E) IDE Con
/0/100/1f.1/0.0.0    /dev/sda   disk        160GB ST9160823ASG
/0/100/1f.1/0.0.0/1  /dev/sda1  volume      149GiB EXT4 volume
/0/100/1f.2          scsi2      storage     82801HBM/HEM (ICH8M/ICH8M-E) SATA AH
/0/100/1f.2/0.0.0    /dev/sdb   disk        63GB Patriot PS-100 6
/0/100/1f.2/0.0.0/1  /dev/sdb1  volume      3906MiB Linux swap volume
/0/100/1f.2/0.0.0/2  /dev/sdb2  volume      55GiB EXT4 volume
/0/100/1f.3                     bus         82801H (ICH8 Family) SMBus Controlle
/1                              power       42T4530

```

I will note that running this command, copy/pasting, and typing this response took a good 8 minutes. I also note that as I write this, the cursor constantly locks up and Chrome is freezing over and over again (same with Firefox) - maybe every 2-10 seconds. The computer isn't necessarily frozen, as the clock is still ticking and I can hover my mouse over icons and get tooltips. To prove the behavior isn't due to my browser, I tried to click Applications->Accessories->Terminal. The system hung up on clicking 'Accessories'. The menu pops up the same time my browser starts working again. This behavior exists both in a fresh install of Lucid as well as a Karmic install->Lucid upgrade.

---

### Post by azredwing on 2010-03-30
I suppose I'm the only person with this issue, then?

I'll probably revert to my non-SSD drive with Karmic on it. Lucid is totally unusable for me unless it's plugged in, and that pretty much defeats the purpose of having a laptop in the first place. :(

---

### Post by miegiel on 2010-03-30
> **azredwing said:**
> I suppose I'm the only person with this issue, then?

I'll probably revert to my non-SSD drive with Karmic on it. Lucid is totally unusable for me unless it's plugged in, and that pretty much defeats the purpose of having a laptop in the first place. :(

That might help, or a clean install. :-k It could be a power management configuration hiccup, but I wouldn't really know how to troubleshoot that.

---

### Post by azredwing on 2010-03-30
> **miegiel said:**
> That might help, or a clean install. :-k It could be a power management configuration hiccup, but I wouldn't really know how to troubleshoot that.

It's interesting because I originally started as a clean install, and that didn't work, which is why I started from Karmic and upgraded.

---

### Post by hugmenot on 2010-03-30
I have a Lenovo Thinkpad with an SSD in it. I have no problems at all. Neither on AC nor on battery.

So I think something odd is going on on your box. And from your description of the latencies you get, something rather grave goes wrong there.

No idea what it is however.

---

### Post by miegiel on 2010-03-30
> **azredwing said:**
> It's interesting because I originally started as a clean install, and that didn't work, which is why I started from Karmic and upgraded.

What went wrong with the clean install? Did you try the *alternate iso* instead of the *desktop iso*? The alternate iso is more simple and less picky than the desktop iso, but it lacks the live-CD boot option.

---

### Post by azredwing on 2010-03-30
> **miegiel said:**
> What went wrong with the clean install? Did you try the *alternate iso* instead of the *desktop iso*? The alternate iso is more simple and less picky than the desktop iso, but it lacks the live-CD boot option.

I'll give that a try. Nothing went wrong with the clean install, I just had the same latency issues and I wanted to see if the clean install was the issue. (Clearly it isn't.) I'll give the alternate iso a shot sometime this week.

---

### Post by miegiel on 2010-03-30
> **azredwing said:**
> I'll give that a try. Nothing went wrong with the clean install, I just had the same latency issues and I wanted to see if the clean install was the issue. (Clearly it isn't.) I'll give the alternate iso a shot sometime this week.

Ok, I misunderstood you there. In that case the alternate iso might not help, but you never know ;)

There should be a Thinkpad T61 thread in the forums somewhere, maybe someone in the thread has already installed lucid too.

---

### Post by azredwing on 2010-03-30
> **miegiel said:**
> Ok, I misunderstood you there. In that case the alternate iso might not help, but you never know ;)

There should be a Thinkpad T61 thread in the forums somewhere, maybe someone in the thread has already installed lucid too.

As expected, a clean install using the alternate iso did not work. Additionally, I tried a clean install with no swap partition and with my second HDD disconnected. Still having issues.

At this point I'm going to revert to Karmic. I'll see if I'm having issues with Karmic on the SSD as well.

---

### Post by azredwing on 2010-03-30
Running Karmic with SSD, 2GB swap and my 160GB secondary HDD (SATA 7200rpm) yields no problems - so the issue must be in Lucid.

I'll file a bug report... (but against what package?...) maybe someone else has some idea of what the hell is going on. I will also try an upgrade from Karmic to Lucid one more time to confirm the issue.

---

### Post by hugmenot on 2010-03-30
Have you looked around dmesg and in syslog?

---

### Post by azredwing on 2010-03-31
Running dmsg when my lappy is plugged in looks fine. Immediately after unplugging it, however, this occurs over and over again:

```

[   78.263100] ata3.00: exception Emask 0x10 SAct 0x0 SErr 0x4040000 action 0xe frozen
[   78.263104] ata3.00: irq_stat 0x00000040, connection status changed
[   78.263107] ata3: SError: { CommWake DevExch }
[   78.263110] ata3.00: failed command: READ DMA
[   78.263114] ata3.00: cmd c8/00:08:67:63:42/00:00:00:00:00/e0 tag 0 dma 4096 in
[   78.263115]          res 50/00:08:5f:63:42/00:00:00:00:00/e0 Emask 0x10 (ATA bus error)
[   78.263117] ata3.00: status: { DRDY }
[   78.263121] ata3: hard resetting link
[   79.010376] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   84.010355] ata3.00: qc timeout (cmd 0xec)
[   84.010376] ata3.00: failed to IDENTIFY (I/O error, err_mask=0x4)
[   84.010383] ata3.00: revalidation failed (errno=-5)
[   84.010396] ata3: hard resetting link
[   84.360215] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   84.363544] ata3.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[   84.363555] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[   84.370494] ata3.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[   84.370505] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[   84.373425] ata3.00: configured for UDMA/133
[   84.380390] ata3.00: configured for UDMA/133
[   84.380421] ata3: EH complete

```

So it looks to be a HDD issue for sure - but why only on battery mode?

I was thinking of upgrading the firmware on the SSD. (However, I don't have a Windows machine to do it. Ha.)

---

### Post by azredwing on 2010-03-31
It looks like some guys ran into the same things:

[http://swiss.ubuntuforums.org/showthread.php?t=1034762](http://swiss.ubuntuforums.org/showthread.php?t=1034762)

Not sure if this applies to me, since I'm not getting { DRDY ERR }'s. Somehow I hit a kernel panic and can't boot up, so I'm in the process of reinstalling (again!) now. 

I will try again and set 

```

options libata noacpi=1

``` 

in /etc/modprobe.d/options . 

All signs seem to point to a HDD failure, but (1) this HDD is brand new and (2) it works fine when running Karmic.

(man, this CANNOT be good for my SSD.)

---

### Post by azredwing on 2010-03-31
Setting that option does nothing. I tried adding 

```

noapic acpi=off

```

to /boot/grub/grub.cfg, but doing so actually causes the ata error to appear before getting to the login screen, even with the computer plugged in.

I'll keep investigating... 

Does anyone know if there's a way to flash new firmware for the SSD HDD in Linux?

---

### Post by azredwing on 2010-03-31
```


$ sudo hdparm -i /dev/sda

/dev/sda:

 Model=Patriot, FwRev=VER2.006, SerialNo=7B420701140800003044
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=32256, SectSize=512, ECCbytes=4
 BuffType=DualPort, BuffSize=1kB, MaxMultSect=1, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=124780320
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: unknown setting WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode


```

---

### Post by miegiel on 2010-04-01
I had to use *libata.force=noncq* as a kernel parameter in grub to be able to boot linux on this laptop for a while. That bug is solved for me now, but there's a whole list of *libata....* kernel parameters to give the kernel as it boots. [Check this]("http://www.kernel.org/doc/Documentation/kernel-parameters.txt"), libata stuff is just above the middle of the long page. *libata.noacpi* is in there too, just use it like that, no *=1* at the end (*libata.acpi* forces it on).

Hope this helps a bit, good luck.

---

### Post by azredwing on 2010-04-01
> **miegiel said:**
> I had to use *libata.force=noncq* as a kernel parameter in grub to be able to boot linux on this laptop for a while. That bug is solved for me now, but there's a whole list of *libata....* kernel parameters to give the kernel as it boots. [Check this]("http://www.kernel.org/doc/Documentation/kernel-parameters.txt"), libata stuff is just above the middle of the long page. *libata.noacpi* is in there too, just use it like that, no *=1* at the end (*libata.acpi* forces it on).

Hope this helps a bit, good luck.

libata.noacpi and libataforce=noncq did not work for me. Neither did upgrading my BIOS.

**HOWEVER**

I changed the SATA controller type from AHCI to "Compatible" in the BIOS and it seems to be running perfectly now! I will investigate whether it was JUST this that did the trick, or if it was a combination of that + the kernel boot options.

I'd like to point out again that the SSD was working just fine in Karmic with AHCI and no other kernel options. Should this issue be considered a bug and written up?

Thanks a ton for your help!

---

### Post by miegiel on 2010-04-02
> **azredwing said:**
> libata.noacpi and libataforce=noncq did not work for me. Neither did upgrading my BIOS.

**HOWEVER**

I changed the SATA controller type from AHCI to "Compatible" in the BIOS and it seems to be running perfectly now! I will investigate whether it was JUST this that did the trick, or if it was a combination of that + the kernel boot options.

I'd like to point out again that the SSD was working just fine in Karmic with AHCI and no other kernel options. Should this issue be considered a bug and written up?

Thanks a ton for your help!

It might be a good idea to stick your laptop's SSD into a friends windows machine to update the firmware before reporting this as a bug. Laptop sata disks have the same size/type connectors as the larger sata disks in desktop PCs.

Your "Compatible" mode is the old ATA mode and a fall back in case of incompatibilities. It turns of some functions you might want to keep: NCQ (improves performance if your disk supports it too), hot-swapping disks (useful for servers, but not for laptops), improved security (on my laptop I can't secure the disk with a BIOS password unless AHCI is enabled) and some other little things.

---

