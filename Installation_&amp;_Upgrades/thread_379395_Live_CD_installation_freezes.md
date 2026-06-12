---
title: "Live CD installation freezes"
date: 2007-03-08
forum: Installation &amp; Upgrades
---

### Post by doesnotexist on 2007-03-08
Help! here's my system:


Intel Core 2 Duo E4300, LGA 775, 1.8GHz, 64-Bit Dual-Core, 2M L2 Cache
Asus Intel 945GZ,LGA 775, Core2/QX,DDR2,PCIex16,w/Sound,w/LAN,w/Video. [ P5GZ-MX ]
DDR2: 1024MB 533MHz / PC4200 
80GB SATA-II 7200RPM w/8MB Buffer
ROM:Combo:Black 52x24x52X16 CDRW/DVD Combo
PCI-E16: Geforce 7100GS: 128MB w/SLI.
SC:32-Bit 3D/Surround Sound
NIC: 10/100 or 10/100/1000 Ethernet Port 


I've tried using ubuntu 6.06 x86, ubuntu 6.10 x86, ubuntu 6.10 AMD64, and ubuntu 6.10 AMD64 alternative CD.

The first three tried booting from the CD, and froze at the splash screen.  I deleted the options "quiet and splash" so I could see what's going on.  Every time I try installing, I get different error messages, but sometimes the same error message happens twice, or three times...   The error message always happens at the same place though.  

I get:

Begin: Running /scripts/init-bottom ...
Done.
* setting preliminary keymap...
* preparing restricted drivers...
* starting basic networking...
* starting kernel event manager...
[some number] agpgart: Detected an Intel 945G Chipset.
[some number] agpgart: Detected 7932K stolen memory.
[some number] Unable to handle kernel paging request at ffff81003f37ca10 RIP:
[some number] <fffffffff8020c4ab>{do_path_lookup+299}
[some number] BAD
[some number] Oops: 000b [1] SMP
[some number] CPU 0
[some number] Modules linked in:   ...lots of stuff here...
[some number] PiD:3385, comm:udevsettle Not tainted 2.6.17-10-generic #2
[some number] RIP: 0010:[<ffffffff8020c4ab>] <ffffffff8020c4ab>{do_path_lookup+299}
[some number] RSP: 0018:ffff810038e5fdf8 EFLAGS:00010286


Sometimes there is much more error messages (mostly memory addresses it looks like) and sometimes it stops right at 
[some number] agpgart: Detected 7932K stolen memory.

The ubuntu 6.10 AMD64 alternative CD partitioned fine, installed grub fine, even installed ubuntu fine (I thought) but when I try to boot it up I get the same problem.

I used the flag "break=bottom" and at the command line typed "chroot /root nano etc/x11/xorg.conf" but my etc folder had no folding in it named x11

Any suggestions anybody could offer would be greatly appreciated!  I've tried everything!

---

### Post by doesnotexist on 2007-03-08
some other errors I have got are (rebooting and using the same options every time):

"
[some number] EIP:[<c0112981>] send_IPI_mask_bitmask+0x31/0x80 SS:ESP 0068:c03ebd78
[some number]  <0> Kernel panic - not syncing: attempted to kill the idle task!
[some number] 
" 
and 
"
[some number] <1> Fixing recursive fault but reboot is needed!
[some number]  Fixing recursive fault but reboot is needed!
"
and
"
[some number] <c03f0210> unknown_bootoption+0x0/0x270
[some number] <0> Kernel panic - not syncing: Fatal execption in interrupt
[some number]  
"

---

### Post by doesnotexist on 2007-03-08
no help?

And I doomed to use windows?

---

### Post by wpshooter on 2007-03-08
No, probably not.

First thing, have you checked the integrity of the Ubuntu CDs by running the verification function that is found on the initial Ubuntu boot screen menu ?

Secondly, I would recommend that you NOT attempt to install 64 bit version at this time.

---

### Post by doesnotexist on 2007-03-08
yes, every CD was verified.

---

### Post by Kateikyoushi on 2007-03-08
Boot from the cd at the menu press F6 then press E to edit the startupline and add add these options to the end of the line.
Do not use all of them the same time.

noapic
nolapic
pci=irqroute
pci=noacpi
acpi=off
pci=acpi
nolapic
framebuffer=false
linux irqpoll

---

