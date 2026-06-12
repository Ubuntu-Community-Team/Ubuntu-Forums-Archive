---
title: "Ubuntu won't boot after clean install"
date: 2017-07-06
forum: Installation &amp; Upgrades
---

### Post by bayzoo on 2017-07-06
Hi,

I purposely bought a new laptop (a very basic Acer Aspire with a hard drive size of 32GB. My intention was to remove Windows 10 and run a single OS (Ubuntu), but I have tried installing Ubuntu about 15 times now (via a USB install) and it still won't boot!

Does this mean I have wasted my money and this laptop can't run Ubuntu? Does anyone know what the common reasons for this are?

Really appreciate any advice; and although I'm relatively technical, I'm new to all of this so putting things in laymans terms would also be much appreciated.

Thank you

Fraser

---

### Post by CatKiller on 2017-07-06
If you're able to install OK, but not boot, it's possible that you've installed in UEFI mode but are trying to boot in Legacy mode, or vice versa. That would give you those symptoms. Other people are more experienced with that than I am.

You haven't given us a lot of information about what you're doing and what results you're getting.

---

### Post by bayzoo on 2017-07-06
Thanks

OK so I downloaded Ubuntu version 16.04, and installed it onto a USB stick using Rufus with the following settings:

[IMG]http://www.bayzoo.co.uk/ubuntu1.png[/IMG]

I then insert the USB into my new laptop, and because it doesn't recognize my previous installation (and I over-wrote Win 10), it then gives me the option to install Ubuntu from my USB stick.

I then just follow the installation process...it asks me whether I want to over-write the disk and start again, or do I want to reinstall etc. and I have tried each of these options but to no avail.

When I got to restart my laptop without the USB stick inserted (and I've changed my boot order) it just says 'No boot device found'.

How do I change it so it doesn't boot in legacy mode?

Thanks

Fraser

---

### Post by CatKiller on 2017-07-06
> **bayzoo said:**
> How do I change it so it doesn't boot in legacy mode?

It would be an option in the BIOS of your computer. Legacy mode, BIOS mode or CSM would be the things you'd need to disable. It's called different things on different computers. You might also have the option where you're selecting the boot device, too; some will have separate entries for booting in UEFI mode or not.

I believe the Ubuntu installer looks different, depending on whether it's trying to install in UEFI mode or Legacy mode but, as I said, others have more experience on this than I do.

---

### Post by bayzoo on 2017-07-06
Thanks

If i leave the USB stick in, an error message really quickly appears then disappears before it goes to the Ubuntu installer:

[IMG]http://www.bayzoo.co.uk/IMG_0306.PNG[/IMG]

---

### Post by CatKiller on 2017-07-06
Ah, OK, so it looks like it's not able to boot in UEFI mode, even though the device itself is capable of it (which you determined when you wrote the image to it in your screenshot in the earlier post). If you look at the other error messages in this picture, you should see that it's not booting in UEFI mode because Secure Boot is preventing it.

You can turn off Secure Boot in the BIOS. That should let the installer boot properly, and will allow it to write to the EFI partition of the hard drive. Which will then mean that you'll be able to boot from the EFI partition normally. I know even less about Secure Boot than I do about UEFI, though.

---

### Post by bayzoo on 2017-07-06
OK - I can't seem to find anywhere in the BIOS that lets me turn off secure boot:

[IMG]http://www.bayzoo.co.uk/IMG_0307.JPG[/IMG]

---

### Post by CatKiller on 2017-07-06
I did find [this]("https://itsfoss.com/disable-secure-boot-in-acer/") that might help. Since you've already nuked Windows, you'll want to start at Step 5. The important thing seems to be that you can't disable it until you've set a Supervisor Password.

---

### Post by bayzoo on 2017-07-06
Thanks - appreciate your help.

I disabled but it seems to still not want to boot... I'm going to start from scratch and will try to see where I'm going wrong (apart from wanting to set fire to the dam thing)!

---

### Post by oldfred on 2017-07-06
Acer in UEFI mode has a unique requirement, of setting UEFI password which opens more settings and enabling "trust" on the .efi grub/ubuntu boot files. As far as I have seen, every model Acer in UEFI mode needs this.

Some older models needed newer UEFI, some older threads had users downgrade UEFI to older version, but newer posts say newest UEFI from Acer works. But make sure you have newest UEFI fro your model system.

 Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392](http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392)
 InsydeH20 setup utility
Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)

---

### Post by bayzoo on 2017-07-06
Thanks oldfred but after following the guide I'm still no further forward. I actually installed Win 10 back on just to update the BIOS, but where I get stuck is at step number 8 (highlight in red below). I don't get that option as you can see in my screenshot, unless I'm missing something?

If I can't get this fixed soon it's going straight back to the shop... a dual boot isn't an option due to the laptops 32GB capacity.

Thanks again.

[IMG]http://www.bayzoo.co.uk/IMG_0310.JPG[/IMG]

