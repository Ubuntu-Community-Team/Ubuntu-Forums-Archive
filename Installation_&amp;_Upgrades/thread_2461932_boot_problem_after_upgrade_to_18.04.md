---
title: "boot problem after upgrade to 18.04"
date: 2021-05-10
forum: Installation &amp; Upgrades
---

### Post by Dan Z on 2021-05-10
I recently upgaded my HP laptop from 16.04 to 18.04.

Since then the machine boots direct to 18.04.

There is no machine page where I might select F12 or BIOS etc., no GRUB page either.

The machine goes direct to:

"booting in secure mode", then 18.04 loads and runs just fine.

Under 16.04, this was a dual boot machine with WIN10.

I would get the GRUB screen, where I could select Win 10, system setup so I could change boot order with F9.

I ran boot-repair, the GUI opens, I click repair, but nothing happens.

sudo boot-repair --verbose
[sudo] password for dan: 
boot-repair version : 4ppa130
boot-sav version : 4ppa65
boot-sav-extra version : 4ppa65
glade2script version : 3.2.3~ppa4

I also ran:

sudo grub-install /dev/sda

Installation finished. No error reported.

I searched for other solutions, nothing I found was appropriate to my situation or did not work.

I am willing to ditch the WIN10 bootup, I don't ever use it.

Any assistance would be appreciated!

Thanks DAN

---

### Post by oldfred on 2021-05-10
Did you also recently boot into Windows?
Windows may have run updates including both Windows & UEFI.
Windows updates may have turned on Windows fast start up, which sets hibernation flag & prevents Linux NTFS driver from correctly seeing it and prevents grub from booting it.
A UEFI update, often resets to defaults and maybe turned UEFI Secure Boot back on. It also then will turn UEFI fast boot on which assumes no system changes. That then boots without scanning system and writing new info to drive for operating system. And is so fast you normally do not have time to press any keys to get into UEFI.

Try turning UEFI Secure boot off in UEFI settings.
You may have to fully shut down, or "cold" boot. Not "warm" reboot. Make sure system fully powered down, hold power switch for 10 sec to remove any remaining power with mains disconnected. And if battery powered remove it, so system has no power.

Also if you did not set grub default to 0 seconds, you may have time to press down arrow multiple times. The last grub menu entry is usually a boot entry directly into UEFI.

---

### Post by tea for one on 2021-05-10
> **Dan Z said:**
> There is no machine page where I might select F12 or BIOS etc., no GRUB page either.

[COLOR="#0000FF"]F10[/COLOR] is the key to access UEFI/BIOS options for HP devices.

---

### Post by Dan Z on 2021-05-11
Thanks for your reply- 

"Try turning UEFI Secure boot off in UEFI settings."=== I cannot access this as no machine page offering access to BIOS/UEFI is ever seen. First page shown is  "booting in secure mode"to Ubuntu without showing this. 

"You may have to fully shut down, or "cold" boot. Not "warm" reboot. Make sure system fully powered down, hold power switch for 10 sec to remove any remaining power with mains disconnected. And if battery powered remove it, so system has no power."=== did this twice, no changes.

"Also if you did not set grub default to 0 seconds, you may have time to press down arrow multiple times. The last grub menu entry is usually a boot entry directly into UEFI."=== no GRUB menu ever comes up,  Machine boots "booting in secure mode"to Ubuntu without showing this. 

Further thoughts?

Thanks Dan

---

### Post by tea for one on 2021-05-11
Power off the PC completely
Power on
Press F10 gently at one second intervals as PC is [COLOR="#0000FF"]P[/COLOR]ower [COLOR="#0000FF"]O[/COLOR]n [COLOR="#0000FF"]S[/COLOR]elf [COLOR="#0000FF"]T[/COLOR]esting - [COLOR="#0000FF"]POST[/COLOR]

Do you access UEFI set up pages?

---

### Post by Dan Z on 2021-05-11
F10 brought up insydeh20 setup utility. 

I did not see any UEFI items except boot order.

I did find an item the said SECURE boot was disabled'

When I exited the utility the PC booted to Windows. 

A re-boot went back to original problem, no change.

Thanks DAN

---

### Post by tea for one on 2021-05-11
Post no. 1 - Since then the machine boots direct to 18.04.
Post no. 6 - When I exited the utility the PC booted to Windows. 

Therefore, both Ubuntu and Windows are accessible.

Please power off completely.
Then power on and press F9 gently while PC is in POST.

Do you see boot options?

---

### Post by Dan Z on 2021-05-11
Yes F9 brings up boot menu:
choices:
OS Manager
Ubuntu
OS Manager
boot fro UEFI file

Thanks dan

---

### Post by Dan Z on 2021-05-20
So my solution has been to hit f9, select Ubuntu, it boots up and runs fine.

I did notice the first OS manager boot to win10, 

the 2nd OS manager brings up GRUB, which then boots as it should. 

PC boots to win 10 on power up if no f9 invoked.

DAN

---

