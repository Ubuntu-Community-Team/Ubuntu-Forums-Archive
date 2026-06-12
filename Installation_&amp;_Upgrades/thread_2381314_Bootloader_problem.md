---
title: "Bootloader problem"
date: 2017-12-29
forum: Installation &amp; Upgrades
---

### Post by edgar-edding on 2017-12-29
Hello!

I'm quite new to the Linux world and am currently trying to set up a dualboot Windows 10 & Lubuntu 16.04.
After having installed Lubuntu, the grub-menu didn't show up and my PC booted on Windows, without letting me choose.

So I ran the "boot-repair" utility ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)) to fix that problem (the bootinfo link is here: [http://paste.ubuntu.com/26278841/](http://paste.ubuntu.com/26278841/)).
Now when I turn my PC on, I get an error message saying :
"Failed to open \EFI\BOOT\grubx64.efi - Not found
Failed to load image \EFI\BOOT\grubx64.efi : Not found
start_image() returned not found"

And after 2 seconds, another screen prompts me to insert a valid boot media.

How can I solve that problem?

Thanks very much in advance!

---

### Post by oldfred on 2017-12-29
It looks like you have left Windows fast start up on.
And you have Acer.
You may also need to update UEFI from Acer. Older threads mention downgrading UEFI to get correct "trust" screens, but newer threads mention newest UEFI from Acer works.

       Fast Start up off (always on hibernation)
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

Acer has a unique requirement (actually better than some others) of turning on UEFI Secure Boot, setting an UEFI password, and enabling "trust" on the .efi boot files from within UEFI.


 Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
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

### Post by edgar-edding on 2017-12-29
Thank you very much for your answer!

The thing is I actually can't access Windows (the system prompts me to insert a bootable device...) so I can't change the fast start up settings...
Would it be easier to clean install Windows and start from scratch?

[Edit] : I managed to access the command prompt using the windows media installation, is there anything I could do to at least be able to boot on Windows?

---

### Post by oldfred on 2017-12-29
With UEFI, you should always be able to boot Windows from UEFI boot menu.
If it needs repairs, it may need you to press f8 to get into recovery/repair console.
Otherwise you will need to run repairs from your repair or install flash drive.

Its just that grub will not boot Windows that needs chkdsk or if it is hibernated to prevent damage or lost files. And then you have to directly boot Windows.

And with newer UEFI Windows, updates will often turn fast start up back on and/or reset system to make Windows first in boot order. Full install of Ubuntu/grub also resets system to boot Ubuntu first, but some systems do not comply with UEFI standards and will keep Windows as default boot, using description.

---

### Post by edgar-edding on 2017-12-29
I can't manage to find how to boot windows directly from UEFI boot menu. Both Linux and Windows are installed on the same disk and I can't choose between either of those The only thing I can choose is to boot on that disk and I still have the same problem. I'm stuck on a screen asking me to insert a proper boot device...
My BIOS is that one [https://www.youtube.com/watch?v=MwOznvmpJQk](https://www.youtube.com/watch?v=MwOznvmpJQk), do you know which setting I should change or how I could boot directly on Windows from there?

---

### Post by oldfred on 2017-12-29
CSM is BIOS boot mode, not sure if then your system also defaults to UEFI or not.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  
    
If you turn CSM off, do you get different boot options.
With UEFI, you should not be booting by hard drive, but by UEFI boot entries.
But some systems seem to only use /EFI/Boot/bootx64.efi which is supposed to be a fallback or hard drive entry.

You are not showing typical UEFI entries. From report & its efibootmgr -v
VenHw entry may just be using /EFI/Boot/bootx64.efi. 

  ```
 BootOrder: 0001,0003,0000,0002
Boot0000  ubuntu    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)
Boot0001* UEFI: LITEONIT LCT-128M3S    PciRoot(0x0)/Pci(0x1f,0x2)/Sata(0,65535,0)/HD(2,GPT,677d20ae-a0f7-4c57-9488-414aa0c32a46,0xc8800,0x32000)AMBO
Boot0002  Windows Boot Manager    VenHw(99e275e7-75a0-4b37-a2e6-c5385e6c00cb)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...t................
Boot0003  UEFI: disk2go RETRACT 8.07    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(1,0)/HD(1,MBR,0x4294967261,0x800,0x7d6800)AMBO 


```

You have this file, which should be used by a typical UEFI entry.
/EFI/Microsoft/Boot/bootmgr.efi

From terminal in Ubuntu live installer booted in UEFI mode, this should add UEFI entry for Windows, if UEFI set for UEFI boot not CSM:
 sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Microsoft\Boot\bootmgfw.efi" -d /dev/sda -p 2 

Other alternative is to change bootx64.efi, Boot-Repair backed it up as bkpbootx64.efi and that probably is just a copy of the Windows .efi boot file.
to confirm entry is there.
sudo efibootmgr -v

---

### Post by edgar-edding on 2017-12-29
Even if CSM is turned off, I only get the choice on which disk I want to boot.
Does adding the file you said add the UEFI entry for Windows as first choice in boot order?

[COLOR=#000000]> [/COLOR][COLOR=#000000]Other alternative is to change bootx64.efi, Boot-Repair backed it up as bkpbootx64.efi and that probably is just a copy of the Windows .efi boot file.[/COLOR][COLOR=#000000]
[/COLOR]
Which one is best? What should I do about the grubx64.efi file that's apparently not there?

[COLOR=#000000]

[/COLOR]

---

### Post by oldfred on 2017-12-29
Best to fully backup your ESP - efi system partition. As FAT32 easy to copy to another drive or device and it is not large.

As far as I know /EFI/Boot/grubx64.efi will not work. You could try copying that file into /EFI/Boot.

I would like to see what adding entry does, it should not hurt and can easily be removed.

Then only alternative is rename of /EFI/Boot/bootx64.efi back to the original file, now bkpbootx64.efi.
But then to boot Ubuntu again you have to change it back to be shimx64.efi or grubx64.efi if Secure Boot off. And grub only boots working Windows so you may have to go thru procedure after Windows updates or if Windows has issues. Not very user friendly.

What model Acer?
There are a lot of posts with Acer and various models that seem to have worked.

---

### Post by edgar-edding on 2017-12-29
> [COLOR=#000000]I would like to see what adding entry does, it should not hurt and can easily be removed.[/COLOR]

I still get the exact same error...
I have an Acer Predator G3260

---

### Post by oldfred on 2017-12-29
did you update UEFI from Acer.
That is now a bit older system and Acer should have updates.

Not sure if any of these are similar or not, most Acer posts have been laptops.
       Acer Very latest UEFI/BIOS works, downgrade not required:
[URL="http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141"]http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141
[/URL]
 Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
[https://askubuntu.com/questions/870022/how-to-get-grub-boot-option/870074](https://askubuntu.com/questions/870022/how-to-get-grub-boot-option/870074) 

[URL="http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141"]
[/URL]

---

### Post by edgar-edding on 2017-12-30
Thanks for your answer!
I finally managed to do it by mounting the boot partition on the LiveUSB linux I had and finding the files the bootloader wanted (those were hidden somewhere else, not in the right place...)

---

### Post by oldfred on 2017-12-30
Glad you resolved it.

You can change to [Solved].

---

