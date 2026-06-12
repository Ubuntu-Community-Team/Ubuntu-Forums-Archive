---
title: "Trouble Installing 14.04 on Rocket RAID"
date: 2016-02-08
forum: Installation &amp; Upgrades
---

### Post by malfindin on 2016-02-08
9.10 64 Bit worked just fine for 5 years updating it.  No later version will install.

Some time after a kernal update I started getting errors while running 14.04.

If I install anything newer than 9.10 I get the error:

“attempt to read or write outside of disk 'hd0'”

Boot Repair and all the online advice on this error have failed to work.

I'm running a 4.5 Terabyte Rocket Raid. In 4 drive RAID 5 configuration.

And as I said. 9.10 worked fine for 5 years...'

Actually 9.10 still installs and runs. I simply can't install software or update it. I reinstalled 9.10 to see if it still worked, it does. Also tried 10.04 and later. No luck!

---

### Post by malfindin on 2016-02-09
It's worth noting that originally I did upgrade Ubuntu 9.10 to 14.04 and it worked for a full year. The a kernel update came in and I started getting the attempt to read or write outside of disk 'hd0' error. For a while I could use old kernel's to boot. When I tried to reinstall from scratch is when all install efforts began failing.

ALSO: nothing on this page works for my problem: [http://askubuntu.com/questions/397485/what-to-do-when-i-get-an-attempt-to-read-or-write-outside-of-disk-hd0-error](http://askubuntu.com/questions/397485/what-to-do-when-i-get-an-attempt-to-read-or-write-outside-of-disk-hd0-error)

---

### Post by oldfred on 2016-02-09
How old is BIOS.
Is BIOS set to RAID, AHCI or IDE for drives?

Some old IDE based BIOS will not boot from any file beyond 137GB on a drive. So if / is large & at beginning of drive it may work until an update puts a kernel or grub files beyond the 137GB point.

Suggestion then is smaller / fully inside the first 100GB or so, or a separate /boot at beginning of drive.

---

### Post by malfindin on 2016-02-09
Unfortunately, I have tried this as well.

I did just try installing 15.10 and got a totally different error message. "no boot device selected"... Again install went without errors.

---

### Post by oldfred on 2016-02-09
Where did you install grub?
With RAID it may be installed to the root of the RAID not the MBR (sda).
But that depends on type of RAID and I do not know all types.

If BIOS or "fake" RAID.
 "fakeRaid" with nVidia, note p1 is partition, without p1 is root of RAID volume
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0

---

