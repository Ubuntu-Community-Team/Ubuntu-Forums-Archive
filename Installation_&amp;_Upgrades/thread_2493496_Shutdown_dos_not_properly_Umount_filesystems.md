---
title: "Shutdown dos not properly Umount filesystems"
date: 2023-12-17
forum: Installation &amp; Upgrades
---

### Post by ewnr4 on 2023-12-17
Ubuntu 22.04 LTS

After a shutdown (manually or via Powerbutton) the filesystems seems not to be properly umounted.

Restarting the server, I can see am fsck on some of the Filesystems.

After Booting, smartctl -A /dev/sda shows an increase of 1 on the Parameter 188 - Command Timeout.

```
smartctl -A /dev/sda
smartctl 7.2 2020-12-30 r5155 [x86_64-linux-5.15.0-91-generic] (local build)
Copyright (C) 2002-20, Bruce Allen, Christian Franke, [www.smartmontools.org]("http://www.smartmontools.org")


=== START OF READ SMART DATA SECTION ===
SMART Attributes Data Structure revision number: 16
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x002f   100   100   050    Pre-fail  Always       -       0
  5 Reallocated_Sector_Ct   0x0032   100   100   001    Old_age   Always       -       0
  9 Power_On_Hours          0x0032   100   100   000    Old_age   Always       -       87
 12 Power_Cycle_Count       0x0032   100   100   001    Old_age   Always       -       39
170 Reserved_Block_Pct      0x0033   100   100   010    Pre-fail  Always       -       0
171 Program_Fail_Count      0x0032   100   100   000    Old_age   Always       -       0
172 Erase_Fail_Count        0x0032   100   100   001    Old_age   Always       -       0
173 Avg_Block-Erase_Count   0x0032   100   100   000    Old_age   Always       -       1
174 Unexpect_Power_Loss_Ct  0x0032   100   100   000    Old_age   Always       -       8
183 SATA_Int_Downshift_Ct   0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   000    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   100   100   000    Old_age   Always       -       0
188 Command_Timeout         0x0032   100   100   000    Old_age   Always       -       23
194 Temperature_Celsius     0x0022   069   067   000    Old_age   Always       -       31 (Min/Max 19/33)
195 Hardware_ECC_Recovered  0x0032   100   100   000    Old_age   Always       -       0
196 Reallocated_Event_Count 0x0032   100   100   000    Old_age   Always       -       0
197 Current_Pending_Sector  0x0032   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0030   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x0032   100   100   000    Old_age   Always       -       0
202 Percent_Lifetime_Remain 0x0030   100   100   001    Old_age   Offline      -       0
206 Write_Error_Rate        0x000e   100   100   000    Old_age   Always       -       0
246 Total_LBAs_Written      0x0032   100   100   000    Old_age   Always       -       132342254
247 Host_Program_Page_Count 0x0032   100   100   000    Old_age   Always       -       4135750
248 Bckgnd_Program_Page_Cnt 0x0032   100   100   000    Old_age   Always       -       1311028
180 Unused_Rsvd_Blk_Cnt_Tot 0x0033   100   100   000    Pre-fail  Always       -       6323
210 RAIN_Success_Recovered  0x0032   100   100   000    Old_age   Always       -       0
211 Integ_Scan_Complete_Cnt 0x0032   100   100   000    Old_age   Always       -       15
212 Integ_Scan_Folding_Cnt  0x0032   100   100   000    Old_age   Always       -       13


root@nr4:/etc/systemd#
``` 


any suggestions to make a save shutdown?

Thanks.

---

### Post by MAFoElffen on 2023-12-17
Yes, it you powerdown manually via the power button, that would do a cold forced powerdown without shutting down the filesystems, and the default power-on process would include a fsck to ensure that the filesysten was okay... That is normal.

