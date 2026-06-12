---
title: "Suspend/Resume Call for Testing - Ubuntu 9.04 Beta"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ubuntu27 on 2009-03-27
Hi Everyone,

With the Ubuntu Jaunty Jackalope 9.04 [Beta release]("http://www.ubuntu.com/testing/jaunty/beta") [1], the Ubuntu
Kernel Team would like to request your assistance with suspend/resume
testing.  The team has been gathering information about Ubuntu's
suspend/resume support for varying pieces of hardware.  If you would
like to participate and volunteer to perform tests, the Ubuntu Kernel
Team has provided a suspend_test script [2].  The script has been
packaged with checkbox 0.7 and should be available with the Jaunty 9.04
Beta release.  The script will perform a number of suspend/resume tests.
The first few tests will require human interaction.  In total, the tests
should take approximately 30min to complete and will perform 34
suspend/resume cycles.  For information on how to run the script and
other details, refer to the [SuspendResumeTesting wiki]("https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting") [3].

Test results are also being tracked on the [Ubuntu wiki]("https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting/Feedback") [4] so please be
sure to add any information for hardware that is not yet listed.  Also,
feel free to include any additional information for hardware that is
currently listed.  In the event that a test should fail, hooks have been
added to apport to automatically detect failures and subsequently file a
report in Launchpad.  Upon rebooting the system after a failure, apport
will try to gather as much information from the system and guide one
through the bug filing process.  Please be sure to also visit the
corresponding debugging page [5] which documents additional requested
information that apport is unable to gather.  Please include this
information in the bug report as well.

The team appreciates all the time and feedback that can be dedicated to
suspend/resume testing and reporting.  Please let us know your results.

Thanks in advance,
The Ubuntu Kernel Team

[1] [http://www.ubuntu.com/testing/jaunty/beta](http://www.ubuntu.com/testing/jaunty/beta)
[2] /usr/share/checkbox/scripts/suspend_test
[3] [https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting](https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting)
[4] [https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting/Feedback](https://wiki.ubuntu.com/KernelTeam/SuspendResumeTesting/Feedback)
[5] [https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume](https://wiki.ubuntu.com/DebuggingKernelSuspendHibernateResume)


-- 
ubuntu-devel-announce mailing list
[email]ubuntu-devel-announce@lists.ubuntu.com[/email]
[https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce](https://lists.ubuntu.com/mailman/listinfo/ubuntu-devel-announce)

---

### Post by skitching on 2009-03-28
Generally, suspend/resume seems to work fine on my laptop. However the testing script does not trigger an auto-wake; I need to manually trigger resume each time the script shuts the system down.

On IRC, I received the suggestion to run this:

OLDIFS=$IFS; IFS=$'\n'; find /sys -name wakeup | while read node; do STATUS=$(cat $node); [ ! -z "$STATUS" ] && echo "$node $STATUS"; done; IFS=$OLDIFS

The output is:
/sys/devices/platform/serial8250/tty/ttyS1/power/wakeup disabled
/sys/devices/platform/serial8250/tty/ttyS2/power/wakeup disabled
/sys/devices/platform/serial8250/tty/ttyS3/power/wakeup disabled
/sys/devices/pci0000:00/0000:00:01.0/power/wakeup disabled			--> pci bridge root port
/sys/devices/pci0000:00/0000:00:1b.0/power/wakeup disabled			--> audio
/sys/devices/pci0000:00/0000:00:1c.0/power/wakeup disabled			--> pci bridge port 1
/sys/devices/pci0000:00/0000:00:1c.0/0000:08:00.0/power/wakeup enabled
/sys/devices/pci0000:00/0000:00:1c.1/power/wakeup disabled			--> pci bridge port 2
/sys/devices/pci0000:00/0000:00:1c.1/0000:10:00.0/power/wakeup disabled
/sys/devices/pci0000:00/0000:00:1c.3/power/wakeup disabled			--> pci bridge port 4
/sys/devices/pci0000:00/0000:00:1d.0/usb2/power/wakeup enabled			--> usb controller #1
/sys/devices/pci0000:00/0000:00:1d.0/usb2/2-1/power/wakeup enabled
/sys/devices/pci0000:00/0000:00:1d.1/power/wakeup disabled			--> usb controller #2
/sys/devices/pci0000:00/0000:00:1d.1/usb3/power/wakeup enabled
/sys/devices/pci0000:00/0000:00:1d.1/usb3/3-1/power/wakeup enabled
/sys/devices/pci0000:00/0000:00:1d.2/power/wakeup disabled
/sys/devices/pci0000:00/0000:00:1d.2/usb4/power/wakeup enabled
/sys/devices/pci0000:00/0000:00:1d.2/usb4/4-2/power/wakeup enabled
/sys/devices/pci0000:00/0000:00:1d.3/power/wakeup disabled
/sys/devices/pci0000:00/0000:00:1d.3/usb5/power/wakeup enabled
/sys/devices/pci0000:00/0000:00:1d.7/power/wakeup disabled
/sys/devices/pci0000:00/0000:00:1d.7/usb1/power/wakeup enabled
/sys/devices/pci0000:00/0000:00:1e.0/power/wakeup disabled
/sys/devices/pci0000:00/0000:00:1e.0/0000:02:06.0/power/wakeup disabled
/sys/devices/pci0000:00/0000:00:1e.0/0000:02:06.1/power/wakeup disabled
/sys/devices/pci0000:00/0000:00:1e.0/0000:02:06.2/power/wakeup disabled
/sys/devices/pci0000:00/0000:00:1e.0/0000:02:06.3/power/wakeup disabled
/sys/devices/pci0000:00/0000:00:1e.0/0000:02:06.4/power/wakeup disabled
/sys/devices/pci0000:00/0000:00:1f.2/power/wakeup disabled
/sys/devices/pnp0/00:02/tty/ttyS0/power/wakeup disabled
/sys/devices/pnp0/00:08/power/wakeup enabled


Running lspci reports:
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc M56P [Radeon Mobility X1600]
02:06.0 CardBus bridge: Texas Instruments PCIxx12 Cardbus Controller
02:06.1 FireWire (IEEE 1394): Texas Instruments PCIxx12 OHCI Compliant IEEE 1394 Host Controller
02:06.2 Mass storage controller: Texas Instruments 5-in-1 Multimedia Card Reader (SD/MMC/MS/MS PRO/xD)
02:06.3 SD Host controller: Texas Instruments PCIxx12 SDA Standard Compliant SD Host Controller
02:06.4 Communication controller: Texas Instruments PCIxx12 GemCore based SmartCard controller
08:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5753M Gigabit Ethernet PCI Express (rev 21)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

The fact that the device "PCI Bridge Intel 945GM... Root Port" is disabled seems reasonably important. 

dmesg has the following possibly relevant info:
[    2.977187] rtc_cmos 00:08: RTC can wake from S4
[    2.977408] rtc_cmos 00:08: rtc core: registered rtc_cmos as rtc0
[    2.977600] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    2.979562] Marking TSC unstable due to TSC halts in idle

Do I need to somehow "enable" the disabled devices, or does this just mean auto-wake is not possible on this machine?

---

