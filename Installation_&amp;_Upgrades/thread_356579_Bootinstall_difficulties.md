---
title: "Boot/install difficulties"
date: 2007-02-08
forum: Installation &amp; Upgrades
---

### Post by dizzylizard on 2007-02-08
Ok, folks, here's the hardware:

Motherboard: ECS Elitegroup P4M800PRO-M, Onboard VGA, sound, USB, and LAN...No PCI cards installed 

Chipset: Intel Pentium D 945 Dual Core CPU

Primary IDE Master: Western Digital WD Caviar SE 7200 RPM 160 GB/8MB Cache/100 MB/s

Secondary IDE Master: Liteon 16X Internal DVD +/-R/+/-RW ReWriter

Pretty generic, I know...but that's what Linux is supposed to be good at...all hardware is new, right out of the box.  Cables are all tight, everything "appears" to be hooked up right, so I cable it up, pop in an Ubuntu 6.06 LTS LiveCD, and hit the power stud.  All seems to be going well, the splash screen pops up asking me if I want to start/install, check CD for defects, etc, etc.  On install it begins booting the system, configuring gnome-panel-data, screensaver, preconfiguring /etc/modules and networking, loading preseed file, setting up init, configuring accessibility options, disabling the update-notifier, and a bunch of other stuff it goes through too fast to read...it gets to a line that says "configuring some drivers ----- OK" and stalls for several minutes.  When it finally does resume, the screen fills with lines of code, again too fast to read (and no scrollback).  All the lines appear to begin with the format [(8-digit #string).(6-digit #string)] and then a message...again, it's scrolling too fast to figure out what the numbers are, or what the message is.  I tried downloading the 64-bit ISO for version 6.10, but after burning the CD, I loaded it and got a "Non-boot Media" message.  I'm not a complete noob, but this is beyond me!  Any ideas/suggestions?

---

### Post by skywatcher on 2007-02-08
Ditto, almost.

Windows XP Home, 40 Gbyte hard disk, Pentium 4, disk defragmented, 15 Gbytes available for partition, etc. Get to 'Install', select language. (It already takes about 15 minutes just to get here.)

Then nothing happens -- just a lot of CD activity, for more than an hour. Tried several times, no difference.

---

### Post by dizzylizard on 2007-02-08
trying again, I got this output:

<code>
Booting 'Ubuntu, Kernel 2.6.17-10-386'

Root (hd0,0)
     filesystem type is ext2fs, partition type 0x83
Kernel /boot/vmlinuz-2.6.17-10-386 root=UUID=1e534a23-2fbd-476f-a16c-63fb64a189f1 ro quiet splash
     [Linux-bzimage, setup=0x1c00, size=0x17e83f]
initrd /boot/initrd.img-2.6.17-10-386
     [Linux-initrd@0x9f91c000, 0x6d3127bytes]
savedefault
boot
[17179573.692000]crc error
[17179573.692000]Kernel panic - not synching; VFS: unable to mount root fs on unknown-block (0,0)
[17179573.692000] (blinking cursor)</code>

Any ideas what this means?

---

### Post by soonerborn on 2007-02-08
Hey I am new too.  I am having some install problems also but not similar to yours.  However after reading hundreds of install problem threads I see plenty about booting with no apic lapic for kernel panics.  I would search this forum for those and try various suggestions found there.

---

### Post by wislon on 2007-02-09
I had exactly this problem when I tried booting the Edgy live cd. Put "acpi=force" on your boot line in grub (hit 'e' when the menu comes up, drop down one line to where it shows where the root is situated, and there's all the parameters like 'quiet', 'splash' whatever. Go to the end of the line, hit space bar and put in 'acpi=force' at the end (no quotes obviously). Press Enter, press 'b' to boot, and you should be good to go (give it a few seconds). 

Note that this setting is NOT persistent. To make it so, edit your /boot/grub/menu.lst to make it persistent (you can add it to your default boot options to force it in there every time there's a kernel upgrade too).

Hope that helps, coz it worked for me! I couldn't do ANYTHING with Edgy (and I really wanted to upgrade) until I put this in.

wislon.

---

### Post by dizzylizard on 2007-02-14
Thanks, Wislon...I'll give it a shot...I'm using the Dapper live CD, but it may help...oh, and it may help everyone to know that this box is completely unbooted so far...I haven't been able to get to an installation point, yet.  Checked a couple other threads, and ran a memory test overnight...it did 37 passes with no errors...still no boot from the cd...  I can get into the bios, and the diagnostics there all look good.  I'll try the acpi=force thing and report back!

---

### Post by cbhargava on 2007-02-14
On the same hardware (ecs mobo, etc) I have installed 6.06 LTS Server without any problems. Haven't tried the desktop version though.

---

### Post by geneglover on 2007-02-22
Also bought the ECS P4M800PRO-M with a Pentium with anticipation that this was going to make a great Linux box.  Could not get Dapper or Edgy to load. Most threads pointed to a problem that indicated that there was a problem with this motherboard running the latest kernals.

Tried Suse 10 with limited success...loaded, but would not access sound card. Also ran really slow!

Corrected with two problems:

1. In the bios, shared memory was increased with from 32 to 64 Megs. This corrected the the speed problem.

2. Bios erases the on-board Ethernet connection when the first drivers are loaded...stupid, but can be corrected with a bios upgrade.  I simply shoved in a spare Ethernet card without a bios upgrade after reconfiguration, I had Internet access and upgraded Suse.

3. On a whim, I tried the Ubuntu live disc again and, to my surprise, it loaded with no problems.  Now the system runs fast, like I originally thought it would, and I didn;t have to throw this MB away.:)

---

### Post by dizzylizard on 2007-02-26
sorry it's been a while folks...the laptop I was using to check e-mail died...it's been a banner month for electronics here...catch up real quicklike...the acpi=force tag did nothing when I tried it, but thanks anyway, wislon...

Geneglover- could you possibly post a more detailed description of what you did to fix this problem?  It sounds like you've had the closest experience to mine, and if you got the ECS mobo to work, I'd love to know how!

right now I'm stuck with a winblows box for e-mail, waiting on new Dapper disks to come in the mail...anyone know how to get Edgy CD's snail-mailed?

---

