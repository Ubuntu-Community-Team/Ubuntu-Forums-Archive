---
title: "esata removable drive setup"
date: 2008-02-09
forum: Installation &amp; Upgrades
---

### Post by AnimalMagic on 2008-02-09
How do I install and make an esata drive hot swappable?

I have installed the card and ubuntu detects it if the drive is switched on when booting, but I want to be able to swap it around with other similar external drives.

Drive is a Seagate 500gb drive.

---

### Post by bogolisk on 2008-03-06
It highly depends on the SATA driver for your SATA controller (usually the southbridge.) AHCI compliant controllers have the best linux driver support. My mobo sb, a MCP51 (nforce430), *does* support hotswap but linux's sata_nv driver *doesn't enable that irq* for mcp51, thus I have to do *coldplug* instead of hotplug.

My eSATA disc is connected to SATA port4. So to cold-plug the disc:
```

       sudo scsiadd -s 4 0

```
or if you don't have scsiadd:
```

       sudo sh -c 'echo 0 - 0 > /sys/class/scsi_host/host4/scan'

```

To cold-UNplug the disc (reset the port, spindown the disc, ...):
```

       sudo scsiadd -r 4 0 0 0

```
without scsiadd:
```

      sudo sh -c '  echo 1 > "/sys/class/scsi_disk/4:0:0:0/device/delete"  '

```

Now, to get hal to automount the plugged in disc under /media/ you have to comment out the section in /etc/hal/fdi/preferences.fdi that say *not* to automount *non-removable* volumes:
```

<!--
  <device>
    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      </match>
    </match>
  </device>
-->

```

Once all that were done, the disc would be mount under /media/<PARTITION_LABEL>

Goodluck

---

