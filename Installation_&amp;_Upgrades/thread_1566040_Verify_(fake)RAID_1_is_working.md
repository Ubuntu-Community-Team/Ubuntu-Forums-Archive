---
title: "Verify (fake)RAID 1 is working"
date: 2010-09-01
forum: Installation &amp; Upgrades
---

### Post by FreeThePenguin on 2010-09-01
*I am not booting from raid*

I am using a PCI controller and have setup a raid1 in the cards bios.  Both disks show up seperatly in the disk utility.  I can mount the source disk but get an error mounting the mirror disk.  dmraid shows the mirror.  My question is by writing to the source disk will the mirror disk automatically (by pci controller) be mirrored? I have nothing listed under /dev/mapper, it seems for this to work right i would need to map the "raid disk" vs the physical disk.  Since i cannot mount the mirror drive is there any way to verify that the data is duplicating without removing the drives?

---

### Post by FreeThePenguin on 2010-09-02
i forgot to mention this is ubuntu 10.4 and the pci card is a VIA chipset.  Since there is nothing in /dev/mapper do i need to manualy add it, if so, how?

```

sudo dmraid -r
/dev/sdc: via, "via_bgffibdbch", mirror, ok, 1953525167 sectors, data@ 0
/dev/sdb: via, "via_bgffibdbch", mirror, ok, 1953525167 sectors, data@ 0

sudo dmraid -ay
RAID set "via_bgffibdbch" was not activated

```

---

### Post by epud on 2011-01-29
I am on a quest to figure out the same. What I did notice however is that when I installed dmraid from the Synaptic Package Manager, the two separate drives now show up as one. Maybe it is worth giving a try?

---

### Post by ronparent on 2011-01-29
In a terminal write 'sudo dmraid -ay'. If the message indicates the raid are already active, then the raid1 is functioning as intended. If the message is that the raid drive are now activated then we have to determine why it is not happening on boot! Post how you make out.

I see you are already getting:
> sudo dmraid -ay
RAID set "via_bgffibdbch" was not activated
Until they are activated no mirroring will occur.

---

### Post by epud on 2011-01-29
Then I guess mine are active :P

My output looked like this:

```
RAID set "pdc_gjgbcdghd" already active
RAID set "pdc_gjgbcdghd1" already active
```

---

### Post by nogoodnamesleft on 2011-01-29
> **FreeThePenguin said:**
> *I am not booting from raid*

I am using a PCI controller and have setup a raid1 in the cards bios. Both disks show up seperatly in the disk utility. I can mount the source disk but get an error mounting the mirror disk. dmraid shows the mirror. My question is by writing to the source disk will the mirror disk automatically (by pci controller) be mirrored? I have nothing listed under /dev/mapper, it seems for this to work right i would need to map the "raid disk" vs the physical disk. Since i cannot mount the mirror drive is there any way to verify that the data is duplicating without removing the drives?

why are you writing separately to the disks? you want to mount the array and write to the array.

i do raid with mdadm

i partition manually

then mdadm --create to make it, and --assemble to start it

put it in /etc/fstab to automount it at boot time

check status with cat /proc/mdstat

check out mdadm guides on the web

in maverick i had to use UUIDs in mdadm conf file as the order in which the drives are assigned their names (sda, sdb etc) seems to be random

give me a sec to login and get my config files

edit: OK here they are

I see I did

mdadm --create /dev/md0 --level=1 --raid-devices=2 /dev/sdb1 /dev/sdc1

to create

then i had to use blkid to get the UUIDs of the devices

then i have

ARRAY /dev/md0 UUID=...

in the /etc/mdadm/mdadm.conf

(Only one UUID is needed, that command assembles a raid containing partitions with that matching UUID)

then just mount /dev/md0 as normal and start writing to it

dont forget to tell it to send email notifications if the array status changes (i.e. a drive breaks)

---

