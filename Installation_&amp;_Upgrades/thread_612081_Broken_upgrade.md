---
title: "Broken upgrade"
date: 2007-11-13
forum: Installation &amp; Upgrades
---

### Post by Dave Elliott on 2007-11-13
I started an upgrade using the update manager in gnome, i was on 6.10.
It checked and said all was fine. It started the upgrade, but the network cable got unplugged during the process. I didnt realise until after rebooting, thinking this was taking a while
now to the problem:

the boot loader prompt with loading Kernel 2.6.22-14-386, 
does 
Booting 'Ubuntu 7.10, kernel 2.6.22-14-386'
root (hd0,1)
 Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.22-14-386 root=UUID=79e98bb6-aef1-4365-b102-5b560d6db00d ro quiet splash
   [Linux-bzimage, setup=0x1e00, size=0x19c238]

[5704.239271] PCI: Cannot allocate resources region 4 of device 0000:00:1d.0
[5704.239342] PCI: Cannot allocate resources region 4 of device 0000:00:1d.1
[5705.039719] Kernel panic - not syncing: VFS: unable to mount root fs on unknown-block(0,0)

then the Caps lock flashes..

I shutoff and reboot in to same kernel but recovery mode
it ends in the same scenario i see a lot more text, last 3 lines all read about 
'vfs: cannot open root device' 
then 
'please append a correct "root=" boot option; here are the available partitions:'  
and last line 
'kernel panic - not sysncing: VFS: unable to mount root fs on unknown-block)0,0)' 
with the same flashing Caps lock.
shutoff and start againg this time choosing kernel 2.6.20-16-386
it seems to load fine, except that i dont have graphical gnome. only the terminal. never mind eh!
It starts all the relevent programs, ending in a login screen.

No network, cannot ping, cannot fix updates.
Have tried editing /etc/network/interface setting it to:

auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet auto

did sudo /etc/init.d/networking stop and start
replies:
*Configuring network interfaces...
There is.....
All right...
For info, p....

SIOCSIFADDR: Permission denied
SIOCSIFFLAGS: Permission denied
Listening on LPF/eth0/00:08:0d:71:84:f9
Sending on  LPF/eth0/00:08:0d:71:84:f9
Sending on Socket/Fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
No DHCPDISCOVER received
No working leases in persistent database - sleeping

Then there was silence...doh doh dohhhh!
tried doing static on eth0 with 
address 192.168.100.201
netmask 255.255.255.0
network 192.168.100.0
broadcast 192.168.100.255
gateway 192.168.100.1

No go, no reply for ping but show i have an ip address with ifconfig. cables in (this time), I tripple boot with ubuntu, fedora and xp. my primary boot loader works with fedora and xp, ubuntu does also work but not with newest kernel.

help

dave

---

### Post by Triptol on 2007-11-13
Got yourself some real nice problems here ;-)

I think I would do a reinstall. You could save your homedirectory by mounting it from your fedora installation. Copy over everything and you would be fine to reinstall. Then install in the old partition but first give it a format.

If you want to fix your installation here a few ideas:
- Make sure you have a dvd with the installation packages (since your net is not working)
- Boot with the old kernel and make sure the dvd is referenced in your /etc/apt/sources.list
- aptitude update
- aptitude dist-ugprade (you might need to do a dpkg-reconfigure -a to get it all working, but the system will tell you to do so)

The other thing you could do is try and get your network card running again. For this you will need to get the right module installed. Again you could use your fedora here, boot into that system, check what driver is used (lsmod will be your friend here) and try to load that driver under your running kernel. You might be lucky. Once you have net, the aptitude commands should help you out as well.

---

