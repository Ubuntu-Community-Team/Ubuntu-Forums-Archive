---
title: "Long splash screen pause during boot"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by GreenfrogCT on 2009-04-06
I've already reported this as bug #355299 . . . wonder if anybody else has encountered something similar.

I'm running a fresh clean install of Jaunty (AMD-64) on an ASUS M2N-SLI-Deluxe mobo.  On boot the splash screen begins to advance for about 5 seconds, then it pauses . . .  for a LONG time . . .  roughly 90 seconds . . . and then it continues, and the system comes up and works with no problem.

I've uploaded a bootchart report which is in launchpad under this bug number. 

Anybody else?  Any ideas?

Frog.

---

### Post by ktp on 2009-04-06
Have you tried to install bootchart and see what is taking that long...it might be network or something that is timing out.

sudo apt-get install bootchart

---

### Post by kansasnoob on 2009-04-06
Does the splash screen turn to text during the process?

---

### Post by GreenfrogCT on 2009-04-06
[QUOTE=ktp]Have you tried to install bootchart and see what is taking that long...it might be network or something that is timing out.[/QUOTE]

Yes, if you will notice in my original post I mentioned that I uploaded the bootchart log as part of my bug report.  I agree it is likely to be something timing out - but it's hard (for me) to tell from what I'm looking at.

[QUOTE=kansasnoob]Does the splash screen turn to text during the process? [/QUOTE]
No, the progress "thermometer" just hangs at about 1/10 of the way across.  If I boot using "recovery" (no splash screen) the last item prior to the pause is loading the mouse driver.  The next reported event after the pause is the loading of the kernel.

Ribbitt.

---

### Post by GreenfrogCT on 2009-04-06
I just also enabled boot logging.  It appears the system might be trying to load a USB sound driver just before the pause which according to this log begins at about 16 seconds into the process and lasts until 102 seconds when the process resumes.  By the way . . . I was running Intrepid on this machine prior to installing Jaunty and this wasn't happening.  There have been no hardware changes on the system.



[FONT="Arial"]
  12.892868]  [<ffffffff80236d82>] ioremap_nocache+0x12/0x20
[   12.892870]  [<ffffffffa09582db>] ck804xrom_init_one+0x1ab/0x5ca [ck804xrom]
[   12.892874]  [<ffffffffa095e041>] init_ck804xrom+0x41/0x59 [ck804xrom]
[   12.892877]  [<ffffffffa095e000>] ? init_ck804xrom+0x0/0x59 [ck804xrom]
[   12.892880]  [<ffffffff8020a03b>] do_one_initcall+0x3b/0x170
[   12.892884]  [<ffffffff802424b2>] ? enqueue_entity+0x122/0x2b0
[   12.892886]  [<ffffffff8024870b>] ? enqueue_task_fair+0x7b/0x80
[   12.892889]  [<ffffffff8023e2a9>] ? wakeup_preempt_entity+0x59/0x60
[   12.892891]  [<ffffffff80249330>] ? check_preempt_wakeup+0x210/0x230
[   12.892893]  [<ffffffff8024a3cc>] ? try_to_wake_up+0x12c/0x2e0
[   12.892898]  [<ffffffff8027ef9d>] sys_init_module+0xad/0x1e0
[   12.892901]  [<ffffffff8021253a>] system_call_fastpath+0x16/0x1b
[   12.892903] ---[ end trace d162df9808d761da ]---
[   13.003695] Found: PMC Pm49FL004
[   13.003705] ck804xrom @fff80000: Found 1 x8 devices at 0x0 in 8-bit bank
[   13.009112] ACPI: PCI Interrupt Link [AAZA] enabled at IRQ 20
[   13.009118] HDA Intel 0000:00:06.1: PCI INT B -> Link[AAZA] -> GSI 20 (level, low) -> IRQ 20
[   13.009176] HDA Intel 0000:00:06.1: setting latency timer to 64
[   13.029987] number of JEDEC chips: 1
[   13.029990] cfi_cmdset_0002: Disabling erase-suspend-program due to code brokenness.
[   13.607592] input: ImPS/2 Generic Wheel Mouse as /devices/platform/i8042/serio1/input/input5
[   13.864078] uvcvideo: Failed to query (135) UVC control 1 (unit 0) : -110 (exp. 26).
[   14.864072] uvcvideo: Failed to query (129) UVC control 1 (unit 0) : -110 (exp. 26).
[   14.864078] uvcvideo: Failed to initialize the device (-5).
[   14.864146] usbcore: registered new interface driver uvcvideo
[   14.864198] USB Video Class driver (v0.1.0)
[   15.830715] 2:3:3: cannot set freq 16000 to ep 0x86
[   15.929731] usbcore: registered new interface driver snd-usb-audio

