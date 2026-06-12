---
title: "Installing in pre-existing logical volumes"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by jkeffer on 2007-10-25
I was interested in installing Ubuntu in a pre-existing logical volume on one of my machines.  The scenario is that I had loaded both Fedora and Mandriva on my machine.  It has a 200GB drive, with two major partitions: a small 100MB partition for /boot, and the rest of the drive was set up under LVM for logical drives.  I set up three logical drives.  Two 10GB drives for the Linux distributions and the remainder of the drive for my data files (always loaded as a user-owned partition).

I started by loading Fedora, and then I came back and loaded Mandriva.  I have since decided to replace the Fedora load with Ubuntu.  Here's how I did it.

I started with the 7.04 text install DVD.  Boot the system from the DVD and hit F-6 a couple of times to switch over to expert mode (you might be able to do this in normal mode, but I didn't try it.)   Follow the basic install process, going through these steps just like normal:
 - Select language
 - Select Keyboard
 - Detect CD
 - Load Debconf
 - Load Installer
 - Detect network
 - Configure Network
 - Detect Disks

This is where we break out of the normal process...  Skip to the "Run Shell" option and get to the command prompt.  We now load LVM and search for existing partitions.  Like so:

modprobe dm-mod            # this loads the kernel module
dmsetup mknodes             # this makes some special devices to "hold" the logical volumes
vgscan --ignorelockingfailure                # looks for logical volumes
vgchange -ay --ignorelockingfailure      # and this mounts them

Now we just exit from the shell and go back to installing the distribution.  The next step is to partition the drives.  Choose manual.  Configure LVM.  In my case, it found all my logical volumes (excellent!)  If it doesn't correctly detect your logical volumes, you're probably out of luck.  

I bailed out of the install when it wanted to start configuring the boot loader.  Instead, I just booted back into Mandriva (already loaded) and  went to the /boot directory, and made some manual changes to get the loader to recognize my configuration.  

A quick note here.  When I'm booted under Mandriva, the boot partition is mounted under /boot.  When booted under Ubuntu, it's mounted as media/hda1.

There is a /boot directory under Ubuntu as well, but it has a different meaning.  It holds the kernel images that have been loaded.  On my Mandriva system, the Ubuntu boot directory was mounted at /fedora/boot.

I just copied the initrd.img-2.6.20-15-generic and the vmlinuz-2.6.20-15-generic files to the Mandriva /boot directory.  (Remember, when you boot under Ubuntu the directory gets mounted as /media/hda1... it can get kinda' confusing.)

Then, I went to the grub directory and added these lines to the bottom of the menu.lst file.

title Ubuntu, kernel 2.6.20-15-gemeric
root (hd0,0)
kernel /vmlinuz-2.6.20-15-generic root=/dev/VolGroup00/LogVol00 resume=/dev/hda3 splash=silent vga=788
initrd /initrd.img-2.6.20-15-generic

When you reboot, you now have an Ubuntu option in your grub options.

You still need to do all your regular configuration and run Automatix, if that's what you want.  You probably also want to do something reasonable with /etc/fstab so you can "see" your Mandriva and shared partitions mounted someplace other than under something odd like /media/mapper_VolGroup00-LogVol01.

Seemed to work pretty good for me.  Just a couple of interesting tidbits that might bear further investigation:

1.)  For reasons unknown, the install doesn't recognize my generic nVidia controller.  The video just didn't work at all.  I had to copy major sections out of my Mandriva /etc/X11/xorg.conf file.  I'm pretty sure this is due to my odd install process...  Something is up here, but I haven't worked it out.

2.)  When I ran the upgrade to 7.10, it didn't update the init.rd-etc-etc and the vlinux.etc-etc files in the /media/hda1 directory.  It runs fine on the old kernel and init.rd file.  I'll probably manually copy the new kernel files at some point, like when I set up grub the first time.  Again, I think the update didn't update these files because of the odd install I performed.

Obviously, this process isn't ready for prime time.  But it appears that you can load Ubuntu into a pre-existing LVM module.  I didn't see any other discussions on how to do this, so I thought I'd just jot down these notes in case anybody else is looking at it.

Enjoy!

---

### Post by jkeffer on 2007-10-27
Silly me...

The problem with the upgrade not working was indeed related to my crazy install process.  The problem was that I didn't tell the system to mount /dev/hda1 as /boot.  Pretty obvious, really.  I suspect that the partitioning tool prompted me for that and I just missed it.  I was pretty paranoid about overwriting existing partitions, because I didn't want to wipe out the Mandriva installation.

You can do this manually, by copying all the files from /boot to /media/hda1 and editing the grub configuration like in my original post.  Then, go and edit /etc/fstab to mount /dev/hda1 to /boot and restarting.  That way, any time the kernel gets updated, it gets updated in the "real" boot directory and you don't have to copy any files.

---

