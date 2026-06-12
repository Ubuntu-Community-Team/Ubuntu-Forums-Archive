---
title: "getting the dreadful &quot;Not owner of USB Drive&quot; issue"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Psumi on 2010-03-22
1. The drive is FAT.

2. NO, I AM NOT WILLING TO CHANGE IT TO EXT#, or anything else for that matter, I need it to stay FAT.

3. Changing permissions obviously does not work.

4. I have usb/pmount, so the drive is auto-mounted to usb0.

Sadly, the drive is owned by root, and no one BUT root can copy files to the drive. How do I get around this?

---

### Post by ndefontenay on 2010-03-22
Connect as root, give read and write privilege to all groups

chmod 666 /mnt/wherever/it/is

---

### Post by Psumi on 2010-03-22
> **ndefontenay said:**
> Connect as root, give read and write privilege to all groups

chmod 666 /mnt/wherever/it/is

That doesn't work. permissions don't stay. In fact, when I try it...

```
sudo chmod +rwxXst -R ./
```

on the drive (because I want it recursive...)

it spits out an "Operation Not Permitted" error for every single file it tried to change (yes, even as root.)

and it's /media/usb0, not mnt.

---

### Post by seeker5528 on 2010-03-22
> **Psumi said:**
> That doesn't work. permissions don't stay. In fact, when I try it...

```
sudo chmod +rwxXst -R ./
```

on the drive (because I want it recursive...)

Files in the FAT filesystem don't have permissions, so whatever permissions are used at mount time apply to all the files in the file system.

You can change the mount permissions for a filesystem type in '/etc/usbmount/usbmount.conf'.

There is an example given for FAT in the commented out section above where you actually enter the configuration, that should work for you.

I don't know what the plan is with pmount, it hasn't worked for me for a little while, and in general seems to be a lot of issues with mounting of USB drives recently, different threads, with different workarounds, and not clear any given solution will work consistently for a majority of users. Outside of that there seems to be a change in the way the security rule that enables the capability for users to mount drives is handled, so maybe these things will be sorted out soon and you can do away with usbmount.

Later, Seeker

---

### Post by Psumi on 2010-03-22
> **seeker5528 said:**
> Files in the FAT filesystem don't have permissions, so whatever permissions are used at mount time apply to all the files in the file system.

You can change the mount permissions for a filesystem type in '/etc/usbmount/usbmount.conf'.

There is an example given for FAT in the commented out section above where you actually enter the configuration, that should work for you.

What should I put for the options though:
```
gid=floppy,dmask=0007,fmask=0117
```
These are the example vfat options, but I don't know what to put for the numbers, or is the example fine as-is? (why would I mount a USB drive with floppy gid though?)

---

### Post by seeker5528 on 2010-03-22
> **Psumi said:**
> What should I put for the options though:
```
gid=floppy,dmask=0007,fmask=0117
```
These are the example vfat options, but I don't know what to put for the numbers, or is the example fine as-is? (why would I mount a USB drive with floppy gid though?)

If you use the options as they are given in the example, anybody that is a member of the floppy group should have read/write access to the files, just copy and past that between the quotes on the FS_MOUNTOPTIONS="" line.

There is a read me file in '/usr/share/doc/usbmount/' that gives a little more information.

I only have one user account and it was a member of the floppy group already, but I believe that is the default for any additional accounts created as well.

Later, Seeker

---

### Post by Psumi on 2010-03-22
I added myself to the group floppy:
```
adduser psumi floppy
```

Now the folder /media/usb0 has a big white X on the folder icon, and I can't open it, gives me the error "Permission denied."

usbmount.conf is doing its job though, it says floppy group can read & write to usb0.

I don't want to install another gnome app to manage users and groups though, so can you tell me how to fix this?

---

### Post by seeker5528 on 2010-03-24
Don't know if it makes a difference, but I notice in the example the option starts with a '-' and this works for me:

```
FS_MOUNTOPTIONS="-fstype=vfat,gid=floppy,dmask=0007,fmask=0117"
```

Usbmount will mount the drive at '/media/usb0', '/media/usb1', etc... and places will show a matching 'usbX' listing.

Currently with pmount installed I get an additional listing that is specific to how the USB device identifies itself, but that fails with an indication about not having permission.

Additionally if I want to remove the device I still have to do it from the command line

```
sudo umount /media/usb0
```

or this seems to work without requiring sudo

```
eject /media/usb0
```

For groups that already exist you can edit '/etc/group' if needed, just find the line for the floppy group and add your users there:

```
floppy:x:25:user1,user2,user3
```

Later, Seeker

---

### Post by Psumi on 2010-03-24
Forgot to mention that after I restarted, the usb0 became available, now it works; but no longer appears on the desktop with its label.

---

