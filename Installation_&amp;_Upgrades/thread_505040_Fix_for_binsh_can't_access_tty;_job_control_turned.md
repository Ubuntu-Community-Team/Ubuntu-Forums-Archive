---
title: "Fix for: /bin/sh: can't access tty; job control turned off"
date: 2007-07-19
forum: Installation &amp; Upgrades
---

### Post by jamvegan on 2007-07-19
I just upgraded to 7.04 and encountered the following problem when booting:

> BusyBox v1.1.3 (Debian 1:1.1.3-3ubuntu3) Built-in shell (ash)
Enter "help" for a list of built-in commands

/bin/sh: can't access tty; job control turned off
(initramfs)

I came to search the forums and discovered that many people have this problem, possibly for a variety of reasons.  None of the posts that I read had a solution.  On a whim, I tried the following, and it eliminated the problem (for me).  I hope that it may help others, too.  Apologies if it duplicates a solution found in one of the many posts I haven't read.

I edited /boot/grub/menu.lst, changing the kernel line from:

```
kernel          /boot/vmlinuz-2.6.20-16-386 root=UUID=22f1e290-878d-4666-a2d3-bb6f34ec7956 ro quiet splash
```
to:
```
kernel          /boot/vmlinuz-2.6.20-16-386 root=/dev/hda8 ro quiet splash
```

I don't know what that wacky hexadecimal number is all about, but I remembered that it had caused me trouble (with a different issue) in the past.  Once again, replacing it with the appropriate old fashioned device name worked for me...

---

### Post by yabbadabbadont on 2007-07-19
Just be aware that the next time there is a kernel update, the old UUID line will be put back when update-grub is run after the new kernel is installed.  So the next time there is a kernel update, be sure that you edit your menu.lst file again after the update is installed and before you reboot.

---

### Post by 5-HT on 2007-07-20
> **yabbadabbadont said:**
> Just be aware that the next time there is a kernel update, the old UUID line will be put back when update-grub is run after the new kernel is installed.  So the next time there is a kernel update, be sure that you edit your menu.lst file again after the update is installed and before you reboot.
If you don't feel like manually updating /boot/grub/menu.lst after every kernel upgrade, you can switch the default kernel options line (kopt=root=<device> ro) to use /dev/hda8 instead of the UUID for the partition.
cheers,

---

### Post by yabbadabbadont on 2007-07-20
> **5-HT said:**
> If you don't feel like manually updating /boot/grub/menu.lst after every kernel upgrade, you can switch the default kernel options line (kopt=root=<device> ro) to use /dev/hda8 instead of the UUID for the partition.
cheers,

I doubt that your suggestion will work as update-grub *unconditionally* tries to convert all kopt lines to use UUID if possible.

From update-grub: ```
# Extract the kernel options to use
kopt=$(GetMenuOpt "kopt" "$kopt")

# Update the root device to mount-by-UUID
kopt=$(convert_kopt_to_uuid "$kopt")


```

---

### Post by Pumalite on 2007-07-20
Here is a mix of fixes. See if you can find one that applies to you and try it. What do you have to loose?

when I boot, the screen shows

Starting up

then boots to the following:

/bin/sh: cant access tty; job control turned off.
(initramfs)

so, i try the following command as suggested:


/bin/sh: cant access tty; job control turned off.
(initramfs)modprobe piix
(initramfs)exit


This does the trick, Ubuntu starts up fine, and smoothly.

> Just to simplify a little, however, after the command (in the chroot env):
> sudo echo piix >> /etc/initramfs-tools/modules
> all I needed to do is issue the command
> sudo update-initramfs -u
> to update the initramfs (thus correcting the system) and then
> exit
>

UPDATED FIX!!! I removed the old suggestion that I had written and pasted the new fix from the main thread of this problem...... Credit to this goes to
hbjason as these are his exact words. It appears as though it's a combination of some of my suggestions that I found on the internet etc etc.


f you are getting this error (and you have a SATA harddrive); this is the fix:

At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

You will now boot into the LiveCD normally.

If you choose to install from the LiveCD, you must make the following modifications (or else your installed system will not be able to boot, just like the LiveCD):
o Make note of the device id of the partitions that were used to install (such as /dev/hda1)
-- if you choose to install the '/boot' mount from a different partition make note of it as well (this would be done from the manual partition selection); just a side note -- if you do this, make sure the boot partition is at least 50MB or the install will error at grub setup
o When the install is complete do not reboot -- stay in the LiveCD
o Open a terminal (Applications->Accessories->Terminal)
o You must now mount the installed partitions by typing the following (assuming the install was to /dev/hda1; otherwise replace '/dev/hda1' with the install partition) commands:

mkdir target
sudo mount /dev/hda1 target

*if you also created a boot partition issue (replace /dev/hda2 with the boot partition) the command:
sudo mount /dev/hda2 target/boot

sudo chroot target

o You will now be in a 'chroot' command prompt for your new ubuntu system (be careful here, you are editing with root access!)
o You must edit the /etc/initramfs-tools/modules file; adding a line with the word: piix
-- you should do this with your favorite unix editor; or simply type the command:
echo piix >> /etc/initramfs-tools/modules
o After modifying the file you must update the system with the command
update-initramfs -u
o When complete, type 'exit' to exit the chroot env; you can now close the Terminal and reset your system.

Now when you boot you will be in your new shinny Ubuntu system!

---

### Post by 5-HT on 2007-07-21
> **yabbadabbadont said:**
> I doubt that your suggestion will work as update-grub *unconditionally* tries to convert all kopt lines to use UUID if possible.

From update-grub: ```
# Extract the kernel options to use
kopt=$(GetMenuOpt "kopt" "$kopt")

# Update the root device to mount-by-UUID
kopt=$(convert_kopt_to_uuid "$kopt")


```

Yeah, didn't see that. Couldn't the line just be commented out though, or be replaced with  a constant?

---

### Post by yabbadabbadont on 2007-07-22
> **5-HT said:**
> Yeah, didn't see that. Couldn't the line just be commented out though, or be replaced with  a constant?

Sure, but then you have to remember to always re-edit update-grub after updates...  :D

I prefer the Gentoo way of handling /boot/grub/menu.lst; do it yourself.  Unfortunately, a large number of the users that I help here are either unable, or unwilling, to learn enough to do that.

(actually, menu.lst is just a symlink to grub.conf in Gentoo)

---