### Post by doesnotexist on 2007-03-08
Thanks for your suggestions:

"Boot from the cd at the menu press F6 then press E to edit the startupline and add add these options to the end of the line.
Do not use all of them the same time."

I ran the following one at a time, nod had any effect, froze at the same spot, shortly after
* Starting kernel event manager

here's the assorted errors, though I think they all point to the same problem:
noapic -- [some number] wifi:0 11b rates: 1Mbps 2Mbps ...
nolapic -- [some number] EIP: [<co114cdf>] smp+apic_timer_interrupt
pci=irqroute -- [some number] Kernel panic -- not syncing: fatal exception in interrupt
pci=noacpi -- [some number] Kernel panic -- not syncing: fatal exception in interrupt
acpi=off -- [some number] Kernel panic -- not syncing: fatal exception in interrupt
pci=acpi -- junk, and then, [some number] <3>BUG: soft lockup detected on CPU#0!  , then more junk
framebuffer=false --  [some number]  <0> kernel panic - not syncing - attempted to kill init
linux irqpoll --  [some number] <1> fixing recursive fault but reboot is needed


All load attemps was from ubuntu 6.10 x86 live CD

Any other ideas?

---

### Post by skywatcher on 2007-03-09
Did I read your system specs correctly -- do you only have 128 MB RAM? If so, try to increase your RAM.

I had the same problem on my HP Compaq (Pentium 4) until I added another 256 MB to the existing 256 MB. The installation then went like a dream...

---

### Post by Kateikyoushi on 2007-03-09
Erm no, he has 128 in the video adapter only, has another 1GB in the system.

---

### Post by wpshooter on 2007-03-09
Doesnotexist:

Does this computer already have any "existing" O/S(s) on it or is Ubuntu going to be the one and only O/S ?

---

### Post by doesnotexist on 2007-03-09
Already has windows installed on it.
works perfectly.

---

### Post by doesnotexist on 2007-03-09
but I hate windows.  I love ubuntu, I just want it to work!

---

### Post by doesnotexist on 2007-03-09
There are people who can install Linux on a Sony PSP, surely we can get Ubuntu working on my computer.  My rig is pretty standard, though new.

Could the problem be the Asus Intel 945GZ [ P5GZ-MX ] card?  Nobody seems to report problems with it elsewhere.

How about the new Intel Core 2 Duo E4300 chip.  It's only been available 1.5 months.  Again, nobody seems to have problems with it.

The  NVIDIA® GeForce® 7100 card seems to agree well with Ubuntu, so what could it be?

---

### Post by Kateikyoushi on 2007-03-10
I looked around about your hardware as well, but can't find the reason why does the installer hang.

Your motherboard Asus Intel 945GZ can run ubuntu 6.1 [LINK]("http://www.newegg.com/Product/Product.asp?Item=N82E16813131088")

> Everything works fine, installed Ubuntu 6.10 (Linux distribution) sees on board video, sound and network. Sata works fine too.

The other components seems to be nothing special.

I digged a bit on the asus forum, Did you try to turn off onboard video or wlan ? Try to turn off acpi in bios as well. These are just shots in the dark what would I try reading your error messages.

---

### Post by pradeepadapa on 2007-03-10
hello man,

try seeing this site for the core2duo support of ubuntu latest edgy version

[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

---

### Post by doesnotexist on 2007-03-10
A.Pradeep

I looked at that site.  Nowhere does it mention my card specifically (the P5GZ model), but it does mention trouble with the 945 motherboard.  One person there suggested I try feisty faun.  The installation froze at the exact same spot, shortly after 

Begin: Running /scripts/init-bottom ...
Done.
* setting preliminary keymap...
* preparing restricted drivers...
* starting basic networking...
* starting kernel event manager...
[some number] agpgart: Detected an Intel 945G Chipset.
[some number] agpgart: Detected 7932K stolen memory.
...

I tried the ubuntu 6.10 AMD64 live CD again.  I removed the "slash and quiet" and added "all-generic-idl irqpoll" and the computer rebooted right at the troubled spot in the instillation, the "* starting kernel event manager..."

I turned off ACPI in the BIOS, tried booting, and it froze at the same spot.

---

### Post by yazeed on 2008-04-28
it is your nvidia card, i have the same problem when nvidia 7xx pcie is installed, when i take it out and use the built in video card, works like a charm

---

