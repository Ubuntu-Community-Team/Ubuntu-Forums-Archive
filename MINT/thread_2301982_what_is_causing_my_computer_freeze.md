---
title: "what is causing my computer freeze"
date: 2015-11-06
forum: MINT
---

### Post by mony3 on 2015-11-06
It happens once of couple of days. I checked the log. I post below. I happened from line 11 to line 12, when the time jumped 8 hours. And the computer crashed. No ssh, no desktop.  This dove me crazy.
The os is Mint 17, I think it's based on ubuntu 
Any help will be appreciated.


====================================================================================
```
Nov  6 14:09:01 JCC-Files CRON[19525]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -x /usr/lib/php5/sessionclean ] && [ -d /var/lib/php5 ] && /usr/lib/php5/sessionclean /var/lib/php5 $(/usr$Nov  6 14:09:01 JCC-Files CRON[19526]: (asterisk) CMD ([ -x /var/www/html/admin/modules/dashboard/scheduler.php ] && /var/www/html/admin/modules/dashboard/scheduler.php)
Nov  6 14:10:01 JCC-Files CRON[19539]: (asterisk) CMD ([ -x /var/www/html/admin/modules/dashboard/scheduler.php ] && /var/www/html/admin/modules/dashboard/scheduler.php)
Nov  6 14:11:01 JCC-Files CRON[19542]: (asterisk) CMD ([ -x /var/www/html/admin/modules/dashboard/scheduler.php ] && /var/www/html/admin/modules/dashboard/scheduler.php)
Nov  6 14:12:01 JCC-Files CRON[19546]: (asterisk) CMD ([ -x /var/www/html/admin/modules/dashboard/scheduler.php ] && /var/www/html/admin/modules/dashboard/scheduler.php)
Nov  6 14:13:01 JCC-Files CRON[19549]: (asterisk) CMD ([ -x /var/www/html/admin/modules/dashboard/scheduler.php ] && /var/www/html/admin/modules/dashboard/scheduler.php)
Nov  6 14:14:01 JCC-Files CRON[19553]: (asterisk) CMD ([ -x /var/www/html/admin/modules/dashboard/scheduler.php ] && /var/www/html/admin/modules/dashboard/scheduler.php)
Nov  6 14:15:01 JCC-Files CRON[19556]: (asterisk) CMD ([ -x /var/www/html/admin/modules/dashboard/scheduler.php ] && /var/www/html/admin/modules/dashboard/scheduler.php)
Nov  6 14:16:01 JCC-Files CRON[19559]: (asterisk) CMD ([ -x /var/www/html/admin/modules/dashboard/scheduler.php ] && /var/www/html/admin/modules/dashboard/scheduler.php)
Nov  6 14:17:01 JCC-Files CRON[19563]: (asterisk) CMD ([ -x /var/www/html/admin/modules/dashboard/scheduler.php ] && /var/www/html/admin/modules/dashboard/scheduler.php)
Nov  6 14:17:01 JCC-Files CRON[19564]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Nov  6 22:16:24 JCC-Files rsyslogd: [origin software="rsyslogd" swVersion="7.4.4" x-pid="597" x-info="http://www.rsyslog.com"] start
Nov  6 22:16:24 JCC-Files rsyslogd: rsyslogd's groupid changed to 104
Nov  6 22:16:24 JCC-Files rsyslogd: rsyslogd's userid changed to 101
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] Initializing cgroup subsys cpuset
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] Initializing cgroup subsys cpu
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] Initializing cgroup subsys cpuacct
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] Linux version 3.16.0-38-generic (buildd@allspice) (gcc version 4.8.2 (Ubuntu 4.8.2-19ubuntu1) ) #52~14.04.1-Ubuntu SMP Fri May 8 09:43:57 UTC 2015 ($
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-38-generic root=UUID=fd1b8b1c-93d9-4b2c-916f-f3919c6b25ae ro
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] KERNEL supported cpus:
Nov  6 22:16:24 JCC-Files kernel: [    0.000000]   Intel GenuineIntel
Nov  6 22:16:24 JCC-Files kernel: [    0.000000]   AMD AuthenticAMD
Nov  6 22:16:24 JCC-Files kernel: [    0.000000]   Centaur CentaurHauls
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] e820: BIOS-provided physical RAM map:
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] BIOS-e820: [mem 0x0000000000000000-0x000000000008efff] usable
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] BIOS-e820: [mem 0x000000000008f000-0x000000000008ffff] ACPI NVS
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] BIOS-e820: [mem 0x0000000000090000-0x000000000009dfff] usable
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] BIOS-e820: [mem 0x000000000009e000-0x000000000009ffff] reserved
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] BIOS-e820: [mem 0x0000000000100000-0x000000001fffffff] usable
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] BIOS-e820: [mem 0x0000000020000000-0x00000000200fffff] reserved
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] BIOS-e820: [mem 0x0000000020100000-0x0000000098a7dfff] usable
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] BIOS-e820: [mem 0x0000000098a7e000-0x0000000098aadfff] reserved
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] BIOS-e820: [mem 0x0000000098aae000-0x0000000098abdfff] ACPI data
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] BIOS-e820: [mem 0x0000000098abe000-0x0000000099270fff] ACPI NVS
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] BIOS-e820: [mem 0x0000000099271000-0x0000000099b3ffff] reserved
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] BIOS-e820: [mem 0x0000000099b40000-0x0000000099b8bfff] type 20
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] BIOS-e820: [mem 0x0000000099b8c000-0x0000000099b8cfff] usable
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] BIOS-e820: [mem 0x0000000099b8d000-0x0000000099bcefff] reserved
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] BIOS-e820: [mem 0x0000000099bcf000-0x0000000099d3dfff] usable
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] BIOS-e820: [mem 0x0000000099d3e000-0x0000000099ff9fff] reserved
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] BIOS-e820: [mem 0x0000000099bcf000-0x0000000099d3dfff] usable
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] BIOS-e820: [mem 0x0000000099d3e000-0x0000000099ff9fff] reserved
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] BIOS-e820: [mem 0x0000000099ffa000-0x0000000099ffffff] usable
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] BIOS-e820: [mem 0x00000000e00f8000-0x00000000e00f8fff] reserved
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] BIOS-e820: [mem 0x00000000fed01000-0x00000000fed01fff] reserved
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] BIOS-e820: [mem 0x00000000ffb00000-0x00000000ffffffff] reserved
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] BIOS-e820: [mem 0x0000000100000000-0x000000015fffffff] usable
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] NX (Execute Disable) protection: active
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: EFI v2.31 by Acer Inc.
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi:  ACPI=0x98ab3000  ACPI 2.0=0x98ab3000  SMBIOS=0x99a89d18
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem00: type=7, attr=0xf, range=[0x0000000000000000-0x000000000008f000) (0MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem01: type=10, attr=0xf, range=[0x000000000008f000-0x0000000000090000) (0MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem02: type=7, attr=0xf, range=[0x0000000000090000-0x000000000009e000) (0MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem03: type=0, attr=0xf, range=[0x000000000009e000-0x00000000000a0000) (0MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem04: type=2, attr=0xf, range=[0x0000000000100000-0x00000000014e1000) (19MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem05: type=7, attr=0xf, range=[0x00000000014e1000-0x0000000002000000) (11MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem06: type=2, attr=0xf, range=[0x0000000002000000-0x00000000033e1000) (19MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem07: type=7, attr=0xf, range=[0x00000000033e1000-0x0000000020000000) (460MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem08: type=0, attr=0xf, range=[0x0000000020000000-0x0000000020100000) (1MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem09: type=7, attr=0xf, range=[0x0000000020100000-0x00000000347d4000) (326MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem10: type=2, attr=0xf, range=[0x00000000347d4000-0x00000000363e2000) (28MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem11: type=7, attr=0xf, range=[0x00000000363e2000-0x0000000057813000) (532MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem12: type=2, attr=0xf, range=[0x0000000057813000-0x000000007a000000) (551MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem13: type=4, attr=0xf, range=[0x000000007a000000-0x000000007a020000) (0MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem14: type=7, attr=0xf, range=[0x000000007a020000-0x0000000089e81000) (254MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem15: type=2, attr=0xf, range=[0x0000000089e81000-0x0000000089f6c000) (0MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem16: type=7, attr=0xf, range=[0x0000000089f6c000-0x0000000089f6e000) (0MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem17: type=2, attr=0xf, range=[0x0000000089f6e000-0x0000000089f6f000) (0MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem18: type=7, attr=0xf, range=[0x0000000089f6f000-0x0000000089f71000) (0MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem19: type=2, attr=0xf, range=[0x0000000089f71000-0x0000000089f72000) (0MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem20: type=7, attr=0xf, range=[0x0000000089f72000-0x0000000089f73000) (0MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem21: type=2, attr=0xf, range=[0x0000000089f73000-0x0000000089f76000) (0MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem22: type=7, attr=0xf, range=[0x0000000089f76000-0x0000000089f7b000) (0MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem23: type=2, attr=0xf, range=[0x0000000089f7b000-0x0000000089f7d000) (0MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem24: type=7, attr=0xf, range=[0x0000000089f7d000-0x0000000089f7f000) (0MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem25: type=2, attr=0xf, range=[0x0000000089f7f000-0x0000000089f80000) (0MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem26: type=7, attr=0xf, range=[0x0000000089f80000-0x0000000089f83000) (0MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem27: type=2, attr=0xf, range=[0x0000000089f83000-0x0000000089f84000) (0MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem28: type=7, attr=0xf, range=[0x0000000089f84000-0x0000000089f85000) (0MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem29: type=2, attr=0xf, range=[0x0000000089f85000-0x000000008a071000) (0MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem30: type=1, attr=0xf, range=[0x000000008a071000-0x000000008a1a5000) (1MB)
Nov  6 22:16:24 JCC-Files kernel: [    0.000000] efi: mem31: type=4, attr=0xf, range=[0x000000008a1a5000-0x000000009847e000) (226MB)
```

