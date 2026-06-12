---
title: "Cannot Boot - blinking cursor on black screen after jaunty to karmic beta upgrade"
date: 2009-10-03
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jatinps on 2009-10-03
Hi All,

I was successfully running jaunty 64 bit on my ibm thinkpad x61s. I decided to upgrade to karmic koala beta yesterday.
The upgrade went ok (except for some dbus errors similar to [https://bugs.launchpad.net/ubuntu/+source/libchipcard/+bug/429853](https://bugs.launchpad.net/ubuntu/+source/libchipcard/+bug/429853) ). Post the upgrade the system rebooted and after the grub screen, all I have is a blinking cursor on a black screen. 

I hit upon this thread ([https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/431812](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/431812)) which seemed similar to my problem, however the solution mentioned there did not work.
Specifically i tried multiple times changing in grub, the kernel line to end with 'i915.modeset=0' and 'nomodeset', however nothing works. I just get a blinking cursor on a black screen.
I can type commands but they are not effective till I press a ctrl-alt-del, after which the commands execute, but the system just reboots. Not sure if this is related to mountall or i915.
I am now logged in via jaunty live cd and wanted to know if there is anything I can do to get things working again.
Thanks for any advice!

---

### Post by jatinps on 2009-10-03
ok i tried a few things
when i get the blinking cursor on black screen (after grub screen), I can do a ctrl-alt-del and get to the prompt and quickly do a init 3 and prevent system reboot. After this I can do ctrl-atl-f2 and login. 
I can also do a sudo dhclient eth0 and get an ip addy and get internet access.
However it seems the file system is mounted as ro. 
This also explains the message on tty1 (after I press ctrl-alt-del) which says "cannot remove /forcefsck read-only file-system"
Should I boot from jaunty livecd and add /fastboot to my partition. Will that work?

---

### Post by jatinps on 2009-10-03
Ok I am in - there are lots of errors being automatically reported by apport, I have no wireless and apport picked up some errors in kernel, wicd, emphathy, monitor.py, etc.

To repeat my issues, my system is an x61s, it does not boot correctly after jaunty to karmic beta upgrade. After grub, I get a blinking cursor on a black screen. 

How I finally got in - 
1) I need to do a ctrl-alt-del to get to a prompt, then quickly type init 3 to prevent reboot. 
2) After this I need to remount the file system as rw 
3) then do a sudo service dbus start, followed by sudo service hal start, sudo service gdm start. 
4) This gets me into the gui. This is where I have lots of serious issues reported by apport for kernel, wicd, emphaty, etc.

I can provide any information needed to fix all these issues.

---

### Post by agurk on 2009-10-03
I'm fairly certain that upgrades between alpha or beta releases are not supported. Better install fresh.

---

### Post by jatinps on 2009-10-03
I was not upgrading from an alpha release. I was on jaunty stable 9.04 and decided to upgrade to karmic beta.
I think most of my errors are releated to dbus.

---

### Post by agurk on 2009-10-03
Ah, gotcha, my bad.

---

### Post by darrenm on 2009-10-03
Hmm same here. System boots as normal but gets stuck loading X

Xorg.0.log is just:
```
X.Org X Server 1.6.3
Release Date: 2009-7-31
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server x86_64 Ubuntu
Current Operating System: Linux darrenm-desktop 2.6.31-11-generic #38-Ubuntu SMP Fri Oct 2 11:06:40 UTC 2009 x86_64
Kernel command line: root=/dev/mapper/nvidia_beeccbde3 ro quiet splash
Build Date: 28 September 2009  10:11:45AM
xorg-server 2:1.6.3-1ubuntu7 (buildd@crested.buildd)
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Oct  3 20:21:02 2009
(II) Loader magic: 0xb40
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.4
        X.Org Video Driver: 5.0
        X.Org XInput driver : 4.0
        X.Org Server Extension : 2.0
(II) Loader running on linux
(++) using VT number 7
```

It was working earlier today. Upgraded from Jaunty to Karmic. X is running.

I've tried moving xorg.conf out the way so it's not using the Nvidia binary driver but there's no difference. Not sure how to investigate any further with the new upstart. I've got SSH in to the box but can't switch VTs with CTRL-ALT. It's hung on every one.

---

### Post by aatdark on 2009-10-04
same here but i cann't even boot the live cd.

version: desktop , karmic beta amd64

on an Intel E6600.

i tried disabling acpi=off and noapci (disabled using F6)

if i remove the quit option from the prompt i see a lot of messages but after 2 secs the screen is cleared an a cursor is blinking. Nothing happens.

the system runs a jaunty amd64 without any problems.

any suggestions?

---

### Post by jatinps on 2009-10-04
well after looking around for quite some time, I decided to just do a clean install. Although I could get into X with the solution, I put up above, the system was pretty much un-usable with loads of errors in anything i touched.
I made a usb installer of karmic beta to see if things work in livecd mode. All looked good, so went and did a clean install (had already backed up my office windows vm image and home directory earlier). Now things are working perfectly and I am well on the road to recovery.
I think the upgrade install is a bad idea, if thats what you'll are doing. The clean install is perfect so far!

---

### Post by emarkay on 2009-10-04
This sounds similar to my issue - I presumed it was an ATI/AMD video problem!

[http://ubuntuforums.org/showthread.php?p=8046744#post8046744](http://ubuntuforums.org/showthread.php?p=8046744#post8046744)

---

### Post by mgol on 2009-10-04
Upgrade usually works ok, but there is a HUGE leap between Jaunty and Karmic - just look at:
[http://www.ubuntu.com/testing/karmic/beta](http://www.ubuntu.com/testing/karmic/beta)

Upstart, GRUB2, kernel update from 2.6.28 to 2.6.31, hal depreciation, ext4, KMS (for Intel graphic cards)... It's very rare to have such a large update between two neighbour versions.

So yes, I'd advice to do a fresh install this time, even if You usually (as I do) prefer to upgrade.

---

### Post by jppr on 2009-10-04
> **aatdark said:**
> same here but i cann't even boot the live cd.

version: desktop , karmic beta amd64

on an Intel E6600.

i tried disabling acpi=off and noapci (disabled using F6)

if i remove the quit option from the prompt i see a lot of messages but after 2 secs the screen is cleared an a cursor is blinking. Nothing happens.

the system runs a jaunty amd64 without any problems.

any suggestions?

i try fresh install todays livecd but when i go that install ubuntu goes little time and is same blinking cursor on black screen. i must install 9.04 and sudo do-release-upgrade --devel-release... yes, i know sudo updade-manager -d but i did it that way now  :)

i have little another problem also... when i boot, there is error...  upgrade bios or use force_addr=0xaddr

motherboard is asrock 939A8X-M but i don´t understand system how update bios, i don´t have xp or vista only upgradet 9.10 and i don´t know how update bios without xp or vista...   :)

---

### Post by mgol on 2009-10-04
> **jppr said:**
> i don´t know how update bios without xp or vista...   :)
Sometimes bootable installers (often with DOS-like system) are available, but it depends on Your motherboard supplier.

---

### Post by darrenm on 2009-10-05
Mine was like this:

boot into normal Ubuntu, blank screen and cursor flashing.
reboot into recovery mode, apt-get remove --purge nvidia-* then apt-get install nvidia-glx-185
boot into normal Ubuntu once and it works.
Next reboot it would hang again so I had to do the same process.

But today a hal update seems to have fixed it?

---

