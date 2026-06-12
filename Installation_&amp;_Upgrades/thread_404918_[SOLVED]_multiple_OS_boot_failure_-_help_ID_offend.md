---
title: "[SOLVED] multiple OS boot failure - help ID offending device"
date: 2007-04-09
forum: Installation &amp; Upgrades
---

### Post by gregconquest on 2007-04-09
I have a severe problem, but I am almost happy about it. Occasionally, my Windows XP Pro SP2 will not reboot in normal mode. It has been down for a week and about 50 reboots now. It will go into safe mode OK, but never into normal mode. Some helpful ideas [in another forum]("http://snipurl.com/ScotsBrokenWinBoot") leads to me to believe that some hardware or driver is causing the problem.

Throughout the above problems, however, ubuntu, kubuntu, and openSUSE were working fine. Starting yesterday, though ***all OS's fail to boot completely***. This is true even of recovery mode for my linuxes.

So, here is what I have now. The last two lines of the text on my screen from ubuntu and kubuntu booting in recovery mode are:
```
ACPI: Core revision 20060707
[   40.652842] ACPI: Looking for DSDT in initramfs. . . error, file /DSDT.aml not found.
```

Can anyone see what is causing the problem? If not, is there something I can do to get a more detailed boot log?

Thanks for any help.
Greg Conquest

[http://snipurl.com/ScotsBrokenWinBoot]("http://snipurl.com/ScotsBrokenWinBoot") = [http://forums.scotsnewsletter.com/index.php?showtopic=18294]("http://forums.scotsnewsletter.com/index.php?showtopic=18294")

---

### Post by neilengineer on 2007-04-09
> **gregconquest said:**
> I have a severe problem, but I am almost happy about it. Occasionally, my Windows XP Pro SP2 will not reboot in normal mode. It has been down for a week and about 50 reboots now. It will go into safe mode OK, but never into normal mode. Some helpful ideas [in another forum]("http://snipurl.com/ScotsBrokenWinBoot") leads to me to believe that some hardware or driver is causing the problem.

Throughout the above problems, however, ubuntu, kubuntu, and openSUSE were working fine. Starting yesterday, though ***all OS's fail to boot completely***. This is true even of recovery mode for my linuxes.

So, here is what I have now. The last two lines of the text on my screen from ubuntu and kubuntu booting in recovery mode are:
```
ACPI: Core revision 20060707
[   40.652842] ACPI: Looking for DSDT in initramfs. . . error, file /DSDT.aml not found.
```

Can anyone see what is causing the problem? If not, is there something I can do to get a more detailed boot log?

Thanks for any help.
Greg Conquest

[http://snipurl.com/ScotsBrokenWinBoot]("http://snipurl.com/ScotsBrokenWinBoot") = [http://forums.scotsnewsletter.com/index.php?showtopic=18294]("http://forums.scotsnewsletter.com/index.php?showtopic=18294")



I guess, there might be something wrong with the hardware connection. I suggest you unplug and replug all the wires, especially the wires for the hard drive.  Or could the settings in  BIOS be wrong??  Note the ACPI stuff.

---

### Post by gregconquest on 2007-04-09
Thanks, neilengineer, but this time the three linuxes that simultaneously failed were spread across two different hard drives. So, I can't see how that would be causing the problem . . . However, the general thing about some connection not being seated right might be correct. Again, however this is a DIY system. I installed everything carefully. I'll re-check them, but I think either:
- there is a component failure on the motherboard or one of the devices (blown fuse, melted capacitor, . . .)
- or a device has a strange driver problems.

Since Windows began failing a while ago, and now Linux has done so as well, using drivers unrelated to Windows, my suspicion falls heavily on the hardware.

Thus I am asking if there is any way to diagnose what device is causing the problem by examination of the boot log. Is there some way to generate a more detailed boot log?

Thanks again,
Greg

PS neilengineer, if you click "reply" on the lower left instead of "quote" on the right, you can get a cleaner post. Quote only what you need to -- important snippets here and there. You can edit your post and delete everything before the words you typed (since my post is directly above yours anyway). Just be sure to hit "preview" before "submit reply".

---

### Post by neilengineer on 2007-04-09
You are welcome. Maybe you can try the following:

1)Try to boot from CDROM with a Linux LiveCD and see what happens.

2)Unplug one of the hard drives(e.g. the one for Windows ), and see if Linuxes boot successfully.

3)Reinstall an OS(Windows or Linux) on one of the hard drives(unplug the other one).

4)Check the motherboard for melted capacitor etc. AND go to a PC hospital for help.

5)Make sure your PC power supply is good.     (Sometimes, a weak PC power supply causes weird problems)

---

### Post by gregconquest on 2007-04-11
Hey, neilengineer, your suggestion about a boot CD got me thinking, I downloaded systemrestoreCD and ultimatebootcd and tried the diagnostics, but nothing . . . I searched more on the last error, "DSDT.aml not found" when booting in recovery mode. ACPI again . . . I found some pages on fixing ACPI problems, but they involved more programming than I am willing to try. Then I thought about the BIOS being so central in all this. I checked for a BIOS update, and there was one. I flashed, and all the problems are gone \\:D/ 

I'm embarrassed I didn't try the BIOS flash before :oops: 

Greg

---

