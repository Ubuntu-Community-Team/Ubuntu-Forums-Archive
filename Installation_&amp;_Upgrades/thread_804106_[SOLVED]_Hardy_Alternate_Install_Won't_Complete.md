---
title: "[SOLVED] Hardy Alternate Install Won't Complete"
date: 2008-05-22
forum: Installation &amp; Upgrades
---

### Post by Nazrax on 2008-05-22
I have a desktop machine that I'm trying to install Hardy on, and I'm trying to use the Alternate disk to be able to use LVM. Unfortunately, the install won't complete.

I've verified the disk burned correctly, and I'm booting with all the troubleshooting parameters I could find: vga=771, acpi=off, noapic, nolapic. Whatever I do, the same thing happens: it installs the base system fine, then it tries to install the rest of the packages (I believe the dialog reads "Select and install packages"). It gets to 6%, stops for 20 minutes, then dies.

Each time I've run the installation, the logs have looked the same. Here are the last few lines from dpkg.log:

> 
2008-05-22 15:36:18 configure xserver-xorg 1:7.3+10ubuntu10 1:7.3+10ubuntu10
2008-05-22 15:36:18 status unpacked xserver-xorg 1:7.3+10ubuntu10
2008-05-22 15:36:18 status half-configured xserver-xorg 1:7.3+10ubuntu10
2008-05-22 15:36:20 status installed xserver-xorg 1:7.3+10ubuntu10
2008-05-22 15:36:20 trigproc libc6 2.7-10ubuntu3 2.7-10ubuntu3
2008-05-22 15:36:20 status half-configured libc6 2.7-10ubuntu3
2008-05-22 15:36:20 status installed libc6 2.7-10ubuntu3
2008-05-22 15:56:16 startup packages configure


Notice the 20 minute gap after installing libc6.

Here are the last few lines from apt/term.log:

> 
Setting up xserver-xorg-video-vmware (1:10.15.2-1ubuntu2) ...
Setting up xserver-xorg-video-voodoo (1:1.1.1-5) ...
Setting up xserver-xorg-video-all (1:7.3+10ubuntu10) ...
Setting up xserver-xorg (1:7.3+10ubuntu10) ...
FATAL: Error inserting battery (/lib/modules/2.6.24-16-generic/kernel/drivers/acpi/battery.ko): No such device

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Log ended: 2008-05-22  15:36:20


This is a newer Dell desktop.

How can I get this working?

Thank you.

---

### Post by Pumalite on 2008-05-22
Are you wired to the Internet? How?

---

### Post by Nazrax on 2008-05-23
I'm on a lan with dhcp. I haven't checked manually, but setup reports that it gets an IP.

---

### Post by Pumalite on 2008-05-23
Burn a new CD. Do md5sum on your iso, burn at 4x or less on CD-R, check CD integrity before install,

---

### Post by Nazrax on 2008-05-23
CD integrity check passes, MD5sum matches.

---

### Post by Pumalite on 2008-05-23
We are left with hardware incompatibility, Have you installed other distros?

---

### Post by james_vanb on 2008-05-23
Having same issue.  Hangs at 6% while installing software followed by error message that install failed and option to retry.  In my case, started with Xubuntu Gutsy, upgraded to Xubuntu Hardy, then loaded Gnome desktop to get Ubuntu Hardy.  Was running well, however i found that in some intances gedit would not allow editing but mousepad would (old Xubuntu default text editor).  In an effort to get defaults sorted out, thought clean install best option.  Doesn't sound like a hardware problem as Ubuntu Hardy was running well previous to clean install attempt.  Burned iso at 4x, confirmed burn, etc.  Neither live cd nor alternate will load.

---

### Post by Pumalite on 2008-05-23
Is your burner working well?. Clean the lens, Try your CD in different computer. Burn the iso in another computer and try the CD in yours.

---

### Post by james_vanb on 2008-05-23
Thanks for quick reply.  Have burned 2 live cd's and 2 alternates using Braserio.  Burned the Xubuntu using software in XP.  Would be ironic if I need XP to get Ubuntu back.

---

### Post by Nazrax on 2008-05-23
This machine is already running Ubuntu Gutsy (upgraded from Feisty).

I believe I had the same problem last time around. I wanted LVM, but the alternate installer wouldn't work (same exact problem), so I gave up and used the LiveCD, and it worked fine. This time, I don't have that option - I need LVM.

---

### Post by Nazrax on 2008-05-23
Well, I got it installed.

I ended up using Expert mode, accepting all the defaults, then telling it to load everything from the ISO instead of the CD.

---

