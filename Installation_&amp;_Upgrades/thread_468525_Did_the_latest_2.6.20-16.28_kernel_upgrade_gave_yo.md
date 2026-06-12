---
title: "Did the latest 2.6.20-16.28 kernel upgrade gave you problems?"
date: 2007-06-08
forum: Installation &amp; Upgrades
---

### Post by araz on 2007-06-08
Hello,

Did you had problems with the latest kernel update??

What happened?

---

### Post by syväpaahto on 2007-06-09
I don't know if the problem is from the kernel, but It came with the same update round.

After the update I no longer can see optical drives in nautilus nor does mounting create CD/DVD-icons on the desktop. Automount and unmount from terminal still work. P.S Beryl installed.

---

### Post by amatriain on 2007-06-09
Actually my system is not booting from latest kernel. Had to go back to .15 to boot. Problem seems to be related to nvidia drivers, but I have reinstalled them from repositories and it's still not working with latest kernel...

---

### Post by Error1312 on 2007-06-09
The X server doesn't start anymore :( It's probably related to NVIDIA drivers.

Edit: I reïnstalled the NVIDIA drivers and everything seems to work now.

---

### Post by cro on 2007-06-09
I answered this poll after being awake for too short a time: I voted 'no' when I should have voted 'yes'. Installing 2.6.20-16.28 left me without working wireless (association times out, although I can see access points). To boot I have to use 2.6.20-15.x

Trying .29 now.

---

### Post by ART_Adventures on 2007-06-09
Mine said it failed to StartX, and took me into the blue screen diagnostic menu thingy-ma-bob. I don't really what to do there. Can anybody help?

---

### Post by aks44 on 2007-06-09
2.6.20-16.28 didn't give me problems (at least, not new ones !) but solved a bug that 2.6.20-15 had when recognizing my cd/dvd drives.

---

### Post by latecomer on 2007-06-09
no problems with .28
no problems with .29 either

hp pavilion laptop, intel graphics

---

### Post by southernman on 2007-06-09
> **ART_Adventures said:**
> Mine said it failed to StartX, and took me into the blue screen diagnostic menu thingy-ma-bob. I don't really what to do there. Can anybody help?

When it drops you to a console, do this:

```
sudo dpkg-reconfigure xserver-xorg
```
Press enter then enter your password.

In the process, if you aren't sure of anything it ask you about, just accept the defaults. It'll all be gravy from that point.

Happy consoling.

---

### Post by hollows2 on 2007-06-09
Yes - my samsung cdrw/dvd SM-332B player is no longer recognised. This had stopped working when I initially upgraded to Feisty but had been fixed with 2.6.20-15. It looks like I'll have to keep using 2.6.20-15 if i want to burn any cds or listen to music from my cd collection.

