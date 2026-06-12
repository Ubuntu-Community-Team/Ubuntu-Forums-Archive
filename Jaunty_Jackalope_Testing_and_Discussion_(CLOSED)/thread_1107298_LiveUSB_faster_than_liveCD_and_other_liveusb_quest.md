---
title: "LiveUSB faster than liveCD and other liveusb questions"
date: 2009-03-26
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by andrewabc on 2009-03-26
So I have an empty 4gb ocz rally2.
I am planning on putting ubuntu on several old windows xp computers (complete format, maybe dual boot). Will probably test it on my new computer as well (faster than cd when testing).

1.
I am wondering is liveusb much faster than livecd? Faster to boot, and more responsive than running livecd, faster to install? More noticeable on older hardware as cd-roms are slower than usb2.0 and probably usb1.1?

2.
To do this, I download say jaunty beta .iso. I am using 8.10 (installed) so go to system->admin->create usb startupdisk->select beta .iso, have my usb stick inserted and select it. Then the livecd would basically be on the usb and act the same way?

3.
I would need to go into computer BIOS and set (or check) to make sure that usb is bootable (like making sure it boots/checks from cd-rom before hard disk).

4.
If at some point I want to put say 9.04 final on usb, Do I go through same procedure and it will overwrite the 9.04 beta partition on usb stick?
Is it possible to have say 9.04 ubuntu, xubuntu, kubuntu, ubuntux64 all on the same usb? Would I be presented with grub or something so I could choose which version of ubuntu to boot (which I could then install)?

5.
To get rid liveusb completely on usb stick I would just format usb stick and it goes back to the way it was before I did anything to it? Would a simple open device/view folder and delete all files (and hidden) and it would be gone?

Some links:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

EDIT:
I also have 2gb and 4gb kingston datatravelers that are couple years old and are 6 times slower than rally2, so I could test on them. Would I only notice a speed difference on newer computers that could handle the increased read/write? On older computers slower usb would not make a difference since HD/processor probably could not handle increased speed?

EDIT:
are problems shown in my link above resolved?
> After finishing the installation, edit /etc/fstab and make sure that /media/cdrom0 points to the CD drive and not to the USB drive. If you don't, you might get this error when trying to mount a USB drive: "Cannot mount volume. Invalid mount option when attempting to mount the volume." This is because the installer believes it is installing from a CD drive
I don't want to edit fstab.

EDIT:
installing it to my 2gb kingston now.
copying files to USB took less than 2 minutes. doing other installation stuff to usb took about 15 seconds.
I choose to use the "save documents and settings" to 128mb partition instead of the "forget everything when shutdown"
I'll have to use "forget everything" option for when I am installing to multiple computers so none of my stuff is copied over. Although it could make default firefox+addons+plugins easier to do.

EDIT:
For some reason when done installing to USB stick and restarting my computer (usb stick still mounted), the shutdown background did not appear, but a garbled multicoloured background appeared. It did shutdown normally though.

Booting from USB worked good.
Selected to boot from usb-zip, and ubuntu alpha 6 livecd showed up very fast. Although when I selected to "try ubuntu without making changes to computer" it took about 10 seconds to move away from that screen.
It took a total of 1:42 to boot to working desktop which is really fast and almost just as fast as it takes me to boot with 8.10 installed.

Programs are much more responsive (openoffice/firefox) and faster to load.

So far it looks like I will be switching to liveUSB instead of carrying around several cd-rw

EDIT:
Attempted to install alpha6 to liveusb again (while it was already installed) and tried the "don't remember settings" and got an error. According to the log (relevant part):
```
[18:55:55] Unmounting source volume.
[18:55:55] Install command exited with code: 256
[18:55:55] Forcing shutdown of the install process.
[18:55:55] Unmounting source volume.
[18:55:55] Install failed.
[18:55:55] updating dest_status as part of update_row_state
[18:55:55] prop modified
[18:55:55] device_udi: /org/freedesktop/Hal/devices/volume_uuid_3433_3231
[18:55:55] num_changes: 1
[18:55:55] change: volume.is_mounted_read_only
```
So, what that mean? Have to format usb before installing again? I want to install beta when it is released tonight.

EDIT:
Well I installed gparted, formatted the drive, then installed again. Guess that is the easiest solution.

EDIT:
2:05 to install beta to usb using 2gb kingston
1:27 to boot to beta desktop using 2gb kingston

1:15 to install beta to usb using 4gb oczrally2   1:14 second time.
1:20 to boot to beta desktop using 4gb oczrally2

---

### Post by andrewabc on 2009-03-29
Here are my results:

22 minutes to burn beta to cd-rw
3:48 to boot beta on cd-rw

2:05 to install beta to usb using 2gb kingston
1:27 to boot to beta desktop using 2gb kingston

1:15 to install beta to usb using 4gb oczrally2 1:14 second test.
1:20 to boot to beta desktop using 4gb oczrally2 

1:34 to boot to my installed intrepid partition. Some installed programs probably add 5 seconds.

All on core2duo e6300, 3gb ram, intel 965 video card.

Oddly, with liveusb I never got the login screen (GDM). With livecd I got the login screen (GDM).

Liveusb uses 702mb on usb, and also you can have >128mb of reserved space so it remembers your personal stuff (I think /home folder, it remembered firefox extension/history, wallpapers etc). So you would need 1gb usb to work.
I could not get liveusb to work on my old pentium4 computer. After BIOS kingston usb would give flashing _ at top left of screen. rally2 would give *invalid partition table_* at top left of screen.

So if you have a spare 1gb+ usb, definitely try liveusb, it is much faster. liveusb is much more responsive when opening programs and clicking on menus. I have not installed using liveusb, but I plan on doing so when final is released. And I plan on trying liveusb on other computers when I put ubuntu on them because it is much faster.

---

### Post by wirechief on 2009-04-05
I tried Ubuntu 9.04 USB stick installer and it works great! very
easy to install and use, I then installed Ubuntu on a test partition on my Lenovo. I am going to have to work on the fstab file as mentioned it does not have a entry for cdrom. I will have
to do more testing, I am pleased with the speed and smoothness that
this release has so far.

---

