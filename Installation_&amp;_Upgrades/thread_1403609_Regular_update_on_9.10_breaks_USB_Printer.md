---
title: "Regular update on 9.10 breaks USB Printer"
date: 2010-02-10
forum: Installation &amp; Upgrades
---

### Post by bludy on 2010-02-10
I did an update during a time when power was cycling due do a nasty snow storm, but I'm pretty sure the update was completed successfully before I lost power. What did happen though is that my BIOS setup was reset.

Now if my HP Laserjet 1020 is plugged into USB during boot all other USB devices freeze for a while. So I played with my BIOS setting for USB:

- Enabled V1.1 and V2.0
- Disabled System USB Shadowing

So now my bootup doesn't hang. But now when I actually go into Karmic I still can't print.

dmesg shows the following:

[  205.940008] usb 1-10: new high speed USB device using ehci_hcd and address 9
[  219.510026] hub 1-0:1.0: unable to enumerate USB device on port 10
[  223.430008] usb 1-10: new high speed USB device using ehci_hcd and address 10
[  223.600766] usb 1-10: configuration #1 chosen from 1 choice
[  223.604896] usblp0: USB Bidirectional printer dev 10 if 0 alt 0 proto 2 vid 0x03F0 pid 0x2B17
[  224.780817] usb 1-10: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[  229.660155] usb 1-10: usbfs: USBDEVFS_CONTROL failed cmd hp rqt 128 rq 6 len 255 ret -110
[  230.000138] usb 1-10: usbfs: USBDEVFS_CONTROL failed cmd python rqt 128 rq 6 len 255 ret -110
[  247.100044] usb 1-10: usbfs: USBDEVFS_CONTROL failed cmd hp rqt 128 rq 6 len 255 ret -110
[  354.130146] usb 1-10: usbfs: USBDEVFS_CONTROL failed cmd hp rqt 128 rq 6 len 255 ret -110
[  433.206810] usb 1-10: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[  438.190170] usb 1-10: usbfs: USBDEVFS_CONTROL failed cmd hp rqt 128 rq 6 len 255 ret -110
[  438.410164] usb 1-10: usbfs: USBDEVFS_CONTROL failed cmd python rqt 128 rq 6 len 255 ret -110
[  443.190068] usb 1-10: usbfs: USBDEVFS_CONTROL failed cmd hp rqt 128 rq 6 len 255 ret -110
[  443.410063] usb 1-10: usbfs: USBDEVFS_CONTROL failed cmd python rqt 128 rq 6 len 255 ret -110
[  448.190220] usb 1-10: usbfs: USBDEVFS_CONTROL failed cmd hp rqt 128 rq 6 len 255 ret -110
[  448.414887] usb 1-10: usbfs: USBDEVFS_CONTROL failed cmd python rqt 128 rq 6 len 255 ret -110
[  500.870143] usb 1-10: usbfs: USBDEVFS_CONTROL failed cmd python rqt 128 rq 6 len 255 ret -110
[  505.870039] usb 1-10: usbfs: USBDEVFS_CONTROL failed cmd python rqt 128 rq 6 len 255 ret -110
[  510.870064] usb 1-10: usbfs: USBDEVFS_CONTROL failed cmd python rqt 128 rq 6 len 255 ret -110
[  668.480052] usb 1-10: usbfs: USBDEVFS_CONTROL failed cmd hp rqt 128 rq 6 len 255 ret -110
[  978.480044] usb 1-10: usbfs: USBDEVFS_CONTROL failed cmd hp rqt 128 rq 6 len 255 ret -110
[ 1288.470103] usb 1-10: usbfs: USBDEVFS_CONTROL failed cmd hp rqt 128 rq 6 len 255 ret -110
[ 1598.210070] usb 1-10: usbfs: USBDEVFS_CONTROL failed cmd hp rqt 128 rq 6 len 255 ret -110

/var/log/messages shows this:

Feb 10 12:58:44 localhost foo2zjs-wrapper: foo2zjs-wrapper -P -z1 -L0 -r1200x600 -p1 -m1 -s7
Feb 10 12:58:45 localhost foo2zjs-wrapper: gs -sPAPERSIZE=letter -g10200x6600 -r1200x600 -sDEVICE=pbmraw -dCOLORSCREEN -dMaxBitmap=500000000  
Feb 10 12:58:45 localhost foo2zjs-wrapper: foo2zjs -r1200x600 -g10200x6600 -p1 -m1 -n1 -d1 -s7 -z1  -u 192x96 -l 192x96 -L 0     -P 

cups shows the following error:

