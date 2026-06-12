---
title: "Boot to black screen"
date: 2011-04-25
forum: Installation &amp; Upgrades
---

### Post by jago25_98 on 2011-04-25
I upgraded from I don't know what revision to something newer and all I'm getting on bootup is a black screen. This happens even with `init =/bin/bash` appended to the boot line in grub. 

 I'm now trying to figure out more info on it. 

 I tried mounting / with ext2fs from Windows but that makes the fs look unreadable in that I can't only see the root directory but nothing deeper than one level - i.e. I can see /usr, but not /usr/bin. I put this down to upgrading to ext4, which is mentioned now on boot. 

 Once booted I get a black screen but I can use alt-sysRq-r, then e to terminate all tasks. I briefly get a screen showing X and then it falls back to the various terminals, but none of these terminals are responsive to commmands. They do give some info of services loaded but nothing that would seem helpful. I'll have to take a photo! 
It's the same with various kernel options I kept installed (not out of choice, more that grub2 is a pain to get rid of these options when you want to keep the old kernels installed as a fallback, but that's another matter!

 What can I search for to find info on this problem? 

 How can I find out more about what's going on? 

 Is there a ext4 driver for win32 I need - does that explain being able to read only some of the filesystem? 

 Is appending `init=/bin/bash` to the end of the kernel boot line actually not working?

---

### Post by dino99 on 2011-04-25
how making installation:


[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by jago25_98 on 2011-04-25
It was already installed. I'll try to find a live install CD. 

I share / with /home and use some separate partitions for storage. It's an overly complex partitioning setup setover from previous installs with some laziness on my part in terms of not getting rid of the old home directory and old ubuntu install

---

### Post by Dutch70 on 2011-04-25
Have you tried nomodeset or other boot options? 
[[COLOR="Red"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by jago25_98 on 2011-04-27
Yes I've tried nomodeset . 

Part of it might be that before I had it going into X automatically. alt+f1 etc terminals don't respond until I use alt+sysRq+e to terminate all tasks. After that I still don't get a terminal but I can see logging output. 

I'll paste my /var/log/messages, debug & error here(rescued with backtrack):

[http://pastebin.com/WA4mbkKN](http://pastebin.com/WA4mbkKN)

Some highlights:
Apr 27 02:54:12 laptop pulseaudio[1233]: module.c: Failed to load  module "module-console-kit" (argument: ""): initialization failed.
```

Apr 27 02:52:24 laptop kernel: [    0.681492]   alloc irq_desc for 21 on node -1
Apr 27 02:52:24 laptop kernel: [    0.681495]   alloc kstat_irqs on node -1
Apr 27 02:52:24 laptop kernel: [    0.681563] uhci_hcd 0000:00:1a.1: setting latency timer to 64
Apr 27 02:52:24 laptop kernel: [    0.682251] uhci_hcd 0000:00:1d.0: setting latency timer to 64
Apr 27 02:52:24 laptop kernel: [    0.682933] uhci_hcd 0000:00:1d.1: setting latency timer to 64
Apr 27 02:52:24 laptop kernel: [    0.683614] uhci_hcd 0000:00:1d.2: setting latency timer to 64
Apr 27 02:52:24 laptop kernel: [    0.691328] PM: Resume from disk failed.
Apr 27 02:52:24 laptop kernel: [    0.851081] sr 0:0:0:0: Attached scsi CD-ROM sr0
Apr 27 02:52:24 laptop kernel: [    1.454291] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
Apr 27 02:52:24 laptop kernel: [    2.127463] b43-pci-bridge 0000:0c:00.0: setting latency timer to 64
Apr 27 02:52:24 laptop kernel: [    3.592644] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[354fc00037715470]
Apr 27 02:52:24 laptop kernel: [   24.140246] i915 0000:00:02.0: setting latency timer to 64
Apr 27 02:52:24 laptop kernel: [   24.145924]   alloc irq_desc for 27 on node -1
Apr 27 02:52:24 laptop kernel: [   24.145929]   alloc kstat_irqs on node -1
Apr 27 02:52:24 laptop kernel: [   24.145941] i915 0000:00:02.0: irq 27 for MSI/MSI-X

```
```

init: udevtrigger main process (408) terminated with status 1
 
init: udevtrigger post-stop process (411) terminated with status 1
 
init: udevmonitor main process (407) killed by TERM signal
 
/dev/sda11: clean, 289956/1893120 files, 3803134/7570623 blocks

```
```

Apr 25 12:37:04 laptop gnome-session[637]: WARNING: Could not connect to ConsoleKit: Could not get owner of name 'org.freedesktop.ConsoleKit': no such name

Apr 25 12:40:38 laptop init: Unable to connect to the system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: Connection refused

```
```

/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:02/input/input9
Apr 27 02:52:25 laptop kernel: [   24.861523] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
Apr 27 02:52:25 laptop kernel: [   24.861558] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Apr 27 02:54:14 laptop kernel: [  134.037594] SysRq : Keyboard mode set to system default
Apr 27 02:54:15 laptop kernel: [  134.946942] SysRq : Emergency Sync
Apr 27 02:54:15 laptop kernel: [  134.947181] Emergency Sync complete
Apr 27 02:54:16 laptop kernel: [  135.258380] SysRq : Terminate All Tasks
Apr 27 02:54:16 laptop kernel: imklog 4.2.0, log source = /proc/kmsg started.
Apr 27 02:54:16 laptop rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="1251" x-info="http://www.rsyslog.com"] (re)start
Apr 27 02:54:16 laptop rsyslogd: rsyslogd's groupid changed to 102
Apr 27 02:54:16 laptop rsyslogd: rsyslogd's userid changed to 101
Apr 27 02:54:16 laptop kernel: [  135.362410] udev: starting version 151
Apr 27 02:54:17 laptop kernel: [  136.543572] SysRq : Power Off
Apr 27 02:54:17 laptop kernel: [  136.543640] md: stopping all md devices
```

---

### Post by jago25_98 on 2011-05-06
any tips to help diagnose this?

---

