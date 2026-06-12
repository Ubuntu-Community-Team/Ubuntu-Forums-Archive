---
title: "Xubuntu tune for speed"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by xerman on 2007-04-20
Hello there,

I've just set up an old PentiumMMX computer. The Specs are the following:
PentiumMMX 200 MHz
160 MB Ram
Matrox Millenium 4MB Vram
13'7 GB HD
20x CD
8x/4x/32x CDRW
Lan

I decided for Xubuntu, due to its smaller footprint, but I had the idea that you could remove unused services, daemons, and so on to speed up the box. The use will be for desktop, not connected to internet, just to write some text and do some small graphics. But if i could improve responsiveness would be a great leap forward. Any help on this one would be much appreciated.

Thanks a lot.

---

### Post by kidders on 2007-04-21
Hi there,

All default Ubuntu installations tend to be quite lightweight, with a view to being as performant as possible out of the box. Having said that, it is worth checking your hardware situation though.

Using my machine as an example, **lspci**, **lshw** & similar tell me that Ubuntu doesn't seem to know much about some of my hardware. For instance ...```
kidders@x2:~$ lspci|grep -i unknown
02:00.0 VGA compatible controller: nVidia Corporation Unknown device 0193 (rev a2)
```When I installed my OS, pretty much the first thing I did was took a look through my **dmesg** & read Ubuntu's interpretation of my hardware, just to check that everything was being recognised correctly. One particular thing that can significantly affect performance is proper recognition of graphics cards. You see, if X isn't quite sure what you have, it can't take any clever short cuts, and Ubuntu winds up using your *motherboard's* CPU & RAM  to perform operations that your graphics card's on-board chips may well be able to handle on their own.

Anyhow, as you can see, my graphics card gets called "Unknown" (which isn't encouraging!), so the first thing I did was **lsmod**, to check that the right kernel modules (drivers) were being used.```
kidders@x2:~$ lsmod|grep nv
nvidia               7761432  24 
i2c_core               26624  6 i2c_ec,it87,i2c_isa,eeprom,nvidia,i2c_nforce2
sata_nv                24196  4 
libata                137000  2 ata_generic,sata_nv
```This indicates that (for the mostpart) sensible drivers have, in fact, been chosen for my motherboard's on-board gizmos, graphics card, etc. I was able to check my manufacturer's website for recommendations on the appropriate drivers to use.

So that's my first recommendation. Check that you really do have what Ubuntu thinks you have, and check that it's not using daft kernel modules to drive your hardware.




It has to be said, unfortunately, that your PC is quite low-spec, you you *may* find that you have no hardware recognition problems ... but Ubuntu still won't perform satisfactorily for you. There are several reasons for this:

_** The Kernel**_
Ubuntu's kernel is designed to work with the widest possible range of hardware, which means the developers have had to _repeatedly_ sacrifice performance for compatibility. This puts users at a disadvantage right from the start, because the interface to their hardware is more generic than it needs to be. While this approach has _**major**_ advantages, it can penalise users of older PCs, where every single possible performance refinement counts.

_** Your Software**_
Using pre-packaged software comes with similar drawbacks. The alternative (compiling everything yourself) is awkward and time-consuming, but can result in a performance boost, because both your kernel and your applications would be designed to work on _your_ PC, and nothing else ... and you can often explicitly disable software features you have no intention of using.

So, my second recommendation is to consider optimising your Linux installation, to try to squeeze every last drop of power out of your hardware. 

Unfortunately, if you're not completely comfortable with Linux, doing so would be complicated, time-consuming, and error-prone. Although it doesn't run Ubuntu, I have performed this sort of optimisation on an old Pentium of mine, with satisfactory results. What I lose in the trade-off is the ability to install applications instantly, or perform system updates with a single command.

> I decided for Xubuntu, due to its smaller footprintGood idea. :-)

> I had the idea that you could remove unused services, daemons, and so on to speed up the box.This may produce a _very_ small performance boost, when you put your box under pressure.

For me, getting the most out of old hardware is an exercise in making every single possible performance tweak (at the cost of a great deal of effort), in the hope that the combined effect will produce noticeable results.

Examples:[LIST]
[*]A custom kernel compile.
[*]Optimisation of hard disk performance (**hdparm**).
[*]Careful choice of filesystems.
[*]Going through xorg.conf, doing everything possible to reduce demands on hardware.
[*]I/O optimisation (perhaps by sacrificing RAM).
[*]Exploiting, where applicable, the presence of more than one hard disk.
[*]Disabling and removing support for unused hardware.[/LIST]I suppose the big question is how far you're willing to go!

---

### Post by drachenchen on 2007-04-21
Hello, Xerman.

I'm not much of a software-head, but I have tinkered with hardware a bit.   I've owned a few computers of that age, and I would suggest that you find out what motherboard you have, and whether or not you have maxed-out the RAM on that particular board.  If you google for "(whatevermotherboard) specifications", you can usually find a listing of maximum RAM somewhere.  The greatest performance increases that I got from any of my old boxes came from simply adding the most RAM that they were designed for.  It will not turn it into a modern computer, but it should do fine for your intended uses.  I have a 486 board with a Pentium 1 Pro cpu in it, 166MHz, 128MBs of old-style EDO RAM, three old hard-drives scabbed into it, and an 8MB PCI video card.  This thing still runs, and after maxing-out the RAM, it went from running Tombraider 1 (on the Win-95 partition) at slide-show speed, to running it fast enough to be fun and fairly smooth.  Usually RAM capacities go up by the familiar multiples of 64, so if you have 160 MB installed, your board might take 192 Megs or even 256.  It doesn't seem like much of an increase numerically, but it's a huge percentage increase, and the system will notice.  That, and RAM from that period is generally not very expensive, although it is getting harder to find these days.  Hope this helps.  Cheers!

                                                                                                                                                   -drach

---

### Post by xerman on 2007-04-23
kidders, drachenchen, thanks for the replies.

Actually, i do not feel like compiling kernel nor apps, mostly because i do not have the time to tune that computer that way. I have another, an imac g3 400MHz at work I have to take care about, a portable and a desktop at home, which makes 3 machines to take care about... and doing my work too. All of them have ubuntu installed, Hoary on the imac, edgy on the portable and feisty on the desktop home pc.

Actually, this oldie is my sister's, and I felt like giving it a chance to catch up with the times. But compiling from source, though is a great idea to speed it up, i think it is not worth the time being known the use this oldie will have.

I know about ram, mayb the motherboard will support 1GB ram, right now it has 128+32MB dimms, and has simm slots too, but this motherboard does not allow the use of dimm and simm together, i think i remember this.
Spending money is not an option, as has more sense to buy a new machine, and at the prices we can get it today...

The original machine just had a 2.1 GB hd and 64mb ram with a CD reader. The burner, the ram and the 13 GB hd are stuff i had taking up space on some shelves. So i took this resurrection as a way to learn a bit more about hardware and software. But never as a "./configure, make, sudo make install or whatever else needed"  :).

But the "dmesg, lspci, lsmod, lshw" are things that served me to see more inside the system, and not just for this oldie, but for the rest of machines (though i haven't still figure out why this oldie does not shutdown). Thanks a lot kidders. I'll have a pint of Guinness to thank you. :)


Take care
Xermán

---

### Post by kidders on 2007-04-23
> **xerman said:**
> Actually, i do not feel like compiling kernel nor appsI can certainly understand that... it would be a huge undertaking!

> **xerman said:**
> Spending money is not an optionThis is the main reason I suggested customising your distro. I was looking for _free_ (albeit crazily time-consuming) ways of improving performance. Drachenchen's RAM suggestion might still be worth consideration though ... Memory for most older motherboards is often *extremely* cheap.

[SIZE="1"]Xerman's response: Didn't you hear me?! I said spending money is **not** an option! Hehe.[/SIZE]

> **xerman said:**
> But the "dmesg, lspci, lsmod, lshw" are things that served me to see more inside the systemYep... It's vital that your box is using the right drivers. Your next stop should be xorg.conf though. What to do in order to optimise it is very hardware-specific, but here are some basic guidelines:
[LIST]
[*]Again, be sure you're specifying a suitable (non-generic) driver, if at all possible.
[*]Don't be over-ambitious with things like resolution, colour depth, your use of extensions, etc.
[*]In the right circumstances, reducing buffering can give a graphical environment a slightly "zippier" feel, by reducing latency.
[/LIST]

> **xerman said:**
> I haven't still figure out why this oldie does not shutdownThis happens a lot (especially with older machines) and is most often due to a buggy ACPI implementation. Assuming that your OS shuts down properly, tells you it's about to halt the machine, and just sits there instead, you may not be able to correct the problem. Essentially, your motherboard's power management interface is probably ignoring or misinterpreting the instruction to shut off. You might be able to find a tweak that does the job ... then again, maybe not. :-(

---

