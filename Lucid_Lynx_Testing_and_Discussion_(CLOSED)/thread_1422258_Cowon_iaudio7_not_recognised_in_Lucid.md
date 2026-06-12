---
title: "Cowon iaudio7 not recognised in Lucid"
date: 2010-03-05
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by limE flavoured beans on 2010-03-05
This would connect without any issues in Karmic, and was recognised as an mp3 player, but I can't even see it listed as an explorable device.

lsusb: Bus 001 Device 005: ID 0e21:0750 Cowon Systems, Inc. 
 I don't know how much of this is useful:

dmesg:   163.544559] usb-storage: device found at 5
[  163.544563] usb-storage: waiting for device to settle before scanning
[  168.557725] usb-storage: device scan complete
[  168.558175] scsi 13:0:0:0: Direct-Access     COWON    iAUDIO 7         0100 PQ: 0 ANSI: 0
[  168.558984] sd 13:0:0:0: Attached scsi generic sg9 type 0
[  168.562547] sd 13:0:0:0: [sdh] 32309248 512-byte logical blocks: (16.5 GB/15.4 GiB)
[  168.562905] sd 13:0:0:0: [sdh] Write Protect is off
[  168.562913] sd 13:0:0:0: [sdh] Mode Sense: 37 00 00 08
[  168.562919] sd 13:0:0:0: [sdh] Assuming drive cache: write through
[  168.565155] sd 13:0:0:0: [sdh] Assuming drive cache: write through
[  168.565164]  sdh:
[  168.570435] sd 13:0:0:0: [sdh] Assuming drive cache: write through
[  168.570447] sd 13:0:0:0: [sdh] Attached SCSI removable disk
[  184.032816] end_request: I/O error, dev fd0, sector 0
[  196.120118] end_request: I/O error, dev fd0, sector 0
[  196.120130] __ratelimit: 9 callbacks suppressed
[  196.120136] Buffer I/O error on device fd0, logical block 0
[  208.209768] end_request: I/O error, dev fd0, sector 0
[  208.209781] Buffer I/O error on device fd0, logical block 0
[  220.320509] end_request: I/O error, dev fd0, sector 0
[  220.320521] Buffer I/O error on device fd0, logical block 0
[  232.430519] end_request: I/O error, dev fd0, sector 0

---

### Post by NetJonte on 2010-03-05
fd0 is floppy drive, no?
Does other USB devices connects fine, because to me it sounds like something is trying to access the floppy drive instead of the USB device.

My player (same as yours except 8 GB instead) connects without trouble. But it seems to be recognized as an mass storage device rather than MP3 player. I don't got a floppy drive or those IO errors however.

---

### Post by limE flavoured beans on 2010-03-05
I have two other external hdd's attached working fine, and my friends sony mp3 walkman connected without any issues. Do you think that it thinks its connecting to a floppy? I thought it had assigned the cowon player to "sdh".

I have a multimedia card reader installed instead of the floppy drive. That may be the reason why its having errors trying to connect to the floppy drive

Thanks for trying to help btw

---

### Post by limE flavoured beans on 2010-03-06
Any other ideas people? Cowon have previously had pretty good support in linux, and I haven't had this happen with any other disty.

---

### Post by b3t0n on 2010-03-07
I have siimilar problem, but with Sansa Fuze. It won't work in mass-storage-device mode. All other usb devices work, Fuze works when it's connected to other PC, so it isn't hardware fault.

---

### Post by Sam on 2010-03-07
I do have a Cowon iAudio 7, and I haven't connected it since I upgraded to lucid. Needless to say I had to try. I don't have the same problem as you, but I cannot access the partition either. For any reason, the partition is not recognized (but the player has the songs when I use it itself).

Maybe it's related to hal removal. I'll investigate this issue later and post here if I find something.


Usual dumps (and disk utility screenshot):

```
$ lsusb
Bus 003 Device 008: ID 0e21:0750 Cowon Systems, Inc.
```

```
$ dmesg
[48121.856111] usb 3-2: USB disconnect, address 7
[48145.928086] usb 1-4: new high speed USB device using ehci_hcd and address 24
[48161.020135] hub 1-0:1.0: unable to enumerate USB device on port 4
[48161.416020] usb 3-2: new full speed USB device using uhci_hcd and address 8
[48161.638102] usb 3-2: not running at top speed; connect to a high speed hub
[48161.780190] usb 3-2: configuration #1 chosen from 1 choice
[48161.812539] scsi21 : SCSI emulation for USB Mass Storage devices
[48161.819874] usb-storage: device found at 8
[48161.819880] usb-storage: waiting for device to settle before scanning
[48164.004006] ehci_hcd 0000:00:10.3: force halt; handhake f801a014 0000c000 00000000 -> -110
[48166.844260] usb-storage: device scan complete
[48166.847210] scsi 21:0:0:0: Direct-Access     COWON    iAUDIO 7         0100 PQ: 0 ANSI: 0
[48166.853765] sd 21:0:0:0: Attached scsi generic sg3 type 0
[48166.869245] sd 21:0:0:0: [sdc] 32309248 512-byte logical blocks: (16.5 GB/15.4 GiB)
[48166.872449] sd 21:0:0:0: [sdc] Write Protect is off
[48166.872460] sd 21:0:0:0: [sdc] Mode Sense: 37 00 00 08
[48166.872465] sd 21:0:0:0: [sdc] Assuming drive cache: write through
[48166.887156] sd 21:0:0:0: [sdc] Assuming drive cache: write through
[48166.887169]  sdc:
[48166.902239] sd 21:0:0:0: [sdc] Assuming drive cache: write through
[48166.902255] sd 21:0:0:0: [sdc] Attached SCSI removable disk
```
[COLOR="Gray"][SIZE="1"]Note to self: Check why it connects at low speed...[/SIZE][/COLOR]

