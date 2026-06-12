---
title: "upgrade to edgy, freezed at bootup"
date: 2006-11-11
forum: Installation &amp; Upgrades
---

### Post by oxygenws on 2006-11-11
i was upgrade to edgy, from dapper, after restarting, it freeze in some steps of booting up, i cannot bootup in recovery mode too :( ](*,) 

i attached tail of some -maybe- needed log files here:

> **syslog]Nov 11 20:56:40 localhost mysqld[5658]: 061111 20:56:40  InnoDB: Shutdown completed said:**
> : 061111 20:56:40 [Note] /usr/sbin/mysqld: Shutdown complete
Nov 11 20:56:40 localhost mysqld[5658]:
Nov 11 20:56:40 localhost mysqld_safe[11014]: ended
Nov 11 20:56:40 localhost hcid[5863]: Can't open system message bus connection: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
Nov 11 20:56:41 localhost xinetd[5818]: Exiting...
Nov 11 20:56:48 localhost rpc.statd[5840]: Caught signal 15, un-registering and exiting.
Nov 11 20:56:48 localhost kernel: Kernel logging (proc) stopped.
Nov 11 20:56:48 localhost kernel: Kernel log daemon terminating.
Nov 11 20:56:48 localhost exiting on signal 15

[QUOTE=Xorg.0.log](II) I810(0): BIOS call 0x5f05 not supported, setting refresh with VBE 3 method.
(II) I810(0): xf86UnbindGARTMemory: unbind key 7
(II) I810(0): xf86UnbindGARTMemory: unbind key 0
(II) I810(0): xf86UnbindGARTMemory: unbind key 1
(II) I810(0): xf86UnbindGARTMemory: unbind key 3
(II) I810(0): xf86UnbindGARTMemory: unbind key 2
(II) I810(0): xf86UnbindGARTMemory: unbind key 4
(II) I810(0): xf86UnbindGARTMemory: unbind key 5
(II) I810(0): xf86UnbindGARTMemory: unbind key 6
(WW) I810(0): Successfully set original devices (2)[/QUOTE]

[QUOTE=messages]Nov 11 20:56:36 localhost gconfd (root-10543): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Nov 11 20:56:36 localhost gconfd (root-10543): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Nov 11 20:56:36 localhost gconfd (root-10543): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Nov 11 20:56:36 localhost gconfd (root-10543): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Nov 11 20:56:36 localhost gconfd (root-10543): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Nov 11 20:56:36 localhost gconfd (root-10543): GConf server is not in use, shutting down.
Nov 11 20:56:36 localhost gconfd (root-10543): Exiting
Nov 11 20:56:48 localhost kernel: Kernel logging (proc) stopped.
Nov 11 20:56:48 localhost kernel: Kernel log daemon terminating.
Nov 11 20:56:48 localhost exiting on signal 15[/QUOTE]

[QUOTE=debug]Nov 11 20:48:51 localhost xinetd[5818]: removing chargen
Nov 11 20:48:51 localhost xinetd[5818]: removing chargen
Nov 11 20:48:51 localhost xinetd[5818]: removing daytime
Nov 11 20:48:51 localhost xinetd[5818]: removing daytime
Nov 11 20:48:51 localhost xinetd[5818]: removing echo
Nov 11 20:48:51 localhost xinetd[5818]: removing echo
Nov 11 20:48:51 localhost xinetd[5818]: removing time
Nov 11 20:48:51 localhost xinetd[5818]: removing time
Nov 11 20:56:35 localhost NetworkManager: <debug info>^I[1163265995.302873] nm_print_open_socks (): Open Sockets List:
Nov 11 20:56:35 localhost NetworkManager: <debug info>^I[1163265995.303006] nm_print_open_socks (): Open Sockets List Done.[/QUOTE]

[QUOTE=bootstrap.log]gpg: key 437D05B5: "Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>" not changed
gpg: /etc/apt/trustdb.gpg: trustdb created
gpg: key FBB75451: public key "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>" imported
gpg: Total number processed: 2
gpg:               imported: 1
gpg:              unchanged: 1
gpg: no ultimately trusted keys found
gpg: keyring `/usr/share/keyrings/ubuntu-archive-removed-keys.gpg' created

Setting up ubuntu-minimal (0.119) ...[/QUOTE]

[QUOTE=dmesg][17179595.164000] EXT3-fs: mounted filesystem with ordered data mode.
[17179595.280000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179595.384000] kjournald starting.  Commit interval 5 seconds
[17179595.392000] EXT3 FS on hda13, internal journal
[17179595.392000] EXT3-fs: mounted filesystem with ordered data mode.
[17179595.392000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179595.496000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179595.496000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179595.496000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17179601.252000] NET: Registered protocol family 17
[/QUOTE]

[QUOTE=kern.log]Nov 11 20:48:52 localhost kernel: [17179686.504000] Bluetooth: HIDP (Human Interface Emulation) ver 1.1-mh1
Nov 11 20:48:52 localhost kernel: [17179686.520000] Bluetooth: RFCOMM socket layer initialized
Nov 11 20:48:52 localhost kernel: [17179686.520000] Bluetooth: RFCOMM TTY layer initialized
Nov 11 20:48:52 localhost kernel: [17179686.520000] Bluetooth: RFCOMM ver 1.7
Nov 11 20:48:56 localhost kernel: [17179690.564000] sound disabled
Nov 11 20:48:56 localhost kernel: [17179690.568000] Cannot find modem h/w supported by this driver
Nov 11 20:56:34 localhost kernel: [17180148.920000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Nov 11 20:56:34 localhost kernel: [17180148.920000] apm: disabled on user request.
Nov 11 20:56:48 localhost kernel: Kernel logging (proc) stopped.
Nov 11 20:56:48 localhost kernel: Kernel log daemon terminating.[/QUOTE]

[QUOTE=acpid][Sat Nov 11 20:56:30 2006] received event "button/lid LID0 00000080 00000001"
[Sat Nov 11 20:56:30 2006] notifying client 4397[0:0]
[Sat Nov 11 20:56:30 2006] client has disconnected
[Sat Nov 11 20:56:30 2006] notifying client 4596[108:108]
[Sat Nov 11 20:56:30 2006] executing action "/etc/acpi/lid.sh"
[Sat Nov 11 20:56:30 2006] BEGIN HANDLER MESSAGES
[Sat Nov 11 20:56:30 2006] END HANDLER MESSAGES
[Sat Nov 11 20:56:30 2006] action exited with status 1
[Sat Nov 11 20:56:30 2006] completed event "button/lid LID0 00000080 00000001"
[Sat Nov 11 20:56:41 2006] exiting[/QUOTE]

---

### Post by oxygenws on 2006-11-11
the last texts in the output, both in recovery and normal mode:

> Begin: Running /scripts/init-bottom ...
Done.
[XXXXXXXX.YYYYYY] usb 1-1: configuration #1 chosen from 1 choice

---

### Post by Jamsa on 2007-02-14
try to disable acpi .

---

