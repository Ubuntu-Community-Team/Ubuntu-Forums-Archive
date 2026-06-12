---
title: "usb automount---what the hell?"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by desleep on 2007-11-26
I love ubuntu, have been using since 5.10 but I have had a guts full of gutsy! Why would canonical release an operating system that doesn't automount usb? Lets face it, it is sooooo basic in year 2007 that most home users need to perform usb mounts daily. I dont want to spend hours searching the net, viewing kernel error logs, editing config files, trying this fix or that. I dont have the skillset to find the bug. but I am not a total dummy either!

Does anyone out there have a cure for this issue in Kubuntu Gutsy?

many thanks

---

### Post by petteriIII on 2007-11-27
Gutsy does automount, too. But automounting may sometimes stand in the way and it must be possible to switch it off. The setting in the beginning is automount on, but it is possible that it has been switched off by some program. In Ubuntu it is set in: System / Settings / Removable drives (the words are re-re-translated from Finnish and may be different) => the tick marks on those squares.

---

### Post by drs305 on 2007-12-03
The first place I'd look is System, Preferences, Removable Drives & Media Preferences to ensure automounting is enabled.

Hey, I swear petteriIII's post, listed as 6 days ago, wasn't there when I posted. In fact, the original post just showed up as new on my computer!

Edited again: Found my error, answer got posted in the wrong thread.  Administrators please delete, otherwise ..... D'OH !!!

---

### Post by desleep on 2007-12-06
thanks for your responses, still havent got it worked out yet! btw I am using kubuntu so is there a way to enable automount via the command line or is there a graphical tool to do that?

---

### Post by ac7ss on 2007-12-07
> **desleep said:**
> thanks for your responses, still havent got it worked out yet! btw I am using kubuntu so is there a way to enable automount via the command line or is there a graphical tool to do that?

Looking for the same thing. Currently I am using some command line scripts and fstab entries to make it quicker. However, it would be nice to automate them.

---

### Post by daimaru on 2007-12-07
fu
> **desleep said:**
> I love ubuntu
just a bit pissed at your original post so here's my answer to your question:
if you love ubuntu then use it (gnome as it was meant to be). maybe you wont have so many problems with "ubuntu" as you have with "kubuntu". did you even try ubuntu ? my usb  devices mount right away, so that stuff about 2007 gutsy not automounting usb just applies to your crappy computer or your choice of kubuntu (which sucks IMHO) .

ps: only posting this because you dissed ubuntu...

---

### Post by desleep on 2007-12-07
> **daimaru said:**
> just a bit pissed at your original post so here's my answer to your question:
if you love ubuntu then use it (gnome as it was meant to be). maybe you wont have so many problems with "ubuntu" as you have with "kubuntu". did you even try ubuntu ? my usb  devices mount right away, so that stuff about 2007 gutsy not automounting usb just applies to your crappy computer or your choice of kubuntu (which sucks IMHO) .

ps: only posting this because you dissed ubuntu...

Thats not an answer, thats just you being a dumbass. I have used (k)ubuntu for 3 years unlike you. So I feel I have a justified complaint/comment regarding this issue. When this is meant to be a user-friendly OS and it takes weeks to nut out something as ubiquitous as mounting a usb drive, well something has gone awry. Its not just me either. I dont want to spend my spare time deciphering kernel messages and editing config scripts just so I can use my machine. I want to do work on it!  So before you get your panties in a wad, there are people who use computers and people who waste their lives in front of the screen. which one are you?

---

### Post by viking777 on 2007-12-07
Not sure if this is going to help but try it anyway.

Start Menu/System Settings/Desktop/Behaviour/Device Icons tab.

Make sure that 'show device icons' is ticked then look through the list and make sure there are ticks in the boxes labelled 'Mounted removable medium' and 'Unmounted removable medium'. As well as that, right click the taskbar, click 'Add applet' and choose the 'Storage Media' applet. 