---

### Post by Giwex on 2010-03-08
I'm a lucky owner of an Iaudio 7 too and in my case the I7 works great in LL. I tried to transfer some music both by nautilus and both my RB and in both case everything works perfectly.

Moreover, differently than Karmic, if you perform a "safely remove drive" action you will have the battery charging icon on I7 display (that also in Vista doesn't work :p)

Regards

---

### Post by limE flavoured beans on 2010-03-09
Thanks peoples, well one not working, one half working, and another working properly. I'm going to retest with all the updates we've had recently, and see if I have any better luck this time. I'll post updates later.

---

### Post by goebbe on 2010-03-09
Please consider reporting bugs on [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu) in order to get the issues fixed for Ubuntu 10.4

---

### Post by limE flavoured beans on 2010-03-09
Sam, thanks for the screenshot. I did the same and it was there with the same settings as your screenshot. 
goebbe: To be honest, I had never needed to fill in a bug report before. I did a bit of reading and used the "ubuntu-bug storage" tool.
Sam & Giwex: I'm using firmware ver 1.18 on cowon iaudio7 ...just curious, are you running the same version?

Cheers.

---

### Post by Giwex on 2010-03-09
Yes, using the same firmware 1.18.

I did a couple of experiment in the meantime. There is just a difference between KK and LL. 
KK correctly recognize I7 as an audioplayer (the icon on the desktop for the mounted volume is an audio player rather than an USB drive) and prompt me to launch RB at insertion. LL doesn't do this. 
Moreover I have to rectify my earlier post: also in KK if you safely remove the drive you get the batery charger icon on the I7 (I believe one of later kernel revision fixed it).

In my case my installation of LL is from Alpha3. I don't think there is the need of bug reporting, maybe it's just caused by massive updating of your installation. Can you try to launch the livecd?

---

### Post by Sam on 2010-03-09
Firmware 1.17 here. I'll test this afternoon at work where I have karmic. I'll take the lucid live cd with me.

---

### Post by NetJonte on 2010-03-09
> **Giwex said:**
> 
Moreover, differently than Karmic, if you perform a "safely remove drive" action you will have the battery charging icon on I7 display (that also in Vista doesn't work :p)


I saw that too yesterday then I charged mine. Finally! Now I don't have too guess how long it will take until the battery is fully charged. :D  Well, I used Hardy (!) before this so I don't know if this was introduced in the previous version.

limE flavoured beans: Mine is 1.18 too and as I said earlier it works.

---

### Post by ViperScull on 2010-03-09
I've got a Meizu M6. It isn't automounted, neither as a mp3 player nor as an USB mass storage device. I have to mount it manually, then it works fine.

In KK it was automounted.

I've got a Cowon D2 as well. I'll try tomorrow.

---

### Post by goebbe on 2010-03-19
For the case that the iaudio7 is recognised only as a usb-stick but not as a mp3/ogg/... media-player, I opened a bug report on launchpad:

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/542321](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/542321)

Feel free to confirm the bug report if you have this issue.

---

### Post by Sam on 2010-03-20
Well it seems that with Lucid Beta 1 my iAudio7 works again. Great!

---

### Post by limE flavoured beans on 2010-03-21
I was just about to install beta 1 as well. Will post results once completed

---

### Post by frogotronic on 2010-03-31
Hello All,

  My iPOD Nano finally died (or won't hold a charge for very long) and I've just bought a Cowan iAudio7.  Should be here in a week or so.

  I use KK and I'm pretty excited about it.

- CH    :popcorn:

---

### Post by frogotronic on 2010-04-26
> **cement_head said:**
> Hello All,

  My iPOD Nano finally died (or won't hold a charge for very long) and I've just bought a Cowan iAudio7.  Should be here in a week or so.

  I use KK and I'm pretty excited about it.

- CH    :popcorn:

Works in Karmic with Firmware 1.18...but how about Lucid?

---

### Post by Sam on 2010-04-26
Still working on Lucid... Using firmware 1.17 though.

---

### Post by goebbe on 2010-04-27
Works on Lucid! With the latest firmware 1.18. 
:-)

---

### Post by Giwex on 2010-04-27
Working ok also for me (both USB and MTP) but I'm not any longer able to have the battery charging picture in the Iaudio when unmounting it :(

---

