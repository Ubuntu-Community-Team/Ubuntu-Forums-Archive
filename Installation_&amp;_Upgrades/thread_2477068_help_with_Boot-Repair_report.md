---
title: "help with Boot-Repair report"
date: 2022-07-13
forum: Installation &amp; Upgrades
---

### Post by citizendeb on 2022-07-13
Hi, I had issues while upgrading Ubuntu 18.04 to 20.04 (connection lost, errors occured and then I wasn't able to access Ubuntu), so I performed an usb boot to repair system. I did manage to access Ubuntu again, but I lost access to the boot menu (ESC key or F10 while booting no longer leads to boot menu, instead it asks me for a setup password). I do want to access the boot options so I can reinstall Ubuntu and make a fresh start. I'm thinking this Boot-Repair utility may be useful but I'm really not knowledgeable about system handling. This is the Boot-Repair report I got now, can you help decide if I should actually do this repair? Thank you very much in advance.

[https://paste.ubuntu.com/p/Dsh862v2fp/](https://paste.ubuntu.com/p/Dsh862v2fp/)

---

### Post by oldfred on 2022-07-13
What password is it asking for?
Is it related to installing a proprietary nVidia driver? That should only be required if UEFI Secure Boot is on. And Boot-Repair is saying your system does not support that, which probably is wrong.

It looks like a normal UEFI install.
What brand/model system?  Some HPs need updates, settings or have other issues.
It looks like you are missing the UEFI boot entry.
Did you update UEFI or change settings in UEFI?

A total reinstall of grub should add the UEFI entry.

---

### Post by yancek on 2022-07-14
On some computers, changes in the BIOS will require the user to input a passphrase/password toverify the user wants the change, in those cases the code should show on screen and the user types it in and hits the Enter key.  INot sure this is what you are seeing?

---

### Post by citizendeb on 2022-07-14
Thank you for responding so quickly! My PC is an HP indeed, and the message that appears when I press ESC while booting just says "Enter setup password".
I obviously don't know this passowrd, and in fact I never had problem accessing the boot menu before, so this is a first. In answer to your question, I did run fsck from the recovery menu when I did the usb boot, but I have no idea if that changes anything in UEFI. Should I do the suggested repair and reinstall the grub then?

---

### Post by oldfred on 2022-07-14
Escape is typically to get grub menu on systems with only one install where grub menu is not normally shown.
I have multiple installs of Ubuntu and set grub to always show menu.

And HP uses these keys.
HP - escape + F9 for UEFI boot menu, F10 for UEFI/bios setup

Which model HP?
So is the escape to get to UEFI boot menu, UEFI setup or grub menu?

HP seems to currently be the only one where a grub install does not change boot order.
You have to go into UEFI settings/setup and change boot order there.
Every other system supports boot order changes with efiboot manager which grub uses, or you normally can manually use to change boot order.
man efibootmgr

hp 250 g3  Change boot order in UEFI settings
[https://ubuntuforums.org/showthread.php?t=2467077](https://ubuntuforums.org/showthread.php?t=2467077)
HP 17-BY4063CL Laptop shows UEFI screens, needed 21.04 since new Intel chip
[https://ubuntuforums.org/showthread.php?t=2462045](https://ubuntuforums.org/showthread.php?t=2462045)
HP Envy - use UEFI to change boot order & f9 f10
[https://askubuntu.com/questions/1332255/dual-boot-only-booting-into-windows-no-option-to-choose-between-windows-or-ubun](https://askubuntu.com/questions/1332255/dual-boot-only-booting-into-windows-no-option-to-choose-between-windows-or-ubun)
HP Pavilion 15t touch (15t cs-200) Post @@ totally remove optane card
[https://ubuntuforums.org/showthread.php?t=2471365](https://ubuntuforums.org/showthread.php?t=2471365)

---

### Post by citizendeb on 2022-07-26
Hi again, I returned to my lab today and tried using ESC+F9 and F10 to access boot menu or bios setup but I stil get the "Enter setup password" screen. The HP I'm using is a Z210 workstation. Do you think the suggested repair could be a solution to regain access to the boot menu? I'm tempted to try it but I hesitate on the last warning in the report: "Please do not forget to make your UEFI firmware boot on the OS you are currently using". Sorry for my ignorance, it's the first time I mess around with these boot settings :S[COLOR=#111111][FONT=monospace]
[/FONT][/COLOR]

---

### Post by oldfred on 2022-07-26
Sounds like you set an UEFI password?
If so you need to use that to change any UEFI settings.
Losing that password converts system to a brick, but there are some extreme work arounds to reset that in some cases.

---

### Post by citizendeb on 2022-07-28
I didn't set any password really, but I guess something went wrong during the upgrade or when I did boot repair and now the system is blocked, as you mention. I was trying to avoid doing an extreme reset, but I'm probably gonna have to do it then. Thank you so much for your help!

---

### Post by yancek on 2022-07-28
Try booting and using Esc and F10 to access the BIOS and go to the Security tab.  You should see both Supervisor Password and Power on password.  What does it show to the right for each?

---

### Post by grahammechanical on 2022-07-28
> I hesitate on the last warning in the report: "Please do not forget to  make your UEFI firmware boot on the OS you are currently using".

It is a standard message that Boot Repair adds at the end of all Boot Repair summary reports. It means that you enter the UEFI settings utility and select Ubuntu and give it the boot priority. This is especially important if a person wants to dual boot with Windows. When Ubuntu loads with a dual boot a Grub boot menu will appear and give the user the option to load either Ubuntu or Windows. If Windows has the boot priority then Windows will load without giving the user an option to load Ubuntu.

Regards

---