Now plug in a USB device and hopefully you should see an icon for it either on the desktop or in the taskbar (or both). Click the taskbar icon (or right click the desktop icon) and choose properties and the 'Mounting' tab. There you will find a check box labelled 'Mount automatically' tick this and voila it should happen. Incidentally the 'mountpoint' box should say '/media/' (no quotes) unless you want it mounted somewhere else.

PS Another thought is that perhaps for some reason you do not have the udev daemon running (udev is the program that mounts plug in devices) try this in a terminal:

sudo ps aux|grep udev

the response should include the the words /sbin/udevd - if it does then that is not the problem.

---

### Post by desleep on 2007-12-07
Viking thanks for your efforts, all the mount device check boxes are ticked,

paul@varuna:~$ sudo ps aux|grep udev
root      2651  0.0  0.1   3040  1384 ?        S<s  10:26   0:00 /sbin/udevd --d                                aemon
paul      6206  0.0  0.0   2976   760 pts/2    R+   10:33   0:00 grep udev

and

paul@varuna:~$ dmesg | grep usb
[   24.772078] usbcore: registered new interface driver usbfs
[   24.772101] usbcore: registered new interface driver hub
[   24.772118] usbcore: registered new device driver usb
[   27.229246] usb usb1: configuration #1 chosen from 1 choice
[   27.330453] usb usb2: configuration #1 chosen from 1 choice
[   27.434468] usb usb3: configuration #1 chosen from 1 choice
[   27.538399] usb usb4: configuration #1 chosen from 1 choice
[   27.698141] usb 1-2: new full speed USB device using uhci_hcd and address 2
[   27.903772] usb 1-2: configuration #1 chosen from 1 choice
[   36.509015] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 2 if 0 alt 1 proto 2 vid 0x03F0 pid 0x1004
[   36.509035] usbcore: registered new interface driver usblp
[   36.509038] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
[  604.132244] usb 3-1: new full speed USB device using uhci_hcd and address 2
[  604.300257] usb 3-1: configuration #1 chosen from 1 choice
[  604.366278] usbcore: registered new interface driver libusual
[  604.394599] usb-storage: device found at 2
[  604.394603] usb-storage: waiting for device to settle before scanning
[  604.394858] usbcore: registered new interface driver usb-storage
[  609.392541] usb-storage: device scan complete

and

paul@varuna:~$ tail /var/log/messages -f
Dec  8 10:36:29 varuna kernel: [  610.914025] end_request: I/O error, dev sda, sector 253
Dec  8 10:36:29 varuna kernel: [  610.921024] end_request: I/O error, dev sda, sector 254
Dec  8 10:36:29 varuna kernel: [  610.928024] end_request: I/O error, dev sda, sector 253
Dec  8 10:36:29 varuna kernel: [  610.935018] end_request: I/O error, dev sda, sector 254
Dec  8 10:36:29 varuna kernel: [  610.944024] end_request: I/O error, dev sda, sector 0
Dec  8 10:36:29 varuna kernel: [  610.951019] end_request: I/O error, dev sda, sector 1
Dec  8 10:36:29 varuna kernel: [  610.958013] end_request: I/O error, dev sda, sector 0
Dec  8 10:36:29 varuna kernel: [  610.965008] end_request: I/O error, dev sda, sector 0
Dec  8 10:36:29 varuna kernel: [  610.972026] end_request: I/O error, dev sda, sector 1
Dec  8 10:38:16 varuna kernel: [  717.276262] usb 3-1: USB disconnect, address 2

