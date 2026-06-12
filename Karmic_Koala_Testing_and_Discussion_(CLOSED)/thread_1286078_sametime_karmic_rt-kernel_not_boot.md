---
title: "sametime karmic rt-kernel not boot"
date: 2009-10-08
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by lemmyg on 2009-10-08
Hi,
sometime kernel-rt not boot. has any one the same problem?





Linux USBK01 2.6.31-6-rt #7-Ubuntu SMP PREEMPT RT Sun Sep 27 10:56:10 UTC 2009 x86_64 GNU/Linux


This is the syslog:





Oct  8 20:37:00 USBK01 NetworkManager: <info>  (wlan0): device state change: 8 -> 3 (reason 38)
Oct  8 20:37:00 USBK01 NetworkManager: <info>  (wlan0): deactivating device (reason: 38).
Oct  8 20:37:00 USBK01 NetworkManager: <info>  (wlan0): canceled DHCP transaction, dhcp client pid 2182
Oct  8 20:37:00 USBK01 NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Sucess#012
Oct  8 20:37:00 USBK01 avahi-daemon[948]: Withdrawing address record for 192.168.0.11 on wlan0.
Oct  8 20:37:00 USBK01 avahi-daemon[948]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.0.11.
Oct  8 20:37:00 USBK01 wpa_supplicant[973]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Oct  8 20:37:00 USBK01 avahi-daemon[948]: Interface wlan0.IPv4 no longer relevant for mDNS.
Oct  8 20:37:02 USBK01 acpid: client 1063[0:0] has disconnected
Oct  8 20:37:02 USBK01 acpid: client 1063[0:0] has disconnected
Oct  8 20:37:02 USBK01 acpid: client connected from 2798[0:0]
Oct  8 20:37:04 USBK01 acpid: client connected from 2798[0:0]
Oct  8 20:37:07 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:07 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:07 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:07 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:07 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:07 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:07 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:07 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:07 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:07 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:07 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:08 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:08 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:08 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:08 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:20 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:20 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:20 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:20 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:20 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:20 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:20 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:20 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:20 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:20 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:20 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:20 USBK01 pulseaudio[2947]: pid.c: Stale PID file, overwriting.
Oct  8 20:37:21 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:21 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:21 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:21 USBK01 rtkit-daemon[1830]: Failed to make ourselves RT: Invalid argument
Oct  8 20:37:42 USBK01 NetworkManager: <WARN>  nm_signal_handler(): Caught signal 15, shutting down normally.
Oct  8 20:37:42 USBK01 init: tty4 main process (965) killed by TERM signal
Oct  8 20:37:42 USBK01 init: tty5 main process (968) killed by TERM signal
Oct  8 20:37:42 USBK01 NetworkManager: <info>  (eth0): cleaning up...
Oct  8 20:37:42 USBK01 init: tty3 main process (1041) killed by TERM signal
Oct  8 20:37:42 USBK01 NetworkManager: <info>  (eth0): taking down device.
Oct  8 20:37:42 USBK01 acpid: exiting
Oct  8 20:37:42 USBK01 avahi-daemon[948]: Got SIGTERM, quitting.
Oct  8 20:37:42 USBK01 kernel: Kernel logging (proc) stopped.
Oct  8 20:37:42 USBK01 rsyslogd: [origin software="rsyslogd" swVersion="4.2.0" x-pid="813" x-info="http://www.rsyslog.com"] exiting on signal 15.

---

### Post by bluesscream on 2009-10-08
At first I'd reinstall. This kernel is running smart as well on my old amd64x2 machine with exotic and legacy hardware as on a modern intel dominated necoc osiris S620II notebook. What's your hardware?

---

### Post by tekstr1der on 2009-10-08
```
Linux galvatron 2.6.31-12-generic #41-Ubuntu SMP Wed Oct 7 18:42:46 UTC 2009 i686 GNU/Linux

```

On a Lenovo S10 netbook, I am seeing the same errors during every boot:

```
Oct  8 11:37:11 galvatron NetworkManager: <debug> [1255016231.000713] ensure_killed(): ppp pid 5146 cleaned up
Oct  8 11:37:13 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:13 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:13 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:13 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:13 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:13 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:13 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:13 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:13 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:13 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:13 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:13 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:14 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:14 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:14 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:28 galvatron gdm-session-worker[5518]: pam_sm_authenticate: Called
Oct  8 11:37:28 galvatron gdm-session-worker[5518]: pam_sm_authenticate: username = [***]
Oct  8 11:37:33 galvatron gdm-session-worker[5529]: Error attempting to add filename encryption key to user session keyring; rc = [1]
Oct  8 11:37:34 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:34 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:34 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:34 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:34 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:34 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:34 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:34 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:34 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:34 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:34 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:34 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:34 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:34 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
Oct  8 11:37:34 galvatron rtkit-daemon[2007]: Failed to make ourselves RT: Invalid argument
```

I am successfully booting, however. Just seeing these errors in syslog.

---

### Post by lemmyg on 2009-10-08
Hi,
my hardware is: 

uname -a
Linux USBK01 2.6.31-6-rt #7-Ubuntu SMP PREEMPT RT Sun Sep 27 10:56:10 UTC 2009 x86_64 GNU/Linux

lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation G84 [GeForce 8600M GT] (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
0c:00.0 Network controller: Intel Corporation



This issue only appears sometimes. One of three times.

---

### Post by bluesscream on 2009-10-09
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/406702](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/406702)

I see it in my notebooks syslog too, but had no boot issues.

---

### Post by lemmyg on 2009-10-09
thanks, I have to wait for a solution.

---

### Post by trulan on 2009-10-09
@lemmyg:  I see you have an NVidia video card.  I had to do this to get my desktop booting on the rt kernel with the NVidia drivers:
[http://ubuntuforums.org/showpost.php?p=8046770&postcount=109](http://ubuntuforums.org/showpost.php?p=8046770&postcount=109)

That may or may not help, but there it is in case you care to try it.

---

### Post by lemmyg on 2009-10-10
Hi trulan, 
thank you very much for the patch.
I try it and works perfectly with 2.6.31-6-rt. I am booting 5 times, and works fantastic. Only when I created the module , I had remove the old module with:

sudo dkms remove -m nvidia -v 185.18.36 -k 2.6.31-6-rt

and then created

sudo dkms build -m nvidia -v 185.18.36 -k 2.6.31-6-rt


now I update to new kernel 2.6.31-7-rt Im going to update it. 
I dont know is this patch is in the kernel 2.6.31-7-rt. I hope, it give me any problems.

---

### Post by trulan on 2009-10-10
Right - if you already had the driver installed, you need to remove the dkms module before building the new dkms module with the patch.  Good job.

So 2.6.13-7-rt is out?  I'll have to check it out!

The NVidia driver should not need to be patched again with a kernel update, only if nvidia-185-glx is updated or re-installed.

Edit:  OK, running here on 2.6.31-7-rt.  As I expected, the NVidia driver module builds correctly and works with no changes made, as the patch is still in place.

---

