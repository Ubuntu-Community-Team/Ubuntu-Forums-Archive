---
title: "Attempts to dual-boot Ubuntu 12.04 and Windows 8"
date: 2013-08-02
forum: Installation &amp; Upgrades
---

### Post by jneedle29 on 2013-08-02
Recently, I got a new laptop (Vaio T Series Ultrabook; can't remember the specific model number) with Windows 8. I've heard great things about Linux and Ubuntu, so I decided to try to dual boot the two of them. My first attempt used Wubi (which I now know isn't the right way to go), and through some hackery I got Ubuntu 12.04 to work on the laptop but not Windows 8. I tried fixing it, and in so doing have deleted Ubuntu from my laptop. I've been looking at the following links so far to solve my problem: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI), [https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot_boot_into_Ubuntu), and most recently, [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition). With this last one, I got to step 6, but the GRUB location box is grayed out, even though I made the partition. What's going on here?

---

### Post by oldfred on 2013-08-02
I have not seen an UEFI system need the separate /boot partition. Leave /boot inside your / (root) partition. If you want extra partitions /home and/or a NTFS partition for shared data make more sense.

With UEFI, grub is installed into its own folder inside the efi partition that already exists.

If you have an Ultrabook you need to remove the RAID info that Intel SRT creates.
        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

 ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
      
 Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)
> Disable the RAID, it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

Ultrabooks also have dual video which may create issues. If booting with nVidia you will need the nomodeset boot parameter and then once booted will proably want to install bumblebee. nVidia just started to support dual video with its very latest release, but you may need the kernel that will be in 13.10 to fully utilize that video driver.

      
 nVidia Optimus and Ubuntu explained 