On your SMART Question: [https://superuser.com/a/1747851](https://superuser.com/a/1747851)

What happens if you do
```

sudo shutdwon -P now

```
To shut down the server normally?

---

### Post by ewnr4 on 2023-12-17
> **MAFoElffen said:**
> Yes, it you powerdown manually via the power button, that would do a cold forced powerdown without shutting down the filesystems, and the default power-on process would include a fsck to ensure that the filesysten was okay... That is normal.

On your SMART Question: [https://superuser.com/a/1747851](https://superuser.com/a/1747851)

What happens if you do
```

sudo shutdwon -P now

```
To shut down the server normally?

The shutdown via Powerbutton was initialized by systemd (logind.conf ->HandlePowerKey=poweroff ).
On the display there is a normal output like shutdown. so its not a cold forced power down. 

if I use shutdown -P now there is the same output... And the same Error on booting the System.

---

### Post by MAFoElffen on 2023-12-17
Please post the output of this, posted within **Code Tags**.. Like this: [noparse]```
 Paste output here 
```[/noparse]
```

journalctl -b -l -r -g systemd | head -n200

```

---

### Post by ewnr4 on 2023-12-18
```

[COLOR=#3B2322][FONT=Courier]journalctl -b -l -r -g systemd | head -n200[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 15:30:46 nr4 systemd[1]: systemd-timedated.service: Deactivated successfully.[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 15:30:16 nr4 dbus-daemon[903]: [system] Activating via systemd: service name='org.freedesktop.timedate1' unit='dbus-org.freedesktop.timedate1.service' requested by ':1.36' (uid=0 pid=1953 comm="timedatectl " label="unconfined")[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:52:40 nr4 systemd[1]: systemd-timedated.service: Deactivated successfully.[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:52:07 nr4 dbus-daemon[903]: [system] Activating via systemd: service name='org.freedesktop.timedate1' unit='dbus-org.freedesktop.timedate1.service' requested by ':1.30' (uid=0 pid=1718 comm="timedatectl set-timezone Europe/Berlin " label="unconfined")[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:50:40 nr4 systemd[1]: systemd-timedated.service: Deactivated successfully.[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:50:22 nr4 systemd[1]: systemd-tmpfiles-clean.service: Deactivated successfully.[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:49:53 nr4 dbus-daemon[903]: [system] Activating via systemd: service name='org.freedesktop.timedate1' unit='dbus-org.freedesktop.timedate1.service' requested by ':1.27' (uid=0 pid=1706 comm="timedatectl " label="unconfined")[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:48:27 nr4 systemd[1]: systemd-timedated.service: Deactivated successfully.[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:47:56 nr4 dbus-daemon[903]: [system] Activating via systemd: service name='org.freedesktop.timedate1' unit='dbus-org.freedesktop.timedate1.service' requested by ':1.22' (uid=0 pid=1589 comm="timedatectl list-timezones " label="unconfined")[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:46:22 nr4 systemd[1]: systemd-timedated.service: Deactivated successfully.[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:45:52 nr4 dbus-daemon[903]: [system] Activating via systemd: service name='org.freedesktop.timedate1' unit='dbus-org.freedesktop.timedate1.service' requested by ':1.20' (uid=0 pid=1583 comm="timedatectl " label="unconfined")[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:39:05 nr4 systemd[1]: systemd-logind.service: Deactivated successfully.[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:36:08 nr4 systemd[1]: systemd-timedated.service: Deactivated successfully.[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:35:47 nr4 systemd[1222]: pam_unix(systemd-user:session): session opened for user gurke(uid=1001) by (uid=0)[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:35:45 nr4 systemd[1]: systemd-fsckd.service: Deactivated successfully.[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:35:38 nr4 systemd[1]: systemd-update-utmp-runlevel.service: Deactivated successfully.[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:35:38 nr4 dbus-daemon[903]: [system] Activating via systemd: service name='org.freedesktop.timedate1' unit='dbus-org.freedesktop.timedate1.service' requested by ':1.12' (uid=0 pid=917 comm="/usr/lib/snapd/snapd " label="unconfined")[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:35:34 nr4 systemd[1]: Started Dispatcher daemon for systemd-networkd.[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:35:34 nr4 rsyslogd[912]: imuxsock: Acquired UNIX socket '/run/systemd/journal/syslog' (fd 3) from systemd.  [v8.2112.0][/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:35:34 nr4 systemd[1]: Starting Dispatcher daemon for systemd-networkd...[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:35:15 nr4 systemd[1]: proc-sys-fs-binfmt_misc.automount: Got automount request for /proc/sys/fs/binfmt_misc, triggered by 825 (systemd-binfmt)[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:35:14 nr4 systemd[1]: Created slice Slice /system/systemd-fsck.[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:35:14 nr4 systemd[1]: systemd 249.11-0ubuntu3.11 running in system mode (+PAM +AUDIT +SELINUX +APPARMOR +IMA +SMACK +SECCOMP +GCRYPT +GNUTLS +OPENSSL +ACL +BLKID +CURL +ELFUTILS +FIDO2 +IDN2 -IDN +IPTC +KMOD +LIBCRYPTSETUP +LIBFDISK +PCRE2 -PWQUALITY -P11KIT -QRENCODE +BZIP2 +LZ4 +XZ +ZLIB +ZSTD -XKBCOMMON +UTMP +SYSVINIT default-hierarchy=unified)[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]root@nr4:/etc/systemd# journalctl -b -l -r -g systemd | head -n300[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 15:30:46 nr4 systemd[1]: systemd-timedated.service: Deactivated successfully.[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 15:30:16 nr4 dbus-daemon[903]: [system] Activating via systemd: service name='org.freedesktop.timedate1' unit='dbus-org.freedesktop.timedate1.service' requested by ':1.36' (uid=0 pid=1953 comm="timedatectl " label="unconfined")[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:52:40 nr4 systemd[1]: systemd-timedated.service: Deactivated successfully.[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:52:07 nr4 dbus-daemon[903]: [system] Activating via systemd: service name='org.freedesktop.timedate1' unit='dbus-org.freedesktop.timedate1.service' requested by ':1.30' (uid=0 pid=1718 comm="timedatectl set-timezone Europe/Berlin " label="unconfined")[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:50:40 nr4 systemd[1]: systemd-timedated.service: Deactivated successfully.[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:50:22 nr4 systemd[1]: systemd-tmpfiles-clean.service: Deactivated successfully.[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:49:53 nr4 dbus-daemon[903]: [system] Activating via systemd: service name='org.freedesktop.timedate1' unit='dbus-org.freedesktop.timedate1.service' requested by ':1.27' (uid=0 pid=1706 comm="timedatectl " label="unconfined")[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:48:27 nr4 systemd[1]: systemd-timedated.service: Deactivated successfully.[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:47:56 nr4 dbus-daemon[903]: [system] Activating via systemd: service name='org.freedesktop.timedate1' unit='dbus-org.freedesktop.timedate1.service' requested by ':1.22' (uid=0 pid=1589 comm="timedatectl list-timezones " label="unconfined")[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:46:22 nr4 systemd[1]: systemd-timedated.service: Deactivated successfully.[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:45:52 nr4 dbus-daemon[903]: [system] Activating via systemd: service name='org.freedesktop.timedate1' unit='dbus-org.freedesktop.timedate1.service' requested by ':1.20' (uid=0 pid=1583 comm="timedatectl " label="unconfined")[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:39:05 nr4 systemd[1]: systemd-logind.service: Deactivated successfully.[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:36:08 nr4 systemd[1]: systemd-timedated.service: Deactivated successfully.[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:35:47 nr4 systemd[1222]: pam_unix(systemd-user:session): session opened for user data(uid=1000) by (uid=0)[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:35:45 nr4 systemd[1]: systemd-fsckd.service: Deactivated successfully.[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:35:38 nr4 systemd[1]: systemd-update-utmp-runlevel.service: Deactivated successfully.[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:35:38 nr4 dbus-daemon[903]: [system] Activating via systemd: service name='org.freedesktop.timedate1' unit='dbus-org.freedesktop.timedate1.service' requested by ':1.12' (uid=0 pid=917 comm="/usr/lib/snapd/snapd " label="unconfined")[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:35:34 nr4 systemd[1]: Started Dispatcher daemon for systemd-networkd.[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:35:34 nr4 rsyslogd[912]: imuxsock: Acquired UNIX socket '/run/systemd/journal/syslog' (fd 3) from systemd.  [v8.2112.0][/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:35:34 nr4 systemd[1]: Starting Dispatcher daemon for systemd-networkd...[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:35:15 nr4 systemd[1]: proc-sys-fs-binfmt_misc.automount: Got automount request for /proc/sys/fs/binfmt_misc, triggered by 825 (systemd-binfmt)[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:35:14 nr4 systemd[1]: Created slice Slice /system/systemd-fsck.[/FONT][/COLOR]
[COLOR=#3B2322][FONT=Courier]Dez 18 14:35:14 nr4 systemd[1]: systemd 249.11-0ubuntu3.11 running in system mode (+PAM +AUDIT +SELINUX +APPARMOR +IMA +SMACK +SECCOMP +GCRYPT +GNUTLS +OPENSSL +ACL +BLKID +CURL +ELFUTILS +FIDO2 +IDN2 -IDN +IPTC +KMOD +LIBCRYPTSETUP +LIBFDISK +PCRE2 -PWQUALITY -P11KIT -QRENCODE +BZIP2 +LZ4 +XZ +ZLIB +ZSTD -XKBCOMMON +UTMP +SYSVINIT default-hierarchy=unified)[/FONT][/COLOR]

```

---

### Post by MAFoElffen on 2023-12-18
I don't see where the last/previous boot shutdown at all, let alone unmounted any of the filesystems. 

Was that a normal shutdown, or a hard pull-the-power?

---

### Post by ewnr4 on 2023-12-19
I set in the /etc/systemd/logind.conf -  [FONT=Courier][COLOR=#3b2322]HandlePowerKey=poweroff[/COLOR][/FONT]

[FONT=Courier][COLOR=#3b2322]While short pressing the Powerbutten, the system shuts down. so it was not a hard-pull-the-Power.
On the Display I can see the stopping of services.

 [/COLOR][/FONT]

---

