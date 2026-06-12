---
title: "no GDM Login on Lucid"
date: 2010-04-14
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by boondocks on 2010-04-14
Two days ago, I installed 9.10 desktop on PC.
Everything was working fine.
Able to login, surf the web, chat, edit documents, logout, reboot, shutdown, ... everything.

Yesterday, I did the "update-manager -d" to upgrade to Lucid.
Followed the instructions.  The upgrade finished and I was asked to reboot.
[LIST=1]
[*]So I rebooted the system.
[*]I can hear the disk spinning.
[*]The system is starting up but there is no GDM.
[*]Then the green light on the display monitor becomes amber in color.
[*]I move the mouse, nothing happens.
[*]I hit the Shift and Ctrl keys, nothing happens.
[*]I hit Ctrl+Alt+F2, and I get the tty2 console screen.
[*]I login at the console and reboot.
[/LIST]
I have repeated these 8 steps several times.
I also did this a few times:
[INDENT]sudo aptitude -q clean
sudo aptitude -q update
sudo aptitude -q  full-upgrade[/INDENT]
But nothing changes.
What should I do?

---

### Post by ranch hand on 2010-04-14
Well for a start you could tell us about your box.  No we do not want a model number.  We want specs.  See my sig (bottom of post) for an example of what is wanted.

---

### Post by boondocks on 2010-04-14
According to  **hwinfo   --short**
```
cpu:
                       Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz, 1600 MHz
                       Intel(R) Core(TM)2 CPU          6300  @ 1.86GHz, 1600 MHz
keyboard:
  /dev/input/event3    AT Translated Set 2 keyboard
mouse:
  /dev/input/mice      Macintosh mouse button emulation
  /dev/input/mice      PS/2 Generic Mouse
graphics card:
                       Intel 965G
sound:
                       Intel 82801H (ICH8 Family) HD Audio Controller
storage:
                       Intel 82801 SATA RAID Controller
network:
  eth0                 Intel 82562V 10/100 Network Connection
network interface:
  lo                   Loopback network interface
  eth0                 Ethernet network interface
disk:
  /dev/sda             ST3250824AS
  /dev/sdb             Generic USB SD Reader
  /dev/sdc             Generic USB CF Reader
  /dev/sdd             Generic USB SM Reader
  /dev/sde             Generic USB MS Reader
partition:
  /dev/sda1            Partition
  /dev/sda2            Partition
  /dev/sda5            Partition
cdrom:
  /dev/sr0             HL-DT-ST DVDRRW GSA-H30L
usb controller:
                       Intel 82801H (ICH8 Family) USB UHCI Controller #4
                       Intel 82801H (ICH8 Family) USB UHCI Controller #5
                       Intel 82801H (ICH8 Family) USB2 EHCI Controller #2
                       Intel 82801H (ICH8 Family) USB UHCI Controller #1
                       Intel 82801H (ICH8 Family) USB UHCI Controller #2
                       Intel 82801H (ICH8 Family) USB UHCI Controller #3
                       Intel 82801H (ICH8 Family) USB2 EHCI Controller #1
bios:
                       BIOS
bridge:
                       Intel 82P965/G965 Memory Controller Hub
                       Intel 82P965/G965 PCI Express Root Port
                       Intel 82801H (ICH8 Family) PCI Express Port 1
                       Intel 82801 PCI Bridge
                       Intel 82801HH (ICH8DH) LPC Interface Controller
hub:
                       Linux 2.6.32-20-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.32-20-generic ehci_hcd EHCI Host Controller
                       Linux 2.6.32-20-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.32-20-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.32-20-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.32-20-generic uhci_hcd UHCI Host Controller
                       Linux 2.6.32-20-generic uhci_hcd UHCI Host Controller
memory:
                       Main Memory
firewire controller:
                       Agere FW323
unknown:
                       FPU
                       DMA controller
                       PIC
                       Timer
                       Keyboard controller
                       PS/2 Controller
                       Intel 82801H (ICH8 Family) SMBus Controller
                       Conexant Soft Data Fax Modem with SmartCP

```
It has 2 Gb of Memory
and a 250 Gb hard disk.

---

### Post by garvinrick4 on 2010-04-14
Does the command Code:

startx

Do anything for you?

