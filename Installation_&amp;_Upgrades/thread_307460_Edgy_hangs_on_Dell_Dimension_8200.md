---
title: "Edgy hangs on Dell Dimension 8200"
date: 2006-11-26
forum: Installation &amp; Upgrades
---

### Post by daveg2 on 2006-11-26
Clean Edgy install using the Alternate CD.  Integrity of the CD was verified first.  Memtest86+ ran successfully overnight.

Hardware:
Dell Dimension 8200
P4 2.26 GHz, 512K, 533 FSB, Socket N, 80532
1.25 GB RAM, PC800, non-ECC RDRAM
Mobo is an Intel 850E chipset, 33 MHz PCI bus, 66 MHz AGP bus
BIOS is 8200A09
GeForce FX5500, 256 MB
Dell P992 Model 5002, 19" 
nv driver running at 1024x768 85 Hz
NVidia 9629 driver locks up also.
120 GB IDE WinXP drive and a CD or DVD writer on the first IDE channel, 40 GB IDE LINUX drive on the second IDE, dual-boot with grub.  

Windows runs fine.  The freeze happens in Edgy after the menus and icons are displayed, after selecting a menu option, and somewhere shortly into using the application.  I had the same problem or a similar problem with Dapper that was never resolved---I gave up first.  Warty was fine, as was the one before Warty.  (Memory failure, sorry!) 

It freezes within 2 or 3 minutes after logging in.  Frequently in Synaptic, Firefox, the terminal, or a drop-down menu.  In fact, it will hang if I do absolutely nothing for a bit.  The cursor hangs, alternate consoles are not available.  A cold boot is required.