Dec  8 10:38:40 varuna kernel: [  741.212015] usb 3-1: new full speed USB device using uhci_hcd and address 3
Dec  8 10:38:40 varuna kernel: [  741.380034] usb 3-1: configuration #1 chosen from 1 choice
Dec  8 10:38:40 varuna kernel: [  741.383082] scsi1 : SCSI emulation for USB Mass Storage devices
Dec  8 10:38:45 varuna kernel: [  746.383351] scsi 1:0:0:0: Direct-Access     NIKON    D40              1.00 PQ: 0 ANSI: 2
Dec  8 10:38:45 varuna kernel: [  746.388348] sd 1:0:0:0: [sda] 1973249 512-byte hardware sectors (1010 MB)
Dec  8 10:38:45 varuna kernel: [  746.391331] sd 1:0:0:0: [sda] Write Protect is off
Dec  8 10:38:45 varuna kernel: [  746.400417] sd 1:0:0:0: [sda] 1973249 512-byte hardware sectors (1010 MB)
Dec  8 10:38:45 varuna kernel: [  746.403334] sd 1:0:0:0: [sda] Write Protect is off
Dec  8 10:38:45 varuna kernel: [  746.403348]  sda: sda1
Dec  8 10:38:45 varuna kernel: [  746.411365] sd 1:0:0:0: [sda] Attached SCSI removable disk
Dec  8 10:38:45 varuna kernel: [  746.411407] sd 1:0:0:0: Attached scsi generic sg0 type 0
Dec  8 10:38:45 varuna kernel: [  746.559274] end_request: I/O error, dev sda, sector 1973248
Dec  8 10:38:45 varuna kernel: [  746.559281] printk: 757 messages suppressed.
Dec  8 10:38:45 varuna kernel: [  746.566277] end_request: I/O error, dev sda, sector 1973248
Dec  8 10:38:45 varuna kernel: [  746.573274] end_request: I/O error, dev sda, s


and

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc /proc proc defaults 0 0
# /dev/hda7
UUID=322fc337-8489-49d2-a800-9cfea99a221a / reiserfs nouser,notail,atime,auto,rw,dev,exec,suid 0 1
# /dev/hda6
UUID=3e35b451-5632-4708-82d3-91a4bc6606c3 /home reiserfs nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hdb1
UUID=567a9949-f87d-464c-8261-6a283fd3b5ad /media/data ext3 nouser,defaults,atime,auto,rw,dev,exec,suid 0 2
# /dev/hda5
UUID=214d78e0-b42f-41ba-ae42-1f779f72737d none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/hdd /media/cdrom1 udf,iso9660 user,atime,noauto,rw,dev,exec,suid 0 0
/dev/sda1 /media/camera vfat noauto,uid=1000,gid=1000,rw,users 0 0
usbfs /proc/bus/usb usbfs devgid=1001,devmode=664 0 0


and

mtab

/dev/hda7 / reiserfs rw,notail 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
/sys /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,noexec,nosuid,nodev,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
procbususb /proc/bus/usb usbfs rw 0 0
udev /dev tmpfs rw,mode=0755 0 0
devshm /dev/shm tmpfs rw 0 0
devpts /dev/pts devpts rw,gid=5,mode=620 0 0
lrm /lib/modules/2.6.22-14-generic/volatile tmpfs rw 0 0
/dev/hda6 /home reiserfs rw 0 0
/dev/hdb1 /media/data ext3 rw 0 0
usbfs /proc/bus/usb usbfs rw,devgid=1001,devmode=664 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0



if you can point me in the right direction....as I am not sure where to start.

---

### Post by ac7ss on 2007-12-08
> **desleep said:**
> Viking thanks for your efforts, all the mount device check boxes are ticked,

