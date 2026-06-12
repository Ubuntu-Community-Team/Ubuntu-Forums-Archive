---
title: "Strange restart during night"
date: 2005-03-03
forum: Installation &amp; Upgrades
---

### Post by pico on 2005-03-03
Hi,
I have istalled a UBUNTU 4.10.
I leave my PC turned ON during the night with a Scrennsaver (protected by pswd).

Every day when I came into my OFFICE I discover the the PC is restarted during the night. I do not know WHY.

Follow a peace of my syslog:

Mar  2 06:25:36 localhost syslogd 1.4.1#14ubuntu4: restart.
Mar  2 06:51:52 localhost -- MARK --
Mar  2 07:11:52 localhost -- MARK --
Mar  2 07:17:01 localhost /USR/SBIN/CRON[3782]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar  2 07:31:52 localhost -- MARK --
Mar  2 07:51:52 localhost -- MARK --
Mar  2 08:11:52 localhost -- MARK --
Mar  2 08:17:01 localhost /USR/SBIN/CRON[3785]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar  2 08:31:52 localhost -- MARK --
Mar  2 08:51:52 localhost -- MARK --
Mar  2 09:11:52 localhost -- MARK --
Mar  2 09:17:01 localhost /USR/SBIN/CRON[3787]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar  2 09:31:53 localhost -- MARK --
Mar  2 09:51:53 localhost -- MARK --
Mar  2 10:11:53 localhost -- MARK --
Mar  2 10:17:01 localhost /USR/SBIN/CRON[3790]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar  2 10:31:53 localhost -- MARK --
Mar  2 10:51:53 localhost -- MARK --
Mar  2 11:11:53 localhost -- MARK --
Mar  2 11:17:01 localhost /USR/SBIN/CRON[3792]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar  2 11:31:53 localhost -- MARK --
mar  2 11:34:18 localhost gdm[3442]: Impossibile autenticare l'utente
mar  2 11:34:24 localhost gconfd (pico-3848): Inizializzazione (versione 2.8.1), pid 3848, utente 'pico'
mar  2 11:34:24 localhost gconfd (pico-3848): L'indirizzo "xml:readonly:/etc/gconf/gconf.xml.mandatory" è stato risolta ad una fonte di configurazione in sola lettura in posizione 0
mar  2 11:34:24 localhost gconfd (pico-3848): L'indirizzo "xml:readwrite:/home/pico/.gconf" è stato risolto ad una fonte di configurazione scrivibile in posizione 1
mar  2 11:34:24 localhost gconfd (pico-3848): L'indirizzo "xml:readonly:/etc/gconf/gconf.xml.defaults" è stato risolta ad una fonte di configurazione in sola lettura in posizione 2
mar  2 11:34:39 localhost gconfd (pico-3848): L'indirizzo "xml:readwrite:/home/pico/.gconf" è stato risolto ad una fonte di configurazione scrivibile in posizione 0
Mar  2 11:51:53 localhost -- MARK --
Mar  2 12:11:53 localhost -- MARK --
Mar  2 12:17:01 localhost /USR/SBIN/CRON[4449]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar  2 12:31:53 localhost -- MARK --
Mar  2 12:51:53 localhost -- MARK --
Mar  2 13:11:53 localhost -- MARK --
Mar  2 13:17:01 localhost /USR/SBIN/CRON[5172]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar  2 13:31:53 localhost -- MARK --
Mar  2 13:51:53 localhost -- MARK --
Mar  2 14:11:53 localhost -- MARK --
Mar  2 14:17:01 localhost /USR/SBIN/CRON[5903]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar  2 14:31:53 localhost -- MARK --
Mar  2 14:51:53 localhost -- MARK --
Mar  2 15:11:53 localhost -- MARK --
Mar  2 15:17:01 localhost /USR/SBIN/CRON[6626]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar  2 15:31:53 localhost -- MARK --
Mar  2 15:51:53 localhost -- MARK --
Mar  2 16:11:53 localhost -- MARK --
Mar  2 16:17:01 localhost /USR/SBIN/CRON[7348]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar  2 16:31:53 localhost -- MARK --
Mar  2 16:51:53 localhost -- MARK --
Mar  2 17:11:53 localhost -- MARK --
Mar  2 17:17:01 localhost /USR/SBIN/CRON[8071]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar  2 17:31:53 localhost -- MARK --
Mar  2 17:51:53 localhost -- MARK --
Mar  2 18:11:53 localhost -- MARK --
Mar  2 18:17:01 localhost /USR/SBIN/CRON[8795]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar  2 18:31:53 localhost -- MARK --
Mar  2 18:51:53 localhost -- MARK --
Mar  2 19:11:53 localhost -- MARK --
Mar  2 19:17:01 localhost /USR/SBIN/CRON[9519]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar  2 19:31:53 localhost -- MARK --
Mar  2 19:51:53 localhost -- MARK --
Mar  2 20:11:53 localhost -- MARK --
Mar  2 20:17:01 localhost /USR/SBIN/CRON[10245]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar  2 20:31:53 localhost -- MARK --
Mar  2 20:51:53 localhost -- MARK --
Mar  2 21:11:54 localhost -- MARK --
Mar  2 21:17:01 localhost /USR/SBIN/CRON[10967]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar  2 21:31:54 localhost -- MARK --
Mar  2 21:51:54 localhost -- MARK --
Mar  2 22:11:54 localhost -- MARK --
Mar  2 22:17:01 localhost /USR/SBIN/CRON[11690]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar  2 22:31:54 localhost -- MARK --
Mar  2 22:51:54 localhost -- MARK --
Mar  2 23:11:54 localhost -- MARK --
Mar  2 23:17:01 localhost /USR/SBIN/CRON[12413]: (root) CMD (   run-parts --report /etc/cron.hourly)
Mar  2 23:31:54 localhost -- MARK --
Mar  2 23:51:54 localhost -- MARK --
Mar  3 00:03:04 localhost syslogd 1.4.1#14ubuntu4: restart.
Mar  3 00:03:05 localhost kernel: klogd 1.4.1#14ubuntu4, log source = /proc/kmsg started.
Mar  3 00:03:05 localhost kernel: Inspecting /boot/System.map-2.6.8.1-5-386
Mar  3 00:03:05 localhost kernel: Loaded 28212 symbols from /boot/System.map-2.6.8.1-5-386.
Mar  3 00:03:05 localhost kernel: Symbols match kernel version 2.6.8.
Mar  3 00:03:05 localhost kernel: No module symbols loaded - kernel modules not enabled. 
Mar  3 00:03:05 localhost kernel: Linux version 2.6.8.1-5-386 (buildd@terranova) (gcc version 3.3.4 (Debian 1:3.3.4-9ubuntu5)) #1 Sat Feb 12 00:19:31 UTC 2005
Mar  3 00:03:05 localhost kernel: BIOS-provided physical RAM map:
Mar  3 00:03:05 localhost kernel:  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
Mar  3 00:03:05 localhost kernel:  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
Mar  3 00:03:05 localhost kernel:  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
Mar  3 00:03:05 localhost kernel:  BIOS-e820: 0000000000100000 - 000000002effc000 (usable)
Mar  3 00:03:05 localhost kernel:  BIOS-e820: 000000002effc000 - 000000002efff000 (ACPI data)
Mar  3 00:03:05 localhost kernel:  BIOS-e820: 000000002efff000 - 000000002f000000 (ACPI NVS)
Mar  3 00:03:05 localhost kernel:  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
Mar  3 00:03:05 localhost kernel: 751MB LOWMEM available.
Mar  3 00:03:05 localhost kernel: On node 0 totalpages: 192508
Mar  3 00:03:05 localhost kernel:   DMA zone: 4096 pages, LIFO batch:1
Mar  3 00:03:05 localhost kernel:   Normal zone: 188412 pages, LIFO batch:16
Mar  3 00:03:05 localhost udev[2758]: creating device node '/dev/vcs1'
Mar  3 00:03:05 localhost udev[2899]: removing device node '/dev/vcs1'
Mar  3 00:03:05 localhost kernel:   HighMem zone: 0 pages, LIFO batch:1
Mar  3 00:03:05 localhost kernel: DMI 2.3 present.

---

