---
title: "BIOS virus warning setting conflict?"
date: 2005-02-02
forum: Installation &amp; Upgrades
---

### Post by Ron W on 2005-02-02
In section 3.6.3.3. of the Ubuntu's Manual files, it says:-

"Disable any virus-warning features your BIOS may provide" as they "aren't compatible with GNU/Linux".

I see this as a potential conflict as this feature is 'Enabled' with my existing O/S (I'm using Windows 98SE and am wanting to dual boot this with Ubuntu). Any suggestions on what to do?

Thanks

Ron

---

### Post by Buffalo Soldier on 2005-02-02
I think the virus-warning feature in BIOS will cause some problem when you try to install GRUB in the harddisk MBR. That's why it is advised to disable it.

---

### Post by dikki on 2005-02-02
Yes, these virus detections monitor the MBR, and if something tries to write it, the BIOS beeps. Useless feature, you can disable it.

---

### Post by Ron W on 2005-02-03
Thanks for the replies.

What do I do once I've installed Linux - do I keep the Virus warning feature disabled (even though it's set enabled for my existing O/S Windows 98, which I want to keep for the time being), or do I change it back to enabled?

Ron

---

### Post by thestarman on 2005-02-03
[QUOTE=Ron W]Thanks for the replies.

What do I do once I've installed Linux - do I keep the Virus warning feature disabled (even though it's set enabled for my existing O/S Windows 98, which I want to keep for the time being), or do I change it back to enabled?

Ron[/QUOTE]
 Ron,
   As soon as the Linux install has written GRUB to your MBR sector, you can re-enable the virus warning feature if you want...  Nothing should change in the MBR until you decide to install another OS distro!

The Starman.

---

