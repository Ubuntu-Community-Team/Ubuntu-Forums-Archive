---
title: "seeking &quot;which cpu arch&quot; utility"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by SaintDanBert on 2009-12-15
Is there some utility that I might run that will tell me which of the various CPU architectures for some-buntu is the best fit for my workstation?

I see "386" and "generic" and "amd64" and all sorts of available downloads and repositories. How do I know which of these is the best fit for my workstation.

**uname -a** includes the string "i686" while the marketing literature says "Intel Core2 Duo". Is it really required that I poke around like some ultra-geek to find the best fit when I download a new edition of my favorite distro?

If uname reports "i686" why don't I find anything-686 on the distro download lists?

I can use uname or lshw or similar. What is a poor win-doze convert supposed to do?

... things might be better if we had some sort of utility that runs anywhere [java anyone?] and tells even non-geeks details so that they can fetch an apropriate distro edition.

~~~ 0;-Dan

---

### Post by zvacet on 2009-12-15
> uname -a includes the string "i686" while the marketing literature says "Intel Core2 Duo".

This means that you are running 32 bit version of Ubuntu.Witch version you want to run depends of ram.If you have more that 4GB of ram you can install 64 bit version of ubuntu even it is not necessary anymore,because you can install linux-image pae and you will have 32 bit version witch recognize all your ram. I don´t know if I was clear enough,so if you have any kind of questions just ask.

---

### Post by oldos2er on 2009-12-15
Intel Core 2 Duo is 64-bit capable. I have a Core 2 Duo also, and I've been running 64-bit Ubuntu on it for a couple years, with both 2GB and later 4GB RAM. Worked/works great in both configurations.

---

### Post by SaintDanBert on 2009-12-15
Thanks to all for this information. All of it falls into the following schematic:

{know things about your workstation} ===> {match things in arcane knowledge} ===> {learn which distro(s) are appropriate}

I continue to wonder why this match game remains "hidden knowledge" without some highly visible table or better a utility.  Obviously, **lshw** gives the report contents that are important
[list]
[*]CPU -- width: 64 bits
[*]CPU -- capabilities: ... mmx ... vmx ...
[*]RAM -- size: 4GiB
[*]CPU -- width: 64 bits
[/list]
How do we expect non-geek win-doze converts to wade through all of this?

**lshw** has this to say:
```

*-cpu:0
    description: CPU
    product: Intel(R) Core(TM)2 Duo CPU     L7500  @ 1.60GHz
    vendor: Intel Corp.
    physical id: 6
    bus info: cpu@0
    version: 6.15.11
    serial: 0000-06FB-0000-0000-0000-0000
    slot: None
    size: 1601MHz
    capacity: 1601MHz
    width: 64 bits
    clock: 200MHz
    capabilities: boot fpu fpu_exception wp vme de pse 
        tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36
        clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64
        constant_tsc pni monitor ds_cpl vmx est tm2 ssse3 cx16 
        xtpr lahf_lm cpufreq
    configuration: id=0

```

and also
```

*-memory
    description: System Memory
    physical id: 22
    slot: System board or motherboard
    size: 4GiB
    *-bank:0
        description: SODIMM Synchronous 667 MHz (1.5 ns)
        physical id: 0
        slot: DIMM 1
        size: 2GiB
        width: 64 bits
        clock: 667MHz (1.5ns)
    *-bank:1
        description: SODIMM Synchronous 667 MHz (1.5 ns)
        physical id: 1
        slot: DIMM 2
        size: 2GiB
        width: 64 bits
        clock: 667MHz (1.5ns)

```

---

