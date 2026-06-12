---
title: "Ongoing issues with &quot;Unable to find a medium containing a live file system&quot;"
date: 2011-11-02
forum: Installation &amp; Upgrades
---

### Post by MechaHeretic on 2011-11-02
I realize this issue has already been beaten into the ground, but i still have yet to find a proper solution to the issue.

**_Problem:**_
Downloaded 11.10 64x ISO from ubuntu
Created Bootable USB stick (instructions directly from Ubuntu Installation Guide)
Computer boots to the Ubuntu splash screen, select "Run Ubuntu from USB stick" (trying to test it before installing it)
Lots of white text on black background.
Ubuntu logo with 6 dots below it lighting up in sequence for about 10 seconds
Back to black screen with white text
Pauses with:
     Quote:
                                                 BusyBox v1.13.3 (Ubuntu 1:1.13.3-ubuntu11) built in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs) Unable to find a medium containing a live file system                                 
(numbers in first line approximate, don't remember exactly, but it's the same ones everytime)

**_So far i've tried:_**
MD5SUM check on iso = Fine
creating a CDROM copy of Ubuntu = same issue
Swapping USB ports (all 6 on my machine) = same issue (5-year old box = no usb3)
Changing boot priorities in BIOS just in case = same issue
Re-creating USB boot stick = same issue
Disable AHCI in bios = American Megatrends BIOS = no AHCI support in the first place.

_**My computer:**_

Gateway DX4720-03 x64-based PC
Pentium Dual-Core E5200 @ 2500GHz
BIOS: American Megatrends a7399NG2.202
SMBIOS 2.5
4gb RAM
600GB SATA HDD
nVidia GeForce 7350 LE

Again, i apologize for posting with the same problem, but every thread  i've scoured seems to end with everyone being happy about switching USB  ports or disabling AHCI, neither of which have worked for me :sad:

This doesn't work with my 16gb Kingston nor 2gb PNY usb stick.....

Also, if it's significant, with the Universal USB installer and 64x  11.10 release, after the "unable to find a medium..." message it would  start trying to "mount" (i think is the word) USB devices 4, 5, 6,  and  7, but returning an error message each time and freezing after 7.....

What the bleep is going on?

_Alright, here's what it's saying after the freeze:_

                                                      > 3.345234 (random) nouveau 0000:02:00.0: Output DVI-I-1 is running on CRTC 0 using Output A
3.345234 [drm] nouveau 0000:02:00.0: 0xC5E6: Parsing digital output script table
3.345234 [drm] nouveau 0000:02:00.0: Setting dpms mode 0 non tmds encoder (output 1)
4.050026 [drm] nouveau 0000:02:00.0: Output DVI-I-1 is running on CRTC 0 using output A
4.050026 [drm] nouveau 0000:02:00.0: GPU lockup - switching to software fbcon
4.050026 Console: switching to colour frame buffer device 180x56

BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) Unable to find a medium containing a live file system

70.640021 usb 1-7: device not accepting address 7, error -110
70.760019 usb 1-7: new high speed USB device using ehci-hcd and address 8
70.640021 usb 1-7: device not accepting address 8, error -110
70.760019 usb 1-7: new high speed USB device using ehci-hcd and address 9
70.640021 usb 1-7: device not accepting address 9, error -110
70.760019 usb 1-7: new high speed USB device using ehci-hcd and address 10
107.451261 usb 1-7: device not accepting address 10, error -110
107.451324 hub 1-0:1.0: unable to enumerate USB device on port Except for all those first numbers in the last couple of lines,  that's a letter for letter reproduction of the error message i've been  getting.  This is taken from the 10.4 64x release off of the Universal  USB Installer on my 16gb Kingston.

I've also tried taking out my nVidia GeForce card and running the computer straight through the default VGA port, since i know nvidia and linux haven't really gotten along well in the past, but the same issue pops up again and again.

_**Recap:**_
Right/Legit ISO
Multiple USB Sticks
Multiple USB Slots (no USB 3.0)
Multiple Ubuntu Distros (11.10, 11.04, 10.04, all in the 86x and 64-bit varieties)
CD-ROM copy of 11.10 64x didn't work either, same error
Two different USB installers (Unetboot and Universal USB Installer)
No "Disable AHCI" option in BIOS
Removal of nVidia card didn't help

Can anyone PLEASE help me? I really want to be able to run Ubuntu.  If there's another distro out there that could work, i'd take that as well.  I'm just looking for something that's newbie friendly, as the only experience i have with linux comes from a couple of years in college working with RedHat.....

---

### Post by Mark Phelps on 2011-11-02
> **MechaHeretic said:**
> If there's another distro out there that could work, i'd take that as well.  I'm just looking for something that's newbie friendly, as the only experience i have with linux comes from a couple of years in college working with RedHat.....

Regarding other distros ...

I've had similar experiences in the past, especially with laptops, where Ubuntu just won't work, but other distros either work OK or work very well.

That's the really great thing about Linux distros -- all it costs you is some time and some optical media, to try out other versions.

Some other that I've tried:
- Mint
- OpenSuse
- PC Linux OS

You can get current versions of these, as well as reviews of those versions, by going to distrowatch.com.

---

### Post by MechaHeretic on 2011-11-03
Thanks for the reply.

I'll check out Mint and OpenSuse, hopefully they will be a little friendlier to run live or install.

---

