---
title: "HOW-TO Feisty Live-CD installation to USB drives - also works from USB CD-Rom"
date: 2007-08-12
forum: Installation &amp; Upgrades
---

### Post by CValentine on 2007-08-12
Alright, since there are some posts around but none of them covers this issue completely (and most require the usage of the alternative CD, which simply won't even boot if you only have an external USB CD-Rom to install from), I decided to write this tutorial to make up for all the help I found on this forum beforehand. Feel free to suggest changes and optimizations, so everyone else can prosper from it...

Be warned, this guide is written with beginners in mind also, so don't blame me for pointing out every single bit in extent... :-)


The idea is to install a full Ubuntu version to your external harddrive, which boots if the drive is plugged in at the start of the computer, but can also be used as a normal storage device on any other computer you run across. That means you can e.g. have Redmonds wonder-full system installed on your internal drive and leave that installation completely untouched, while whenever you want to, you can - by no effort - also have access to the powers of Linux. 

Alright, let's start the installation...


1. Get your hands on a Live-CD, burn it and set your bios to boot from the CD. Also plug in the USB harddrive you want to install to. The Live-CD should boot from external USB CD-Roms also, which is the reason I use this approach rather than the alternative CD, which often simply won't work on USB CD-Roms, rendering previous posts on this issue useless for users not having an internal CD-Rom to install from.

Be aware that this guide is written for a fresh installation ON THE COMPLETE USB DRIVE, so if you have important data on your external drive, back it up NOW!!!


2. Boot the Live-CD, select "Start or install Ubuntu", and you'll end up on the Ubuntu desktop. Open the "System" menu in the upper taskbar and select "Preferences", "Removable Drives and Media". Disable these Options:
Mount removable drives when hot-plugged
Mount removable media when inserted
Browse removable media when inserted
and close it.


3. Open the "System" menu in the upper taskbar and select "Administration", "GNOME Partition Editor".
Once it has opened, you can choose your different drives in the dropdown menu in the top-right and you'll be shown their content. If you've already used your drive or if it's preformated by the manufacturer you'll see one or more /dev/xxx entries in the main window &#8211; that's the partitions.
(If it shows only grey "unassigned space" you can skip the following delete instructions, but right now read on to find the name of your drive first).

Given the displayed names and sizes you should be able to find out which is your desired drive to install to. Note its name as displayed in the top-right window you selected it from, e.g. /dev/sdb.

*******   Be absolutely sure, which drive you want to install to, so we don't mess up your internal drives by accident!!!  ********

Also make sure you note the term as displayed top-right, not one of those in the main window (which will/might have numbers appended, like /dev/sdb1), these are referring to single partitions on the drive, not the whole drive...

Since we want to install from scratch, we'll want to delete any existing partitions on that drive, so the installer has less problems setting everything up. The problem is that Ubuntu has already mounted your drive (you can tell that from the lock symbol in front of the main entries), so right now everything is write protected. To solve this, right-click all entries with a lock and select "Unmount". You might have to do so in specific order, just play around until everything on this drive is unlocked, giving us the ability to perform disk operations on this drive from now on.
Now right-click the entries, followed by an "Delete" click. Again, you might have to do so in specific order. In the end everything on this drive should be deleted and the whole disk should show as unassigned free space.
When you're finally there, select "Apply" from the "Edit" folder in the top menu and let it do it's job. We're good. Close the program.


4. Double-click the "Install" icon on the desktop, go through the initial steps and in step 4 you'll reach the disk selection. Choose the "Guided &#8211; entire disk" option and select your external drive as target. You should have no problems in identifying it by the names and its internal description shown in the bracets, which will match the last part of the expression we noted while setting it up (e.g. sdb).
Continue to the point where there is an "Advanced..." button to the lower right. Click it and instead of the shown expression (mine was (sda) ), type in the name of your drive exactly as we noted before (that's right, no bacets!), e.g. ```
/dev/sdb
``` NOT:
```
(/dev/sdb)
```

That way we'll write the boot menu to the external drive directly, not messing with the boot menu on your internal drive. Run through the rest of the installation.

After it has finished, it will pop up a window asking you to reboot or continue the Live-CD. Choose Reboot, but DON'T TAKE OUT THE CD!. Just close the lid and hit enter when you're told so. Make sure it boots the Live-CD again! If you want to use the whole disk for Ubuntu, skip the next step. If you want to make use of some or even most of the drive accessible as storage room on other systems also, like Windows, just read on...


5. When you're back to the desktop, first disable the Automount options again as shown in Step 2. Afterwards restart the "GNOME Partition Editor" via the "System" menu. Select your drive again in the top-right corner and you'll see its two new partitions. One is shown to use Filesystem "ext", the other one "swap". Right now we want to resize the "ext" partition, so we can use some - or most - of it's space as universal storage space also working on other systems. To do so, first right-click, unmount it again and afterwards right-click it and chose "Resize/Move".
Draw the bar or just enter the new size, so it fits your desire. Take into consideration that you might need some space for Ubuntu updates or additional programs you might want to install later on, so leave Ubuntu some space to breathe. I personally chose to resize the "ext" of my 120GB disk to about 10GB, leaving more than enough space (>6GB) for future expansion, while still having more than 100GB pure storage room, it's your choice...

Once your done, apply your settings. This one might come up with an error, propably because Ubuntu intentionally messed up some things on the filesystem to force an initial disk-check after a fresh installation. So after it has quit the operation, just redo everything and this time it will go through. Once it's done and the screen has refreshed, right-click the new unassigned free space and chose "New" to create a new partition. Select the whole free space and "Primary" if it hasn't done so automatically and choose "fat32" for maximum compatibility with other operating systems like Windows and Mac.
Be aware of the fact, that you won't be able to store single files with a size >4GB on this file system. Shouldn't be a great issue most of the time, but be aware. Choose to apply these modifications which can take a looooong time and - once complete - close the program.


6. Phew, everything's set up on the basic side, so lets proceed to making your system actually work - the hardest part when bringing USB drive installations to life. Perform everything as outlined from now on and use any commands given WITHOUT the apostrophes (meaning these little symbols: " " )!
The problem is, that - by default - the USB device support is loaded later in the boot process than needed, since in fact your very system IS on a USB device. So we'll have to tell Ubuntu and it's boot manager Grub to load them earlier than normal. Here's what to do...

Open up the "Places" menu in the top-left taskbar. Select "Computer" and you'll see a window with all your drives. Both partitions, the one we installed to, and the one we'll use as storage room are shown as seperate drives here. You can identify them by the USB symbol on their icons. Double-click the first one to have it mounted and see its content. If its empty, you selected the wrong one, if you see folders like bin, boot, etc. you're good. When you've found the right one, close its content window, right-click the drive, select "Properties" and click the "Volume" tab at the top. You'll find the "Mount point" of the drive in this tab, e.g. /mount/disk or similar.
Note or remember its mount point and close this window.

Open up a terminal via the "Applications" menu in the top-left, " Accessories", "Terminal", then type in the following commands, always replacing "yourmountposition" with the term you just found and without any apostrophes.

```
gksudo gedit /"yourmountposition"/etc/initramfs-tools/modules
```

It should look similar to this: gksudo gedit /media/disk/etc/initramfs-tools/modules

At the end of this file, add the following lines, each in it's own line and with no # in front of it:

```
ehci-hcd
uhci-hcd
usb-storage
usbcore
usbhid
scsi_mod
sd_mod
```

Save the file and close Gedit. If the above later on won't work for you, it has been mentioned that changing the order to

```
usb-storage
usbcore
usbhid
ehci-hcd
uhci-hcd
scsi_mod
sd_mod
```

might solve the problem. Just keep that in mind. Using the Live-CD and coming back to this point will always be possible if the above doesn't work for you. But for now, let's go on...

Back in the terminal enter:

```
gksudo gedit /"yourmountposition"/etc/initramfs-tools/initramfs.conf
```

At the very top (even before the lines starting with #) enter: WAIT=15
This will give Ubuntu enough time to setup your USB support before trying to access the drive. Save and close the program.
Next type in the terminal:

```
sudo mount --bind /dev /"yourmountposition"/dev
```

The next two commands can give an error at first try, if they do, just repeat them and maybe replace sudo by gksudo and they will go along fine:

```
sudo chroot  /"yourmountposition"
```

```
sudo mount -a
```

Now that everything is set up, let's actually mold our changes into the process:

```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

Once it's done, we're almost there. Just tell the boot manager, how to boot correctly by typing:

```
sudo gedit /"yourmountposition"/boot/grub/menu.lst
```

And search the entrys for a line containing "groot". Edit this line by changing groot(hd1,0) to groot(hd0,0)
Also change any lines below referring to (hd1,0) to (hd0,0)
If you find lines referring to Windows at the very bottom, change them from (hd0,0) to (hd1,0)

Save the file and you're finally ready to boot your brand new system. Shut down, remove the Live-CD and set your bios to boot from the external drive. Sometimes you'll have to change the boot order, so USB devices are booted first, sometimes you'll have to rearrange the boot order of the harddrives that are booted from. It just depends on how your bios integrates the external drive. Be also aware that some mainboards support USB booting on some or even one of it's USB ports only, so try another one if it doesn't work at first try. Maybe you also have to upgrade your bios before, but that's beyond this guide...

P.S.: It might be a good idea to set a soft-link in your home folder linking to the storage partitition we created, and use that folder for your personal data. That way you'll always have access to all your personal files everytime you use this drive on other operating systems (like your old windows for example ;-) ). Just google soft link and linux to get the picture... And if you want to also write to your internal drives (which might be of the NTFS filesystem if you have windows installed) instead of the Ubuntu implemented read-only access, you should have a look at the ntfs-3g and ntfs-3g configuration packages in Synaptic. Find out more in this post: [http://ubuntuforums.org/showthread.php?t=217009]("http://ubuntuforums.org/showthread.php?t=217009")

Best regards,

CV

---

### Post by nblue on 2007-11-03
Thank you very much for this wonderful guide. I was able to successful install ubuntu 7.10 following this guide with 1 minor alternation. 
Near the end when I need to edit the grub menu.lst. I was not able to access it due to permission thing. So I just reboot the comp after that step and during the grub menu, I type e (edit) and change the drive from (hd1,0) to (hd0,0) and it allow me to boot into ubuntu. 
After that I just open the terminal and do the same thing again. 
Note: for me, the mount point name change from media/disk to /boot/grub/menu.lst   It is the path from computer to the file menu.lst 
This guide help me alot, I know there are some installation help from pendrivelinux to install ubuntu to usb external drive but invole internet download and ubuntu network does not work in my laptop so I can not use it.

---

