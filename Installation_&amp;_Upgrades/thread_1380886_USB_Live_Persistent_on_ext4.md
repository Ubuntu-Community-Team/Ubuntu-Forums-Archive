---
title: "USB Live Persistent on ext4 ?"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by xeross on 2010-01-14
Hey, 

I was wondering if it's somehow possible to install the Live USB to an ext4 partition, this because I have a 4gb filesize limit on fat32 and that means I cannot make the casper-rw any larger. And next to that I can decently manage permissions on that.

Thanks, Xeross

---

### Post by Mighty_Joe on 2010-01-14
To my knowledge, the [USB Creator]("https://launchpad.net/liveusb") requires a FAT32 partition.  You can create other partitions on your USB drive that are not FAT32 and reference them from within the Live USB once it's booted up.

---

### Post by xeross on 2010-01-14
Well I want to modify it after the USB install so it uses ext4, this would require copying the files to a seperate hdd and copying them back.

And then I need to do something with grub but I don't know what and was hoping people here could clarify on that.

---

### Post by garvinrick4 on 2010-01-14
You can actually make a USB drive and install from Live CD just like new install to HD. One problem exsists for me and that is you cannot make it mobile because it will look for mbr the
first time it update-grub. Which it will do on an upgrade sooner or later. If it is on a machine
with exsisting Linux with same grub no problem. When you remove it you can update grub back to same state. If on your machine you are cool. If on a friends Windows with no grub it will install and chainload Windows to grub. That freaks the owner of Windows machine out he has never seen a boot menu by default he bypass's and go's straight to boot. Scowling words will give a Windows owner high state of anxiety. 
 With any USB installer program with Fat32 format can get the 4 gig of persistence max. And it
looks and acts like a Live CD but with 4 gig of peristence to hold system settings and upgrades and such. Real nice to have as Live CD is a lot faster booting up than CD.

When get to gparted use /boot 300 meg or so / most of Flash and swap the rest of drive.
Use ext3 and primary and on page 8 or so hit advanced and mirror where you put /boot

Be sure and look out for ADVANCED TAB.

---

### Post by tachuela on 2010-01-14
You could format ext4 Flahdrive or External; then install Ubuntu to it as any hard drive. Make sure Grub install to MBR of Flash or External. You can accomplish this in step 7 (or 8)"Advanced" Tap.

---

### Post by xeross on 2010-01-14
Already tried that but that way ubuntu was 100 times slower compared to running the Live Persistent version.

---

### Post by C.S.Cameron on 2010-01-14
You can make persistent partitions in ext3 or ext4 as follows:

This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 or ext4 partition to the right of this, labeled it "casper-rw".
Created a ext3 or ext4 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, removed CD, rebooted.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Changed desktop background, connected to wireless and installed FontForge.
Rebooted, changes were persistent.

---

### Post by xeross on 2010-01-14
Hmm I don't want to recreate any of my data, just convert the fat32 partition to ext4, as I said that ain't the tricky part, reconfiguring grub is, don't know how I should do that on a USB stick.

---

### Post by C.S.Cameron on 2010-01-14
I think grub on a persistent thumb drive,(created with usb-creator or unetbootin), is part of the image file and is not easily modified.
I have not heard of anyone having success running a Ubuntu Live Disk image in a ext3 or ext4 partition but I wish you good fortune.

---

### Post by Mighty_Joe on 2010-01-15
> **garvinrick4 said:**
> One problem exsists for me and that is you cannot make it mobile because it will look for mbr the
first time it update-grub. 

I have never seen this happen and I've been running Ubuntu off a USB flash drive for almost a year now.  

[QUOTE=xeross]
Already tried that but that way ubuntu was 100 times slower compared to running the Live Persistent version. 
[/QUOTE]

Odd.  My flash drive is much faster than a Live CD or USB.  There are some steps you can take to optimize your flash drive install ([links in this topic]("http://ubuntuforums.org/showthread.php?t=1193680&highlight=partition+table")).  

[QUOTE=xeross]
I said that ain't the tricky part, reconfiguring grub is, don't know how I should do that on a USB stick. 
[/QUOTE]

If you do a full install, it will overwrite your current GRUB configuration with the correct one (provided you select to install GRUB on the flash drive in the last step).

---

### Post by mwildam on 2012-06-21
> **C.S.Cameron said:**
> Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
That did not work for me because /cdrom not writable. :-(

---

