---
title: "Grub issues - boot-repair fail for LVM with seperate /boot"
date: 2012-05-21
forum: Installation &amp; Upgrades
---

### Post by heyasam on 2012-05-21
Having all sorts of problems, production server offline for a while now, help greatly appreciated -

Please note the following URL: [http://paste.ubuntu.com/1000002/](http://paste.ubuntu.com/1000002/)

During the boot-repair process, I get this error:

Auto-detection of a filesystem module failed
Please specify the module with the option `--modules' explicitly.
grub-probe: error: cannot find a device for / (is /dev mounted?).
grub-probe: error: cannot find a device for /boot (is /dev mounted?).
grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).


It may have something to do with this system previously had fakeraid setup?  Because of running into so many problems, I removed one of the mirrored drives, and now just trying to get up as a single harddrive without raid, but running into similar problems.  I haven't been game yet to run something like dmraid -e and not sure if this is necessary?

---

### Post by darkod on 2012-05-21
Hold on, are you trying to run it as degraded array with one disk missing, or a standard install on one disk without any raid?

In case you want a none-raid install you should have cleared the meta data with something like:
sudo dmraid -E -r /dev/sda

On the other hand, if you want to run it as degraded array, don't run that command, leave the meta data.

In any case, not sure if boot-repair can do LVM, so you better do it manually.

From live mode, install lvm2 first to operate LVM:
sudo apt-get install lvm2

Activate the LVM:
sudo vgchange -a y

Double check the LVs:
sudo lvscan

Your /boot seems to be sda5, so the grub2 reinstall would be like:
sudo mount /dev/mapper/cds-root /mnt
sudo mount /dev/sda5 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sda

Also, open sda5 and remove the /boot/grub/core.img file, you don't need it. I guess that's because boot-repair was confused. Since sda5 is a /boot partition, it should only have /grub/grub.cfg and /grub/core.img.

The /boot part is already implemented in the mount point so /boot/geub/core.img is not correct.

---

### Post by heyasam on 2012-05-21
Thanks, but still a bit stuck. 

Following your instructions and deleting the /boot/grub/core.img file I can install grub but end up with only a grub> prompt on boot.  

If I try also the following so that I can get a grub menu to boot from (much needed for me) then I get the following error

sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt

root@ubuntu:/# sudo grub-mkconfig
sudo: unable to resolve host ubuntu
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).


... I only disconnected a raid drive in desperation to try to make things easier.  Should I reconnect the other mirrored raid drive and turn raid back on in bios ?  Or should I run sudo dmraid -E -r /dev/sda ?  Or doesn't matter?  I don't need to have raid, just set it up many years ago as good practice.

... Would it be easier if I boot from the grub prompt?  How do I do this?  If I do

linux /vmlinux-x.x.x-x-xxxxxx root=/dev/sda1 ro
boot

It crashes, says something about adding raid=noautodetect, though adding that command at grub prompt before linux /vmlinux etc.  still crashes?

---

### Post by heyasam on 2012-05-22
Still stuck

I ran sudo dmraid -E -r /dev/sda

Then re ran
sudo apt-get install lvm2
sudo vgchange -a y
sudo lvscan
sudo mount /dev/mapper/cds-root /mnt
sudo mount /dev/sda5 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sda

All good, except it brings me only a grub prompt - what do I do from here?  If I can't rebuild the boot menu, how can I boot from grub prompt?

Tried a few combinations like this, but nothing boots, says problems with root or something

insmod lvm
set root=(cds-root)
linux /vmlinux-xx-xxxx-xx-server root=/dev/mapper/cds-root
boot

crash...?  any ideas?

---

### Post by darkod on 2012-05-22
First of all, when preparing for the chroot did you also mount the root LV and the /boot?

And when you are inside the chroot you don't use sudo, you are already inside your installation as root user.

I would try it again, and in the chroot completely to remove grub2 and reinstall it. So, something like:
```
sudo apt-get install lvm2
sudo vgchange -a y
sudo lvscan
sudo mount /dev/mapper/cds-root /mnt
sudo mount /dev/sda5 /mnt/boot
sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

After that you are inside the installation as root. Clear up grub2 and install again:
```
apt-get remove --purge grub-pc grub-common
apt-get install grub-pc
grub-mkconfig
update-grub
grub-install /dev/sda
```

Exit the chroot and unmount all:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt/boot
sudo umount /mnt
```

Restart and see if it helped. I don't know if this is because the raid is removed, but note that you can't just play like that. If you don't need the raid any more, at some point make a clean install on a single disk.
Lets see if this works.

---

### Post by heyasam on 2012-05-22
Need to change this to 'solved' - can't seem find where to do that on the reply form.

Anyway, many thanks Darko.  Your instructions got me there in the end, though called in some additional tech support, so not sure if removing and reinstalling kernels made any difference, and / or booting using the alternate install cd into recovery prompt, but primarily this is what ended up working  (apologies if a command missing from this list, or slight typo)

sudo apt-get install lvm2
sudo vgchange -a y
sudo lvscan
sudo mount /dev/mapper/cds-root /mnt
sudo mount /dev/sda5 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sda

Then reboot and startup brings to grub prompt:

insmod lvm
set root=(cds-root)  (might have left this one out, can't remember)
linux /vmlinux-xx-xxxx-xx-server root=/dev/mapper/cds-root ro
initrd /initraxxxx
boot

First time boot it crashed, though much further through the boot.  Reboot again and now fine.  Then once booted up purged and reinstalled grub (and other grub commands) and actually ran without error this time.  Was getting before a lot of /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

Yes shouldn't have played with breaking the raid like that, though was desperate and read somewhere that grub2 doesn't like lvm and raid?  And a lot of the stuff I found on google was using mdadm not dmraid.  Do plan to build a fresh server hopefully sooner than later.

---

### Post by darkod on 2012-05-22
Glad you got it going.

The Solved is in Thread Tools above the first post.

---

### Post by YannBuntu on 2012-05-22
Hello

**@heyasam:** good job :) I think the key was in the last operations, but i wished a LVM expert could explain what happened exactly:
> **heyasam said:**
> Then reboot and startup brings to grub prompt:

insmod lvm
set root=(cds-root)  (might have left this one out, can't remember)
linux /vmlinux-xx-xxxx-xx-server root=/dev/mapper/cds-root ro
initrd /initraxxxx
boot

First time boot it crashed, though much further through the boot.  Reboot again and now fine.  Then once booted up purged and reinstalled grub (and other grub commands) and actually ran without error this time.

**@darkod:** Boot-Repair supports LVM, it did the same procedure as your post #5 (except it did "grub-install /dev/sda" instead of grub-mkconfig), but apparently it wasn't enough :(

---

### Post by darkod on 2012-05-22
> **YannBuntu said:**
> 
**@darkod:** Boot-Repair supports LVM, it did the same procedure as your post #5 (except it did "grub-install /dev/sda" instead of grub-mkconfig), but apparently it wasn't enough :(

I'm not a big expert on grub2, but if you purge it I guess it's logical to need the grub-mkconfig. I'm not sure if the grub-install only creates the config files.

Once purged it has no config files present and I guess you need to run grub-mkconfig after installing grb-pc again.

---

### Post by heyasam on 2012-05-22
Hey YannBuntu,

Not sure if the fakeraid confused boot-repair on the several times I tried it?  Even after unplugging one of the mirrored harddisks, then running 

sudo dmraid -E -r /dev/sda

I got the following message from boot-repair when trying it again

RAID detected. You may want to retry after installing the [mdadm] packages. (sudo apt-get install -y --force-yes mdadm --no-install-recommends)

Once I saw this message from boot-repair I did this and got the following message

ubuntu@ubuntu:~$ sudo dmraid -an
no raid disks

??  Don't know if that is of any importance or interest.  But my system is online again now so all happy.

---

### Post by YannBuntu on 2012-05-22
**@darkod:** update-grub is a stub for grub-mkconfig (on some other distros we have to use grub-mkconfig because there is no update-grub), so i think we don't need to use grub-mkconfig+update-grub.

**@heyasam:** i am not a RAID expert, so in the B-R app, i prefer to let the user choose between dmraid or mdadm. Then B-R proposes to install the packages if necessary, and activates the RAID automatically. When using mdadm, B-R proposes also to uninstall dmraid to avoid conflict.

---

