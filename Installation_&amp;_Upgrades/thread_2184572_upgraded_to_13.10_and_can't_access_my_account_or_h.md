---
title: "upgraded to 13.10 and can't access my account or home directory"
date: 2013-10-29
forum: Installation &amp; Upgrades
---

### Post by barrymmm on 2013-10-29
I've upgraded to 13.10 and can't access my account or home directory. I had 13.04 installed on the SSD portion of my hybrid drive and located my home directory on the HDD portion. Since the upgrade I get an error during booting telling me that my home directory is either not present or not ready to be used and I get the option to skip or manually resolve the problem. I don't know what I'm doing with the manual option so I end up skipping to see if I can solve it further along the line. I then get the option to login under my usual name but my password isn't recognised. I can login as a guest but it seems a little unstable and has frozen on me a couple of times. I cannot edit fstab because I'm in a guest session and the sudo command doesn't seem to work because my password isn't recognised.
I'm reasonably sure all my data is safe on the drive and all I need to do is tell Ubuntu where to find it. Anyone know where I go from here?

---

### Post by phaenze on 2013-10-30
Hi,
The first thing to check is that your system is trying to mount /home on the HDD and not the SSD. So, could you post your fstab? Also, please post the results from the command "sudo blkid"?

Thanks.

Peace,
Paul :cool:

---

### Post by barrymmm on 2013-10-30
Thanks phaenze.
My fstab is as follows:
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda2 during installation
UUID=9e4c5ffa-7567-46b6-80db-90f624c3a905 /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/sda1 during installation
UUID=8E01-5118  /boot/efi       vfat    defaults        0       1
# /home was on /dev/sda4 during installation
UUID=b68dc31e-5ebc-4334-a4e6-1ad318132b5a /home           ext4    defaults        0       2
# swap was on /dev/sda3 during installation
UUID=59dacede-bb6a-411c-beda-f7d87191b718 none            swap    sw              0       0
# (identifier)  (sda2)   (ext4)      (some settings) 
UUID=9e4c5ffa-7567-46b6-80db-90f624c3a905   /media/home    ext4          nodev,nosuid       0       2 
# (identifier)  (sdb1)   (ext4)      (some settings) 
UUID=1e373bc2-d9cd-444f-a404-f0202fef4ffd   /home    ext4          nodev,nosuid       0       2 

The last UUID is the HDD I'm looking to mount 
Unfortunately I can't get results for any sudo commands because I'm asked for my password and it won't recognise it. This also means that fstab is read only and I can't alter it.

---

### Post by barrymmm on 2013-10-30
Weird, you know what. I just dropped the sudo command and tried blkid. I got this output:

/dev/sda1: UUID="8E01-5118" TYPE="vfat" 
/dev/sda2: UUID="9e4c5ffa-7567-46b6-80db-90f624c3a905" TYPE="ext4" 
/dev/sda3: UUID="59dacede-bb6a-411c-beda-f7d87191b718" TYPE="swap" 
/dev/sdb1: LABEL="data" UUID="1e373bc2-d9cd-444f-a404-f0202fef4ffd" TYPE="ext4" 
/dev/sr0: LABEL="WL_SAMPLER_2" TYPE="udf"

---

### Post by barrymmm on 2013-10-31
UPDATE:
I've noticed that if I start a guest session my password is recognised when I open gparted. If I mount sdb1 in the guest session I can then switch my session and login as normal to my own account. All my data etc is exactly as before. So what I'm getting for some reason is that Ubuntu is unable to mount my home directory during the boot process.

---

### Post by barrymmm on 2013-11-06
Still stuck with this problem. Anyone got any suggestions?

---

### Post by barrymmm on 2013-11-08
OK I'm getting desperate now. Switched on my machine today and can't open gparted in guest session anymore. I just get little timer for a few seconds and then nothing happens. When I try any sudo commands in terminal I get this error message 
sudo: unable to change to sudoers gid: Operation not permitted
I tried creating a new startup USB but when I hit the "Erase Disk" button or the "Make Startup Disk" button I get this error message
 org.freedesktop.DBus.Python.dbus.exceptions.DBusException: com.ubuntu.USBCreator.Error.NotAuthorized

So at this stage I've lost access to my account and my home directory again. I've also got no sudo permissions anymore. Has anybody got any suggestions?

---

### Post by phaenze on 2013-11-09
Sorry that I haven't responded for awhile-I've been away.
From your fstab, it looks like you are trying to mount /home twice -/dev/sda4 & /dev/sdb1 plus once under /media - /dev/sda2. These are also conflicting with mounting root. Since you have installed the OS on your SSD and /home on your HDD, I am presuming that your SSD is /dev/sda and your HDD is /dev/sdb -- which seems to be reflected when you run blkid.

So, you need to boot the machine one of two ways - using the boot recovery option or the LiveCD. I'll go through the two below:

Boot recovery
[LIST]
[*]Choose recovery option in grub.
[*]At the ncurses option screen, pick the "root" option.
[*]At the prompt, type **mount rw -o remount /** (Note: This remounts your root drive as read/writeable.)
[*]Edit the fstab file, **nano /etc/fstab**
[*]Comment out the spurious home directories by adding ## to the beginning of each line:
[/LIST]
```
[INDENT]# /home was on /dev/sda4 during installation
**## **UUID=b68dc31e-5ebc-4334-a4e6-1ad318132b5a /home ext4 defaults 0 2
...
# (identifier) (sda2) (ext4) (some settings) 
**## **UUID=9e4c5ffa-7567-46b6-80db-90f624c3a905 /media/home ext4 nodev,nosuid 0 2 [/INDENT]

```
[LIST]
[*]Save and exit nano.
[*]Type **sync**
[*]Type **shutdown -r now**
[*]Boot up and test login.
[/LIST]

Live CD is similar:

[LIST]
[*]Boot from LiveCD.
[*]Open a terminal.
[*]Mount the SSD: **sudo mount /dev/sda2 /mnt.**
[*]Edit the fstab file, **sudo nano /mnt/etc/fstab**
[*]Comment out the spurious home directories by adding ## to the beginning of each line:
[*]```
[INDENT]# /home was on /dev/sda4 during installation
**## **UUID=b68dc31e-5ebc-4334-a4e6-1ad318132b5a /home ext4 defaults 0 2
...
# (identifier) (sda2) (ext4) (some settings) 
**## **UUID=9e4c5ffa-7567-46b6-80db-90f624c3a905 /media/home ext4 nodev,nosuid 0 2 [/INDENT]

```
[*]Save and exit nano.
[*]Type **sudo sync**
[*]Type **sudo shutdown -r now**
[*]Boot up and test login.
[/LIST]

Let me know how this works.

Peace, 
Paul :cool:

---

### Post by barrymmm on 2013-11-09
[**[COLOR=#000000]phaenze[/COLOR]**]("http://ubuntuforums.org/member.php?u=1843154") - you beauty! The first option (boot recovery) worked for me. I'll just add for anyone else who ever reads this thread that to save in nano it's Ctrl + x and then hit Y to confirm.
Many thanks Paul!

---

