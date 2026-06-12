---
title: "Ubuntu 14.04 - Does not boot (UEFI)"
date: 2015-07-16
forum: Installation &amp; Upgrades
---

### Post by dvanzo on 2015-07-16
Hi!

I just installed Ubuntu 14.04 into an Acer Z1220 (all in one) but can boot it (Reboot and select proper boot device). This machine has UEFI and cannot disable it. I already disabled SecureBoot. Running boot-repair does not help neither ([http://paste.ubuntu.com/11890135/](http://paste.ubuntu.com/11890135/)). Any idea?

TIA!!

Daniel

---

### Post by oldfred on 2015-07-16
If you press escape key just as computer starts or UEFI loads, do you get a grub menu.
With just Ubuntu you will not normally get grub menu, it just continues to boot.

I do not know AMD Radeon, but it may need proprietary driver. You may be able to boot with lower quality graphics with nomodeset or other boot parameters.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[URL="http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710"]http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710
[/URL]
 AMD drivers alternatives
[http://ubuntuforums.org/showthread.php?t=2256824](http://ubuntuforums.org/showthread.php?t=2256824)

Also Acer requires you to set an UEFI password (never lose that) to enable trust for other than Windows.
       
 Video on getting into UEFI - 1 Min Acer but similar to all Windows 8
[URL="http://www.youtube.com/watch?v=QGiG1oljjZI"]http://www.youtube.com/watch?v=QGiG1oljjZI
[/URL]
 Screenshots of secure boot settings Asrock, Asus, HP, Acer
[URL="https://neosmart.net/wiki/disabling-secure-boot/"]https://neosmart.net/wiki/disabling-secure-boot/
      [/URL]
 Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[URL="https://www.youtube.com/watch?v=7SkBFkzOW0A"]https://www.youtube.com/watch?v=7SkBFkzOW0A

[/URL]
 Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[URL="http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot"]http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot
      [/URL]
 black list some drivers for shutdown issues - post #9 link to Mint
[http://ubuntuforums.org/showthread.php?t=2256083](http://ubuntuforums.org/showthread.php?t=2256083)
Acer E3 requires UEFI password to allow added settings Post #8
[http://ubuntuforums.org/showthread.php?t=2253311](http://ubuntuforums.org/showthread.php?t=2253311)
[URL="http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710"]
[/URL]

---

### Post by dvanzo on 2015-07-17
Grub does not shows at all... Its like the disk were inexistent... The message in screen says : "Reboot and Select proper Boot Device or Insert Boot Media in selected device and press a key".

Regards,

Daniel

---

### Post by oldfred on 2015-07-17
Error is from Acer's UEFI.
Acer needs you to set trust for ubuntu entry. See links above.

There are other work arounds, Acer should not need them.
Link in my signature has most of the different work arounds that are used.

---

### Post by dvanzo on 2015-07-18
Sorry to bother you again... I already look at the links you provided without luck... More info:

Ubuntu is the only OS in this PC.
No way found to set trust for Ubuntu entry.

Secure Boot already disabled.
[IMG]http://s21.postimg.org/ceekz8stz/secureboot.png[/IMG]

Supervisor password installed.
[IMG]http://s21.postimg.org/e8w0uq587/supervisor.png[/IMG]

Launch CSM: always
[IMG]http://s21.postimg.org/wn6jyphiv/CSM.png[/IMG]

No luck booting. 
[IMG]http://s21.postimg.org/71pql44xj/boot.png[/IMG]

Already posted the boot-repair utility result. Any info inside it could be relevant??

Regards,

Daniel

---

### Post by oldfred on 2015-07-18
You have grub installed to MBR for CSM/legacy/BIOS boot, but it looks like Boot-Repair converted or install is UEFI.

I would turn on UEFI boot/turn off CSM boot.
Did you see this in the threads on Acer's UEFI, after setting password?

> Also the secure boot mode options from security  menu will be active. In  this last one at: select an uefi file as trusted  for executing -  select HDD0 - then <EFI> - then <ubuntu>  and finally enable  the 3 efi files inside (shimx64.efi, grubx64.efi and  mokmanager.efi) -  be sure to type exactly Yes (not yes) for confirmation  for all 3 files  (nice homework for a user). Press F10 to save bios settings.


---

### Post by dvanzo on 2015-07-18
I can't turn off UEFI boot, so its enabled.
Turned off CSM and boot... Same result... :(

Regarding selecting an UEFI file as trusted (select HDD0 - then <EFI> - then <ubuntu>). Where is this option available? I don't see any place into the BIOS settings for this task...

Really appreciated your help!!!

Regards,

Daniel

---

### Post by oldfred on 2015-07-18
I so not have Acer, but every model Acer so far has posted that they have to set the password and then more options appear & they then can set trust for Ubuntu entry.
Not sure if video or explanations from the various links above help explain it. Without having done it myself I cannot explain any more that trust needs to be set.

---

