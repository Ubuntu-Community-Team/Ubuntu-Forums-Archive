---
title: "USB Devices only mount during boot"
date: 2010-05-31
forum: Installation &amp; Upgrades
---

### Post by David Brant on 2010-05-31
After upgrading to Lucid 10.4, I find that after booting I can no-longer auto-mount any USB drive when they are plugged in. They simply doesn't appear on the desktop as they did. Swap my PATA drive back to the one with 9.10 still installed on it and all is well.

However, if I have USB drives plugged in before boot, they appears on the desktop, but are not auto-mounted as previously. Also when I click on any drive icon for the first time there is no response. Try again (on any drive) an the devices will all auto-mount revealing their contents in the window that subsequently opens. Everything them seems fine. I can unmount and remount at my leisure with any number of devices.

I do not have the problem of root only access that others have mentioned. 
I have played with usbmount and pmount as others have suggested, to no avail. They have both been removed.
I have the HAL installed as default, and have already checked media_automount_open for Nautilus on the gconf-editor.
Disabling the floppy in the BIOS has not effect and I do not use autologin option.

With (say) two USB drives attached, whether the devices are recognised at boot or not after boot,
lsusb reveals:

Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 090c:1000 Feiya Technology Corp. Flash Drive
Bus 001 Device 002: ID 0781:5151 SanDisk Corp. Cruzer Micro Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Leaving an old USB stick plugged in to make post boot mounting an option is hardly elegant!

Any ideas as to what the problem might be and a possible solution would be very much appreciated.

---

### Post by Mr_Lazy on 2010-06-10
I would like to bump this thread by saying I have exactly the same issue... Is this a kernel problem? I have Lucid on three PCs (one is remix) and they all suffer from poor (or no) USB auto mounting since upgrading to Lucid.

I am finding it hard to sing the praises of Ubuntu to my Windows using colleagues when they know I have to reboot to use a USB stick.

---

### Post by Brunellus on 2010-06-17
Thread bump.  Same issue.  I have disabled the floppy in BIOS and blacklisted the floppy module in /etc/modprobe.d/blacklist.conf and I STILL cannot automount USB drives.

---

### Post by RichOlson on 2010-06-17
A similar problem for me after upgrading to 10.4. I have two external USB hard drives that I leave plugged in, but not always mounted. At boot bot will appear on the desktop and work normally. They also appear in the "Places" menu on the menu bar and in the "Places" menu in Nautilus. If I right click a drive icon and select "Safely remove drive" the drive disappears from the desktop, and it disappears from the "Places" menus, so I cannot easily remount it. I usually reboot.

I can live with this by leaving my USB drives mounted.

It appears that I also have a problem with USB flash drives. I just plugged one in and it automounted as USB0 rather than its normal descriptive name. I can't dismount it because I'm not root and it is not listed in the fstab

Looking for ideas.

---

### Post by ryguy999 on 2010-06-17
Easiest way to combat this is to use Disk Utility (System -> Administration -> Disk Utility).  You don't need to have the devices plugged in at boot for this to work.  If anyone needs any help, please don't hesitate to ask.

---

### Post by RichOlson on 2010-06-17
Thank you ryguy999, your suggestion will work for me. The USB flash drive still gets automounted as USB0 rather than its label, but that is a minor annoyance. I can use disk utility to dismount it, and thenremounting it displays the volume label.

---

### Post by ryguy999 on 2010-06-17
Glad I could help.

---

### Post by David Brant on 2010-06-19
Disk Utility does not work for me. Any USB plugged in after boot is simply not recognised whatsoever.

---

### Post by darkod on 2010-06-19
I'm not sure if it relates, but I think I noticed in 10.04 in User and Groups that the option automount usb is NOT selected by default.

Check your user permissions and add automount if necessary.

---

### Post by David Brant on 2010-06-19
Thanks for the feedback darkod. It's nice to see others sharing my concern. Unfortunately i have the full range of user permissions already set, but you are absolutely right that some are not set by default.

---

### Post by Anilix on 2010-06-22
I also confirm this problem and looking desperately for a solution. (USB HDs or sticks do not mount automatically no matter what)

Small detail, disk utility on my Lucid opens up with just an empty window.
I can only manually mount/unmount usb HDs and sticks through Storage Device Manager
(it does edit though the fstab if drive left mounted resulting in the hanging of the OS during the next boot)

Hoping for a solution soon

---

### Post by thahir1986 on 2010-06-22
thank you ryguy999...now i can auto-mount usb drives.

---

### Post by piccia on 2010-07-25
I had exactly the same problem, and it was caused by a bug/conflict/whoknows with the ndiswrapper kernel module. In the end, I had to recompile this module with the option DISABLE_USB.

---

