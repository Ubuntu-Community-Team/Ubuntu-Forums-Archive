---
title: "Dual boot"
date: 2007-02-26
forum: Installation &amp; Upgrades
---

### Post by matoxxx on 2007-02-26
Hi, 
iam just curious, why i cant dual boot DApper an Feisty, when i use one standalone /boot partition for both distos, there are just grub files and configuration files what to boot and they arent conflicting cause they are differend for each kernel.

---

### Post by Herman on 2007-02-26
Normally when we try to add another file to a directory in Linux when it has the same filename as another file that is already there, the new file will overwrite the older one. That means if you had a seperate /boot for your edgy, say for example, and you try to use the same /boot partition again for fiesty, the new boot files will overwrite most of the existing boot files because they have the same filename.

You can still do it, but you would be best to make a copy of edgy's menu.lst file and save it somewhere safe, or rename it a different filename.

See this thread, [two linux, same /boot]("http://www.ubuntuforums.org/showthread.php?t=364368&highlight=herman")

Regards, Herman :)

---

### Post by matoxxx on 2007-02-27
Thank you for answering, 
i thought it is a simple task to do it, but anyway i give a try and follow your instructions to do this. Its because i like to have CLEAN system and everythng in order. 

I would suppose that developers could look at this and include the choice of separate /boot partition for multiple OS in installation method. It could be very helpfull

---

### Post by Herman on 2007-02-27
Well actually there is very little if any advantage in setting one's system up to have two or more operating systems share the same separate /boot partition, at least I can't think of any. And it is far more complicated than necessary. But if you already have yours set up that way then that link describes a good way to finish setting it up so everything will work properly.
By a separate shared /boot partition I mean one /boot partition which is mounted as a /boot partition (in etc/fstab), by more than operating system, and contains the kernels for each operating system.

On the other hand, I can understand someone wanting a separate grub partition, meaning a special partition with grub in it which can boot all your operating systems from the one central location. It would not need to be mounted in /etc/fstab or if it is, as a data partition. 
It is quite simple to make your own grub partition any time you like by making a small partition with [GParted -- LiveCD]("http://gparted.sourceforge.net/livecd.php") or any partition editor and copying a /boot directory (with grub in it), to it.
Then just open a grub shell and install grub from the new partition to MBR, and edit your menu.lst in the new grub partition to either chainload or configfile boot all your operating systems. Each operating system can then keep it's own /boot/grub directory and maintain its own menu.lst or grub.conf file. That would be a much more practical thing to do, in my opinion.

What I would suggest to the developers which would only be a trivial matter, but nevertheless a nice touch, would be if the /sbin/update-grub files could be edited to print "Kubuntu Edgy Eft" or "Xubuntu Feisty Fawn" in the title line for the grub menu instead of just "Ubuntu" no matter what flavour or version we have installed. Then those who may be multi booting can see which system they are booting a little easier. :)
I doubt if any developers will be reading this post, but if I see an appropriate place to file a user's suggestion for ideas for improvements for a future release I might suggest this,

Exrtact from around 1/4 down from top of /sbin/update-grub file,
```
 # Full path to the menu.lst
menu_file=$grub_dir/menu.lst

# the device for the / filesystem
root_device=$(find_root_device)
root_device_2_6=$(convert_kernel26 "$root_device")

# the device for the /boot filesystem
boot_device=$(find_device "/boot")

# Full path to the device.map
device_map=$grub_dir/device.map

# Default kernel options, overidden by the kopt statement in the menufile.
kopt="root=$(awk '$2 == "/" {print $1}' /etc/fstab) ro"

# Title
[COLOR=Red][B] title="Ubuntu"
[COLOR=DarkRed]#leave as Ubuntu or change to Kubuntu or Xubuntu if appropriate, followed by the name of the release
[/COLOR][/B][/COLOR] 
# should update-grub remember the default entry
updatedefaultentry="false"

# Drive(in GRUB terms) where the kernel is located. Overridden by the
# kopt statement in menufile.
# if we don't have a device.map then we can't use the convert function.
check_removable=""
if test -f "$device_map" ; then
```Regards, Herman :)

---

