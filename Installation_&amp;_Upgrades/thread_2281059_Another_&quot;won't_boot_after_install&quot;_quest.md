---
title: "Another &quot;won't boot after install&quot; question - (sorry) - Acer Aspire 15 win8.1 Ub14.04"
date: 2015-06-04
forum: Installation &amp; Upgrades
---

### Post by chas4 on 2015-06-04
Hi Folks

As a long term dyed in the wool mac user I have recently been forced to get a Windows laptop for work (don't ask) but I just cant stand windows 8.1 so I thought i'd give linux a try and ubuntu was recommended to me.
So ....... to cut a long story short. I made a bootable copy of the 14.04 iso using pendrivelinux and installed that way following the instructions on the ubuntu installer guide here ....[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop).

Now all that happens is the machine boot every time in windows without offering the dual boot option at startup (as i expected it would).

Any assistance greatly appreciated as I know you folks must get bored to tears of all us noobs with no clue asking the same questions over and over :(

---

### Post by grahammechanical on 2015-06-04
A machine purchased with Windows 8 pre-installed will most likely have a UEFI boot system and not a BIOS boot system and there are certain rules that apply when installing Ubuntu on to a machine with UEFI and Windows 8. The rules are here:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Please confirm that you met all the conditions when installing Ubuntu. You may need to use Boot Repair.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Use it to create a boot info report. It will be stored on Pastebin and you can post a link to the report in this thread. Some us may then be able to give more accurate advice. And then you may want to run boot repair a second time and accept the repair options offered.

Regards.

---

### Post by chas4 on 2015-06-04
> **grahammechanical said:**
> A machine purchased with Windows 8 pre-installed will most likely have a UEFI boot system and not a BIOS boot system and there are certain rules that apply when installing Ubuntu on to a machine with UEFI and Windows 8. The rules are here:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Please confirm that you met all the conditions when installing Ubuntu. You may need to use Boot Repair.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Use it to create a boot info report. It will be stored on Pastebin and you can post a link to the report in this thread. Some us may then be able to give more accurate advice. And then you may want to run boot repair a second time and accept the repair options offered.

Regards.

Hi Graham. 
Thanks for the response, I really appreciate it.
Done the boot-repair.
Link --> [http://paste.ubuntu.com/11567353/](http://paste.ubuntu.com/11567353/)

---

### Post by chas4 on 2015-06-04
A little bit further ..... have now managed to disable secure boot. (its slightly different with Acer laptops)
I have re-run the boot repair and have another link to the frest info ---> [http://paste.ubuntu.com/11568525/](http://paste.ubuntu.com/11568525/)

---

### Post by oldfred on 2015-06-04
It should be saying ubuntu.

```
 BootCurrent: 0002
Timeout: 2 seconds
BootOrder: 2001,0001,2002,2003
Boot0000* [COLOR=#ff0000]Unknown Device[/COLOR]: 	HD(2,12c800,96000,2f837212-c9af-4749-b338-595b2a6777fd)File(EFIubuntushimx64.efi)RC
Boot0001* Windows Boot Manager	HD(2,12c800,96000,2f837212-c9af-4749-b338-595b2a6777fd)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0002* USB HDD: SanDisk	ACPI(a0341d0,0)PCI(14,0)USB(2,0)USB(1,0)HD(1,2,ee8bfe,00000000)RC


```

But from UEFI boot menu or perhaps a one time boot key like f10 or f12, can you boot that choice?

But just about every Acer we have seen requires to to set a UEFI password (never ever lose that) and allow new entries to work.

       Video on getting into UEFI - 1 Min Acer but similar to all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)

 Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
      
 Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

---

### Post by chas4 on 2015-06-05
> **oldfred said:**
> It should be saying ubuntu.

```
 BootCurrent: 0002
Timeout: 2 seconds
BootOrder: 2001,0001,2002,2003
Boot0000* [COLOR=#ff0000]Unknown Device[/COLOR]:     HD(2,12c800,96000,2f837212-c9af-4749-b338-595b2a6777fd)File(EFIubuntushimx64.efi)RC
Boot0001* Windows Boot Manager    HD(2,12c800,96000,2f837212-c9af-4749-b338-595b2a6777fd)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}....................
Boot0002* USB HDD: SanDisk    ACPI(a0341d0,0)PCI(14,0)USB(2,0)USB(1,0)HD(1,2,ee8bfe,00000000)RC


```

But from UEFI boot menu or perhaps a one time boot key like f10 or f12, can you boot that choice?

But just about every Acer we have seen requires to to set a UEFI password (never ever lose that) and allow new entries to work.

       Video on getting into UEFI - 1 Min Acer but similar to all Windows 8
[http://www.youtube.com/watch?v=QGiG1oljjZI](http://www.youtube.com/watch?v=QGiG1oljjZI)

 Acer Aspire ES1-512-C39M Details on password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
      
 Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)


Hi Fred.

Thanks for the response.
When I bring up the f12 boot menu on startup you don't get the HDD0 option to boot from, you only get the windows boot manager. There is nothing else to select.

I already knew how to get into the uefi menu to alter settings and had already set a supervisor password and turned off secure boot.

It would appear that the key to the issue might be the suggestions made by Buhuhu in the [2256083]("http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044") thread.
However it would appear he has missed out a step :(
As you go in to trust the three .efi files inside the uefi menus via the following sequence .... 
s[COLOR=#000000]elect an uefi file as trusted for executing - select HDD0 - then <EFI> - then <ubuntu> and finally enable the 3 efi files inside (shimx64.efi, grubx64.efi and mokmanager.efi)
[/COLOR]it asks you to enter something in a "Boot Description" field before you have the option to click "yes" in order to get the uefi to trust those files and hopefully thereby allowing the boot of ubuntu.

Any suggestions ??

---

### Post by oldfred on 2015-06-05
Have only seen others post they had to "trust" by manually adding entries. 
Not sure of all the details. 

My desktop with an Asus motherboard did require a lot of UEFI settings that for some strange reason were under the CSM menu that you only saw when you changed from Windows to "other" as boot option. I think other meant no secure boot. It also had a lot of UEFI fast boot settings both with reboot and full boot from shutdown. That is different from Windows fast startup and UEFI fast boot can prevent or make it difficult to get into UEFI to change settings.

And on a Dell SFF desktop I only had to turn off secure boot, only a few settings otherwise and it just worked.

---