Dmesg and a review of /var/logs/* reveals nothing of interest to me.

I'm very suspicious of the GUI environment because I've never experienced a hang at the command line booting into recovery mode.

Any questions, suggestions, and tips will be gratefully accepted.  Thank you in advance.

---

### Post by Caraibes on 2006-11-26
As of me, Edgy freezes whenever I open Skype...

This is on my laptop... I am actually keeping Edgy on the laptop to see how it does, but re-installing Dapper on the desktop, since it is a work machine...

---

### Post by daveg2 on 2006-11-30
I have twice been in an alternate console after the gui login and gotten a kernel panic.  This time it was Ctrl-Alt-F4.

The kernel is 2.6.17-10-generic.

ngs+0x344/0x3a0
[17179680.148000] <c02525b1> ide_do_request+0x6a1/0x8a0 <f8875293> cdrom_decode_status+0x2f3/0x330 [ide_cd}
[17179680.148000] <c0115acf> umask_IO_APIC_irq+0x1f/0x40 <c0149956> enable_irq+0xb6/0xe0
[17179680.148000] <f8875b30> cdrom_read_intr+0x0/0x390 [ide_cd] <f8875b30> cdrom_read_intr+0x0/0x390 [ide_cd]
[17179680.148000] <c025304c> ide_timer_expiry+0xcc/0x2f0 <c012be69> run_timer_softirq+ox159/0x1a0
[17179680.148000] <c01278ef> do_soft_irq+0x35/0x40 <c010413c> apic_timer_interrupt+0x1c/0x30
[17179680.148000] <c0102080> default_ide+0x0/0x60 <c01020aa> default_idel+0x2a/0x60
[17179680.148000] <c0102122> cpu_idle+0x42/0xb0 <c03f07a1> start_kernel+0x321/0x3a0
[17179680.148000] <c03f0210> unknown_boot_option+0x0/0x270
[17179680.148000] Code 89 cd 89 5c 24 10 89 04 24 b8 80 85 3e c0 88 54 24 07 8b 5e 6c 89 5c 24 08 8b 5b 08 e8 b6 67 08 00 89 44 24 0c 8b 0b 85 c9 74 08 <0f> 0b af 03 ad 4b 30 c9 8b 53 24 89 2b 89 bb f0 00 00 00 a1 00
[17179680.148000] EIP: [<c0254254>] ide_execut_command+0x44/0xc0 SS:ESP 0068:c03ebdfc
[17179680.148000] Kernel panic - not syncing: Fatal exception in interupt
[17179680.148000]

What do I need to do next to debug this and get it solved?  Is there a log somewhere that contains it?  This was copied with pencil/paper and entered in, so errors and typos are quite possible.

---

### Post by daveg2 on 2006-12-04
Update:  I found that going into recovery mode never hangs at the command line.  I found that startx at the command line launches an X environment that never hangs.  I'm in Edgy running Firefox now with no hangs.

Problem:  Startx doesn't give me a login option, so I can't see Synaptic in the menu or enable the menu option.  

Questions:  How can I get into X from recovery mode and still login?

What's different about X launched from the recovery mode command line with startx vs X when I go in the usual way?  

My system always hangs within about 2 minutes when I go in the usual way.  It locks up so tight that power down is required.  I don't believe it's X locking up because alternate consoles are not available.  It appears to be a kernel panic.

---

### Post by daveg2 on 2006-12-04
Found it!  Work around now in place.  Steps:
Select the recovery mode option.
/etc/init.d/gdm start

The last, minor, issue is that after logging in, I get a warning that HAL failed to initialize.  Hardware Application Layer?  Sounds serious, but "everything" is now running fine.  Quotes around everything, because I obviously haven't run everything yet!  All does, however, look good so far.

I'd still like to know what the difference is between recovery mode, /etc/init.d/gdm start and the usual way of launching Edgy.  If I knew more, I might be able to figure out how to bug report it.

---

### Post by daveg2 on 2006-12-08
So no one has any ideas about what is the difference between recovery mode, /etc/init.d/gdm start vs GUI mode?

---

### Post by daveg2 on 2006-12-13
How disappointing....

---

### Post by raydar on 2007-05-19
Hii--

I'm having just the same thing happen in Feisty, on a Dell Latitude cpi d300xt laptop.  I first tried installing Xubuntu Edgy, then managed to update it to Feisty, but started encountering the same problem of crashing after 2 or 3 minutes.  Usually, in fact, I'll get a mini-hang for about 5 seconds; then another minute or two of functionality before the hard hang.  I had nothing to lose, so I tried a fresh install of Kubuntu just to see what might change.  No dice; same hard hang after 2 or 3 minutes.  I even had it happen when I just let it sit at the login prompt.  Like others who've posted in this thread, I don't ever get a crash when I boot to a command prompt in recovery mode, or using a Linux system recovery CD I downloaded.


The only way I got the OS to install each time was by messing around with boot prompt switches.  Otherwise, I'd always get lots of hard drive and cdrom timeouts.  I tried a few, one even supposedly particularly applicable to my model of laptop, but finally found that ide=nodma did the trick, though I still got suspicious timeouts here and there, especially on the floppy controller since I don't have a floppy installed in the machine.

One strange thing I found when the problem first started occurring is that stepping back to the previous kernel version at the grub menu remedied the crashing problem for a while--I could start the machine and leave it alone for well over an hour.  But two or three restarts later, the hanging problem came back, and after a couple times of repeating this step, I ran out of previous kernels to boot!

I left my machine alone for a couple weeks to work on other projects, but tried it again this morning.  First boot lasted for several hours just fine, and a couple restarts after that, it started hanging again. I was thinking ahead a little this time and had running the system monitor and log viewer.  This is a PII300 with 192MB RAM (it ran WinXP just fine before I erased that partition in favor of a Linux-only machine), with a 10GB hdd and a  swap partition of just under 450MB.  The swap file was barely being used according to the system monitor--I'd feared I made its partition too small, but that doesn't appear to be the culprit, anyway.  

The output of my system log at the time of the crash--all that was displayed on my screen, that is--is this:

<c01493ed> __do_IRQ+0x9d/0x11...
<c018b73e> seq_printf+0x2e/0x6...
<c018bc00> seq_read+0x0/0x2a0...
<c018bc69> seq_read+0x69/0x2a...
<c020020f> acpi_ds_create_opera...
<c020027b> acpi_ds_create_oper...
<c020bde9> acpi_ns_evaluate+0x...
<c020d7be> acpi_ps_parse_aml+...
<c020e4bd> acpi_ps_append_arg...
<c020e898> acpi_ps_execute_pas...
<c021346a> acpi_ut_delete_inter...
<c0213e2e> acpi_ut_allocate_obj...
<c0252253> ide_do_request_0x3...
<c0252f80> ide_timer_expiry+0x0/...
<c025304c> ide_timer_expiry+0xc...
<c0253273> ide_inb+0x3/0x10 <...
<c0253ffb> reset_pollfunc+0xdb/0...
hdc: drive not ready for command
hdc: status timeout: status=0x90 {...
ide: failed opcode was: unknown
hdc: ATAPI reset timed out, sta...

Which looks similar to some of the messages displayed when installation commenced to hang for me, before I found the "boot:  ide=nodma" switch.  

I am pretty much a just-barely initiated Linux tinkerer, able to break things without knowing precisely what I've done but also apparently able to hack an xorg.conf file for a dual monitor setup successfully.  I'm just bold enough to think I'd like to try turning dma off for regular boots, since that's what made installations succeed; but I'm only finding threads about how to turn it off at a "boot:" prompt for installation.  

Am I on the right track, and does anyone know how I can turn off dma for regular boots?

I should also mention:
1. I tried the above suggestions to boot into recovery mode and run startx, and to get a password prompt with, in my case, /etc/init.d/kdm start (because I'm running KDE at the moment). Like they did for daveg2 above, those gave me a crashless session, pasword-promptless and a password-prompting respectively.
2. I sometimes get pixel errors on my screen--inch-or-two-long lines of wrong-color pixels.  I don't know that this is related, but it's the only other decidedly bizarre symptom I've experienced since I started trying to run Linux on this machine.

Thanks for any help!

--Raydar

---

