---
title: "Can't chainload Windows since grub update"
date: 2009-08-27
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by VMC on 2009-08-27
Thee have been several updates today, and one involved grub. When I rebooted I can no longer boot Windows.It complained about C/H/S.

What I had to do was edit grub.cfg as so, for Windows to work:

```
menuentry "Windows XP (on /dev/sda1)" {
	set root=(hd0,1)
#	search --no-floppy --fs-uuid --set e2444e41444e1925
#	drivemap -s (hd0) ${root}
	chainloader +1
}
```

BLKID:
```
/dev/sda1: UUID="**E2444E41444E1925**" LABEL="XPSP3" TYPE="ntfs" 
/dev/sda5: UUID="6FAAFC6330D89A83" LABEL="DOWNLOADS" TYPE="ntfs" 
/dev/sda6: UUID="3c09b1da-04e4-49a0-bc64-8edef15610df" TYPE="swap" 
/dev/sda7: LABEL="karmic" UUID="1aaf00ab-be7a-4d50-92ab-af29618ac473" TYPE="ext4" 
/dev/sda8: LABEL="Fedora-11" UUID="5dbd9c5c-b1de-489a-a3da-6c3d7fe3ddd3" TYPE="ext4" 
/dev/sda9: LABEL="jaunty" UUID="5d67fd00-0856-4ce1-b278-9acf3e926a5c" TYPE="ext4" 
/dev/sda10: UUID="715f6e42-c092-4875-9e4c-da8dc2683c27" TYPE="ext4" 
/dev/sda11: UUID="3e5e53ec-b2cb-463e-993d-06ce71f82e07" SEC_TYPE="ext2" TYPE="ext3" 
```


Nothing regarding Windows partition has changed. Anyone else with this issue?

---

### Post by yelo3 on 2009-08-28
This also happens to me. Let me know if you find something

---

### Post by dinxter on 2009-08-28
hmmm, i'm sure ${root} should have expanded on running script.
looking at /etc/grub.d/30_os-prober
should,
drivemap -s (hd0) \${root}

not be,
drivemap -s (hd0) ${root}

try changing that before running update-grub and seeing if grub.cfg shows the proper drivemap command

[EDIT] sorry, i dont have windows at the moment to test it out

---

### Post by cecilpierce on 2009-08-28
In grub.cfg:
menuentry "Windows XP  (on /dev/sda1)" {
        insmod ntfs
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set 169cf1cc9cf1a681
        drivemap -s (hd0) ${root}
        chainloader +1

Just tried booting windows and it worked OK but it does say in os-prober:
if [ "${LONGNAME}" != "Windows Vista (loader)" ] ; then
        cat << EOF
        drivemap -s (hd0) \${root}

---

### Post by dinxter on 2009-08-28
> **dinxter said:**
> hmmm, i'm sure ${root} should have expanded on running script.
looking at /etc/grub.d/30_os-prober
should,
drivemap -s (hd0) \${root}

not be,
drivemap -s (hd0) ${root}

try changing that before running update-grub and seeing if grub.cfg shows the proper drivemap command

[EDIT] sorry, i dont have windows at the moment to test it out
 
Ignore this, this is rubbish :) ah fridays...

---

### Post by VMC on 2009-08-28
> **cecilpierce said:**
> In grub.cfg:
menuentry "Windows XP  (on /dev/sda1)" {
        insmod ntfs
        set root=(hd0,1)
        search --no-floppy --fs-uuid --set 169cf1cc9cf1a681
        drivemap -s (hd0) ${root}
        chainloader +1

Just tried booting windows and it worked OK but it does say in os-prober:
if [ "${LONGNAME}" != "Windows Vista (loader)" ] ; then
        cat << EOF
        drivemap -s (hd0) \${root}

I think the key to it booting is the insmod. I hadn't noticed that before. (insmod ntfs). It's missing on my menu.

---

### Post by cecilpierce on 2009-08-28
VMC, check your UUID, in blkid you have capital 'E' and in grub.cfg its a small 'e' ???

---

### Post by Robstarusa on 2009-08-28
I have this same issue.

This is what the CLI looks like if I go to edit it at the grub menu screen:

insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set 4a30c94a30c93e27
drivemap -s (hd0) ${root}
chainloader +1


If I select windows, it just hangs with the cursor in the upper left corner of the screen, forever.

I have already booted the XP cd and run fixboot on the C:\ partition (recovery cd can see it).

The only difference from a normal install is that the first partition is at the 1MB mark (it is aligned on an SSD).

Any hints how to fix this ?

Rob

---

