---
title: "UNetbootin not working"
date: 2013-09-25
forum: Installation &amp; Upgrades
---

### Post by aaron14 on 2013-09-25
I'm trying to install Ubuntu for the first time and I'm trying to use UNetbootin to do so.  When I select UNetbootin in the boot menu I get this message

[COLOR=#323232][FONT=verdana]Boot Manager:[/FONT][/COLOR]
[COLOR=#323232][FONT=verdana]Windows failed to start. A recent hardware of software change might be the cause. To fix the problem:[/FONT][/COLOR]

[COLOR=#323232][FONT=verdana]1.Insert your Windows installation disc and restart the computer.[/FONT][/COLOR]
[COLOR=#323232][FONT=verdana]2.Choose your language settings, and then click "Next".[/FONT][/COLOR]
[COLOR=#323232][FONT=verdana]3.Click "Repair your computer."[/FONT][/COLOR]

[COLOR=#323232][FONT=verdana]If you do not have this disc, contact your system administrator or computer manufacturer for assistance.
[/FONT][/COLOR]
File: \ubnldr.mbr
Status:0xc000000f
Info: The selected entry could not be loaded because the application is missing or corrupt.

I'm using a Asus Zenbook UX31A which has Windows 8 installed.  Any help would be awesome.

---

### Post by aaron14 on 2013-09-25
I forgot to add, I ran bcdedit as an admin and I got this:

[FONT=lucida console]Windows Boot Loader
___________________
identifier              {current}
device                  partition=C:
path                    \Windows\system32\winload.efi
description             Windows 8
locale                  en-US
inherit                 {bootloadersettings}
recoverysequence        {5d4987ed-55bd-11e2-a572-e955acc203d3}
recoveryenabled         Yes
isolatedcontext         Yes
allowedinmemorysettings 0x15000075
osdevice                partition=C:
systemroot              \Windows
resumeobject            [/FONT][FONT=lucida console]{5d4987ed-55bd-11e2-a572-e955acc203d3}[/FONT][FONT=lucida console]
nx                      OptIn
bootmenupolicy          Standard
detecthal               Yes

Real-mode Boot Sector
_____________________
identifier              [/FONT][FONT=lucida console]{5d4987ed-55bd-11e2-a572-e955acc203d3}
device                  partition=C:
path                    \ubnldr.mbr
description             UNetbootin[/FONT]

---

### Post by atrioom on 2013-10-21
Exact same problem here. I saw other forums, where the device for UNetbootin was "boot", which could be fixed by changing it to "partition=C:". For me, this is already set and it still won't boot Linux install.
Any news on this?
Regards

---

### Post by fantab on 2013-10-21
Unetbootin is to BURN the .iso image to USB drive and make it bootable. You don't boot with Unetbootin.

Tell us what exactly are you doing.

---

