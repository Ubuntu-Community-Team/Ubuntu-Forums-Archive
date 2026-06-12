---
title: "Windows 8/Ubuntu dual boot not happening"
date: 2013-03-31
forum: Installation &amp; Upgrades
---

### Post by gobotsoup on 2013-03-31
Hello I am trying to boot 12.10 64 bit from my DVD/CD drive. When I boot it just always goes right to Windows. I went to the UEFI Firmware settings (BIOS) and disabled secure boot and fast boot. During one of my boot trials I saw my CD/DVD drive listed as "ATAPI CD/DVD Drive", but now it's not showing any longer. The one time I did see it listed I moved it up to #1 in the boot order, but it still just booted straight to Windows. Could there be an issue with my DVD drive not being recognized as a bootable disk? I'm not really sure how to check on that. Any help would be really appreciated!

---

### Post by Jay_E on 2013-03-31
hi there.

Been there, done that.

Please try this.
re-enable the secure boot.
   -- On my system, the DVD drive with ubuntu CD/DVD is seen as secure/UEFI.

my bios did not remember boot priority for some reason.
I had to go into bios and set boot device each time.
(might apply to you.)

If you have an **old** system the rrive may be cd only - so it can't read a dvd.
(Probably won't apply - but need to rule out.)

When you try booting, does the cd/dvd spin up and make reassuring noises?
(something else to rule out. On another system, will the cd boot? If there is a check CD option, try it.)

if all this fails, try resetting the bios to default settings.
(most have this.)

Sounds like you are doing OK - plenty of patience.

I watched Gallagher on youtube to reset frustration.

:-)

Jay

---

### Post by oldfred on 2013-03-31
You should also have a one time boot key.

       UEFI/BIOS Boot keys - about halfway down on this Microsoft page
[http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](http://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

What system is this?
I prefer flash drives now as it installs quicker and they are reusable. But only some brands of flash drives seem to work. 
Double check that download is ok. And that you have burned it as bootable DVD, not just a copy of ISO to DVD.

      
 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

---

### Post by gobotsoup on 2013-03-31
Thanks for the suggestions. I am trying to boot the 64 bit version of 12.10, but I am still not able to boot from my DVD. It just goes straight to Windows 8. I ensured that the DVD I made is bootable, and I was able to boot from it on my laptop. Maybe this is something wrong with my computer or something. I have tried both with secure mode enabled and disabled, and with fast boot enabled and disabled. Neither seems to make any difference. I wonder why I was able to see my DVD drive in the boot order menu once, but now it doesn't show up anymore. Very strange stuff. May have to hit up some Gallagher per Jay's suggestion lol.

---

### Post by oldfred on 2013-04-01
It seems many systems will not try to boot anything else unless secure boot is off. And fast boot needs to be off.

Some systems seem to get locked up. A hard or cold boot sometimes can help. If laptop remove battery and hold down power switch for 30 sec or more to get capacitors to discharge also.

---

### Post by gobotsoup on 2013-04-06
Welp, turns out the problem was a combination of at least these two things. 
1. I needed to boot with legacy mode enabled, then re-boot in order to see my DVD/CD drive in my BIOS. 
2. I was booting an X86 version of Ubuntu rather than AMD (derp)...
Not sure if Secure boot or Fast boot really makes much of a difference with 12.10. I ended up booting from USB and it seems to be working now. Although after a re-start I got a blank black screen the first time. 
Now back to Gallagher.

---