[COLOR=#000000]This probably also applies to other Acer models using InsydeH2O BIOS. After much messing around, this is how I got dual boot working on my Acer Aspire R14-471T:[/COLOR]

[COLOR=#000000]1) Update to the latest BIOS (I know, it's UEFI, but I'm going to call it a BIOS). My new laptop shipped with 1.07, 1.10 is the latest as of this posting.[/COLOR]
[COLOR=#000000]2) Shut down, then while starting back up hit the F2 button many times until the BIOS Setup Utility loads.[/COLOR]
[COLOR=#000000]3) In the "Main" menu, set the "F12 Boot Menu" option to "Enabled". Press F10 to Save and Exit, then once Windows loads shut down again.[/COLOR]
[COLOR=#000000]4) Insert your USB flash drive with your 64-bit Ubuntu installer on it.[/COLOR]
[COLOR=#000000]5) Power on and keep pressing F12 until the boot menu pops up. Select the flash drive, boot, and install Ubuntu.[/COLOR]

[COLOR=#000000]This is where things get tricky:[/COLOR]
[COLOR=#000000]6) After ubuntu reboots, it will boot back into Windows. Shut down again. Reboot and hit F2 to enter the BIOS again.[/COLOR]
[COLOR=#000000]7) Under "Security", choose "Set Supervisor Password", and set one. You will need this password any time you go back into the BIOS. A bunch of options on the page should change from grey to blue.[/COLOR]
[COLOR=#000000]8) [/COLOR][COLOR=#ff0000]The "Select an UEFI file as trusted for executing" should now be available. If it's not available, check that Secure Boot is still Enabled, if not, Enable it. Select it, and navigate to HDD0->EFI->ubuntu->grubx64.efi. The BIOS will ask you for a name for it, I called it Grub.[/COLOR][COLOR=#000000][/COLOR]
[COLOR=#000000]9) Hit F10 to save and exit, then immediately hit F2 again to re-enter the BIOS. [/COLOR]
[COLOR=#000000]10) Now go to "Boot", set "Secure Boot" to "Disabled", and arrow down to the bottom of the list to your new "Grub" entry. Hit F6 until it's the top of the list.[/COLOR]
[COLOR=#000000]11) Hit F10 one last time. Your system should now reboot to the Grub boot loader![/COLOR]

---

### Post by oldfred on 2017-07-06
I thought most had Secure boot off.
grubx64.efi for for UEFI boot.
shimx64.efi is for UEFI Secure Boot. 
I have secure boot off, but use shim, so it works whether Secure boot is on or off. (not sure why we need grub then?)

But it probably depends on whether you booted Ubuntu installer in UEFI mode or UEFI Secure Boot mode.
Secure boot mode will install signed kernels & grub, but then you cannot install any proprietary driver blobs. Which may be required for nVidia, if you have that or some Wireless drivers.

---

### Post by bayzoo on 2017-07-06
Ok

I'm very new to all this but understand some of it (my plan was to learn Linux by using it).

I don't remember it allowing me to choose these options during the installation process; how do I choose to install in UEFI mode or UEFI Secure Boot mode?

---

### Post by oldfred on 2017-07-06
It is all about how you boot installer.
If UEFI Secure boot is on, and you boot installer in UEFI secure boot mode, then it installs in UEFI mode with the signed kernel & grub. You probably also have to specifically allow USB boot as that is normally not allowed with Secure Systems.
If you boot in UEFI mode, it installs in UEFI mode.
If you boot in BIOS mode it installs in BIOS mode.

Both Windows & Ubuntu work the same, how you boot install media, is then how it installs.

 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen:
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Boot-Repair can also add signed kernel & reinstall signed version of grub with its advanced options, if you boot Ubuntu live installer in UEFI mode with Secure boot on.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use second option:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by bayzoo on 2017-07-07
OK - so it's definitely loaded in UEFI mode and when I ran Boot Repair this error message came up:

[FONT=arial]GPT detected. Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios_grub flag). This can be performed via tools such as Gparted. Then try again.

Any ideas, in simple terms, how this can be resolved? Is this likely the reason why I'm having problems?

Thanks again[/FONT]

---

### Post by oldfred on 2017-07-09
You booted live installer in BIOS boot mode not UEFI boot mode.
Then to repair grub for BIOS boot it wants a bios_grub partition which you do not have nor want, since you have UEFI.
Reboot flash drive in UEFI boot mode. You can tell how you have booted by looking at first screen. But UEFI should give two boot options, one UEFI and one not UEFI, it usually just has name/label of flash drive.
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Did you set "trust" on the Ubuntu/grub .efi boot files as posted above.
One user with an Acer said he had to leave Secure boot on. If so you need to have installed the signed copies of grub & kernel which are only installed if you boot installer in UEFI Secure Boot mode. Boot-Repair should also offer to install the signed copies, if you boot installer in UEFI Secure Boot mode.

[https://ubuntuforums.org/showthread.php?t=2365529](https://ubuntuforums.org/showthread.php?t=2365529)

---