---

### Post by tgalati4 on 2015-11-06
That is strange.  If you have a real hardware problem, then the log files don't help much.  Do you have an UPS protecting this computer?  Check your power supply voltages.  Look in /var/log at your other log files to see if there is any consistent pattern.

In the meantime, run *memtest* and check your RAM.  Run it for 30 complete cycles.

---

### Post by mony3 on 2015-11-09
I do have ups powering the server. 

The crash happened again during the weekend.  I found this in /var/log/kern.log
The last line shows the manual reboot(with power button). The time stamp shows Greenwich time, while my machine is located in different timezone.
After the reboot, the "date" shows correct time zone.



> Nov  6 22:16:29 JCC-File kernel: [   26.152724] usbcore: registered new interface driver xpp_usb
Nov  6 17:24:51 JCC-File kernel: [ 4136.499882] perf interrupt took too long (2555 > 2500), lowering kernel.perf_eve$
Nov  6 18:27:52 JCC-File kernel: [ 7924.561172] perf interrupt took too long (5012 > 5000), lowering kernel.perf_eve$
Nov  6 19:51:06 JCC-File kernel: [12928.856885] perf interrupt took too long (10385 > 10000), lowering kernel.perf_e$
Nov  7 00:47:26 JCC-File kernel: [30743.115834] PPP MPPE Compression module registered
Nov  7 03:42:08 JCC-File kernel: [41245.148652] [drm:vlv_set_rps_idle] *ERROR* timed out waiting for Punit
Nov  7 04:11:21 JCC-File kernel: [43001.566178] [drm:vlv_set_rps_idle] *ERROR* timed out waiting for Punit
Nov  7 08:50:56 JCC-File kernel: [59809.239535] [drm:vlv_set_rps_idle] *ERROR* timed out waiting for Punit
Nov  7 12:17:21 JCC-File kernel: [72218.368997] [drm:vlv_set_rps_idle] *ERROR* timed out waiting for Punit
Nov  7 13:08:24 JCC-File kernel: [75287.323291] [drm:vlv_set_rps_idle] *ERROR* timed out waiting for Punit
Nov  7 18:17:10 JCC-File kernel: [93849.412487] [drm:vlv_set_rps_idle] *ERROR* timed out waiting for Punit
Nov  7 19:20:25 JCC-File kernel: [97651.804961] [drm:vlv_set_rps_idle] *ERROR* timed out waiting for Punit
Nov  9 15:14:06 JCC-File kernel: [    0.000000] Initializing cgroup subsys cpuset

---

### Post by tgalati4 on 2015-11-09
When was the last time you cleaned out the server?  They generally require yearly cleaning.  Unplug the server from the UPS and plug in a 100-watt incandescent lamp (not a flourescent or LED bulb).  Pull the plug on the UPS and mark the time.  You should get 20 minutes minimum of battery time.  It's possible that a micro power outage caused your server to reboot.  

Time is generally kept by the RTC in UTC and then converted to local time as shown in /etc/timezone after boot.  So that is not unusual to have UTC entries in your log file.

---

### Post by oldos2er on 2015-11-10
Moved to MINT.

---

