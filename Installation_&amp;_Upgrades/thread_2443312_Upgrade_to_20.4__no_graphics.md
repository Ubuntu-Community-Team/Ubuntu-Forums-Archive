---
title: "Upgrade to 20.4 : no graphics"
date: 2020-05-14
forum: Installation &amp; Upgrades
---

### Post by karel2 on 2020-05-14
After I upgraded to 20.4 with do-release-upgrade -d, the system still boots, and presents the login screen. I can authenticate with account and password, and then the monitor is re-initialised and shows "Input not Supported", which normally indicates that it is set for a resolution it cannot manage.
I suspect the login is done in VGA mode, and that things go wrong when the Nvidia-specific driver is started. Yes, there is an NVidia card, a GT710 according to lspci.
Rest of system works fine, for example I can ssh to it from elsewhere, just like before.

~$ lspci | grep -i nvidia
09:00.0 VGA compatible controller: NVIDIA Corporation GK208B [GeForce GT 710] (rev a1)
09:00.1 Audio device: NVIDIA Corporation GK208 HDMI/DP Audio Controller (rev a1)

How to see what resolution has been set?
How to correct it?
Is there a way to force the Nvidia driver into a quite low resolution, so that at least I have a usable X?

---

### Post by CelticWarrior on 2020-05-14
The Nvidia driver should work unless Secure Boot is enabled. Please check that before anything else.

---

### Post by karel2 on 2020-05-14
Thanks! Excuse my ignorance, but how do I check (from the command line, for lack of a working gui!) whether secure boot is active/enabled? It is a feature that I have never come across, but it might of course be silently present.

 And how (and why) why would that setting have changed with the upgrade?

---

### Post by CelticWarrior on 2020-05-14
Secure Boot is a UEFI ("BIOS") feature.

---

### Post by karel2 on 2020-05-14
It worked before, and the BIOS settings have not been touched. Issue cannot be there.

---

### Post by CelticWarrior on 2020-05-14
There's a reason for the UEFI ("BIOS") I posted before... UEFI replaced BIOS many years ago. UEFI is NOT BIOS.

The new firmware - again, UEFI - has lots of new features, among them Secure Boot. Secure Boot prevents loading of unsigned drivers like the proprietary drivers from Nvidia.
This is now basic stuff any user installing OSes, including Windows, should know. Also any user installing OSes should know the hardware *and* the firmware settings. That you were unaware of all this before I mentioned it, is really not a good starting point. And after being made aware of it, instead of checking the settings, you came back with an "attitude". We're going from bad to worse... Please note that to clear up any confusion, I'm not saying Secure Boot is the problem, just that it's one of the first things to check.

Unfortunately we don't even know if you actually installed Nvidia drivers (and which version) and neither if it's a dual-boot with Windows. So, here are a few more thing thast you should know:

[LIST]
[*]Windows feature updates often change UEFI settings - This is "new", it didn't happen before with BIOS.
[*]Any UEFI reset changes settings - This is NOT new, happened with BIOS as well.
[*]A Nvidia GT710 is old but still supported (for now). However the last driver version supporting it is 418 and is this the only one you'll be able to use from now on and until the Linux release/kernel version supports this particular driver version.
[*]In the absence of proprietary drivers all Nvidia graphics are driven by the open-source community driver *nouveau.*
[*]*Nouveau *works with Secure Boot enabled; Nvidia proprietary drivers don't unless manually signed (mokutil utility)
[/LIST]

Now, keeping in mind all the above, please try to remember whether or not you installed Nvidia drivers in the previous release, prior to the release upgrade to 20.04. If not you were using nouveau and the version in the previous release supported the GT710, at least partially, whereas the upgraded version might not (nouveau is a 'best effort' with zero help from the manufacturer, it's far from perfect, and older hardware is sometimes dropped).

In spite of all that I previously commented, at this point, arguably the fastest way to recover your system is a fresh installation. You can boot a live session, do the backups you should have done already but likely didn't, and install 20.04 from scratch. Make sure Secure Boot is disabled and that you're booting the USB media in UEFI mode and then select the installation of third-party drivers/firmware as they should automatically install the recommended drivers for the Nvidia card (it must be confirmed after installation though).

---

### Post by karel2 on 2020-05-14
Thank you for explaining patiently, and excuse the perceived "attitude". I will check and report back.
(And do not worry about my backups, they are very well looked after. The system in question does not hold any critical data, anyway).

I took a look in the /var/log/syslog and found the below text at the last reboot, early this morning; it seems to indicate that nouveau is still being used; presumably as upgraded from the previous 18.04

May 14 05:02:52 suske /usr/lib/gdm3/gdm-x-session[2713]: (II) AIGLX: Loaded and initialized nouveau
May 14 05:32:42 suske kernel: [    6.309488] fb0: switching to nouveaufb from EFI VGA
May 14 05:32:42 suske kernel: [    6.310401] nouveau 0000:09:00.0: NVIDIA GK208B (b060b0b1)
May 14 05:32:42 suske kernel: [    6.437581] nouveau 0000:09:00.0: bios: version 80.28.a6.00.11
May 14 05:32:42 suske kernel: [    6.439121] nouveau 0000:09:00.0: fb: 2048 MiB DDR3
May 14 05:32:43 suske kernel: [    8.443652] nouveau 0000:09:00.0: DRM: VRAM: 2048 MiB

---

