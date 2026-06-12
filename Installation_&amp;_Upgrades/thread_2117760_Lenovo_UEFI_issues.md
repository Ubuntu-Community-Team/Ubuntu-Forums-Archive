---
title: "Lenovo UEFI issues"
date: 2013-02-18
forum: Installation &amp; Upgrades
---

### Post by tanstaaflwdm on 2013-02-18
Well, I've managed to brick my new laptop and am hoping someone can help me.

Brand new Lenovo Ideapad. Decided I couldn't handle Windows 8 and so try to set up a dual boot to 12.10, 64-bit.

Installed as a separate partition and everything seemed to go well, but when I rebooted I got "Image failed to verify with *ACCESS DENIED*" From there it proceeded to boot into Windows.

OK, so I ran boot-repair. Boot-repair says it ran successfully but now nothing works. I get the grub menu but selecting ubuntu gives me a blank screen and nothing else and selecting anything else gives me an invalid image error. So right now I have nothing.

The url it gave me is [http://paste.ubuntu.com/1679821](http://paste.ubuntu.com/1679821)

Please tell me I haven't given myself an expensive doorstop. Any suggestions?

---

### Post by oldfred on 2013-02-19
Welcome to the forums.

Moved to your own thread as in the mega-tread it gets confusing on who is getting what instructions.

Did you turn off secure boot and fast boot in Windows first. And can you still get into UEFI/BIOS?

You may be having video issue or other boot parameter is required with Ubuntu. At grub menu press e and replace quiet splash with nomodeset. Screens shown:
       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
Or from Boot-Repair:
       Boot-Repair --> Advanced options --> GRUB options tab --> tick "Add kernel option: nomodeset" --> Apply
    
It looks like Boot-Repair added the correct entries to boot. This is the correct one even though it says recovery.
"Windows UEFI recovery bootmgfw.efi"

These are incorrect as grub still has a bug.
'Windows 8 (loader) (on /dev/sda5)'

---

### Post by tanstaaflwdm on 2013-02-19
Thanks for the move. Was just following the link from the boot-repair page.

> **oldfred said:**
> Did you turn off secure boot and fast boot in Windows first. And can you still get into UEFI/BIOS?
Uh-oh. Might have shot myself in the foot then. I thought the secure boot/fast boot options were in the BIOS, not in Windows. I didn't see them so didn't change anything.

Since it's a brand-new machine if I could get to the recovery partition I would just reset the thing and start over; there's no data to lose. But I can't seem to get it to boot either. On this Lenovo there is a smaller button next to the power button that is used to access the BIOS/recovery partition, but boot-repair has apparently grabbed it too.

---

### Post by oldfred on 2013-02-19
Secure Boot is definitely in UEFI/BIOS. 
But fast boot may be a Windows setting or in UEFI. It seems that it bypasses UEFI booting like with BIOS we had the BIOS loading before grub. But it may be a Windows setting that changes UEFI? 
And on some systems then you cannot get into UEFI at all unless Windows is working. Grub has added a new entry to get into UEFI, it should be the last on the grub menu.

Some have totally reset system by reinstalling UEFI/BIOS, but I do not know how to do that unless you can get into UEFI?
And some systems with UEFI have just totally reset (the key you are talking about?) and then it boots Windows again. But this varies by Vendor as each has implemented UEFI differently. 

       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

    
Two that have worked: lenovo may have similar UEFI but only minor differences for each version?
       Lenovo Z580 laptop
[http://ubuntuforums.org/showthread.php?t=2112271](http://ubuntuforums.org/showthread.php?t=2112271)
Lenovo Ideapad Y500 LiveUSB Problem
[http://ubuntuforums.org/showthread.php?t=2095063](http://ubuntuforums.org/showthread.php?t=2095063)


But some have reported issues.
       
 The current state of UEFI and Linux = Feb 1, 2013 - Matthew Garrett
Samsung, Lenovo & Toshiba UEFI issues
[http://mjg59.dreamwidth.org/22028.html](http://mjg59.dreamwidth.org/22028.html)
Matthew Garrett's Blog
[http://mjg59.dreamwidth.org/](http://mjg59.dreamwidth.org/)

---

### Post by tanstaaflwdm on 2013-02-19
OK, I have the z580 too but I didn't see an option to turn off secure boot in the bios. I'll check again.

---

### Post by tanstaaflwdm on 2013-02-19
OK, I haven't made too much progress, but my system is partially useful.

Normally I get the Grub menu. Selecting "ubuntu" gives me a blank, grey screen and selecting anything else gives me a variety of errors.

But if I power off and on a few times it will eventually let me into ubuntu. At this point it seems to work fine until I shut down again. Then I have to try a few more times before it will work again.

The power cycle sounds like something is getting caught in cache somewhere or something, if that makes any sense at all, but I can't imagine what it could be. Or maybe hardware related. I'm not sure.

I'm going to avoid doing anything else to the system right at the moment. The reason this became an issue is that I'm in a training class the next few days (mongo db), needed the laptop for it, and my old laptop was a 6 year old Celeron with a bad power switch. So if I can get through the class I'll have time to sort things out.

Our company is moving towards Linux in general and are trying to get us developers migrated over, hence the class, so I'm not exactly bleeding edge when it comes to setting this stuff up. I did perl development on hp-ux for a while, but apparently it's easier to use a server that someone else set up than to do it myself.

I'm tempted just to blow Windows completely away and do a full ubuntu install but I'm afraid it may make this worse at this point. Cthulhu knows that what little I saw of Windows 8 before everything went west did nothing to make me want to use it, but I guess I still need my security blanket. :)

Anyway, thanks for the help so far. It's given me something to investigate at least. I'll be back in a few days probably asking a lot of dumb questions.

---

### Post by skwalas on 2013-02-19
Can you get to diagnostics by pressing F1 upon immediate startup, or boot menu by pressing F12?  Both might allow you get get back to the UEFI settings.

I have a new Lenovo T430s, but I would bet the general setup (keys for getting to UEFI) are the same.

But maybe I'm misreading, and your issue is a little deeper than that...

---

### Post by oldfred on 2013-02-20
I would not un-install Windows 8. 

There are some UEFI systems that just do not work without Windows being able to do some things. Not sure about your system but better to be safe for now. Its a lot of changes with new UEFI designs, Windows requirements and the usual Linux developers having to find the work arounds to bugs by others (and fixing their own).

---

### Post by tanstaaflwdm on 2013-02-20
Thanks for the warning. I'll hold off nuking from orbit until a final resort.

I did find what seems to be the cause of my having to boot a few times to get anything to load. This is from the Lenovo support forums

> To get windows to boot fast, it takes some shortcuts and bypasses the BIOS. Turn off your computer by holding the power button (a dry shutdown). If when you turn on the computer, you still don't see the bios option, redo the dry shutdown. After the 2nd or 3rd shutdown, windows will let go of the bios.

[Full support thread here](http://forums.lenovo.com/t5/IdeaPad-Y-U-V-Z-and-P-series/z580-can-t-access-bios-setup-or-boot-menu-after-changing-to/td-p/812737/page/2)

This seems to be what I'm seeing. I failed to disable that because I thought it was a bios setting, not a Windows setting. My mistake there. First thing I'm fixing when I manage to get back into Windows again.

OTOH, it's working well in my class. I'll pass on that the version of mongodb that ubuntu installs through apt-get is an out of date version. I had to manually add a repository at 10gen and install their package to get an up-to-date version.

---

### Post by tanstaaflwdm on 2013-02-21
Progress! Some good, some frustrating, but progress!

First, I've managed to get back into Windows again.

Apparently the button next to the power button isn't the only way to get into the bios. With the laptop off, if you hold down the F2 key *then* push the power button the laptop goes straight into the bios.

But, if you hold down the F12 key and power on, you go into a "boot menu". One of the options here was the hard drive (ubuntu was another) and selecting the hard drive booted into Windows.

So I can dual-boot as long as I power on while holding the F12 key.

I'm not quite ready to call this solved though as this is more of a workaround than a fix. Booting normally into grub is still a mess.

Here's the ongoing problem. I can't access the part of the bios that lets me turn off secure boot. Here's what the screen looks like.

[https://www.sugarsync.com/pf/D8551579_760_898129724](https://www.sugarsync.com/pf/D8551579_760_898129724)

I can only select the first two items on this screen. The other items are grayed out and inaccessible. Unfortunately, that's the secure boot settings.

So, if I can figure out how to access those I may be able to run boot-fix and get grub working correctly.

But things are looking up. I'll keep everyone informed as to what I find.

---

### Post by tanstaaflwdm on 2013-02-22
Two steps forward, one step back.

OK, more progress. I've managed to turn off secure boot. That bios screen that I couldn't access most of the options on? Turns out that you need to create an admin password first. Once you have done that the grayed out options become available and I was able to turn off secure boot. So yeah, you have to *add* security to *remove* security.

Things still aren't working quite right. I can't get into Windows from the grub menu though it will boot ubuntu. Sometimes. Usually I have to power on or off two or three times before it will finally "take".

I can consistently get into Windows by using F12 to reach a boot menu and selecting the hard drive. Selecting ubuntu there sends me to grub, which works as above.

Windows fast boot is turned off as well as I can determine so I don't know what the problem with the ubuntu boot is.

I'm going to try to run boot-repair again. We'll see how this goes.

---

### Post by tanstaaflwdm on 2013-02-23
OK, a few more passes of boot-repair and I may or may not be working. Here's where I am.

I finally can boot into where I need. My grub menu now looks like this.

Ubuntu
Advanced options for Ubuntu
Windows UEFI recovery bkpbootmgfw.efi
Windows Boot UEFI recovery
Windows UEFI recovery LvsBootmgr.efi
Windows Boot UEFI recovery bkpbootx64.efi
Windows 8 (loader) (on /dev/sda5)
System setup

The first two take me to ubuntu... sometimes
The third and forth both go to Windows
The fifth and sixth both go to Windows recovery
The seventh gives an error

Here's my final boot-repair report
[http://paste.ubuntu.com/5560283](http://paste.ubuntu.com/5560283)

Now my problem is with ubuntu. I can get into it, but usually only after powering my machine on and off several times. Usually it "hangs" during startup.

If I disable quiet splash in the grub options I can sometimes see things loading, except it tends to stop randomly at some point like this

[https://www.sugarsync.com/pf/D8551579_760_899959313](https://www.sugarsync.com/pf/D8551579_760_899959313)

It doesn't always stop in the same place. Other times it never displays anything at all. Usually it will let me in on the second or third try, but at least once today it took over a dozen tries to get in.

I thought maybe something had got corrupted in my installation and did a full reinstall. Still having the same problem.

I've tried both with and without nomodeset.

I thought that maybe ubuntu just doesn't like this laptop but running from a live cd has always worked (and believe me, I've been using that cd a lot over the last few days trying variations on boot-repair).

When I get in it works fine. It just takes multiple tries to get it to boot.

The actual fix I did (and I should have done this *before* installation) was:

1) Disable Windows 8 Fast Boot. To do this, go to the Control Panel (in Windows 8 hold X while hitting the Windows key and select "Control Panel") and select Power Options -> Choose What the power buttons do. Then select the link that says "Change settings that are currently unavailable". This will give you access to the checkbox "Turn on fast startup (recommended)". Turn it off.

2) Then disable secure boot in the bios. You get to the bios on the Lenovo Z580 by holding down F2 while powering on. The secure boot option is inaccessible until you create an admin password. Then you can turn secure boot off.

At this point boot repair worked.

Now, I'm still having the problem with ubuntu taking multiple tries to boot but at least I can get to everything. Usually. So, should I mark this thread "solved" and start a new one with my having to boot multiple times problem, or keep researching it here?

---

### Post by oldfred on 2013-02-23
If you have Log File Viewer use it to look at dmesg to see if the log file is recording boot issues. 

If not look a log files (there are many) I usually look at dmesg first.

       /var/log/dmesg

[https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

---

### Post by tanstaaflwdm on 2013-02-24
I looked at dmesg and dmesg.0. Both seem to be from complete boots so I'm not seeing anything really missing. The only things I saw that looked suspicious are:

[   18.626755] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[   18.626759] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   18.626762] ACPI Warning: 0x0000000000000500-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20120320/utaddress-251)
[   18.626766] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver

And this seemingly fairly long delay here
[    2.740681] usb 1-1.4: Product: BCM20702A0
[    2.740684] usb 1-1.4: Manufacturer: Broadcom Corp
[    2.740687] usb 1-1.4: SerialNumber: 74E543C78AFE
[    4.745442] EXT4-fs (sda8): INFO: recovery required on readonly filesystem
[    4.745445] EXT4-fs (sda8): write access will be enabled during recovery
[    7.612447] EXT4-fs (sda8): recovery complete
[    7.627039] EXT4-fs (sda8): mounted filesystem with ordered data mode. Opts: (null)
[   18.528797] Adding 6148092k swap on /dev/sda9.  Priority:-1 extents:1 across:6148092k 
[   18.532360] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.561945] udevd[370]: starting version 175
[   18.615970] mei 0000:00:16.0: setting latency timer to 64
[   18.616036] mei 0000:00:16.0: irq 43 for MSI/MSI-X

I find this spot suspicious because that mention of "Manufacturer: Broadcom Corp" is a spot in the log that I have seen it hang on a few times (like the screenshot I posted earlier)

Is there anything specific I should be looking for?

---

### Post by westie457 on 2013-02-24
According to this site [http://forums.lenovo.com/t5/T400-T500-and-newer-T-series/Mystery-device-BCM20702A0-in-Device-Manager/td-p/907261](http://forums.lenovo.com/t5/T400-T500-and-newer-T-series/Mystery-device-BCM20702A0-in-Device-Manager/td-p/907261)
> And this seemingly fairly long delay here
[ 2.740681] usb 1-1.4: Product: BCM20702A0
[ 2.740684] usb 1-1.4: Manufacturer: Broadcom Corp is a bluetooth device.

For some reason the drivers have not installed with the rest. Somehow the LiveCD/USB is picking it up.

Is there a hardware switch or button to turn off bluetooth, or an option in the bios.

Lets dig a little deeper anyway.

Boot into the Live Desktop (try mode) open a terminal and run ```
lspci -vnn

lsusb

rfkill list all

lsmod
```
Post all the output please between {code} { /code} tags by highlighting in the terminal and in a new reply click on # at the top of the message pane and pasting between the brackets.

Thank you.

---

### Post by tanstaaflwdm on 2013-02-24
Here's what I'm seeing from a live CD boot

```
ubuntu@ubuntu:~$ lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
    Subsystem: Lenovo Device [17aa:3977]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device [17aa:3902]
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04) (prog-if 30 [XHCI])
    Subsystem: Lenovo Device [17aa:3977]
    Flags: bus master, medium devsel, latency 0, IRQ 41
    Memory at f0700000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
    Subsystem: Lenovo Device [17aa:3977]
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f0715000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei
    Kernel modules: mei

00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device [17aa:3977]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f0719000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
    Subsystem: Lenovo Device [17aa:3977]
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f0710000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f0600000-f06fffff
    Prefetchable memory behind bridge: 00000000f0400000-00000000f04fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 [8086:1e14] (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f0500000-f05fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device [17aa:3977]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f0718000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge [0601]: Intel Corporation HM76 Express Chipset LPC Controller [8086:1e59] (rev 04)
    Subsystem: Lenovo Device [17aa:3977]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: lpc_ich

00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Lenovo Device [17aa:3977]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 40
    I/O ports at 3088 [size=8]
    I/O ports at 3094 [size=4]
    I/O ports at 3080 [size=8]
    I/O ports at 3090 [size=4]
    I/O ports at 3060 [size=32]
    Memory at f0717000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
    Subsystem: Lenovo Device [17aa:3977]
    Flags: medium devsel, IRQ 255
    Memory at f0714000 (64-bit, non-prefetchable) [size=256]
    I/O ports at efa0 [size=32]
    Kernel modules: i2c-i801

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Lenovo Device [17aa:3975]
    Flags: bus master, fast devsel, latency 0, IRQ 42
    I/O ports at 2000 [size=256]
    Memory at f0404000 (64-bit, prefetchable) [size=4K]
    Memory at f0400000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2200 [8086:0891] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2200 BGN [8086:4222]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f0500000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

ubuntu@ubuntu:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 5986:0295 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 004: ID 0bda:0139 Realtek Semiconductor Corp. Card reader
Bus 001 Device 005: ID 04ca:2003 Lite-On Technology Corp. 

ubuntu@ubuntu:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

ubuntu@ubuntu:~$ lsmod
Module                  Size  Used by
dm_crypt               23011  0 
snd_hda_codec_hdmi     32007  1 
arc4                   12529  2 
snd_hda_codec_realtek    77876  1 
snd_hda_intel          33491  3 
snd_hda_codec         134212  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
iwlwifi               386826  0 
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                96580  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
coretemp               13400  0 
mac80211              539908  1 iwlwifi
snd_seq_midi           13324  0 
snd_rawmidi            30512  1 snd_seq_midi
rts5139               356158  0 
uvcvideo               76749  0 
snd_seq_midi_event     14899  1 snd_seq_midi
videobuf2_core         32851  1 uvcvideo
videodev              120309  2 uvcvideo,videobuf2_core
kvm                   414070  0 
snd_seq                61521  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29425  2 snd_pcm,snd_seq
videobuf2_vmalloc      12860  1 uvcvideo
snd_seq_device         14497  3 snd_seq_midi,snd_rawmidi,snd_seq
videobuf2_memops       13368  1 videobuf2_vmalloc
snd                    78734  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bnep                   18140  2 
joydev                 17457  0 
ghash_clmulni_intel    13180  0 
psmouse                95552  0 
ideapad_laptop         18086  0 
mac_hid                13205  0 
rfcomm                 46619  0 
parport_pc             32688  0 
cryptd                 20403  1 ghash_clmulni_intel
soundcore              15047  1 snd
sparse_keymap          13890  1 ideapad_laptop
cfg80211              206566  2 iwlwifi,mac80211
ppdev                  17073  0 
snd_page_alloc         18484  2 snd_hda_intel,snd_pcm
mei                    40690  0 
bluetooth             209199  10 bnep,rfcomm
dm_multipath           22828  0 
serio_raw              13215  0 
lpc_ich                17061  0 
lp                     17759  0 
microcode              22803  0 
scsi_dh                14554  1 dm_multipath
parport                46345  3 parport_pc,ppdev,lp
squashfs               36522  1 
overlayfs              28007  1 
nls_utf8               12557  1 
isofs                  39842  1 
nls_iso8859_1          12713  0 
dm_raid45              76812  0 
xor                    17152  1 dm_raid45
dm_mirror              22028  0 
dm_region_hash         20806  1 dm_mirror
dm_log                 18529  3 dm_raid45,dm_mirror,dm_region_hash
hid_generic            12493  0 
usbhid                 46947  0 
hid                   100366  2 hid_generic,usbhid
wmi                    19070  0 
i915                  520519  3 
r8169                  61650  0 
drm_kms_helper         46784  1 i915
drm                   275528  4 i915,drm_kms_helper
i2c_algo_bit           13413  1 i915
video                  19335  1 i915

```

---

### Post by westie457 on 2013-02-25
Well this is strange. The Live Desktop does not show anything to do with Broadcom.

Could you run those same commands again please, this time from your installation.
If nothing obvious stands out we will have to dig deeper.

---

### Post by sms88 on 2013-02-25
> **tanstaaflwdm said:**
> Progress! Some good, some frustrating, but progress!

First, I've managed to get back into Windows again.

Apparently the button next to the power button isn't the only way to get into the bios. With the laptop off, if you hold down the F2 key *then* push the power button the laptop goes straight into the bios.

But, if you hold down the F12 key and power on, you go into a "boot menu". One of the options here was the hard drive (ubuntu was another) and selecting the hard drive booted into Windows.

So I can dual-boot as long as I power on while holding the F12 key.

I'm not quite ready to call this solved though as this is more of a workaround than a fix. Booting normally into grub is still a mess.

Here's the ongoing problem. I can't access the part of the bios that lets me turn off secure boot. Here's what the screen looks like.

[https://www.sugarsync.com/pf/D8551579_760_898129724](https://www.sugarsync.com/pf/D8551579_760_898129724)

I can only select the first two items on this screen. The other items are grayed out and inaccessible. Unfortunately, that's the secure boot settings.

So, if I can figure out how to access those I may be able to run boot-fix and get grub working correctly.

But things are looking up. I'll keep everyone informed as to what I find.

I just went through about four days of pain trying to get Windows 8 and 12.10 to boot, but it's on a Lenovo desktop, not a laptop.

First of all, you may want to get back to the original state of the laptop by booting into windows, creating a USB recovery key, and reinstalling, allowing it to rewrite the whole drive (I forget the exact wording of the option to totally rewrite the drive). This will likely undo the damage that Boot Repair caused. NEVER run Boot Repair on a system with Windows installed. I thought I had a bricked system as well.

On the desktop, I installed 12.10 on a separate drive (with the Windows drive temporarily disconnected) so this may not be helpful to you. Once it was installed, it didn't boot of course, but with the Windows drive disconnected I ran Boot Repair which fixed whatever the 12.10 installer had screwed up. Then I found the UUID of the Windows boot partition (using Gparted from a live USB stick) and then booted Ubuntu and manually created an entry in 40_custom (under /etc/grub.d) for Windows 8, then installed and ran Grub Customizer (for some reason I could not do the Grub update from the terminal) to update the grub.cfg file. The reason for the manual entry is that Grub's automatic OS prober did not detect the Windows 8 EFI partition; whether this is because it was on different physical drive, or because there's a problem with the OS-prober and EFI boot partitions, I don't know.

I think the bottom line is that _if_ you can get to the point where the machine powers up and the Grub bootloader comes up for only Ubuntu, then you can solve the dual boot issue by manually editing the 40_custom file by adding the following:

menuentry "Windows 8" {
insmod part_gpt
insmod fat
insmod search_fs_uuid
insmod chain
set root='(hd0,gpt3)'
search --fs-uuid --no-floppy --set=root E20F-0E2C
chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

You may need to change the 6th line to match whatever the Windows EFI boot partition is, and you definitely need to change the 7th line to match the UUID of your hard drive.

One other thing I found on the Lenovo desktop is that installing from the LiveDVD didn't work, I had to use a LiveUSB stick because the DVD drive was not a UEFI bootable device so the Ubuntu installer did a legacy installation. This was the cause of most of the pain I went through. It may be different on the laptop.

One other thing is that on the Lenovo desktop, Secure Boot is NOT enabled. If you enable it and boot you get an error message about an invalid key, though if you press enter twice the system goes ahead and boots windows.

Clearly the Ubuntu installer needs some work to play nice with Windows 8, GPT drives, UEFI, and Secure Boot. I think the big problem is that with pre-installed WIndows you don't get the OS DVD so you can't do a clean install, you must deal with the pre-installed OS and try not to break things.

---

### Post by tanstaaflwdm on 2013-02-25
OK, I got it finally. It literally took me a dozen reboots before ubuntu would start up.

```
dennis@dennis-Lenovo-Z580:~$ lspci -vnn
00:00.0 Host bridge [0600]: Intel Corporation 3rd Gen Core processor DRAM Controller [8086:0154] (rev 09)
    Subsystem: Lenovo Device [17aa:3977]
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:02.0 VGA compatible controller [0300]: Intel Corporation 3rd Gen Core processor Graphics Controller [8086:0166] (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device [17aa:3902]
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at f0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:14.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller [8086:1e31] (rev 04) (prog-if 30 [XHCI])
    Subsystem: Lenovo Device [17aa:3977]
    Flags: bus master, medium devsel, latency 0, IRQ 41
    Memory at f0700000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller [0780]: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 [8086:1e3a] (rev 04)
    Subsystem: Lenovo Device [17aa:3977]
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f0715000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei
    Kernel modules: mei

00:1a.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 [8086:1e2d] (rev 04) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device [17aa:3977]
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f0719000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device [0403]: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller [8086:1e20] (rev 04)
    Subsystem: Lenovo Device [17aa:3977]
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at f0710000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 [8086:1e10] (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 [8086:1e12] (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f0600000-f06fffff
    Prefetchable memory behind bridge: 00000000f0400000-00000000f04fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge [0604]: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 [8086:1e14] (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f0500000-f05fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller [0c03]: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 [8086:1e26] (rev 04) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device [17aa:3977]
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f0718000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge [0601]: Intel Corporation HM76 Express Chipset LPC Controller [8086:1e59] (rev 04)
    Subsystem: Lenovo Device [17aa:3977]
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: lpc_ich

00:1f.2 SATA controller [0106]: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] [8086:1e03] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Lenovo Device [17aa:3977]
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 40
    I/O ports at 3088 [size=8]
    I/O ports at 3094 [size=4]
    I/O ports at 3080 [size=8]
    I/O ports at 3090 [size=4]
    I/O ports at 3060 [size=32]
    Memory at f0717000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus [0c05]: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller [8086:1e22] (rev 04)
    Subsystem: Lenovo Device [17aa:3977]
    Flags: medium devsel, IRQ 255
    Memory at f0714000 (64-bit, non-prefetchable) [size=256]
    I/O ports at efa0 [size=32]
    Kernel modules: i2c-i801

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Lenovo Device [17aa:3975]
    Flags: bus master, fast devsel, latency 0, IRQ 42
    I/O ports at 2000 [size=256]
    Memory at f0404000 (64-bit, prefetchable) [size=4K]
    Memory at f0400000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

03:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 2200 [8086:0891] (rev c4)
    Subsystem: Intel Corporation Centrino Wireless-N 2200 BGN [8086:4222]
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at f0500000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi

dennis@dennis-Lenovo-Z580:~$ lsusb
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 5986:0295 Acer, Inc 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 045e:0745 Microsoft Corp. Nano Transceiver v1.0 for Bluetooth
Bus 001 Device 004: ID 0bda:0139 Realtek Semiconductor Corp. Card reader
Bus 001 Device 005: ID 04ca:2003 Lite-On Technology Corp. 

dennis@dennis-Lenovo-Z580:~$ rfkill list all
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

dennis@dennis-Lenovo-Z580:~$ lsmod
Module                  Size  Used by
rfcomm                 46620  12 
bnep                   18141  2 
parport_pc             32689  0 
ppdev                  17074  0 
binfmt_misc            17501  1 
nls_iso8859_1          12714  1 
snd_hda_codec_hdmi     32049  1 
snd_hda_codec_realtek    78147  1 
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
videodev              120310  2 uvcvideo,videobuf2_core
videobuf2_vmalloc      12861  1 uvcvideo
snd_hda_intel          33492  3 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
videobuf2_memops       13405  1 videobuf2_vmalloc
snd_hwdep              17699  1 snd_hda_codec
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
coretemp               13401  0 
btusb                  22475  0 
rts5139               356200  0 
snd_seq_midi           13325  0 
snd_rawmidi            30513  1 snd_seq_midi
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
bluetooth             209249  22 rfcomm,bnep,btusb
snd_timer              29426  2 snd_pcm,snd_seq
joydev                 17458  0 
arc4                   12530  2 
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
iwlwifi               386799  0 
kvm                   414071  0 
snd                    78921  16 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac80211              540032  1 iwlwifi
ghash_clmulni_intel    13221  0 
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
i915                  520615  3 
cfg80211              206797  2 iwlwifi,mac80211
drm_kms_helper         49113  1 i915
drm                   288721  4 i915,drm_kms_helper
psmouse                95595  0 
cryptd                 20404  1 ghash_clmulni_intel
mei                    40691  0 
microcode              22804  0 
ideapad_laptop         18087  0 
wmi                    19071  0 
sparse_keymap          13891  1 ideapad_laptop
lpc_ich                17062  0 
i2c_algo_bit           13414  1 i915
mac_hid                13206  0 
serio_raw              13216  0 
video                  19391  1 i915
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
hid_generic            12541  0 
usbhid                 46987  0 
hid                   100411  2 hid_generic,usbhid
r8169                  61651  0 
```

But, I found this! Someone asked about *enabling* bluetooth on the same laptop as mine (Lenovo Z580) and this was the response:

> Not supported in Ubuntu's default kernel

Bus 001 Device 004: ID 04ca:2003 Lite-On Technology Corp. 

Is your bluetooth receiver. It's not supported in the stable Ubuntu Linux kernels at the time of writing. A patch to enable support on it has been submitted: Patchwork Bluetooth: Add support for BCM20702A0 [04ca, 2003] in September 2012.

Try a more recent kernel and it should just work. I'm running Linux 3.7.3 and it's supported

That's Bus 001 Device 005 in my lsusb report.

Full article - [How do I enable Bluetooth on my Lenovo IdeaPad Z580?](http://askubuntu.com/questions/239827/how-do-i-enable-bluetooth-on-my-lenovo-ideapad-z580)

I've looked into disabling bluetooth in the bios but there doesn't seem to be a setting for it. Lenovo support says to press Fn-F5 but that just toggles airplane mode.

So, do I need to try my hand at updating my kernel? Or am I going down the wrong rabbit hole here?

@sms88 - Thanks for the suggestion but I can get into Windows fine after the steps I went through above (though having looked at Windows 8 I'm not sure I want to; could they have made that any uglier if they tried?). The problem now is I can't consistently get into ubuntu; I keep hanging on startup.

---

### Post by sms88 on 2013-02-25
> **tanstaaflwdm said:**
> 
@sms88 - Thanks for the suggestion but I can get into Windows fine after the steps I went through above (though having looked at Windows 8 I'm not sure I want to; could they have made that any uglier if they tried?). The problem now is I can't consistently get into ubuntu; I keep hanging on startup.

Unfortunately there are still a lot of applications that I need to run which are Windows only.

I agree, Windows 8 is pretty awful, clearly it's intended for tablets and touch screens.

There are shells (free) which give Windows 8 the look and feel of Windows 7 or Windows XP.

I worry about my next laptop, this all makes choosing a laptop much more difficult. Definitely I'll go to Costco so if I brick it the return policy will save me.

---

### Post by westie457 on 2013-02-26
[http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade](http://askubuntu.com/questions/119080/how-to-update-kernel-to-the-latest-mainline-version-without-any-distro-upgrade)

The kernel upgrade might work. The link above should help you achieve that.

Am googling to locate drivers for you.

Edit: Found this on the Arch Linux Forum.

[https://bbs.archlinux.org/viewtopic.php?id=133093](https://bbs.archlinux.org/viewtopic.php?id=133093)

It might work.

---

### Post by wnelson on 2013-02-26
This works for my Lenovo B575

Set UEFI to boot from hard drive not ubuntu created UEFI menu object.

Install grub onto the Window8 gpt partition. 
mv /boot/efi/EFI/ubuntu/grubx64.efi /boot/efi/EFI/boot/bootx64.efi

grub-probe --target=fs_uuid [MOUNTPOINT]/EFI/Microsoft/Boot/bootmgfw.efi

add to /etc/grub.d/40_custom

menuentry "Microsoft Windows x86_64 UEFI-GPT Setup" {
    insmod usbms  
    insmod part_gpt  
    insmod part_msdos  
    insmod fat  
    insmod search_fs_uuid  
    insmod chain  
    search --fs-uuid --no-floppy --set=root [GPT partition XXXX-XXXX]
    chainloader /EFI/Microsoft/Boot/bootmgfw.efi  
}

update-grub

This works perfectly fine for my system. My UEFI bios is really buggy. I expect the same for yours?

Walt

---

### Post by wnelson on 2013-02-26
On my system I had shutdown problems and had to use noefi to have the system shutdown correctly. 

Warning: I you see that the kernel update has the following patch, it will break noefi

x86, efi: Make "noefi" really disable EFI runtime serivces

A fix has been done not yet sent to new kernel update ie. 3.8.1

Walt

---

### Post by tanstaaflwdm on 2013-02-27
Thanks for the input everyone. I tried to get into my system last night but gave up after 5 or 6 tries. Most of them never gave me anything other than a blank screen but I did get this once.

[https://www.sugarsync.com/pf/D8551579_760_890194931](https://www.sugarsync.com/pf/D8551579_760_890194931)

Yeah, it's another stop on the bluetooth adapter. On another try it got a bit further before stopping.

[https://www.sugarsync.com/pf/D8551579_760_890194291](https://www.sugarsync.com/pf/D8551579_760_890194291)
(Sorry for the bad pic; screenshots aren't working at that point, obviously)

The rest of the time I just got a blank screen.

Nomodeset is on, quiet splash is off.

What's odd is when it does let me in everything works fine, including the bluetooth (I've used it) and booting with my install dvd and selecting "Try ubuntu without installing" *always* works, so I don't think there's anything fundamentally incompatible between the laptop and the system, but this intermittent failure is really frustrating.

If I can get into it I'll try again today and see what I can come up with.

---

### Post by tanstaaflwdm on 2013-02-28
Well, for the past two days I have been unable to get into ubunut at all. I have rebooted my laptop dozens of times and it always stalls during startup.

I finally managed to get bluetooth turned off in the bios once I realized that the field labeled "BT" was probably "BlueTooth". (Duh). I also found a "Bios optimization" setting that was set to "Windows 64 bit" that I changed to "Other OS" (the only other option). (Also, duh.)

At this point I no longer get just blank screens and get *something* as I boot, but now I'm consistently hanging at this point.

[https://www.sugarsync.com/pf/D8551579_760_891338768](https://www.sugarsync.com/pf/D8551579_760_891338768)

Sometimes it stops a row or two up, but this is the last thing I see while booting. If I hit the power button it detects it and seems to do a normal shutdown (so I don't have to hold the power button to force a shutdown anymore).

What really bugs me about this is that when I first installed it would boot on the second or third try, but it seems like every time I booted it took another try or two until now it won't boot at all.

I've already done one full reinstall and it didn't seem to make any difference. Right now I can't get in at all (unless I use the live DVD which still works perfectly fine).

So yeah, I can't get in to try moving grub around.  Any ideas anyone?

---

### Post by oldfred on 2013-02-28
All I can suggest is include other boot options at grub menu using e. Experiment until something works?

Some have used one or more of these:
 pci=nomsi  or  ACPI=Off
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w


 [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

---

### Post by tanstaaflwdm on 2013-03-01
Thanks, I'll play around with those.

I've found a couple of things saying that a hang right after the "Checking Battery Status" message seems to indicate an nVidia driver problem. Unfortunately, the suggestion in all of them is to hit some combination of keys (usually ctrl-alt-F2) to enter terminal mode and start x manually but my system doesn't seem to recognize any key combination.  

I'll keep working at it.

---

### Post by tanstaaflwdm on 2013-03-17
Didn't mean to leave this hanging for so long but I haven't made any progress so haven't had anything to add.

The system is still behaving erratically. Sometimes I can get it to display a status as it boots, sometimes it doesn't. I've actually managed to get into ubuntu twice in the past two weeks but that's it. Usually I give up after four or five tries.

My latest discovery is this repeating message.

[https://www.sugarsync.com/pf/D8551579_760_800143722](https://www.sugarsync.com/pf/D8551579_760_800143722)

The "blocked for 120 seconds" message led me to this thread where it seems other people are having the same problem.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1093217](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1093217)

The thread implies that the system will eventually boot but I haven't seen that happen myself. Maybe I just haven't let it sit long enough. It also says that some people have had success by booting with the battery removed but my system won't work at all without the battery.

Anyway, just didn't want to leave the thread hanging and wanted to give what little new info I have.

Edit: Immediately after posting this I tried booting with the battery out again. Turns out I had to flip the battery lock switch back into position.

It booted into ubuntu immediately...

---

### Post by tanstaaflwdm on 2013-03-17
And the last piece of the puzzle turned out to be nomodeset.  I took that back out of my grub options and my system now boots on demand.  As long as the battery is removed.

This makes using the laptop as a laptop a bit problematic but in the meantime I suppose I can use the Windows partition if I absolutely have to use it someplace without power. It looks like the problem is in the official bug list so I am presuming that at some point it will get fixed. Until then I think I'm working.

Here's the various bits of solution 

For the Lenovo Z580 laptop...
1) To get into the bios (to turn off secure boot) hold down the F2 key while powering on to get access to the bios menu. To turn off secure boot you have to set a bios password. Once that is set, turn off secure boot. There is also a setting to optimize the bios for Windows. Change that to "other os".

2) Install ubuntu

3) To get ubuntu to actually boot, remove the battery. There are two release buttons for the battery. One is spring loaded and the other is not (and will show a red mark when "open"). Close the non-spring loaded button after removing the battery, otherwise the laptop will not power up. You have to be plugged in, obviously.

4) I have disabled bluetooth (bt in the bios). I am not positive that this has an effect anymore but have not tested with it re-enabled yet.

5) Based on what I have found (link in last post) the problem with the battery check was introduced in a relatively recent build. That is why the install disc I was using worked; it was an older version. It was only after I had used the system for a bit and it downloaded and installed an automatic update that the problem appeared.

So that's it.  I'm going to call this one closed and keep an eye out for an update that fixes the battery issue.

And that was an annoying couple of weeks. Hope this short-circuits the puzzle for someone.

---

### Post by nozyczek on 2013-04-05
My Lenovo Z580 is finally behaving as expected. [Here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1093217/comments/63") is the workaround you can use to fix the problem. Also don't forget to thank Tom for finding and documenting this DSDT workaround.

---

### Post by viperstrike2 on 2014-02-03
I am somewhat convinced this workaround ([http://askubuntu.com/questions/239707/ideapad-z580-wont-boot-kernels-above-3-2-0-32/353999#353999](http://askubuntu.com/questions/239707/ideapad-z580-wont-boot-kernels-above-3-2-0-32/353999#353999)) isn't working anymore (or maybe it's just me).  Can anyone verify this works with 12.04 LTS with 3.5.0-35-generic kernel?

Following the above instructions, here is my "sudo update-grub2" output:
```
Generating grub.cfg ...
**Found custom ACPI table: /boot/dsdt.aml**
Found linux image: /boot/vmlinuz-3.8.0-35-generic
Found initrd image: /boot/initrd.img-3.8.0-35-generic
Found linux image: /boot/vmlinuz-3.8.0-29-generic
Found initrd image: /boot/initrd.img-3.8.0-29-generic
Found memtest86+ image: /memtest86+.bin
done

```

However, after rebooting it still hangs with the battery installed.
I rebooted without the battery and ran "dmesg | grep DSDT" and it shows "20061109" (which according to the original Comment #63 means it isn't running the updated dsdt) :
```
[    0.000000] ACPI: DSDT 00000000daff1000 0AD3E (v02 LENOVO  IVB-CPT 00000000 INTL **20061109**)
[    0.097625] ACPI: EC: Look up EC in DSDT
```

But my dsdt is there...here's the output from "ls -l /boot/dsdt.aml" :
```
-rw-r--r-- 1 root root 44354 Feb  3 20:21 /boot/dsdt.aml
```

Furthermore, 01_apci is executable...here's the output from "ls -l /etc/grub.d/01_apci" :
```
-rwxr-xr-x 1 root root 640 Feb  3 18:43 /etc/grub.d/01_acpi
```


**Does anybody have a clue as to why grub isn't loading the modified dsdt??**

---

