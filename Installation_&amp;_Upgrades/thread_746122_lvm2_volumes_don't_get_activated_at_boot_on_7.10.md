---
title: "lvm2 volumes don't get activated at boot on 7.10"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by Peter Westley on 2008-04-05
I have a fresh install of 7.10 server with a couple of l-vols created for backuppc and mythtv storage. Root and boot are on raid1 filesystems and this all works fine.

Problem is when I reboot, it seems the [FONT="Courier New"]vgchange -a y[/FONT] command is not being issued, or if it is, it's too early and all needed modules aren't yet loaded (I'm guessing on this last point)

I see an error flash past during boot "[FONT="Courier New"][COLOR="Red"][FAIL][/COLOR][/FONT]" instead of the usual [FONT="Courier New"]"[OK]"[/FONT], but can't see what it is (by the way, where does one see logs of the boot messages? I have looked evrywhere in /var/log but can't find anything)

After the system finishes booting, the filesystems are not mounted. If I issue

[FONT="Courier New"]# vgchange -a y
# mount -a

[/FONT]All the lvols are mounted correctly.

It's not that the lvols aren't working, it's just that they don't get activated and therefore mounted at the right time.

Clues?

Thanks,
Peter

---

### Post by Peter Westley on 2008-04-11
Fixed:

It seems that lvm2 *should* get started automagically but this isn't happening.

The [tldp lvm how-to]("http://tldp.org/HOWTO/LVM-HOWTO/lvm2_boot.html") says that initrd should have:

```
dmsetup mknodes
vgscan --ignorelockingfailure
vgchange -ay --ignorelockingfailure
```

In the mkinitrd script. I don't understand mkinitrd yet so I decided to use the lvm init.d script (also found in the [tldp lvm how-to]("http://tldp.org/HOWTO/LVM-HOWTO/initscriptdebian.html")) instead:

```
#!/bin/sh

case "$1" in
  start)
	/sbin/vgscan
	/sbin/vgchange -ay
        ;;
  stop)
	/sbin/vgchange -an
        ;;
  restart|force-reload)
	;;
esac

exit 0
```

Now it works.

Now it's time to understand mkinitrd...

---

