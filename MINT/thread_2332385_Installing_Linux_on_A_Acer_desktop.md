---
title: "Installing Linux on A Acer desktop"
date: 2016-07-31
forum: MINT
---

### Post by RobGoss on 2016-07-31
Hello everyone I'm having a hard time getting Linux to dual boot with Windows 10. I installed it and everything seem to go ok but after trying to boot mint it just keeps going into Windows 10 and does not give me any options to choose between what OS I want

Here is a boot summary 

[http://paste2.org/hWHUXAUL](http://paste2.org/hWHUXAUL)

And thanks for any help with this

---

### Post by howefield on 2016-07-31
Thread moved to the "*MINT*" forum.

---

### Post by yancek on 2016-07-31
You left windwos hibernated which creates problems.  You can see numerous lines in the boot repair output such as the one below which also tells you what to do.

> The NTFS partition is in an unsafe state. Please resume and shutdown
 	Windows fully (no hibernation or fast restarting), or mount the volume
 	read-only with the 'ro' mount option.

Some manufacturers do not comply with UEFI standards.  If this computer was purchased from one of the major manufacturers, which one?

---

### Post by RobGoss on 2016-07-31
As far as I can tell  hibernation is disable on my system

---

### Post by oldfred on 2016-07-31
If you are sure you turned hibernation/fast start up off, then Windows NTFS partition needs chkdsk.
But Windows on updates may turn its fast startup back on.
       Fast Startup off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html) 
    

Acer requires you to set a Supervisory password in UEFI and then enable "trust" and the .efi grub/Ubuntu boot files.
Every model of Acer we have seen so far is the same as far a "trust" required.
 Acer Trust Settings - details _ similar but slightly different explanations which may then make it more clear:
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)

---

### Post by RobGoss on 2016-07-31
> [COLOR=#000000]Acer requires you to set a Supervisory password in UEFI and then enable "trust"[/COLOR]

Hello Fred this is something I can't seem to do I don't see any options to enable TRUST UEFI am I missing something

---

### Post by oldfred on 2016-07-31
Edit.
Some older posts said you have to downgrade UEFI from Acer. Newer ones say the newest UEFI from Acer works. So make sure you have the newest UEFI from Acer.

I have only read the various posts from Acer users. Many and all seem to say you do not see settings until you set a supervisory password.
Then you have to find where to change settings and it will show the ESP and you drill down to the /EFI/ubuntu folder and set trust on the .efi files.

Many more all say the same thing. I do not think any had screen shots, but some do describe it better than others.
       Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)
Details on password & trust setting:
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi)
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi/653202#653202](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi/653202#653202)
How to install Ubuntu for dual-boot with Windows 8 on Acer Aspire V5-551G. Post #3 Supervisory password required
[http://ubuntuforums.org/showthread.php?t=2176273](http://ubuntuforums.org/showthread.php?t=2176273)

---

### Post by RobGoss on 2016-07-31
Ok I guess I'll have to figure out how to fix this BIOS issue this machine is only about a year old

---