paul@varuna:~$ tail /var/log/messages -f
Dec  8 10:38:40 varuna kernel: [  741.212015] usb 3-1: new full speed USB device using uhci_hcd and address 3
Dec  8 10:38:40 varuna kernel: [  741.380034] usb 3-1: configuration #1 chosen from 1 choice
Dec  8 10:38:40 varuna kernel: [  741.383082] scsi1 : SCSI emulation for USB Mass Storage devices
Dec  8 10:38:45 varuna kernel: [  746.383351] scsi 1:0:0:0: Direct-Access     NIKON    D40              1.00 PQ: 0 ANSI: 2
Dec  8 10:38:45 varuna kernel: [  746.388348] sd 1:0:0:0: [sda] 1973249 512-byte hardware sectors (1010 MB)
Dec  8 10:38:45 varuna kernel: [  746.391331] sd 1:0:0:0: [sda] Write Protect is off
Dec  8 10:38:45 varuna kernel: [  746.400417] sd 1:0:0:0: [sda] 1973249 512-byte hardware sectors (1010 MB)
Dec  8 10:38:45 varuna kernel: [  746.403334] sd 1:0:0:0: [sda] Write Protect is off
Dec  8 10:38:45 varuna kernel: [  746.403348]  sda: sda1
Dec  8 10:38:45 varuna kernel: [  746.411365] sd 1:0:0:0: [sda] Attached SCSI removable disk
Dec  8 10:38:45 varuna kernel: [  746.411407] sd 1:0:0:0: Attached scsi generic sg0 type 0
Dec  8 10:38:45 varuna kernel: [  746.559274] end_request: I/O error, dev sda, sector 1973248
Dec  8 10:38:45 varuna kernel: [  746.559281] printk: 757 messages suppressed.
Dec  8 10:38:45 varuna kernel: [  746.566277] end_request: I/O error, dev sda, sector 1973248
Dec  8 10:38:45 varuna kernel: [  746.573274] end_request: I/O error, dev sda, s

...

if you can point me in the right direction....as I am not sure where to start.

