---
title: "New Feisty install locks keyboard"
date: 2007-05-31
forum: Installation &amp; Upgrades
---

### Post by Yendor on 2007-05-31
Okay guys, I'm in some real trouble here.  I tried upgrading my wifes computer from Edgy to Feisty, got errors about the Nvidia driver, locked up and had to hard reboot.  The system wouldn't come back up.  I ended up doing a fresh install of Feisty from the alternate CD (same CD I used to install on my sons laptop with no problems).  It installed just fine, but now when it boots up, I'm stuck at the log-in screen with a non-responsive keyboard.  The mouse still works, got a blinking cursor in the Username box, but nothing I do on the keyboard does anything (shift-lock won't even light up the keyboard light).  I can click Options to reboot or shut down, so it would seem everything else is fine.

Nothing changed on the system except re-formatting and installing Feisty, and it worked wonderfully with Edgy (as my wife keeps reminding me).  The keyboard works to get into bios, and thumping enter boots up without waiting for the timer on the grub screen.  The moment the log-in screen appears though, all keyboard response stops.

Not sure what stats would be helpful here ... or what I can get from the computer.  It's a PS/2 keyboard, USB mouse on a 1.8Ghz celeron with 2 gigs of ram.

---

### Post by southernman on 2007-05-31
The thing that comes to mind right off, when you did the install, is it possible you entered incorrect info about the keyboard setup?

Do you have a copy of the Livecd? If so, try booting the computer with it in and see what happens... just a suggestion.

---

### Post by southernman on 2007-05-31
uh oh! I can see it now. Yendors wife came home - found out what he'd done - and began beating him about the head... profusely with her keyboard!

Just joshing, Mrs. Yendor... lol ;)

---

### Post by Yendor on 2007-05-31
Thank you southernman, your suggestion makes sense.  I thought I chose the proper keyboard during install, but it's not working.  Looks like I'll try re-installing, just as soon as I can get these keyboard keys put back in their proper places.

---

### Post by Yendor on 2007-05-31
Okay, did a fresh reinstall ... same problem.  I'm sure I have the proper keyboard selected this time.  Booting into recovery mode from Grub also gives no keyboard response.  I can run the live CD with no problems, so can edit config files and get info if anyone has any suggestions.

---