[COLOR="Red"]**THE LONG PAUSE IS HERE**[/COLOR]


[  102.107018] lp0: using parport0 (interrupt-driven).
[  102.222128] Adding 104380k swap on /dev/sdb3.  Priority:-1 extents:1 across:104380k
[  102.799431] EXT3 FS on sdb1, internal journal
[  103.857281] type=1505 audit(1239072183.044:2): operation="profile_load" name="/usr/share/gdm/guest-session/Xsession" name2="default" pid=2178
[  103.899287] type=1505 audit(1239072183.084:3): operation="profile_load" name="/sbin/dhclient-script" name2="default" pid=2182
[  103.899420] type=1505 audit(1239072183.084:4): operation="profile_load" name="/sbin/dhclient3" name2="default" pid=2182
[  103.899463] type=1505 audit(1239072183.084:5): operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" name2="default" pid=2182
[  103.899499] type=1505 audit(1239072183.084:6): operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" name2="default" pid=2182
[  104.017193] type=1505 audit(1239072183.204:7): operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" name2="default" pid=2187
[  104.017364] type=1505 audit(1239072183.204:8): operation="profile_load" name="/usr/sbin/cupsd" name2="default" pid=2187
[  104.058845] type=1505 audit(1239072183.244:9): operation="profile_load" name="/usr/sbin/tcpdump" name2="default" pid=2191
[  107.574291] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[  107.574294] Bluetooth: BNEP filters: protocol multicast
[  107.585557] Bridge firewalling registered
[/FONT]

---

### Post by caryb on 2009-04-06
Per chance do you have a static entry in your /etc/network/interfaces file?
That will make the boot hang.


Cary

---

### Post by GreenfrogCT on 2009-04-06
> **caryb said:**
> Per chance do you have a static entry in your /etc/network/interfaces file?
That will make the boot hang.


Cary

Nope. Default automatic configuration.

---

### Post by kansasnoob on 2009-04-06
Are you certain that you've not resized or moved the swap partition?

This:

> Adding 104380k swap on /dev/sdb3. Priority:-1 extents:1 across:104380k

makes me wonder about initramfs, so (at your own peril) try running:

```
sudo update-initramfs -u
```

---

### Post by GreenfrogCT on 2009-04-09
> **kansasnoob said:**
> Are you certain that you've not resized or moved the swap partition?

This:



makes me wonder about initramfs, so (at your own peril) try running:

```
sudo update-initramfs -u
```

Absolutely certain.  Swap was defined (by default) at install, and is exactly as it was on the earlier (Intrepid) installation.  This issue wasn't created by any change I made.  The Ubuntu installation on this particular machine is on a partition I use for testing and playing.  I installed Jaunty as a clean install, reformatting the existing Intrepid EXT3 partitions.  The problem started happening on the first boot of the newly installed OS, and has persisted through all of the updates, and despite my doing such things as disconnecting every unessential piece of ancillary hardware.  I did this because if you look at the chart output by [bootchart]("http://launchpadlibrarian.net/24816445/cosmos-jaunty-20090404-1.tgz") it looks suspiciously as if the pause begins shortly after modprobe starts up.

Once again, Intrepid (64-bit version) was installed in the same partition and didn't have the problem.  All that changed was the OS.

Still stumped.

---

