---
title: "Install hangs at usbhid or Attached SCSI removable disk"
date: 2011-12-14
forum: Installation &amp; Upgrades
---

### Post by vt.dave on 2011-12-14
Hey Everyone,

I just built a new Shuttle SX58H7 Pro:
[http://us.shuttle.com/barebone/Models/SX58H7Pro.html](http://us.shuttle.com/barebone/Models/SX58H7Pro.html)

and put an OCZ Agility 3 SSD in it:
[http://www.ocztechnology.com/ocz-agility-3-sata-iii-2-5-ssd.html](http://www.ocztechnology.com/ocz-agility-3-sata-iii-2-5-ssd.html)

and am having a terrible time installing Ubuntu on this system.

I have already installed Windows 7 on 200 of the 240 GB and was going to put ubuntu on the other 40, but when I boot off the CD the install hangs at:
```
usbhid: USB HID core driver
```

and when I install off of a USB drive the install hangs at:
```
sd 6:0:0:0: [sdb] Attached SCSI removable disk.
```

I have tried both SATA 3 and SATA 2 ports on the motherboard, and I have changed the IDE type to AHCI in the bios for both the SATA 2 and SATA 3 ports, no difference.  The install will always hang at either of those 2 points depending on the boot medium I choose.

Please help, as I'm itching to get Ubuntu up on this machine asap :)

Thanks,
-Dave

---

### Post by vt.dave on 2011-12-15
I also wanted to point out that my SSD has the 2.11 firmware and OCZ has 2.15 firmware out for the drive, however I'm not sure if it's the drive that's causing problems or the chipset / sata controller itself :-/

Any guru's out there know what might be happening?

---

### Post by vt.dave on 2011-12-16
Well if no one has any ideas, is there some way to do a more interactive boot / install process where I can try to determine what is causing the install to hang?  Or perhaps some sort of "safe-mode" type of boot process?

I'd really like to get this all installed and configured.

Thanks!

---

### Post by dai_trying on 2011-12-16
I don't know if this will help you, but I have been having problems installing 11.10 from cd, each time it crashed and left me an unstable system that wouldn't shut down. I tried five times with different options but in the end I removed all usb connections (printer scanner, webcam etc) and everything worked as it should have. It may just be dodgy hardware that i have but thought it worth mentioning.
Hth
Dai

---

### Post by vt.dave on 2011-12-16
Thanks for the reply!

I would love to remove all excess hardware, but the only usb peripherals plugged in are the keyboard and mouse (and the USB stick if I'm installing off of that).

There is the front USB port board that is plugged in, perhaps I can unplug that and give it another go.

Anyone else ever run into this kind of situation?

---

### Post by t_echtenkamp on 2011-12-17
I'm having this problem too, except I can't get Windows 7 to install either. 

Here's my situation:
I built my computer with a ASRock P67 Extreme 6, two OCZ Vertex 3 SSDs (RAID 0) and tried to boot up Windows 7. During the Windows installation, it gave me an error message > "A required CD/DVD drive device driver is missing." That's expected because it needs drivers for the SATA controller, so I pop that cd in and it finds the drivers. But then it gives me another error: > "No new devices could be found.  Make sure the driver files are correct and located on the driver installation media." I think that's its way of saying "I don't see any hard drives to install this on.

So thinking it's my RAID that's tripping up windows, I take that off and subsequently try all sorts of combinations -- IDE mode, AHCI mode, and all the way down to disconnecting everything except a DVD and normal HDD.

Thinking my burn of Windows 7 is bad, I figure I'll try a tried and true Ubuntu CD and that's when I get the above problems. It either hangs on ```
usbhid: USB HID core driver
``` or ```
[sdb] Attached SCSI removable disk.
```

At this point I can't help but think it's a bad motherboard :(

---

### Post by t_echtenkamp on 2011-12-17
Ok, good news. It was a bad Windows 7 image after all -- at least it's not bad hardware. I still don't know what the problem with Ubuntu is though. I'm gonna finish getting Windows on here, get the raid set up, and then I'll download Ubuntu 11.10 and try that. I was using 11.04.

---

### Post by vt.dave on 2011-12-20
Hello Internet!

Well I'm back to report that I have updated the firmware on the OCZ Agility 3 and...it's made no difference :(

I just tried to install off of a freshly burned image and it still hangs right after it identifies the USB devices.  

Slightly above the USB Identification messages I do see "End Stack Trace" so something before the USB identification has already died.  is there any way to do a step by step load where after ever driver or system it says press a key, so I can interactively figure out what is failing?

Thanks,
-Dave

---

### Post by vt.dave on 2011-12-21
I did notice there is an interactive boot option on the CD after you hit esc, how can I use that to debug what's going on?

Thanks!

---

### Post by t_echtenkamp on 2011-12-21
Hey dave, I was able to get mine to boot by using the acpi=off option on bootup. (Using esc for the interactive boot and then F6 to select acpi=off). If that doesn't work, try a couple of the other ones.

---

### Post by thechris on 2011-12-23
this may be an issue with p67-based motherboards, or perhaps specific p67 based mobos.  I have the same issue with my MSI p67a-g43.  Note that sdb is the usb disk, and for me, the issue persists even with all other disks disconnected.  it will then hang at sda, as the usb-key is the only device left.

setting ACPI=off allowed the usb-key to run.  I haven't tried anything beyond that.  specifically, I can't turn off the computer -- it turns itself back on.  given the number of power-on/off failures I've had in the past, I don't like that at all.

---

### Post by vt.dave on 2012-01-05
Thanks for the reply everyone, setting ACPI=off allows me to boot from a CD, however when I get into the setup it says I do not have at least 4.5 GB of disk space so it clearly doesn't like my SSD :(

Is there a way to tell the ubuntu installer that I've left it 40 gigs unpartitioned?  I just need it to see that space and have it format and install there.

Again, any help is appreciated

---

### Post by vt.dave on 2012-01-05
So after I exit the setup the live CD boots, and I can run baobab, but it only shows the 4gb (memory?) partition, how can I try to force it to see my SSD?

Thanks!
-Dave

---