Steve :(

---

### Post by AsAbr on 2007-06-09
Hi, 

I had the same problem :( I don't speak english, the portuguese forum is off, so if I wrote anything wrong, sorry!:D I want to reinstall the nvidia driver, but, how can I do it? I'm new in a linux and ubuntu, 2 months. I tried the command: sudo apt-get install nvidia, but doesn't work.

AsAbr

---

### Post by understracker on 2007-06-09
I use the official Nvidia-drivers. The upgrade was successful for me and the kernel-module for Nvidia installed   successfully as well. No problems here! Thanks! :D

```
chris@regulator:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
        Subsystem: Giga-byte Technology GA-8IPE1000 Pro2 motherboard (865PE)
        Flags: bus master, fast devsel, latency 0
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, fast devsel, latency 64
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        Memory behind bridge: f8000000-faffffff
        Prefetchable memory behind bridge: e0000000-efffffff

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology GA-8IPE1000/8KNXP motherboard
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at bc00 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology GA-8IPE1000 Pro2 motherboard (865PE)
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at b000 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology GA-8IPE1000 Pro2 motherboard (865PE)
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at b400 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Giga-byte Technology GA-8IPE1000 Pro2 motherboard (865PE)
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at b800 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Giga-byte Technology GA-8IPE1000 Pro2 motherboard (865PE)
        Flags: bus master, medium devsel, latency 0, IRQ 20
        Memory at fd000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=32
        I/O behind bridge: 0000a000-0000afff
        Memory behind bridge: fb000000-fcffffff
        Prefetchable memory behind bridge: 88000000-880fffff

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Giga-byte Technology GA-8IPE1000 Pro2 motherboard (865PE)
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at f000 [size=16]
        Memory at 88100000 (32-bit, non-prefetchable) [size=1K]

00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02) (prog-if 8f [Master SecP SecO PriP PriO])
        Subsystem: Giga-byte Technology GA-8IPE1000 Pro2 motherboard (865PE)
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 16
        I/O ports at c000 [size=8]
        I/O ports at c400 [size=4]
        I/O ports at c800 [size=8]
        I/O ports at cc00 [size=4]
        I/O ports at d000 [size=16]

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
        Subsystem: Giga-byte Technology GA-8IPE1000 Pro2 motherboard (865PE)
        Flags: medium devsel, IRQ 9
        I/O ports at 1400 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Giga-byte Technology GA-8IPE1000/8KNXP motherboard
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at d800 [size=256]
        I/O ports at dc00 [size=64]
        Memory at fd001000 (32-bit, non-prefetchable) [size=512]
        Memory at fd002000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600/GeForce 6600 GT] (rev a2) (prog-if 00 [VGA])
        Subsystem: ASUSTeK Computer Inc. N6600GT TD 128M AGP
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 17
        Memory at f8000000 (32-bit, non-prefetchable) [size=16M]
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Memory at f9000000 (32-bit, non-prefetchable) [size=16M]
        [virtual] Expansion ROM at fa000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:09.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
        Subsystem: Giga-byte Technology GA-8I915ME-G Mainboard
        Flags: bus master, 66MHz, medium devsel, latency 64, IRQ 19
        I/O ports at a000 [size=256]
        Memory at fc000000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 88000000 [disabled] [size=64K]
        Capabilities: <access denied>

chris@regulator:~$ 

```

---

### Post by AsAbr on 2007-06-09
> **understracker said:**
> I use the official Nvidia-drivers. The upgrade was successful for me and the kernel-module for Nvidia installed   successfully as well. No problems here! Thanks! :D
(...)


Ok, but I don't know how to install a nvidia card driver from a terminal console yet :( I downloaded a drive from Nvidia's site, the version NVIDIA-Linux-x86-100.14.09-pkg1.run. My question: Need I, or not, uninstall a old drive before install a new drive? And, how can I do it? Can I put a live CD and copy the drive to my home directory and install, or I really need to install in a console mode?

Thanks,

AsAbr

---

### Post by csisgro on 2007-06-09
Just did the .29 upgrade. still no wireless and still messed up sound. only right speaker working and alsamixer gives errors.

Tried manually starting wireless with "modprobe ath_pci" and get symbol errors and stuff and module refuses to load.

Also see a message at the beginning of boot messages about kernel modules not configured.

---

### Post by understracker on 2007-06-09
> **AsAbr said:**
> Ok, but I don't know how to install a nvidia card driver from a terminal console yet :( I downloaded a drive from Nvidia's site, the version NVIDIA-Linux-x86-100.14.09-pkg1.run. My question: Need I, or not, uninstall a old drive before install a new drive? And, how can I do it? Can I put a live CD and copy the drive to my home directory and install, or I really need to install in a console mode?

Thanks,

AsAbr

Look [here]("http://ubuntuforums.org/showthread.php?t=263851") STEP 2: Install nvidia drivers -> Option2. It works in feisty as well. Just do not install gcc-3.4.

---

### Post by AsAbr on 2007-06-09
understracker, thank you for your consideration,

in my lunch I installed the drive and reconfigured a xserver, it's running! but, the system is crashed. Beryl doesn't run and synaptic to. I'm in my job. When arrive in my home I'll send what erros are indicated. 

thank you,

AsAbr

---

### Post by H4rm0ny on 2007-06-09
Yes. As per usual my Wacom Volito2 graphics tablet became unrecognised. But then that happens *every* kernal update. I'm quite used to the reinstallation procedure by now.

---

### Post by NeoLithium on 2007-06-09
I'm happy to report that everything went perfect. Though I don't have any fancy video card driver requirement since I'm on my laptop.  Guess I'm just lucky until I get my desktop.  However I did notice that the speed went up a bit more from the last kernel I was using; though that's not a problem, that's a good thing.

---

### Post by markoloka on 2007-06-09
Tiny problem... won't boot (hangs in beginning of booting). Haven't checked yet without quiet so i have no idea why it stops. 
Kernel 12 is still only one that boots.

---

### Post by kelvin spratt on 2007-06-09
no problems here as usual

---

### Post by DarkN00b on 2007-06-09
No problems here **and** the phantom cd drive I got after the last update disappeared.

---

### Post by southernman on 2007-06-09
No problems here, either.

---

### Post by deadlikeoscar on 2007-06-09
Both -16 updates have edited my fstab drives from hdx to sdx. Had to change it but other than that it has been okay.

---

### Post by Cris70 on 2007-06-09
Yes! After yesterday's update I lost sound :-(
My MoBo has nVidia chipset.

Here is sound device:

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)

Please help!

Thank you
Bye

Cris

---

### Post by Portable_Jim on 2007-06-09
Not sure where the ".28" comes from, but I have had problems that came up in GRUB as "2.6.20-16-386". I lost my network connection, and had to reconfigure my screen (resolution too small for my linking).

---

### Post by southernman on 2007-06-09
> **Cris70 said:**
> Yes! After yesterday's update I lost sound :-(
My MoBo has nVidia chipset.

Here is sound device:

00:05.0 Audio device: nVidia Corporation MCP61 High Definition Audio (rev a2)

Please help!

Thank you
Bye

Cris

Cris, not a hugh problem to fix. Just do this:

Go to System > Preferences > Sound

In the dialogue box that opens you can choose the driver of your choice. For instance, in mine I use the "Nvidia nForce 2" the only thing I am not sure that works properly (cause I don't use it) is Audio Conferencing - sound capture. Once you change the settings click the "Test" button to be sure it's working.

If your happy with it, just close the box and enjoy your sound once again.

Happy Listening! ;)

---

### Post by AhuraMazda on 2007-06-09
Hi, I am a linux noob!! After the kernel upgrade to 29 I can no longer access the wireless network. The network shows up just fine but then nothing.... any help (at least where to start from). Thanks in advance and cheers

AM

Toshiba Sat 2435
Ubuntu 7.04

---

### Post by Cris70 on 2007-06-09
> **southernman said:**
> Cris, not a hugh problem to fix. Just do this:

Go to System > Preferences > Sound

In the dialogue box that opens you can choose the driver of your choice. For instance, in mine I use the "Nvidia nForce 2" the only thing I am not sure that works properly (cause I don't use it) is Audio Conferencing - sound capture. Once you change the settings click the "Test" button to be sure it's working.

If your happy with it, just close the box and enjoy your sound once again.

Happy Listening! ;)

Southernman,
thank you for your reply.

Under System -> Preferences -> Sound I have the following choices:
- Autodetect (used this till now)
- ALC883 Analog
- ALSA
- ESD
- OSS

Now the only one that is working when I press the "test" button is OSS. Previously I have been using the "autodetect" option and I was under the impression that ALSA was in charge.
Unfortunately even if OSS works with the "Test" button, I'm still without sound :-(
Should I have an "nVidia" entry also?

Thank you!
Bye

Cris

---

### Post by southernman on 2007-06-09
Your welcome, Cris. 

hmm - let's see if you can find a restricted driver for your motherboard chipset perhaps. Normally the ALSA driver will work on most platforms (my understanding at least), but I digress.

Have you checked in:

System > Administration > Restricted Drivers Manager

yet?

If I recall correctly, I installed the RD for my chipset on an ASUS A7N8X VM/400, though looking at it just now, all I see there is the driver for my ATI card. 

> Should I have an "nVidia" entry also?I would think so Cris. It appears from what you did post, that your board has an onboard audio.

*shrugs*

---

### Post by Nanoboy on 2007-06-09
I'm a newbie.  I have an update manager and i downloaded some updates last night without looking what it was actually updating.  My "uname -a" reads:
```

Linux hedgehog 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

```

I'm not sure if I'm using 2.6.20-16.28.  But after the update last night and reboot, the fsck appeared to be not detecting my Windows partition, or my /home directory which is on a separate partition.
It reads the following:
```
fsck 1.40-WIP (14-Nov-2006)
dosfsck 2.11, 12 Mar 2005, FAT32, LFN
/dev/sda1: 88 files, 3627/36051 clusters
/dev/sda3: clean, 7973/7094272 files, 720233/14161297 blocks
fsck.ext3: No such file or directory while trying to open /dev/hda3
/dev/hda3:
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

```

Then I typped in "reboot", which then showed the log in screen, and let me log into a clean desktop environment, i.e. no data from my /home.

I'm starting to think this MAY be due to the kernel update, or I don't know what caused it?

---

### Post by Nanoboy on 2007-06-10
Just solved my problem by using UUID instead of /dev/hda3 to specify the location of my /home directory.  Just one simple line to change.

See post:
[http://ubuntuforums.org/showthread.php?p=2815294#post2815294](http://ubuntuforums.org/showthread.php?p=2815294#post2815294)

It was a kernel upgrade problem.

---

### Post by _simon_ on 2007-06-10
Just the usual reinstall of the NVIDIA drivers which I don't see as being a problem, so I voted No

---

### Post by dart1007 on 2007-06-10
Sony Vaio Desktop

no problems on .28 and .29

---

### Post by jjbean on 2007-06-10
This one went really well for me. No problems with my Nvidia driver(1st time that happened with a kernal update). I am very happy, as the update magically fixed my wine and flash sound problems.

---

### Post by Cris70 on 2007-06-11
Southernman,
I checked my restricted drivers but I only have an entry for the graphics card.
My modo has indeed onboard audio, but it  was handled by ALSA (I believe) until the last upgrade.
Now I don't get sound even if I choose the old kernel in GRUB.
I tried reinstalling the restricted nVidia drivers with no success (that is: it went smoothly but I still don't have sound).

---

### Post by Bohlio on 2007-06-11
I had sound problems, Which i got fixed, Two ghost CD drives, Which i also got fixed, And an inoperable DVD+-RW drive, Which i havent got fixed yet.

---

### Post by IntuitiveNipple on 2007-06-11
Against my better judgement, and only because I need the latest kernel to do some kernel driver builds, I allowed the latest Feisty 2.6.20-16 update on a Feisty 32-bit installation.

After reboot the PC hangs just after init-bottom with:
```

Begin: Running /scripts/local-bottom ...
Done.
Done.
Begin: Running /scripts/init-bottom ...
Done.
request_module: runaway loop modprobe binfmt-464c
request_module: runaway loop modprobe binfmt-464c
request_module: runaway loop modprobe binfmt-464c
request_module: runaway loop modprobe binfmt-464c

```
What is worse is the same problem happens when I try to boot to the original 2.6.20-15 32-bit kernel. 

The alternative *64-bit kernel installation* boots and starts Gnome, but as soon as I log-in, after the welcome sound, the X display goes totally white with an I-bar mouse cursor in the center and a standard pointer elsewhere, as if the log-in username/password prompt is waiting. The Compiz cube is there and rotates but every cube face is totally white!

I can switch out to a terminal and through that restart gdm but the same thing happens.

It seems the problem is to do with the update to GRUB's /boot/grub/menu.lst. I had the boot partitions set to /dev/sdaX style and the update replaced these with UUIDs which, it seems, now point to the 64-bit partition for the 32-bit kernel boot lines too.

To boot I hit Escape to get to the GRUB menu, then manually edited the boot line, removing the root=UUID and replacing with root=/dev/sda6.

I have the disk partitioned thus:
```
sda1 Sony Windows Recovery
sda2 Windows Vista
sda3 Linux Swap
sda4 Extended
->sda5 /boot
->sda6 / (for 32-bit kernel)
->sda7 / (for 64-bit kernel)
->sda8 /home (for both kernels)
```
I've just checked by doing ls -l /dev/disk/by-uuid/ and I can see that the GRUB update assigned the UUID of /dev/sda7 (the 64-bit kernel) to **all** the kernel entries!

Obviously the update script blindly ignores the previous menu.lst and ought to be corrected.

---

### Post by grantmasterflash on 2007-06-12
I know this is an Ubuntu forum but I had the same problem with CentOS5... I changed the root= line to point to /dev/sda1 instead of a label and it booted. Weird. Anyway thanks.

---

### Post by bananabob on 2007-06-13
Some time when I boot I get this message:
> Log of fsck -C -R -A -a 
Thu Jun 14 10:17:08 2007

fsck 1.40-WIP (14-Nov-2006)
fsck.ext3: No such file or directory while trying to open /dev/Volume0/lvol0
/dev/Volume0/lvol0: 
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

fsck died with exit status 8

Thu Jun 14 10:17:08 2007
----------------

When I > shutdown -r now the system goes to a logon screen. Then I reboot the system and I am in all good and working.

> uname -a 
Linux thorium 2.6.20-16-generic #2 SMP Thu Jun 7 20:19:32 UTC 2007 i686 GNU/Linux

So can I change the kernel, is there a bug fix what is happening?

---

### Post by Stormspireiv on 2007-06-24
For me, the wireless card on my laptop is no longer recognized after the update.

---

