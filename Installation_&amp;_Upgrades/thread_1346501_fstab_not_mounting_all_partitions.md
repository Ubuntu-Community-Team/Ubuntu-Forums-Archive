---
title: "fstab not mounting all partitions"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by neilblue on 2009-12-05
Hello,

I have recently found a problem with fstab mounting some partitions. My current configuration have run fine for over a year, but after an upgrade about a week ago -ish (I don't reboot the machine unless there is a kernel upgrade) I found that some fstab mounts were not taking place.

Here is my fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

UUID=8be06026-82dc-408d-babb-ee27cf446223	/		ext3   relatime,errors=remount-ro 0       1
UUID=3c3976e6-9bac-435b-8da9-b1b4e507a629	/boot		ext3    relatime        0       2
UUID=7574b82b-bf06-4473-9111-dc05fe44847e	none		swap    sw              0       0
UUID=5569d79c-f228-4fcf-9713-0b8baec5dc05	none		swap    sw              0       0
UUID=fac3aa71-68ed-4d46-a6dd-1065425e0ece	/home/store	ext3	relatime 0 2

```

When I now boot, the /home/store partition is not mounted. If I try to run:

```

sudo mount -a

```

or 

```

sudo mount /dev/sdc1 /home/store

```

I get:

```

mount: /dev/sdc1 already mounted or /home/store busy

```

but df -h does not list it:

```

Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/vg0-root  222G  122G   89G  58% /
udev                  2.0G  336K  2.0G   1% /dev
none                  2.0G  196K  2.0G   1% /dev/shm
none                  2.0G  324K  2.0G   1% /var/run
none                  2.0G     0  2.0G   0% /var/lock
none                  2.0G     0  2.0G   0% /lib/init/rw
/dev/md0             1012M  139M  822M  15% /boot
/dev/sr1              4.0G  4.0G     0 100% /media/New

```

If however I boot with the /home/store line commented out of fstab, I can then manually mount /dev/sdc1 once I have logged in.

Can anyone help with this please. My suspicion at the moment is something to do with the gnome VFS, but that is little more than a guess.

Thanks
Neil

---

### Post by amauk on 2009-12-05
does the /home/store directory exist (and is it empty)?

---

### Post by neilblue on 2009-12-05
It does exist and is empty. I have had the system running for well over a year with the configuration until last week when there was an upgrade.

---

### Post by amauk on 2009-12-05
try using /dev/sdc1 instead of the UUID
(the uuid may have changed)

---

### Post by neilblue on 2009-12-05
Sorry I should have said that I have tried. I have also checked that the UUID has not changed.

---

### Post by oldfred on 2009-12-05
You have gone thru what I would think but a stab in the dark. Make sure it is umounted and run fsck. It may have a problem that you have not seen?

---

### Post by neilblue on 2009-12-05
Thanks for the suggestion oldfred, but that too was one of the first things I tried.

It just seems really strange that after the recent upgrade it stopped working. As a work around I have removed the fstab entry and added a mount call in rc.local. It works but it is a bit of a hack.

I also have a lot of cpu thermal errors in the logs (which seems to be a bug that is already recorded), and the printer drivers seem a bit messed up too since the upgrade :(

Thanks
Neil

---

