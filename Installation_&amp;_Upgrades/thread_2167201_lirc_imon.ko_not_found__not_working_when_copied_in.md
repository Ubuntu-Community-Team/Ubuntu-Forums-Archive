---
title: "lirc_imon.ko not found / not working when copied in"
date: 2013-08-12
forum: Installation &amp; Upgrades
---

### Post by z7APXKm on 2013-08-12
I'm trying to get my IMON (pad?) remote working on Ubuntu 12.04.2 LTS (kernel version Linux Myth 3.5.0-26-generic).

I started by performing a clean install of lirc, but I got the following error:

```

# modprobe lirc_imon

FATAL: Could not read '/lib/modules/3.5.0-26-generic/kernel/drivers/staging/media/lirc/lirc_imon.ko': No such file or directory

```

So I did a locate:

```

# locate lirc_imon.ko

/lib/modules/3.5.0-26-generic/kernel/drivers/staging/media/lirc/lirc_imon.ko

```

...but it didn't exist.

I thought I could maybe restore the file from backup , but then a modprobe gave me a different message:

```

FATAL: Error inserting lirc_imon (/lib/modules/3.5.0-26-generic/kernel/drivers/staging/media/lirc/lirc_imon.ko): Invalid argument

```

From the syslog:

```

Aug 12 23:42:02 Myth kernel: [ 2583.556188] imon 1-1.1:1.0: Looks like you're trying to use an IR protocol this device does not support
Aug 12 23:42:02 Myth kernel: [ 2583.556193] imon 1-1.1:1.0: Unsupported IR protocol specified, overriding to iMON IR protocol
Aug 12 23:42:10 Myth kernel: [ 2591.631517] lirc_imon: module is from the staging directory, the quality is unknown, you have been warned.
Aug 12 23:42:10 Myth kernel: [ 2591.631641] lirc_imon: disagrees about version of symbol lirc_register_driver
Aug 12 23:42:10 Myth kernel: [ 2591.631644] lirc_imon: Unknown symbol lirc_register_driver (err -22)

```

Can anybody help?

---