### Post by xilon82 on 2007-05-31
I have the same problem too :(

---

### Post by bulldog on 2007-05-31
What kind of connectors do your keyboards have?
Do you have an old board some where to try?

It's hard to get some instructions to ubuntu without a keyboard.

---

### Post by Yendor on 2007-05-31
Pulled the USB keyboard off my son's computer ... it works fine on my wife's computer.  It must be something wrong in the PS/2 stuff.  Kinda need to get my son's keyboard back to him though ... any suggestions on how I can fix this so the PS/2 keyboard will work?

---

### Post by xilon82 on 2007-06-01
I've got a logitech ps/2 keyboard (mod. Corded DEluxe access)

---

### Post by southernman on 2007-06-01
From the FWIW category... I still use a ps/2 keyboard also. Not a bit of a problem with it regarding Ubuntu. *shrugs*

---

### Post by MartynT on 2007-06-03
I have a similar problem.

Installed 7.04 yesterday, and managed to apply some updates, including the new kernel.

Shortly after that my keyboard stopped working.  It's as if it's not plugged in.

So I re-installed again this morning and everything was fine again, for a while.

I've changed the /boot/grub/menu.lst ( to make windows the default).
I've also deleted a few resolutions from /etc/X11/xorg.conf (to try to get my system t odisplay 1024x768).

That's it.  No further downloads.

Now my keyboard doesn't work again.

If I boot into rescue mode the keyboard works (at least long enough to edit menu.lst to have the correct default).

Almost time to throw the towel in. :(

---

### Post by MartynT on 2007-06-03
One other thing I notice is that the system wont shut down properly.  I click shutdown and the screen goes blac and stays like that until I power down.

---

### Post by ceder on 2007-06-03
Also having same problem as that posted in [http://ubuntuforums.org/showthread.php?t=459742&page=2](http://ubuntuforums.org/showthread.php?t=459742&page=2).

Ubuntu 7.04 Feisty. Update resulted in PS/2 keyboard problem (locked-up) [03 June 2007].

Installed Ubuntu 7.04 Feisty on a brand new PC with nothing previously on hard drive. Graphics card is MSI NX7600GS-TD256EH. Motherboard is INTEL BLKD946GZISSL Iselton Dual Core LGA775. CPU is INTEL CORE 2 DUO E6420 LGA775. Install went perfectly, apart from Ubuntu not being able to recognise native resolution of monitor (1400x1050 LCD Acer AL2017). Maximum resolution offered was 1024x768. System prompted for updates. Downloaded and installed the lot, about 80 Mb. Rebooted PC, and keyboard failed to be detected, dead as a dodo.

Spent some time trawling the web for solutions. So far have found a few postings, but nothing which has really solved the problem. Some postings referred to USB 'conflicts'. Tried many permutations of unplugging USB mouse, trying old PS/2 mouse, unplugging both mouse and keyboard until after restart, etc etc. Just about anything I could think of. Also tried various permutations of changing USB settings in the BIOS, to no avail.

Eventually out of desperation decided to re-install Ubuntu from scratch. Keyboard up and running once again. Second time round decided to only install selected updates, focussing on those which might help sort out display resolution problems, mostly related to restricted modules (proprietary drivers) (linux-restricted-modules). This download about 64Mb. Restarted PC, and hey presto, back to square one, dead keyboard. The keyboard failure problem therefore seems to be related to a bug in the linux-restricted-modules. Noticed one or two postings about issues related to linux-restricted-modules and nVidia drivers, bugs #33418 and #39073. If I boot from the live CD, keyboard is available. 

Rather frustrated. Any ideas for a solution would be greatly appreciated.

---

### Post by pilpi on 2007-06-17
As reported in the [other thread]("http://ubuntuforums.org/showthread.php?t=440141"), unless there are many different issues, for me it can be fixed just by rebooting the PC. Sometimes I need to reboot just once, but lately it's been more like 10 times before I can use the keyboard. I have an Asus K7V-something motherboard with a basic Logitech PS/2 mouse.

---

### Post by pilpi on 2007-06-18
Hi again,

Today there's another interesting effect with the keyboard; letters get repeated even though  I'm not holding keys down any more than usual; at times the keyboaaaaard input just halts for half a second or so and produces several of the characters of the key I pressed, an authentic example above :).

---

### Post by pilpi on 2007-06-23
Seems that this bug is specific to kernel version 2.6.20-16. I had 2.6.20-15-generic in my grub /boot/grub/menu.lst also, so I booted to that and so far the keyboard seems to be present at every boot. Commented out .20-16 now, so the section in my menu.lst looks like this now:

#title          Ubuntu, kernel 2.6.20-16-generic
#root           (hd0,4)
#kernel         /boot/vmlinuz-2.6.20-16-generic root=UUID=51f486c0-17e0-4ee9-9483-376a16ef4a0b ro q
uiet splash
#initrd         /boot/initrd.img-2.6.20-16-generic
#quiet
#savedefault

#title          Ubuntu, kernel 2.6.20-16-generic (recovery mode)
#root           (hd0,4)
#kernel         /boot/vmlinuz-2.6.20-16-generic root=UUID=51f486c0-17e0-4ee9-9483-376a16ef4a0b ro s
ingle
#initrd         /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=51f486c0-17e0-4ee9-9483-376a16ef4a0b ro q
uiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=51f486c0-17e0-4ee9-9483-376a16ef4a0b ro s
ingle
initrd          /boot/initrd.img-2.6.20-15-generic

---

### Post by pilpi on 2007-06-23
I'm afraid I was mistaken, due to being too lucky with 2.6.20-15 a couple of times. The problem occurs after all with that one, too. Numlock stops working at boot during loading Hardware Abstraction Layer hald.

---

### Post by pilpi on 2007-07-08
I'm really puzzled about this but nowadays still using .15 and keyboard seems to work at every boot. Not sure what the factor is that makes even .15 not work, but whenever I try .16, at least that does not work.

---

### Post by mactece on 2007-07-08
I installed Edgy  6:10 in March and upgraded it  ot Feisty  7:04 in April. LAst week the fan for my CPU failed and scrambled my harddrive so I have done a complete re-install. Including windows. Now I can't get the keyboard to work - exactly the same as described above but the weird thing is it was working yesterday. Another weird thing - I installed 7:04 on a spare hard-drive before setting about rescuing my scrambled drive and the keyboard worked there. Today I can't get the keyboard to work on the spare hard drive, the reinstalled hard drive or the live CD version! It works fine in windows  during post and bios and also in other live distros of linux. Just to rub salt in the wounds I'm posting this using the live cd version of edgy 6:10.

So 3 questions - is this a date specific bug or is it mb related  (I'm on an ASUS kt7a) or was it there all the time and I escaped cos I upgraded from 6:10?.

---

### Post by mactece on 2007-07-10
As I posted above I had the same problem. However my wife has fixed it by simply plugging the keyboard into the mouse port! This blindingly simple solution was beyond me because I know what the mouse port is for. My mouse is a USB so no conflict. Unfortunately I don't have a PS2 mouse so I cannot check if the ports are reversed. Meanwhile every other OS I have (Windows on dual boot and live distro cdroms (inc Ubuntu 6:10)) can still see the keyboard in the correct port. Windows (of course) needs it to be there and cannot see it if its in the mouse port whereas the rest can.

Interested to know if this works for you too and will post this as a bug, anyway.

ATB

David

---

### Post by sailent on 2007-07-12
Same problem here Running 2.6.20.16-generic. PS/2 on amd system. Mouse ps/2 swap no go, and I am not really willing to accept a full reinstall yet, knowing that this works when I boot from an older version from the menu.
My stats
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 03)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 1a)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:0a.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:0a.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)
00:0d.0 Ethernet controller: D-Link System Inc DL10050 Sundance Ethernet (rev 12)
00:0f.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]

