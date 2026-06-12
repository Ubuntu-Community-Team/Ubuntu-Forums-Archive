---
title: "Bootable USB wont boot"
date: 2008-11-17
forum: Installation &amp; Upgrades
---

### Post by Chuchaqui on 2008-11-17
I have been trying to install Ubuntu 8.10 using the usb-creator tool on 8.10 but the drive isn't bootable. Every time I reboot and tell my computer to boot from the drive all that comes up is a semicolon (';') and nothing happens. When I then click a button (any button) my computer proceeds to boot normally, as though the drive wasn't plugged in to begin with. The flashdrive is a 'Kingston DataTravler 2.0'. I have tried running the usb-creator regularly ('$usb-creator') and in safe mode ('$usb-creator -s').

Installation Output:
```

####@##########:~$ usb-creator -s

-- Starting up at 20:40:32 --
[20:40:32] new device:
{'capacity': dbus.UInt64(999554560L), 'uuid': '722E-ED09', 'label': '', 'free': 997564416L, 'fstype': 'vfat', 'device': '/dev/sdb1', 'mountpoint': '/media/disk', 'udi': '/org/freedesktop/Hal/devices/volume_uuid_722E_ED09'}
[20:40:32] adding: /dev/sdb1
[20:40:42] mounting /home/rob/Torrents/ubuntu-8.10-desktop-i386.iso
[20:40:42] updating dest_status as part of update_row_state
[20:40:48] Installing...
[20:40:48] Source CD: /home/rob/Torrents/ubuntu-8.10-desktop-i386.iso
[20:40:48] Destination disk: /dev/sdb1
[20:40:48] Persistence size: 242 MB
[20:40:48] Marking partition 1 as active.
[20:40:48] installing the bootloader to /dev/sdb1.
[20:40:49] ['/usr/share/usb-creator/install.py', '-s', '/tmp/tmpPL9K0w/.', '-t', '/media/disk', '-p', '242']
[20:50:10] Unmounting source volume.
[20:50:11] Install command exited with code: 0
#####@############:~$ 

```

I've also tried using the USB on other computers with the same result.
I have also tried downloading new '.iso's and using those with the same result.

---

### Post by C.S.Cameron on 2008-11-17
This seems to be a common problem with 8.10's install tool and Kingstons over 2GB.
The only solution I have found found is to first install 8.10 using Unetbootin, then erase the Unetbootin files and then install using the 8.10 tool.
The 8.10 tool will allow persistence where as Unetbootin takes a bit more work to get persistence.

---