[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)
Bumblebee:
[https://wiki.ubuntu.com/Bumblebee](https://wiki.ubuntu.com/Bumblebee)
[http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html](http://www.webupd8.org/2013/04/set-up-bumblebee-with-bumblebee.html)
12.10 with bumblebee
[URL="http://ubuntuforums.org/showthread.php?t=2077451"]http://ubuntuforums.org/showthread.php?t=2077451
[/URL]
 Released 319.17 certified driver May 2013 only uses nVidia so power consumption high
[http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html](http://www.nvidia.com/object/linux-display-amd64-319.17-driver.html)
Some discussion of limits of new nVidia driver with some Optimus support
[http://ubuntuforums.org/showthread.php?t=2142215](http://ubuntuforums.org/showthread.php?t=2142215)

See also link in my signature for more info.

Other threads with Sony, may be similar.
 Sony Vaio T13 
[http://ubuntuforums.org/showthread.php?t=2127699](http://ubuntuforums.org/showthread.php?t=2127699)
Sony T & Intel SRT ubuntu 12.10 & Windows 8 oem 
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)
Sony Vaio [SOLVED] dual boot ubuntu 12.10 & windows 8 problem 
[http://ubuntuforums.org/showthread.php?t=2094761](http://ubuntuforums.org/showthread.php?t=2094761)
 Sony SVE15125CXS Notebook  Only could Install in BIOS mode, Boot-Repair to UEFI dual boot works
[http://ubuntuforums.org/showthread.php?t=2126389&p=12562570#post12562570](http://ubuntuforums.org/showthread.php?t=2126389&p=12562570#post12562570)
Sony VAIO E Series Windows 8/Ubuntu 12.10 Dual Boot, EFI help UEFI screens shown
[http://ubuntuforums.org/showthread.php?t=2087991](http://ubuntuforums.org/showthread.php?t=2087991)




[URL="http://ubuntuforums.org/showthread.php?t=2077451"]
[/URL]

---

### Post by jneedle29 on 2013-08-02
Thanks for responding. I don't think the nVidia thing's an issue for my laptop. 
I tried dealing with the SRT stuff, but I couldn't find anything about it.

Long story short, I tried to follow the steps on [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI), including doing boot-repair after my laptop went straight into Windows8. Even after running boot-repair, it still skipped straight into Windows8. My paste link is [http://paste.ubuntu.com/5942224](http://paste.ubuntu.com/5942224). I don't know what I'm reading on it; any advice?

Btw I tried installing 13.04 this time, just in case a more advanced version might make this easier.

Tried the boot-repair again, this time with secure boot enabled (I don't think it changed much). This time it told me to type the following lines into the command prompt:

[FONT=arial]sudo chroot "/mnt/boot-sav/sda8" dpkg --configure -a[/FONT]
[FONT=arial]sudo chroot "/mnt/boot-sav/sda8" apt-get install -fy[/FONT]
[FONT=arial]sudo chroot "/mnt/boot-sav/sda8" apt-get purge -y --force-yes grub*-common shim-signed linux-signed*
[/FONT][FONT=arial]sudo chroot "/mnt/boot-sav/sda8" apt-get install -y --force-yes grub-efi-amd64-signed shim-signed linux-signed-generic

my new paste page is: [/FONT][http://paste.ubuntu.com/5942417/](http://paste.ubuntu.com/5942417/)

Doesn't seem to have done much though- Windows still boots right up. No GRUB or anything

---

### Post by oldfred on 2013-08-02
Since you have both grub & Windows boot loader in the efi partition, you do have to go into UEFI and choose to boot the ubuntu entry. 

Sometimes you have to either turn on secure boot or turn it off. Some Windows only boot with it on, although they should work with it off. You do not yet show signed kernels for Ubuntu installed so secure boot for Ubuntu will not work yet.

---

### Post by jneedle29 on 2013-08-02
> [COLOR=#000000]Since you have both grub & Windows boot loader in the efi partition, you do have to go into UEFI and choose to boot the ubuntu entry. [/COLOR]

I don't understand what that means. (Also, I have re-disabled secure boot. No change.)

---

### Post by oldfred on 2013-08-03
In UEFI do you have boot choices for Windows & ubuntu? This example that someone posted shows 2 ubuntu entries but you should only have one.

---

### Post by jneedle29 on 2013-08-03
No, I'm not getting anything resembling that.

---

### Post by oldfred on 2013-08-03
BootInfo report does a dump of what data UEFI should show. I do not know which you really see as dump has three entries like this:

This starts at line 1170, also 1181 & 1188 have similar entries.
```
BootOrder: 0001,0003,0000,2001
Boot0000* Windows Boot Manager	HD(1,800,82000,110f443f-c07f-464c-9a7f-f5001b8d1c7b)File(EFIMicrosoftBootbootmgfw.efi)RC
Boot0001* [COLOR=#ff0000]ubuntu[/COLOR]	HD(3,363800,82000,4becfe8f-ac20-40ed-8ff6-d46e28071199)File(EFIubuntushimx64.efi)
Boot0003* Windows Boot Manager	HD(3,363800,82000,4becfe8f-ac20-40ed-8ff6-d46e28071199)File(EFIMicrosoftBootbootmgfw.efi)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}...4................
Boot0004* EFI DVD/CDROM (MATSHITADVD-RAM UJ8C2)	ACPI(a0341d0,0)PCI(1f,2)03120a00040000000000CD-ROM(1,6168c,11c0)RC
Boot2001* EFI USB Device	RC

```

---

### Post by jneedle29 on 2013-08-03
Yea, my BIOS/UEFI screens seem to be relatively bare-bones; I'm not seeing anything even asking me for a boot device anywhere

---

### Post by jneedle29 on 2013-08-03
ran boot-repair again. It's weird- those lines about the boot order look different this time; there's no sign of ubuntu at all:

```
 [COLOR=#000000]chroot /mnt/boot-sav/sda8 efibootmgr -v[/COLOR]BootCurrent: 0005
Timeout: 0 seconds
BootOrder: 0003,0001,0004,0002,0000,2001
Boot0000* Windows Boot Manager	HD[COLOR=#666666]([/COLOR]1,800,82000,110f443f-c07f-464c-9a7f-f5001b8d1c7b[COLOR=#666666])[/COLOR]File[COLOR=#666666]([/COLOR]EFIMicrosoftBootbootmgfw.efi[COLOR=#666666])[/COLOR]RC
Boot0003* Windows Boot Manager	HD[COLOR=#666666]([/COLOR]3,363800,82000,4becfe8f-ac20-40ed-8ff6-d46e28071199[COLOR=#666666])[/COLOR]File[COLOR=#666666]([/COLOR]EFIMicrosoftBootbootmgfw.efi[COLOR=#666666])[/COLOR]WINDOWS.........x...B.C.D.O.B.J.E.C.T.[COLOR=#666666]=[/COLOR].[COLOR=#666666]{[/COLOR].9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.[COLOR=#666666]}[/COLOR]...4................
Boot0005* EFI DVD/CDROM [COLOR=#666666]([/COLOR]MATSHITADVD-RAM UJ8C2[COLOR=#666666])[/COLOR]	ACPI[COLOR=#666666]([/COLOR]a0341d0,0[COLOR=#666666])[/COLOR]PCI[COLOR=#666666]([/COLOR]1f,2[COLOR=#666666])[/COLOR]03120a00040000000000CD-ROM[COLOR=#666666]([/COLOR]1,6168c,11c0[COLOR=#666666])[/COLOR]RC
Boot2001* EFI USB Device	RC 
```

link: [http://paste.ubuntu.com/5942601/](http://paste.ubuntu.com/5942601/)

I don't think I changed anything since the last time; where'd it go?

---

### Post by jneedle29 on 2013-08-03
Also- I may have been wrong about the intelRST stuff. It looks active, but the mode is AHCI. I've been trying to manipulate the accelerator settings, but I can't access them. None of the links seem to directly address what to do here- or at least not in a way I can understand.

---

### Post by oldfred on 2013-08-03
Strange as I understood once an entry is added in UEFI it saves it and you have to manually remove it. One  or more of the dumps of entries may be just last used as one of yours now shows the DVD as a default.

It also may have to do with secure boot on or off? 

I do not know Intel SRT but have some more links.
       Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Details in post #10 on an install that worked
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
Ubuntu on hard drive, re-enable SRT post #19 details
[http://ubuntuforums.org/showthread.php?t=2129157](http://ubuntuforums.org/showthread.php?t=2129157)

---

### Post by jneedle29 on 2013-08-04
Progress has been made! I switched my BIOS settings to place return boot priority to my hard drive, then ran the boot-repair stuff in the trial mode of the Ubuntu cd, and after running boot-repair and rebooting, I finally got the GRUB menu. My GRUB choices looked as follows:

Ubuntu
Advanced Options for Ubuntu
Windows UEFI bootmgfw.efi
Windows Boot UEFI Launcher
Windows UEFI Recovery bootmgfw.efi
Windows Boot UEFI Recovery
Windows Recovery Environment (loader) (on /dev/sda2)
Windows 8 (loader) (on /dev/sda3)
System Setup

Went into Ubuntu, and everything was great. The only thing seems to be that when I chose Ubuntu, I get a message of the form:
```
 [              X.XXXXXX] kvm: disabled by BIOS
```

X's are numbers, and sometimes there's more than one of these numbers. Anyway, aside from that, Ubuntu loaded up fine. I shut down, reboot, and was returned to GRUB.

This second time, I tried to boot Windows 8. The first option I tried was the second to last one (Windows 8 (loader) (on /dev/sda3)), but I got the following message:
```

error: can't find command 'drivemap'
error: invalid EFI file path
press any key to continue: 

```

So the next thing I tried was the Windows UEFI bootmgfw.efi option. This brought me into Windows 8, but when I shut down and rebooted, it skipped GRUB and sent me straight to Windows 8. So, I popped in the Ubuntu cd, rebooted from the disk, and did the boot-repair again. Once again, I got into the GRUB menu, and Ubuntu worked fine. Then, I again shut down my laptop and booted it back up. This time I chose the Windows Boot UEFI Launcher. This produced the same result as the other Windows option; it got me in, but it prevented GRUB from loading up the next time. So, once more I did the boot-repair, and am avoiding Windows at the moment.

Basically, my questions are as follows: 1) Should I be worried about the message I'm getting when I choose to boot Ubuntu, 2) Is my inability to use the Windows 8 (loader) (on /dev/sda3) option a (fixable) problem, the related 3) How do I boot into Windows 8 without losing GRUB, and 4) what are those other options for?

Thank you so much for all the help you've already provided, oldfred; hopefully, I'm almost done.

---

### Post by laugustogs on 2013-08-04
> **jneedle29 said:**
> [...]

Basically, my questions are as follows: 1) Should I be worried about the message I'm getting when I choose to boot Ubuntu, 2) Is my inability to use the Windows 8 (loader) (on /dev/sda3) option a (fixable) problem, the related 3) How do I boot into Windows 8 without losing GRUB, and 4) what are those other options for?

Thank you so much for all the help you've already provided, oldfred; hopefully, I'm almost done.
I have exactly the same problem here, bro. No luck on finding a solution, though. I already tried disabling the fast startup on Windows, which was the first thing I thought (since it's skipping GRUB), but I still got the same behavior.

---

### Post by oldfred on 2013-08-04
Do not know about the kvm BIOS error. Is this install in a qemu/kvm or do have have some setting in UEFI/BIOS for kvm?

It seems like Windows is having to run repairs on its reboot and that is resetting it to the default in UEFI. Did you turn off fastboot (always used hibernation?).

Grub2's os-prober has a bug and only creates BIOS type boot entries that do not work with UEFI. You can turn os-prober off as the entries in 25_custom as the correct efi boot entries. More discussion and how to edit files are in the link in my signature.

 grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
menuentry "Windows UEFI bkpbootmgfw.efi" {
menuentry "Windows Boot UEFI loader" {
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

---

### Post by patspiper on 2013-08-04
For the kvm error, check if there is a Virtualization setting in the bios and make sure it is enabled.

As for the booting issues, I have the exact symptoms on an HP Pavilion g6 (Win8/Ubuntu 13.04).

---

### Post by jneedle29 on 2013-08-06
patspiper- thanks for the tip! Changed the setting in my BIOS, and the message went away

oldfred- I've had fastboot turned off- actually, oddly, it stopped showing up in the options where I did deselect it.
             I followed your instructions on [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295) about efi menu cleanup, but I'm confused about what to do at the end- once I'm in /etc/grub.d/25_custom,              what am I supposed to do in it?

---

### Post by oldfred on 2013-08-06
Any entries you do not want you can just delete. Just be sure to keep each entire boot stanza that you do want. You can also edit menu entry to anything that makes sense to you instead of default if you like.
If you have the backup then you can restore entries if need be.

---

### Post by jneedle29 on 2013-08-06
So, after having done this code I should be able to run Windows 8 and still get the grub screen every time I start up?
```

[COLOR=#000000]sudo bash -c "echo GRUB_DISABLE_OS_PROBER=true >> /etc/default/grub"[/COLOR]
[COLOR=#000000]sudo update-grub

```[/COLOR]

---

### Post by oldfred on 2013-08-06
That should just add a line to the grub configuration that stops os-prober, but the rest of grub runs. And os-prober does not work with UEFI. When they fix os-prober your just need to delete line, comment it out, or change to false.
I have it off on my systems as I have too many old installs and it keeps finding all of them. So I just add the one's I want into my 40_custom.

---

### Post by jneedle29 on 2013-08-06
SUCCESS!
Ok, so the only two things that I did that I think could have finally allowed me to dual-boot were:
1) running boot-repair from Ubuntu on my drive, as opposed to from the LiveCD
2) running update-grub2 as well as update-grub

Either way, I am overjoyed to be able to say that I can boot both Windows 8 and Ubuntu 13.04 and still have GRUB do its stuff.
Thank you so much for your help, oldfred!

---

### Post by oldfred on 2013-08-07
Glad you got it working. :)

sudo update-grub2 just calls sudo update-grub or they are the same thing and both call another file with a long command.

---

