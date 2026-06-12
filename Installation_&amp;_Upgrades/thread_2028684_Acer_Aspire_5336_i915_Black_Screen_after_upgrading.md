---
title: "Acer Aspire 5336 i915: Black Screen after upgrading from 10.04 to 12.04"
date: 2012-07-18
forum: Installation &amp; Upgrades
---

### Post by vichor on 2012-07-18
Hi all,

I know this topic has been discussed in several other threads, but I needed to check several of them and several other web pages to get the picture of what was the problem and how to workaround it. I am no expert at all, so maybe some reasonings are not the proper ones. Sorry about this.

First, the problem itself...

I have a low end laptop Acer Aspire 5336 fitted with, it seems to be, an i915 VGA controller. This was running fine with 10.04 using 2.x kernel series. This week I decided to apply updates. When updating subsequently to newer versions, the screeen suddenly turned black. Kernel was of 3.x series. Previous 2.x kernel was still working fine, so I was able still to boot and keep on working.

I thought that that effect may be caused by an intermediate version, so I decided to boot with previous 2.x versions and keep on with the upgrades until I reached 12.04 (the last one when writing this) and upgraded to the latest level, even installed the ppa of the driver and installed the latest version from launchpad... but the problem persisted.

Then my research began...

The main references supplying my workaround are:

[http://ubuntuforums.org/showthread.php?t=1744809]("http://ubuntuforums.org/showthread.php?t=1744809")
[http://askubuntu.com/questions/136593/how-can-i-fix-broken-i915-drivers-for-intel-gpus]("http://askubuntu.com/questions/136593/how-can-i-fix-broken-i915-drivers-for-intel-gpus")

other references
[https://launchpad.net/~glasen/+archive/intel-driver?field.series_filter=precise]("https://launchpad.net/~glasen/+archive/intel-driver?field.series_filter=precise")
[http://askubuntu.com/questions/155629/ubuntu-12-04-video-issue-on-dell-inspiron-1100]("http://askubuntu.com/questions/155629/ubuntu-12-04-video-issue-on-dell-inspiron-1100")
[http://askubuntu.com/questions/59135/how-can-i-know-list-available-options-for-kernel-modules]("http://askubuntu.com/questions/59135/how-can-i-know-list-available-options-for-kernel-modules")

The problem about the blackscreen seems to be a brightness management + acpi issue.

The first one is due to the i915 driver booting at near to 0% brightness (I don't know the reason for this). The second one is causing the keyboard not allowing to change the brightness.

I don't know a fix for the first one, but a workaround is to manually set the brightness to, say, 70% after the laptop has booted. To do so, we need to modify the file _/etc/rc.local_ adding before the exit 0 command the command

```
setpci -s 00:02.0 F4.B=30
```

The 00:02.0 address comes from the lspci command

```
 $ lspci -v
**_00:02.0_** VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
	Subsystem: Acer Incorporated [ALI] Device 048a
	Flags: bus master, fast devsel, latency 0, IRQ 44
	Memory at 90000000 (64-bit, non-prefetchable) [size=4M]
	Memory at 80000000 (64-bit, prefetchable) [size=256M]
	I/O ports at 4110 [size=8]
	Expansion ROM at <unassigned> [disabled]
	Capabilities: <access denied>
	Kernel driver in use: i915
	Kernel modules: i915
```

The /etc/rc.local file is then something like

```
setpci -s 00:02.0 F4.B=30
exit 0
```

With this, when booting you will not see any splash (or logs!) logo, but when the login screen is loaded, the brightness of the screen will be set to something visible and you will see. You can work already with this, but you won't be able to change the brightness with the keyboard. To do so, you need to apply the next fix.

The brightness control issue seems to be related with the acpi kernel configuration. This is set up in _/etc/default/grub_ file. Be sure that below lines are found in this file:

```
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_backlight=vendor"
GRUB_CMDLINE_LINUX="acpi_osi=Linux"
```

Then regenerate grub configuration:

```
$ sudo update-grub
```

And that's it, the screen won't be black on boot and besides you will be able to change the brightness using the keyboard.

Luck!

---

### Post by speacock on 2013-04-12
I finally upgraded my 10.04 today on my HP dm4-1160 laptop. Spent most of the day fighting this issue. This post solved it, thanks.

---

