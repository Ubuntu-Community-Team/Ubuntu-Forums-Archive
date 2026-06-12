---
title: "Trying to upgrade from 8.04 to 10.04, but only 8.10 is offered?"
date: 2010-10-12
forum: Installation &amp; Upgrades
---

### Post by dishbert on 2010-10-12
I've updated 8.04, rebooted, and update manager shows the system is up to date, but 8.10 is shown as the new available release.

Did I miss the "best by" date for 10.04.1?

---

### Post by lisati on 2010-10-12
No, you didn't do anything wrong. The usual path using update manager is to the next release, which isn't necessarily the newest version.

---

### Post by dishbert on 2010-10-12
Thanks for the reply lisati.

I thought it was possible to upgrade from an LTS version to the next LTS version directly.

Am I wrong on this?

---

### Post by kostkon on 2010-10-12
> **dishbert said:**
> Thanks for the reply lisati.

I thought it was possible to upgrade from an LTS version to the next LTS version directly.

Am I wrong on this?
No, you aren't. You can upgrade from 8.04 to 10.04 indeed. Try opening your software sources (System &#8594; Administration &#8594; Software Sources or in Synaptic select Settings &#8594; Repositories), select the Updates tab and make sure that the Release Upgrade is set to LST releases. Press Close and then Reload.

---

### Post by ssam on 2010-10-12
LTS to new LTS should work. can you check in system->administation->software sources on the updates tab. there is an option as to whether it shows new distro releases for normal releases or LTS ones.

(other wise a back up and reinstall might be worth it. it can work out quicker)

---

### Post by dishbert on 2010-10-12
Thank you very much ssam and kostkon, I changed the software update tab to LTS, and I'm good to go.

I just knew it had to be something simple like that!

---

### Post by mörgæs on 2010-10-12
Just remember that you will end with a 10.04 running on Grub 1, not Grub 2. Upgrading Grub (if you want to) is a step in itself. 

A clean install is always worth considering.

---

### Post by dishbert on 2010-10-12
Thanks, mörgæs, I'll keep that in mind.  

Grub 1 has always worked well for me on dual and triple boot systems, but I'll look into Grub 2 to see if has some advantages for me.

The upgrade is still in progress.  I'll report back upon completion.

---

### Post by dishbert on 2010-10-12
OK, the upgrade seemed to go well until I rebooted.  Then the Grub boot sequence showed only the old 8.04 and XP options with no 10.04 option.  The system boots to XP fine, but booting to 8.04 gives a seg fault saying that:

/dev/disk /byuuid/ddf7a82e-ebca-4dfe-b571-6bb568be614d Does not exist.

I've had a problem like this before, got advise from this forum, and solved it by comparing the output of bllkid with the contents of /etc/fstab and editing /etc/fstab with the correct uuid.

Now, the output of blkid is:

ubuntu@ubuntu:~$ blkid -c -o
ubuntu@ubuntu:~$ blkid 
ubuntu@ubuntu:~$ sudo blkid -c -o
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="B69828159827D2A3" TYPE="ntfs" 
/dev/sda5: UUID="ddf7a82e-ebca-4dfe-b571-6bb568be614d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="cb944276-6f8b-4cae-bef6-12d573557e92" TYPE="swap" 
/dev/sdb1: LABEL="DRV2_VOL1" UUID="6250A65050A62B2D" TYPE="ntfs" 
/dev/sdb5: LABEL="DRV2_VOL2" UUID="28A6-7066" TYPE="vfat" 
/dev/sdb6: UUID="e473d790-129c-4f55-926d-0ce11db19c57" SEC_TYPE="ext2" TYPE="ext3" 

But /etc/fstab looks like this:

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0

As I remember it, last time I ran into this, it was obvious what to edit, but this time I'm stuck.

---

### Post by kostkon on 2010-10-13
> **dishbert said:**
> OK, the upgrade seemed to go well until I rebooted.  Then the Grub boot sequence showed only the old 8.04 and XP options with no 10.04 option.  The system boots to XP fine, but booting to 8.04 gives a seg fault saying that:

/dev/disk /byuuid/ddf7a82e-ebca-4dfe-b571-6bb568be614d Does not exist.

I've had a problem like this before, got advise from this forum, and solved it by comparing the output of bllkid with the contents of /etc/fstab and editing /etc/fstab with the correct uuid.

Now, the output of blkid is:

ubuntu@ubuntu:~$ blkid -c -o
ubuntu@ubuntu:~$ blkid 
ubuntu@ubuntu:~$ sudo blkid -c -o
/dev/loop0: TYPE="squashfs" 
/dev/sda1: UUID="B69828159827D2A3" TYPE="ntfs" 
/dev/sda5: UUID="ddf7a82e-ebca-4dfe-b571-6bb568be614d" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="cb944276-6f8b-4cae-bef6-12d573557e92" TYPE="swap" 
/dev/sdb1: LABEL="DRV2_VOL1" UUID="6250A65050A62B2D" TYPE="ntfs" 
/dev/sdb5: LABEL="DRV2_VOL2" UUID="28A6-7066" TYPE="vfat" 
/dev/sdb6: UUID="e473d790-129c-4f55-926d-0ce11db19c57" SEC_TYPE="ext2" TYPE="ext3" 

But /etc/fstab looks like this:

aufs / aufs rw 0 0
tmpfs /tmp tmpfs nosuid,nodev 0 0
/dev/sda6 swap swap defaults 0 0

As I remember it, last time I ran into this, it was obvious what to edit, but this time I'm stuck.
Something along the lines of?:
```
# /dev/sda5
UUID=ddf7a82e-ebca-4dfe-b571-6bb568be614d / ext3 defaults,errors=remount-ro 0 1
```

---

### Post by dishbert on 2010-10-13
Thanks again Kostkon, but I'm not sure exactly what you mean.

Should I try inserting the lines:

# /dev/sda5
UUID=ddf7a82e-ebca-4dfe-b571-6bb568be614d / ext3 defaults,errors=remount-ro 0 1

into the /etc/fstab file/

I did manage a work around to boot 10.04 by copying the revised menu.lst from the upgraded partition to the old Mint partition after I determined that's where the system was booting.

---