I still have a similar problem. However, yours is showing, in the /var/log/messages file, an IO error from the kernel where mine doesn't. Other than that, my outputs are very similar to yours (with the exception of an entry in fstab for each usb drive so that they mount at specific points.) Have you tried to mount it manually ```
sudo mount /dev/sda1 /media/mountable
``` with the /media part pointing at an actual mountpoint directory?

From the /var/log/messages it looks like you have more problems than merely the automount, but I could be mistaken. Can you mount the drive on another machine?

---

### Post by desleep on 2007-12-08
It worked perfectly on Feisty, which is so annoying! 

the problems occurred after an upgrade. Actually I did a clean install but kept my home directory.

---

### Post by ac7ss on 2007-12-08
Now comparing the desktop (not working) to the laptop (working):

uname -a             __    same kernel (build times off by about 30 minutes.)
/var/log/messages  __ same output.
dmesg |grep usb __    same output.
fstab            __           laptop does not have lines for the devices. but the desktop did not at first either.
/sbin/udevd      __       same size and date.
/etc/udev/rules.d  __  some extra files on the laptop (related to RAID drives that I do not have)

I am still stymied.

---

### Post by viking777 on 2007-12-08
[QUOTE=desleep

the problems occurred after an upgrade. Actually I did a clean install but kept my home directory.[/QUOTE]

This is probably the cause then. The technique of keeping settings from one release and expecting them to work on another release is one that I have tried myself and has always,always failed. I know there will be a lot who disagree with me here but I am only speaking from my own experience.

My advice is to get your install disk and start again with a new installation complete with new home folder, the only things you want to copy into it are things you have created or downloaded yourself like documents, photos, music, programs etc.

You will have to spend time reconfiguring things I know but at least simple things like automounting will work properly.

---

### Post by desleep on 2007-12-08
ok I will do that now and report back!

---

### Post by desleep on 2007-12-09
Well, fresh install formatted my home dir and / partition.

The expectations was running high but denada zero zilch difference!

---

### Post by desleep on 2007-12-09
Dec 10 11:55:10 varuna kernel: [ 6590.003848] usb 3-1: new full speed USB device using uhci_hcd and address 3
Dec 10 11:55:11 varuna kernel: [ 6590.171857] usb 3-1: configuration #1 chosen from 1 choice
Dec 10 11:55:11 varuna kernel: [ 6590.174913] scsi1 : SCSI emulation for USB Mass Storage devices
Dec 10 11:55:16 varuna kernel: [ 6595.175175] scsi 1:0:0:0: Direct-Access     NIKON    D40              1.00 PQ: 0 ANSI: 2
Dec 10 11:55:16 varuna kernel: [ 6595.180154] sd 1:0:0:0: [sda] 1973249 512-byte hardware sectors (1010 MB)
Dec 10 11:55:16 varuna kernel: [ 6595.183150] sd 1:0:0:0: [sda] Write Protect is off
Dec 10 11:55:16 varuna kernel: [ 6595.192146] sd 1:0:0:0: [sda] 1973249 512-byte hardware sectors (1010 MB)
Dec 10 11:55:16 varuna kernel: [ 6595.195170] sd 1:0:0:0: [sda] Write Protect is off
Dec 10 11:55:16 varuna kernel: [ 6595.195178]  sda: sda1
Dec 10 11:55:16 varuna kernel: [ 6595.203205] sd 1:0:0:0: [sda] Attached SCSI removable disk
Dec 10 11:55:16 varuna kernel: [ 6595.203246] sd 1:0:0:0: Attached scsi generic sg0 type 0
Dec 10 11:55:16 varuna kernel: [ 6595.341102] end_request: I/O error, dev sda, sector 1973248
Dec 10 11:55:16 varuna kernel: [ 6595.341108] printk: 757 messages suppressed.
Dec 10 11:55:16 varuna kernel: [ 6595.348098] end_request: I/O error, dev sda, sector 1973248
Dec 10 11:55:16 varuna kernel: [ 6595.355094] end_request: I/O error, dev sda, sector 1973240
Dec 10 11:55:16 varuna kernel: [ 6595.362092] end_request: I/O error, dev sda, sector 1973241
Dec 10 11:55:16 varuna kernel: [ 6595.370089] end_request: I/O error, dev sda, sector 1973240
Dec 10 11:55:16 varuna kernel: [ 6595.377099] end_request: I/O error, dev sda, sector 1973241
Dec 10 11:55:16 varuna kernel: [ 6595.384085] end_request: I/O error, dev sda, sector 1973248
Dec 10 11:55:16 varuna kernel: [ 6595.391081] end_request: I/O error, dev sda, sector 1973248

---

### Post by viking777 on 2007-12-10
I'm sorry to hear that. 

I have been having trouble with an external device recently although it was mainly my fault I guess, it was an external hard drive that was working fine when formatted FAT32, but I decided to reformat it to NTFS after which it wouldn't mount properly. I don't know if this is relevant to your situation or not but just in case it is I will pass on the fix I found as it is a very easy one.

First I should say that I use KDE desktop so if you are using Gnome you will have to work out a way to translate the instructions to fit that desktop. Second it only works if you actually get a desktop icon for your device. This is what I did.

Right click desktop icon, select properties and go to the 'mounting' tab. In there you will find a checkbox titled 'mount as user' which will probably be selected. If it is then unselect it. For me that was all that was required, my devices now worked normally again. As I said I am not sure if that is relevant to your situation, but if it is then give it a try.

---

### Post by ingo on 2007-12-10
Oddly enough my kubuntu 07.10 installation has NO problems with USB drives/sticks. But I did have that problem some time ago. It was related to the ehci_hcd module - here is the link for what it's worth: [https://bugs.launchpad.net/bugs/88746](https://bugs.launchpad.net/bugs/88746)

---

### Post by LarryJ2 on 2007-12-10
> **viking777 said:**
> Not sure if this is going to help but try it anyway.

Start Menu/System Settings/Desktop/Behaviour/Device Icons tab.

Make sure that 'show device icons' is ticked then look through the list and make sure there are ticks in the boxes labelled 'Mounted removable medium' and 'Unmounted removable medium'. As well as that, right click the taskbar, click 'Add applet' and choose the 'Storage Media' applet. 

.

Thanks a thousand times Sir Viking777.  I spent an hour googling before I came to your post.  My usb devices now show up on the desktop when I plug them in as I am used to.   I have no idea how Show Device Icons  was unchecked or  turned off.  I did do the install from the Alt DVD's  so that might be the problem.  Anyway THANK YOU!

Larry

---

### Post by ac7ss on 2007-12-16
Gave up (along with another problem, the / drive was failing.) kept the /home drive and changed to a new / drive, installed Ubu 7.10. Works fine now. (Must... Change.... Colors.... AARG!) :)

---

