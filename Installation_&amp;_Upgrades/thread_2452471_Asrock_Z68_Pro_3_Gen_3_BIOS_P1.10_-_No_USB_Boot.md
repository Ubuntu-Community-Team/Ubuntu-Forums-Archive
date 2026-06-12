---
title: "Asrock Z68 Pro 3 Gen 3 BIOS P1.10 - No USB Boot"
date: 2020-10-22
forum: Installation &amp; Upgrades
---

### Post by electrosteam on 2020-10-22
Got a 2012 Desktop to use in my workshop for CAD/CAM/CNC duties.

Currently with Lubuntu 20.04 installed from a DVD.
It would be much easier if I could boot from a USB.
Searching did not produce (for me) any method for adding USB boot.
I placed an enquiry on the Asrock forum a couple of days ago, but no response so far.

Any suggestions ?

Thanks in advance for any assistance,
Keep well,
John.

Apologies for putting post in wrong section - should be in Hardware.

---

### Post by oldfred on 2020-10-22
My old BIOS system from 2006 had multiple devices shown USB-CD,USB floppy, etc, but did not seem to want to boot from a USB flash drive.
Then one day I had flash drive plugged in and was checking drives and there it was. Even though in USB port, it was considered as a hard drive.
Check  your drives.

---

### Post by electrosteam on 2020-10-23
Thanks oldfred,

The problem here is that when I access UEFI, there is no mention of booting from USB.
Only the DVD, hardrive or LAN for booting.
Tried a USB in various ports, the machine ignored them on boot.

USB options are confined to operational issues, which all seem Ok.
I use keyboard and mouse via USB.

I will research a new BIOS flash and see if that helps.
I am having troubles with Lubuntu:
 - 20.04.1 is sluggish and Firefox crashes,
 - 18.04.2 crashes Firefox,
 - after 30 minutes display shows a single vertical red line 2/3 way across.

This machine has a history of problems:
 - mate purchased 2012 with W7 and retired it not long after because of 'issues', after removing hard drive,
 - I installed second-hand hard drive and gave it to a relative who is an IT professional,
 - W7 installed on replacement drive, but it could not be upgraded to W10,
 - handed back to me with W7.

Keep well,
John.

---

### Post by oldfred on 2020-10-23
If you have bootable flash drive plugged in, do you have another hard drive in boot menu?
Early UEFI often had issues. Updates helped, some just worked better with old BIOS.
I did start conversion to gpt on drives in 2010 as I wanted eventually to get new system with UEFI.
But in 2011 added a small SSD - 60GB just for booting. It made old BIOS system so much better, I did not do a new build with UEFI for another 3 years.

---

### Post by tea for one on 2020-10-23
When a PC is being uncooperative with the request to boot from a usb device, try this silly idea.

Power off
Physically remove all internal drives
**Only** insert your prepared usb boot device
Power on

As there is no other bootable drive present, the PC is possibly [COLOR="#0000FF"]forced[/COLOR] to act on the usb device.

If it works, the usb device is sometimes remembered in the UEFI boot log for future use.

Power off, leave the usb device inserted and re-attach your original internal drive.

---

### Post by electrosteam on 2020-10-24
tea for one,
What a diabolical cunning plan !

Tried it out and got success.
But, it appears UEFI can only handle two options, so boot from USB only works (in practice) if the DVD is disconnected.

Then its all go.
Thank you very much for that suggestion.
I will mark the thread as Solved, and independently see if there is an UEFI upgrade that deals with this issue.

Keep well,
John.

---

### Post by tea for one on 2020-10-24
> **electrosteam said:**
> What a diabolical cunning plan !

Yes, rescued from the Stygian gloom ;)

>  But, it appears UEFI can only handle two options, so boot from USB only works (in practice) if the DVD is disconnected.

I suspect that those two options may be the limitation of the UEFI on your specific PC.
You mentioned that your PC is around 8 years old and UEFI firmware has undoubtedly improved since then.

Generally UEFI boot managers are pretty cooperative with multiple boot choices but, of course, exceptions exist.

Anyway, it's gratifying to read about a successful result.

Best wishes

---

### Post by oldfred on 2020-10-24
Do you have Asmedia ports.
Many systems would not correctly work if any drive, including DVD, were plugged into one of the Asmedia ports.

---

