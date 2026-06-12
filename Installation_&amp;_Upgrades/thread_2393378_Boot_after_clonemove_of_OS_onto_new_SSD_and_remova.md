---
title: "Boot after clone/move of OS onto new SSD and removal of old SSD"
date: 2018-06-02
forum: Installation &amp; Upgrades
---

### Post by aeronutt on 2018-06-02
I'm installing a PCIe SSD into my laptop, and want to clone my Ubuntu OS from my current SATA SDD to the new PCIe SSD. And then, soon thereafter,  replace the SATA SSD with a higher capacity SSD.
Ok, I think the cloning part is easy enough with Clonezilla, or even dd.
But after cloning....how do I get the laptop to see and boot the OS image on the PCIe SSD ? 
Somehow install grub onto the PCIe SSD, and/or run boot-repair from a live USB?

Thanks!

---

### Post by oldfred on 2018-06-02
While you can clone, you cannot keep old drive plugged in, unless you change its UUIDs.
Duplicate UUIDs are not allowed.

Is system UEFI or BIOS?

I prefer to just do a new install, and then restore my data from backup. Also becomes good test that backup has everything, but you still have old drive to go back to in case you missed something. Most of what you want is in /home and you may want to export list of installed apps to make it easy to reinstall them.

---

### Post by aeronutt on 2018-06-03
System is UEFI.

I usually would just do a new install and restore stuff from backup....just thought I'd try cloning for a change.

---

### Post by oldfred on 2018-06-03
With gpt partitioning, you can only use dd for entire drive. And it is intended for same size to same size drive.

I have not used clonezilla. 
But with UEFI the ESP is just another partition which you should include. Do not know if clonezilla then updates UUIDs & GUIDs or copies them. 
If GUID changes you have to add new UEFI entry with efibootmgr or reinstall grub as UEFI uses GUID. And then update grub and fstab if UUIDs have changed.

---

### Post by aeronutt on 2018-06-03
Thanks for the info and help.
Clonezilla was a bit of a struggle. It had an option to clone a partition, but near the end, would blow away all the partitions on the target device, and ask to recreate. Ug. I gave up.
I used dd to clone OS to a partition on the new PCIe SSD, Then removed previous/old SSD, then installed a new copy of Ubuntu on another partition on the new PCIe SSD. .
On the cloned (dd'd) version, files are present, grub found the OS, but it will not boot. I may play around a bit to see if I can get it boot, just for educational purposes.

I'm configuring the new install of Ubuntu now. So will work out.

So, I'm

---

### Post by oldfred on 2018-06-03
With gpt, it is difficult to do anything other than full drive to full drive dd copy.

Gpt partitioning uses GUID as well as UUIDs. And the GUID for each partition is stored in the gpt partition table and the backup gpt partition table. So copy of a partition may get GUIDs out of sync.
May be possible to repair with gdisk, but better not to create issue in first place.

---

### Post by aeronutt on 2018-06-03
Well, if YOU think it's difficult, then I know I'll never get there. :)

Thanks again for you're help. I'll just scrub the partitions and use those for my test installs.

---

### Post by C.S.Cameron on 2018-06-03
What I did was a little different, 
I installed the latest version of Ubuntu fresh to the new SSD leaving room for my /home partition.
(A lot of people swear by fresh installs, you can upgrade versions).
I copied the /home partition from the old drive to the new SSD using gparted copy/paste.
I then reset the UUID of /home in /etc/fstab.
Then the user installed programs were reinstalled.

If the old drive does not have a /home partition the home directory can be copied to it's own partition using rsync or grsync, (GUI).
The path to the home partition then needs to be listed in /etc/fstab.

Alternately the home directory can be copied from the old drive's home folder to the new drive's home folder using rsync.

I have only found duplicate UUID's a problem if both partitions are mounted at the same time, and I am booted from one of the drives.
Gparted has a function to automatically change UUID's if needed.

---

### Post by aeronutt on 2018-06-04
Thanks, that's good info. This latest restore causes me to reconsider where/how I have my home folder and personal data files (eg email folders, browser folders, etc). I've kind of got them spread over a few directories, some of which I encrypt (with veracrypt).
When I upgrade to a new release, I tend to do a fresh install and reconfigure fresh, with the exception of a few things like email client and browser settings, which I don't keep in /home.  But reinstalling a current release because of a new disk, or failure, I should just be able to restore /home into the new install. So...rethinking things a bit.

Thanks again for all the help and ideas, good stuff.

---

