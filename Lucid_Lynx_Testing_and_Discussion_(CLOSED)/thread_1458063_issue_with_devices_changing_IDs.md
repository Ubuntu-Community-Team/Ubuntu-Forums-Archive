---
title: "issue with devices changing IDs"
date: 2010-04-19
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Cr0n_J0b on 2010-04-19
I have just installed 10.04 fresh onto my system.  I had Karmic running fine before, but decided on moving up.

I have about 11 hard drives that i run in the system.  My issue is that after installing Lucid, my devices seem to shift around randomly.  On the initial boot, my Maxtor drive might be /dev/sda, but on reboot a different drive will take over the /dev/sda slot.  I have installed without the DMRAID stuff (nodmraid) since that tended to hose my raid sets when i was using Karmic.

I just can't figure out what could be causing this.  I thought that it might be caused by a disk going bad, so i've tested with all sorts of differnt disk combinations and it still seems to happen.

any thoughts?

---

### Post by cariboo on 2010-04-19
Use uuid instead of the device label to mount a drive:

```
# / was on /dev/sda1 during installation
UUID=71e5211f-6be6-417f-958e-8b0dc9ae3f40 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda3 during installation
UUID=386d0109-5af3-45a1-a049-7d76a277fece /home           ext4    defaults        0       2
# swap was on /dev/sda2 during installation
UUID=53c80ab9-9fd1-412b-a4aa-5b2163e9e9b7 none            swap    sw              0       0

```

the above is what my fstab looks like. to find the uuid's of you drives, open a terminal and type:

```
sudo blkid
```

the output should look something like this:

```
sudo blkid
[sudo] password for me: 
/dev/sda3: UUID="1ed92b59-c6db-4ad3-a73d-17f6bed9bfc8" TYPE="ext4" 
/dev/sdb1: UUID="71e5211f-6be6-417f-958e-8b0dc9ae3f40" TYPE="ext4" 
/dev/sdb2: UUID="53c80ab9-9fd1-412b-a4aa-5b2163e9e9b7" TYPE="swap" 
/dev/sdb3: UUID="386d0109-5af3-45a1-a049-7d76a277fece" TYPE="ext4"
```

---

### Post by Cr0n_J0b on 2010-04-19
thanks for the suggetion.  my issue is that I'm building the devices into raid sets and the sets seemt to keep getting hosed when I reboot and the IDs change.

---

### Post by Cr0n_J0b on 2010-04-19
Well I tried adding dmraid back in with the package manager and it's still flipping my devices around like crazy

---

### Post by StuartN on 2010-04-19
> **Cr0n_J0b said:**
> any thoughts?

This was happening in 9.10, but I have not seen any resolution of the cause nor any solution.

---

### Post by Cr0n_J0b on 2010-04-19
Well I don't really know what to say.  I added the dmraid back in and the devices are still shifting around, but at least my raid drives are now sticking.

wierd stuff.

---