D [10/Feb/2010:12:58:50 -0500] [Job 542] prnt/backend/hp.c 720: ERROR: cannot open device stat=12: hp:/usb/HP_LaserJet_1020?serial=FN1DEW2
D [10/Feb/2010:12:58:50 -0500] [Job 542] Backend returned status 1 (failed)
D [10/Feb/2010:12:58:50 -0500] [Job 542] End of messages
D [10/Feb/2010:12:58:50 -0500] [Job 542] printer-state=3(idle)
D [10/Feb/2010:12:58:50 -0500] [Job 542] printer-state-message="/usr/lib/cups/backend/hp failed"
D [10/Feb/2010:12:58:50 -0500] [Job 542] printer-state-reasons=none

I tried changing kernels but the same problem is there. When I unplug the printer this error goes away. My gut says that USB 2.0 is not working anymore but I can't verify it.

I'm on an AMD64 Athlon CPU.

Help?

---

### Post by bludy on 2010-03-18
Wow. I got another update which included cups and a new kernel and all of a sudden the printer started working again.

Then I lost power and now it's broken in exactly the same way.  When I try to print dmesg shows:

[334457.830185] usb 1-10: usbfs: USBDEVFS_CONTROL failed cmd hp rqt 128 rq 6 len 255 ret -110

This is so confusing :confused:

---

### Post by Kevinator on 2010-03-24
Hey, bludy. I recommend following this guide I wrote:

[http://ubuntuforums.org/showthread.php?t=1438177](http://ubuntuforums.org/showthread.php?t=1438177)

It looks like you are currently set up to use hplip (the printer URI starts with hp:/), so you'll need to delete and re-create the printer using the usb:/ interface.

If you want to stick with hplip I don't have any specific advice. I've never gotten it to work, myself. But at least a few details from that guide are still relevant, like the need for the firmware to be loaded (and I think you'll get the same sign when it works), though the method to load the firmware is different. You can also use the same commands for checking whether CUPS is detecting the printer.

---

### Post by bludy on 2010-03-26
SWEET!  Changing from hp:/ to usb:/ did the trick.


Who's the man? Kevinator's the man!!!

---

### Post by bludy on 2010-04-08
Jeez.  It's borken again. Now dmesg shows this repeatedly:

[  156.760644] usb 1-10: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[  166.760694] usb 1-10: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[  176.760707] usb 1-10: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[  186.760608] usb 1-10: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[  196.760637] usb 1-10: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[  206.760657] usb 1-10: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[  216.760925] usb 1-10: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[  226.760712] usb 1-10: usbfs: interface 0 claimed by usblp while 'usb' sets config #1
[  236.760621] usb 1-10: usbfs: interface 0 claimed by usblp while 'usb' sets config #1

Firmware is being uploaded to the printer on boot.  I don't understand what the hell is going on.

---

### Post by Yetisaurus Akjas on 2012-07-04
I see the same message after each reboot : 

usb 1-2: usbfs: interface 1 claimed by usblp while 'usb' sets config #1 

but sometimes accompanied by another one : 

usb 1-2: usbfs: interface 1 claimed by usblp while 'simple-scan' sets config #1 

The /etc/cups/printers.conf file says : 

<DefaultPrinter Canon-MF4350d>
Info Canon MF4350d
Location
MakeModel Canon MF4320-4350 ver.2.4
DeviceURI usb://Canon/MF4320-4350%20(UFRII%20LT)
State Idle
StateTime 1341380807
Type 8393876
Filter application/vnd.cups-raw 0 -
Filter application/vnd.cups-postscript 0 pstoufr2cpca
Accepting Yes
Shared Yes
JobSheets none none
QuotaPeriod 0
PageLimit 0
KLimit 0
OpPolicy default
ErrorPolicy retry-job
Option orientation-requested 3
</Printer>

Any ideas ? 

Observation: I managed to make scanning possible, but printing, especially PDF files is not working anymore. 

/var/log/cups/error_log says : 

E [04/Jul/2012:08:22:21 +0300] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [04/Jul/2012:08:22:36 +0300] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [04/Jul/2012:08:23:12 +0300] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [04/Jul/2012:08:28:22 +0300] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [04/Jul/2012:08:28:28 +0300] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [04/Jul/2012:08:37:41 +0300] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [04/Jul/2012:08:37:41 +0300] [Job 245] Aborting job because it has no files.
E [04/Jul/2012:08:49:51 +0300] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [04/Jul/2012:08:49:56 +0300] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [04/Jul/2012:08:52:03 +0300] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [04/Jul/2012:09:02:41 +0300] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory
E [04/Jul/2012:09:02:45 +0300] [cups-driverd] Bad driver information file "/usr/share/cups/drv/sample.drv"!
E [04/Jul/2012:09:14:15 +0300] Unable to remove temporary file "/var/spool/cups/tmp/.hplip" - Is a directory

hplip, hplip-data, hpijs and libhpmud0 have been "purged" 

Thanks in advance for any suggestions. :)

---

### Post by nothingspecial on 2012-07-04
Rather than bumping an old thread to the top, please start a new one.

Thanks.

Closed.

---

