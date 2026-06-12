---
title: "Switching working install to new HD?"
date: 2005-04-26
forum: Installation &amp; Upgrades
---

### Post by Redemption042 on 2005-04-26
I've got a working customized install of hoary going on an old ide hard drive on /dev/hda

I recently purchased a new SATA harddrive that is recognized as /dev/sda. I can mount it, play with it, copy stuff to it, everything I want.  

What I want to do is copy over all of hda1 to sda1, set up the computer to boot off up grub installed on the sata drive and remove the old hard drive.  

How would I do this? 

I can easily copy everything over, but I'm really unsure about getting grub to work.

Thanks for help!

---

### Post by ian! on 2005-04-27
I guess you already created some new partitions on the new drive. Don't forget to create one for swap too.
If your using one partition for / and /boot and the new drive/partition is mounted on /mnt/newdrive the following should do the trick:

rsync -av / /mnt/newdrive --exclude="/sys" --exclude="/proc" --exclude="/mnt" --exclude="/dev"

Afterwards you should find all files of you old harddisk on the new one with the same permissions and so on. We don't copy sys, proc etc. because these are created dynamically by the system at boot time.

Now edit /mnt/newdrive/boot/grub/menu.lst with your favourite editor and change the device entries from hdaX to sdaX and hdX to sdX.

Run /sbin/grub --config-file=/mnt/newdrive/boot/grub/menu.lst and tell grub to write the bootloader on the new harddrive ("setup (sdX)" etc.; take a look at the manpage or the grub website for further information).

Edit /mnt/newdrive/etc/fstab and replace all hdaX entries with sdaX ones.

I hope I didn't forget anything important. Hope it works for you.

Edit: Make a backup of all your data first.

---

### Post by Redemption042 on 2005-04-27
[QUOTE=ian!]I guess you already created some new partitions on the new drive. Don't forget to create one for swap too.
If your using one partition for / and /boot and the new drive/partition is mounted on /mnt/newdrive the following should do the trick:

rsync -av / /mnt/newdrive --exclude="/sys" --exclude="/proc" --exclude="/mnt" --exclude="/dev"

Afterwards you should find all files of you old harddisk on the new one with the same permissions and so on. We don't copy sys, proc etc. because these are created dynamically by the system at boot time.

Now edit /mnt/newdrive/boot/grub/menu.lst with your favourite editor and change the device entries from hdaX to sdaX and hdX to sdX.

Run /sbin/grub --config-file=/mnt/newdrive/boot/grub/menu.lst and tell grub to write the bootloader on the new harddrive ("setup (sdX)" etc.; take a look at the manpage or the grub website for further information).

Edit /mnt/newdrive/etc/fstab and replace all hdaX entries with sdaX ones.

I hope I didn't forget anything important. Hope it works for you.

Edit: Make a backup of all your data first.[/QUOTE]
 Thanks for your reply!

What I ended up doing was mounting the drive in a tmp directory then 
cd /
cp -axR "dir in old drive root dir" "mount new drive root dir"
except for the proc dir.  for that mkdir proc in /mnt/joe where /mnt/joe is where I mounted my new drive.

then editing device map in /mnt/joe/boot/grub/device.map to reflect my new setup.
then editing /mnt/joe/boot/grub/menu.list to reflect my new setup 

then sudo grub-install /dev/sda1


Everything works fine with the switch, but now when I boot up I get "Warning, .devdb already in old /dev.  don't know what it means, but everything works fine. *shrug*

---

