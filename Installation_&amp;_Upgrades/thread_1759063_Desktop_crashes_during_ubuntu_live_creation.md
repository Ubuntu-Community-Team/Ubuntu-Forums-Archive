---
title: "Desktop crashes during ubuntu live creation"
date: 2011-05-15
forum: Installation &amp; Upgrades
---

### Post by cccc on 2011-05-15
hi

I try to create natty live using live-build and during creation Gnome Desktop crashes and goes to the Login Mask:

```

# lb config -p xubuntu_desktop --mode ubuntu --distribution natty -b usb-hdd 
# lb build

# tail -f /var/log/messages

May 13 16:37:50 ubuntu kernel: [17280.668731] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on tmds encoder (output 2)
May 13 16:39:31 ubuntu sudo: pam_sm_authenticate: Called
May 13 16:39:31 ubuntu sudo: pam_sm_authenticate: username = [ubuntu]
[B][COLOR="Red"]May 13 16:39:34 ubuntu kernel: [17384.416036] end_request: I/O error, dev fd0, sector 0
May 13 16:39:34 ubuntu kernel: [17384.440030] end_request: I/O error, dev fd0, sector 0
May 13 16:48:48 ubuntu init: /home/ubuntu/test/chroot/etc/init: Configuration directory deleted
May 13 17:06:09 ubuntu console-kit-daemon[813]: WARNING: Couldn't read /proc/27353/environ: 
Failed to open file '/proc/27353/environ': No such file or directory
May 13 17:06:09 ubuntu NetworkManager[801]: <warn> error requesting auth for org.freedesktop.NetworkManager.network-control: (3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: 
Could not get UID of name ':1.60': no such name
May 13 17:06:09 ubuntu NetworkManager[801]: <warn> User connections unavailable: 
(3) GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID of name ':1.60': no such name[/COLOR][/B]
May 13 17:06:12 ubuntu acpid: client 19132[0:0] has disconnected
May 13 17:06:12 ubuntu acpid: client connected from 27240[0:0]
May 13 17:06:12 ubuntu acpid: 1 client rule loaded
```

What's wrong and howto solve this problem?

---

### Post by dino99 on 2011-05-15
what im seeing is "fd0" (eg your floppy drive), check its empty or better disable it into bios (of course you are not trying to boot on it ?)

---

### Post by cccc on 2011-05-15
> **dino99 said:**
> what im seeing is "fd0" (eg your floppy drive), check its empty or better disable it into bios (of course you are not trying to boot on it ?)

Floppy drive is empty, but I'll try to disable the floppy drive in the bios.

---

### Post by cccc on 2011-05-16
Floppy drive is disabled now in the bios and it doesn't help, this problem still occurs.

---

### Post by cccc on 2011-05-27
still cannot find a solution for this problem.

---

### Post by cccc on 2011-06-13
BTW has someone sucessfully created naty usb-hdd live?

---