---

### Post by ranch hand on 2010-04-14
Or "service gdm start"?

Another thing to try is editing the menu entry.  If you have a hidden menu you will need to hit the shift key to see the menu.

Highlight the entry and hit e.  Edit the "linux" line bu removing the "splash" instruction and maybe the "quiet" instruction too.  I would do them one at a time starting with splash.  If that doesn't work remove both and see is you get, and can read (they go fast) any messages.

I have not seen too much complaint about intel graphics but as I use ATI I do not follow it closely.  I had the impression that both intel support and ATI support with the open drivers was much better.  It is vastly better with my card.

The reason for removing the "splash" may be my predilection to blaming plymouth for all boot problems.  I am sure that there are some not caused by it but it doesn't "feel" that way to me.  I think it is worth a shot.

Trying to boot through recovery would be my next attempt at getting in.

If you are getting a terminal you may want to run
```

sudo dpkg --configure -a

```
just to see if something shakes loose there.

I do not use aptitude but those things you already ran seem to be along the right lines to me.  I take it you did not get any errors returned from that.  Is this right?

---

### Post by boondocks on 2010-04-14
**startx** produces:
```
_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running

Please consult the The X.Org Foundation support 
         at http://wiki.x.org
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log
```
These are the contents of the "/var/log/Xorg.0.log" file.

---

### Post by garvinrick4 on 2010-04-14
Is X already running?  ctrl/alt/F7

---

### Post by boondocks on 2010-04-15
I tried all of the suggestions mentioned above.
Still no GDM login screen.
But in console mode it works fine. (*That was the tricky part.*)
So then:
[LIST]
[*]On another Ubuntu desktop system I burned the same iso on a USB stick.
[*]The current system's chassis was open so I powered off this system.
[*]Removed the power to the hard disk.
[*]Plugged the USB stick in a USB port.
[*]Booted off the USB stick.
[*]The plan was to see what a live Lucid CD would do...
[/LIST]
But the exact same thing happened again.

To summarize:
[LIST=1]
[*]Up to date installed 9.10 Desktop = everything works.
[*]Up to date installed Lucid Desktop = Console works fine but no GDM login.
[*]Live CD Lucid Desktop = Console works fine but no GDM login.
[/LIST]

Then:
[LIST]
[*]I powered off this system.
[*]Removed the USB stick.
[*]Re-connected the power cable to the hard disk.
[*]Disconnected the current monitor. An IBM E74M monitor.
[*]Connected a different monitor.  A Daewoo monitor.
[*]Powered on this system.
[*]Without missing a beat - it goes to the GDM login screen!
[/LIST]
I login to the desktop (for the first time) and its working.
Apparently, it is a monitor issue.
[COLOR="Blue"]This IBM E74M monitor does not seem to work properly in this Lucid setup.[/COLOR]
This IBM E74M monitor does work correctly with the Ubuntu 9.10 Desktop.
Then I connected this IBM E74M monitor to a Windows XP system and booted it up. It works.

---

### Post by gnwiii on 2010-04-18
I have a similar problem on a Dell system with nvidia graphics.  So far I have done:

1.  edit /etc/X11/xorg.conf to change the driver from "nvidia" to "nouveau"
    
    X11 starts, but no login panel appears

2.  sudo service gdm stop ; sudo service kdm start

    This gets the kdm login panel, but the Desktop is empty except for a cursor and the single folder in ~/Desktop.  After a while (screensaver?) the display goes black and the cursor is not displayed except when moving.  dmesg shows a large number of segfaults:

[14890.429170] gnome-screensav[3774]: segfault at 140 ip 00007fb87b47f12f sp 00007fffb865c548 error 4 in libgraphite.so.3.0.0[7fb87b43b000+64000]

3.  change the driver from nouveau to vesa

The nouveau modules were still being loaded, so I added nouveau to blacklist.conf.  This got 
a kde login and session, but many apps were still failing with segfault in libgraphite, so
I used aptitude to remove libgraphite.
 
4. switch back to nouveau.  System boots to a screen with just the background and no GDM login.  
Using aptitude in a terminal, remove pango-graphite-0.9.2-3.1 and then "sudo service gdm stop ; sudo service gdm start" to get a GDM login.

---

