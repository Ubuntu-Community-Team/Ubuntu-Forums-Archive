---
title: "AMD64 installation flaky"
date: 2006-02-20
forum: Installation &amp; Upgrades
---

### Post by atpat on 2006-02-20
I'm brand new to Linux.  I've been trying to install Ubuntu Linux 5.10 for AMD64.  

Specification: Athlon 64 3700+, Abit KN8 Ultra, 1Gb Kingston ValueRAM DDR400, SATA 300MB/s 250 Gb.

Windows 2000 installed fine.

After I removed my D-link wireless card, the installation stopped hanging the machine a minute or so after the network detection step.  This usually worked out to be in the middle of partitioning.

It seemed to be slightly less inclined to fail also if I add the "noapic nolapic" switches at initiation.

Then the installation kept falling over after retrieving and unpacking the stage one files.  Having read [this thread]("http://ubuntuforums.org/showthread.php?t=124112"), which referred to an identical error and suggested enabling SMP, I was forced to guess how to do this because, although I found many threads referring to SMP,  I couldn't find one anywhere which actually said *how* to enable it.  Actually, I did find references to what appears to be a different version of the installation files specifically for SMP machines, but I have no idea how to obtain or install them.  I did get the impression that if I installed from the DVD instead of the CD then it might work.

So, I ran the installation with "linux smp=true noapic nolapic", which was a complete guess and thus might be nonsense, but this time it did make it through Stage One but failed at some point during Stage Two (that is, after reboot).  The dual boot with W2k seems fine and I get the Ubuntu loader screen, but instead of going into the GUI it just goes to a command line.  I can log in, but having no clue how to work Linux I don't know what to do next.

Help?

Should I reinstall from scratch?
How can I find out whether the GUI is really there but just not being activated automatically?
Is my guess about the syntax for enabling SMP during the installation right or wrong, and if it's wrong, what is right?

---

### Post by ma77smith on 2006-02-21
I have very similar hardware to yourself (3700+, DFI Mobo)

and are having the same thing, mine flashes up with an X-server error just when it should be booting the GUI then drops back to a command line.

If anyway out there can give a nooblet like me a bit of advice then I would be most appreciative.

Ta

---

### Post by atpat on 2006-02-22
I'm going to try installing from the DVD instead.  I'll post here how I get on.

---

### Post by atpat on 2006-02-27
Well, I've been trying the 32-bit version now, and both CD and DVD seem to make no difference.  I've also installed a new optical drive.  The installation just gives up during partitioning: no error.  Sometimes the system hangs completely, sometimes a ctrl-alt-del reset works.  I've tried deleting the partitions entirely and writing them with zeros.  Same deal.

Why doesn't it work? :-k

---

### Post by opensourcerocks on 2006-02-27
We all seem to be having the same problem.
Are you using the 64 bit ubuntu or just 32.
I have only tried with the 64 bit kubuntu 5.10 and 6.04







[http://www.ubuntuforums.org/showthread.php?t=136745]("http://www.ubuntuforums.org/showthread.php?t=136745")

---

### Post by opensourcerocks on 2006-02-27
Have you tried the live cd?
I have very limited bandwidth which only allows for a bout on 700 mg file a month.

---

### Post by atpat on 2006-02-28
Originally I was trying the 64-bit version, but now I've switched to trying the 32-bit version having done some more research on which one is most likely to meet my needs (if I ever get it working at all).

I haven't tried Kubuntu.  I have tried both DVD and CD, and I have tried booting the live version which had similar problems.

Last night I had another go.  I disabled ACPI and APIC using "linux noapic nolapic acpi=off" and this seemed to make things a bit more stable; that is to say, it eventually made it past partitioning and to the end of the Stage One file copying.  The disc came out and the machine rebooted giving me the GRUB boot menu as expected.  Windows 2000 boots fine from that, but Stage Two of the Linux installation just went haywire.  It boots to the Ubuntu graphic and gives me the list of services being initialised, then it goes into the installation of the rest of the base system.

I tried two installations and got to this point both times, but then almost identical things happened.  After installing a few files or whatever it is doing, the display went crazy.  I don't mean it became unintelligible, I mean it the background went grey and it looked to me like the log was being dumped on the screen; and then the process stopped altogether.  Numlock etc. worked, so the machine hadn't completely hung, but would not soft-reset so I just had to hard-reset.  Linux would then boot to a command line, but GNOME did not appear to have been installed.  After the second try I gave up and vented my frustration in Command and Conquer, and then got in to trouble with my wife because it was 2.30am and I woke her up creeping into bed :( 

The second time around was interesting because, for a few seconds at least, the installation could be seen continuing amidst the screen-full of characters.  You know how the file names are displayed as they are installed, under a progress bar?  Well, the progress bar was obliterated by all the log text, but the file names continued to be displayed, albeit in the wrong place on the screen.  Then the installation stopped as described.

The one time I got the 64-bit installation to work was using similar command switched to kick off the installation, and it ended in a similar way.  This suggests that there is no problem with the 64-bit version on my machine, rather that the problem affects all versions.

Maybe it's my PCI-e graphics card?  It's an nVidia 6600GT.  Or chipset drivers?  The chipset is nForce 4 Ultra, and I know there are Linux drivers available but I don't know of any way to install them during rather than after installation.

:-k but approaching ](*,)

---

### Post by opensourcerocks on 2006-02-28
Go 
Here
[http://www.ubuntuforums.org/showthread.php?p=780116&posted=1#post780116]("http://www.ubuntuforums.org/showthread.php?p=780116&posted=1#post780116")
I think that it is my Sahipper X700 PCI express card as well:-?

---