Is this a linux kernel problem and that is why this issue doesn't seem to be getting addressed?

---

### Post by oferfrid on 2007-07-13
> **mactece said:**
> As I posted above I had the same problem. However my wife has fixed it by simply plugging the keyboard into the mouse port! This blindingly simple solution was beyond me because I know what the mouse port is for. My mouse is a USB so no conflict. Unfortunately I don't have a PS2 mouse so I cannot check if the ports are reversed. Meanwhile every other OS I have (Windows on dual boot and live distro cdroms (inc Ubuntu 6:10)) can still see the keyboard in the correct port. Windows (of course) needs it to be there and cannot see it if its in the mouse port whereas the rest can.

Interested to know if this works for you too and will post this as a bug, anyway.

ATB

David

Having the same problem, that solution didn’t work for me... :-(

---

### Post by sailent on 2007-07-17
If you run the following command under the kernel for feisty and rerun it under your old kernel where the keyboard you notice the following.  

cat /proc/bus/input/devices

Kernel 2.6.20-16
I: Bus=0017 Vendor=0001 Product=0001 Version=0100
N: Name="Macintosh mouse button emulation"
P: Phys=
S: Sysfs=/class/input/input0
H: Handlers=mouse0 ts0 event0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=3

I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input1
H: Handlers=kbd event1 
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 feffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2 
B: EV=40001
B: SND=6

I: Bus=0003 Vendor=045e Product=0040 Version=0110
N: Name="Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)"
P: Phys=usb-0000:00:07.2-2/input0
S: Sysfs=/class/input/input3
H: Handlers=mouse1 ts1 event3 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0019 Vendor=0000 Product=0002 Version=0000
N: Name="Power Button (FF)"
P: Phys=ACPI_FPB/button/input0
S: Sysfs=/class/input/input4
H: Handlers=kbd event4 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0001 Version=0000
N: Name="Power Button (CM)"
P: Phys=PNP0C0C/button/input0
S: Sysfs=/class/input/input5
H: Handlers=kbd event5 
B: EV=3
B: KEY=100000 0 0 0

I: Bus=0019 Vendor=0000 Product=0003 Version=0000
N: Name="Sleep Button (CM)"
P: Phys=PNP0C0E/button/input0
S: Sysfs=/class/input/input6
H: Handlers=kbd event6 
B: EV=3
B: KEY=4000 0 0 0 0

Kernel 2.6.17-11
I: Bus=0011 Vendor=0001 Product=0001 Version=ab41
N: Name="AT Translated Set 2 keyboard"
P: Phys=isa0060/serio0/input0
S: Sysfs=/class/input/input0
H: Handlers=kbd event0 
B: EV=120013
B: KEY=4 2000000 3802078 f840d001 f2ffffdf ffefffff ffffffff fffffffe
B: MSC=10
B: LED=7

I: Bus=0003 Vendor=045e Product=0040 Version=0300
N: Name="Microsoft Microsoft 3-Button Mouse with IntelliEye(TM)"
P: Phys=usb-0000:00:07.2-2/input0
S: Sysfs=/class/input/input1
H: Handlers=mouse0 event1 ts0 
B: EV=7
B: KEY=70000 0 0 0 0 0 0 0 0
B: REL=103

I: Bus=0010 Vendor=001f Product=0001 Version=0100
N: Name="PC Speaker"
P: Phys=isa0061/input0
S: Sysfs=/class/input/input2
H: Handlers=kbd event2 
B: EV=40001
B: SND=6


Great fun detected as macintosh mouse. Anyone know how to hard code this, to the old setup?

---

### Post by sailent on 2007-07-17
Okay found this from here...
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106289](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/106289)

In /boot/grub/menu.lst:

title Ubuntu, kernel 2.6.20-15-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=9f952ca3-ffa6-4adb-903a-5399619f1630 ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
savedefault

like so?

title Ubuntu, kernel 2.6.20-15-generic
root (hd1,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=9f952ca3-ffa6-4adb-903a-5399619f1630 ro quiet splash acpi=off
initrd /boot/initrd.img-2.6.20-15-generic
savedefault

It worked from me ignore everything other then the addition of acpi=off.

---

