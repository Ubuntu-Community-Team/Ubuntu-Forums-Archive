---
title: "Reboot failure after Ubuntu 14.04 LTS install on Gateway desktop/AMI BIOS"
date: 2016-03-19
forum: Installation &amp; Upgrades
---

### Post by theo-stillwater-sc on 2016-03-19
[COLOR=#000000][FONT=Trebuchet MS]Gateway DX4870, i5, 8GB memory, 1TB drive, AMI System BIOS version P11-A3, build date 10/18/2012[/FONT][/COLOR]

[COLOR=#000000][FONT=Trebuchet MS]Trying to install 64bit Ubuntu 14.04 LTS, but after install and reboot get the message:[/FONT][/COLOR]

[COLOR=#000000][FONT=Trebuchet MS]Reboot and Select proper Boot device[/FONT][/COLOR]
[COLOR=#000000][FONT=Trebuchet MS]or Insert Boot Media in selected Boot device and press a key[/FONT][/COLOR]

[COLOR=#000000][FONT=Trebuchet MS]The HDD is in UEFI mode and the DVD which booted the install media was in UEFI mode as well. Cycled through all the combinations of the Secure Boot options in the BIOS, but all configurations yield the same error on reboot.[/FONT][/COLOR]

[COLOR=#000000][FONT=Trebuchet MS]Now have gone through several cycles of boot-repair but still have the same problem. Boot-repair indicates that it has solved all the problems, but my system is not booting.[/FONT][/COLOR]

[COLOR=#000000][FONT=Trebuchet MS]For those skilled in boot-info diagnostics:[/FONT][/COLOR]
[COLOR=#000000][FONT=Trebuchet MS][http://paste.ubuntu.com/15419666/](http://paste.ubuntu.com/15419666/) <- boot-info report without having run boot-repair
[http://paste.ubuntu.com/15420024/](http://paste.ubuntu.com/15420024/) <- boot-info report after having run boot-repair
[http://paste.ubuntu.com/15420365/](http://paste.ubuntu.com/15420365/) <- boot-info report after rebooting and rerunning boot-repair[/FONT][/COLOR]

[COLOR=#000000][FONT=Trebuchet MS]rebooting the broken system of course implies starting up in "Try Ubuntu" mode, and manually installing the boot-repair toolkit.

I am out of ideas, what to try next to get this system to boot from HDD?[/FONT][/COLOR]

---

### Post by oldfred on 2016-03-20
I do not know LVM nor encryption.

But you have an UEFI boot with separate /boot partition. After each kernel update make sure you house clean out an old one. They may have fixed issue of doing that, but best to be sure. We have many threads on full /boot partitions and system is locked up and difficult to houseclean from live installer.

It shows UEFI Secure Boot on, but standard (non-secure boot kernels) installed.
Probably easiest just to turn off Secure boot in UEFI. But leave UEFI boot on and BIOS/CSM/Legacy boot off.
Some systems call Secure boot Windows and non-Secure boot "Other". But that is not totally correct as Windows 7 can be UEFI boot and does not support Secure boot, so it also has to use "Other" UEFI setting.

---

### Post by theo-stillwater-sc on 2016-03-20
Thanks for your reply. I had tested the set up with both Secure Boot on and off and both generate the same behavior on this system. 

Does that information generate any additional insight how to get this system working?

---

### Post by oldfred on 2016-03-20
Is the UEFI/BIOS the latest version from Gateway.
Others with Gateway seem to have a limited UEFI.

But many systems are violating UEFI spec that says not to use description as part of boot.
The only allow one description which happens to be "Windows Boot Manager".

Since not using Windows, you can delete the Windows folder in UEFI and the Windows entry that uses those files to boot. Best to fully back up ESP - efi system partition first.
Then you can create a new "Windows" entry that actually uses shim to boot. System is only checking description not actual boot file.
Another alternative is to use the fallback or default hard drive boot entry which is always /EFI/Boot/bootx64.efi and make that really be shimx64.efi. 
On my system I have done both.

Details also in link in my signature below.

       # from liveDVD or flash booted in UEFI mode and use efibootmgr, your current Windows entry is 0002
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root.
efibootmgr -b XXXX -B
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[URL="http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD"]http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD

[/URL]
  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 

[URL="http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD"]
[/URL] Boot-Repair should have copied shim to bootx64.efi. But does not add entry to UEFI.
Not sure if your 0003 is UEFI boot using bootx64.efi or not.
But we can add one if need also.
      
 # You may need new hard drive entry:
sudo efibootmgr -c -L "UEFI Hard drive" -l "\EFI\Boot\bootx64.efi"
# confirm entries:
sudo efibootmgr -v

---

### Post by theo-stillwater-sc on 2016-03-20
I am very grateful that you are looking into this issue.

Conceptually, I understand your description and solution to the problem. However, I am missing the knowledge how to investigate what is behind the efibootmgr Boot0002 entry. You indicate that I need to do a backup of this, but I don't know where or what that points to.

Also, as the Boot order is #3, #4, #2, #0, and #3 is the HDD, I don't know if the message is generated by an incorrect configuration of #3 or if it falls through to #2, the Windows Boot Manager, entry and fails.

If I remember correctly, during the installation, it indicated that there was going to be a separate EFI boot partition, but the /boot directory in the root partition is empty. There is an "EFI System Partition" in partition #1, but I haven't found a way yet to look into Partition #1 to see what it contains. 

When searching for efi files I see them in partition #2, under the grub subdirectory, but there is no bootx64.efi. I have a suspicion that they are present in the boot partition #1. 

I conceptually understand what you described, but I am not skilled enough to articulate an investigatory principle that finds the cause of the failure, and subsequently finds a solution.

If you don't mind, I would like to focus on your assertion: "[COLOR=#000000]Another alternative is to use the fallback or default hard drive boot entry which is always /EFI/Boot/bootx64.efi and make that really be shimx64.efi. "
[/COLOR]
I suspect that resides in Partition #1; how do I look inside that partition on my ephemeral Ubuntu instance?

I created a new pastebin for the current state of my system: [http://paste.ubuntu.com/15441721/](http://paste.ubuntu.com/15441721/)

---

### Post by theo-stillwater-sc on 2016-03-20
More confusion on my part:

When looking at the output of boot-repair, I see this:

chroot /mnt/boot-sav/mapper/ubuntu--vg-root efibootmgr -v
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0000,0003,0004,0002
Boot0000* ubuntu	HD[COLOR=#666666]([/COLOR]1,800,100000,a41a9cd8-2a7d-447f-8bb7-4eb438e69d41[COLOR=#666666])[/COLOR]File[COLOR=#666666]([/COLOR]EFIubuntushimx64.efi[COLOR=#666666])[/COLOR]
Boot0002  Windows Boot Manager	Vendor[COLOR=#666666]([/COLOR]99e275e7-75a0-4b37-a2e6-c5385e6c00cb,[COLOR=#666666])[/COLOR]WINDOWS.........x...B.C.D.O.B.J.E.C.T.[COLOR=#666666]=[/COLOR].[COLOR=#666666]{[/COLOR].9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.[COLOR=#666666]}[/COLOR]..._................
Boot0003* UEFI: ST1000DM003-1CH162	ACPI[COLOR=#666666]([/COLOR]a0341d0,0[COLOR=#666666])[/COLOR]PCI[COLOR=#666666]([/COLOR]1f,2[COLOR=#666666])[/COLOR]03120a000200ffff0000HD[COLOR=#666666]([/COLOR]1,800,100000,a41a9cd8-2a7d-447f-8bb7-4eb438e69d41[COLOR=#666666])[/COLOR]AMBO
Boot0004* UEFI: HL-DT-ST DVDRAM GH82N	ACPI[COLOR=#666666]([/COLOR]a0341d0,0[COLOR=#666666])[/COLOR]PCI[COLOR=#666666]([/COLOR]1f,2[COLOR=#666666])[/COLOR]03120a000400ffff0000CD-ROM[COLOR=#666666]([/COLOR]1,19a7,11c0[COLOR=#666666])[/COLOR]AMBO

that is slightly different from the boot order I see on my ephemeral instance, with difference in the #0 entry as well. 
The "chroot /mnt/boot-sav/mapper/ubuntu--vg-root efibootmgr -v" I assume provides the context how to interpret the information,
the problem is that I can't seem to be able to look into that /mnt/boot-sav area: it manifests itself as a "block special" device, not a file system.
I don't know how to interpret that...

---

### Post by oldfred on 2016-03-21
You have the ESP - efi system partition which is sda1. That is where all systems store boot files in folders.
You do not need Windows folder.
And sda1 is what I suggest backing up. That is all the files used by EFI to boot.

Then UEFI has its own NVRAM where it stores boot entry. Some auto create entries like the fallback entry from the ESP. Most require you to use efibootmgr or from within UEFI add entries. 

This shows the label, drive, GUID, and path/file used to boot. 
sudo efibootmgr -v 

New versions of Ubuntu make the fstab entry for the ESP to be read only, Boot-Repair changes it back to defaults which was what was used before. I manually edited fstab to defaults.

       
 From live installer mount the efi partition on hard drive:
mount /dev/sda1 /mnt
cd /mnt/EFI
ls

---

### Post by theo-stillwater-sc on 2016-03-21
How do I make efibootmgr state stick to the underlying HDD installation?

I deleted the Windows entry and added the shim:
> efibootmgr -b 0002 -B
> [COLOR=#000000]efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 

but on reboot the same error message appears, and when I reinstall an ephemeral Ubuntu to reengage the system, the output of efibootmgr pertains to the ephemeral instance.

I do not understand the workflow of using efibootmgr which bits it is manipulating. It appears on first reading that they are the ephemeral bits, not hdd or nvram bits.

I need more education....[/COLOR]

---

### Post by oldfred on 2016-03-21
Post this:
sudo efibootmgr -v

What is your ephemeral? Is that just the live installer in live mode. 

The efibootmgr should be directly updating the UEFI NVRAM entries that are on motherboard. Those entries do automatically get erased if you disconnect the drive the entries refer to.

---

### Post by theo-stillwater-sc on 2016-03-21
Indeed, ephemeral is the live installer instance of Ubuntu that comes off the LiveCD.

Here was my progression: starting with the system articulated by [http://paste.ubuntu.com/15441721/](http://paste.ubuntu.com/15441721/)

root@ubuntu:/mnt/EFI# efibootmgr -v
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0003,0004,0002,0000
Boot0000  ubuntu	Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0002  Windows Boot Manager	Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)WINDOWS.........x...B.C.D.O.B.J.E.C.T.=.{.9.d.e.a.8.6.2.c.-.5.c.d.d.-.4.e.7.0.-.a.c.c.1.-.f.3.2.b.3.4.4.d.4.7.9.5.}..._...............
Boot0003* UEFI: ST1000DM003-1CH162	ACPI(a0341d0,0)PCI(1f,2)03120a000200ffff0000HD(1,800,100000,a41a9cd8-2a7d-447f-8bb7-4eb438e69d41)AMBO
Boot0004* UEFI: HL-DT-ST DVDRAM GH82N	ACPI(a0341d0,0)PCI(1f,2)03120a000400ffff0000CD-ROM(1,19a7,11c0)AMBO


////////  deleting the Windows Boot Manager as indicated by your second reply:
root@ubuntu:/mnt/EFI# efibootmgr -b 0002 -B
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0003,0004,0000
Boot0000  ubuntu
Boot0003* UEFI: ST1000DM003-1CH162
Boot0004* UEFI: HL-DT-ST DVDRAM GH82N

#### adding the entry to point to shimx64.efi
root@ubuntu:/mnt/EFI# efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0001,0003,0004,0000
Boot0000  ubuntu
Boot0003* UEFI: ST1000DM003-1CH162
Boot0004* UEFI: HL-DT-ST DVDRAM GH82N
Boot0001* Windows Boot Manager


root@ubuntu:/mnt/EFI# efibootmgr -v
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0001,0003,0004,0000
Boot0000  ubuntu	Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0001* Windows Boot Manager	HD(1,800,100000,a41a9cd8-2a7d-447f-8bb7-4eb438e69d41)File(\EFI\ubuntu\shimx64.efi)
Boot0003* UEFI: ST1000DM003-1CH162	ACPI(a0341d0,0)PCI(1f,2)03120a000200ffff0000HD(1,800,100000,a41a9cd8-2a7d-447f-8bb7-4eb438e69d41)AMBO
Boot0004* UEFI: HL-DT-ST DVDRAM GH82N	ACPI(a0341d0,0)PCI(1f,2)03120a000400ffff0000CD-ROM(1,19a7,11c0)AMBO

//// removed LiveCD, reboot, and got the same boot failure, so back to a LiveCD and manually installed efibootmgr to get this information
root@ubuntu:~# efibootmgr -v
BootCurrent: 0004
Timeout: 1 seconds
BootOrder: 0003,0004,0000,0001
Boot0000  ubuntu	Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0001  Windows Boot Manager	Vendor(99e275e7-75a0-4b37-a2e6-c5385e6c00cb,)
Boot0003* UEFI: ST1000DM003-1CH162	ACPI(a0341d0,0)PCI(1f,2)03120a000200ffff0000HD(1,800,100000,a41a9cd8-2a7d-447f-8bb7-4eb438e69d41)AMBO
Boot0004* UEFI: HL-DT-ST DVDRAM GH82N	ACPI(a0341d0,0)PCI(1f,2)03120a000400ffff0000CD-ROM(1,19a7,11c0)AMBO

Looking at the first and the last efibootmgr -v output, the Windows Boot Manager config has changed, but not in the way I would have expected it.

---

### Post by oldfred on 2016-03-21
I do not know details of efibootmgr output. Or do not know what vendor entry means or is.
Most entries that I have seen and have on my system are the one shown just after your update. It shows drive, GUID, and path/boot files.
But your UEFI is changing it.
And the other entries referring to just ACPI are probably BIOS boot entries.

You show UEFI from 2012 and early UEFI implementations from Vendors has lots of issues as well. It that the latest version from Gateway for your system?

Acer is the parent of Gateway.
And all Acer require you to set in UEFI a supervisory password, and then set "trust" on the grub/shim/ubuntu boot files.

       Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062)
Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)

---

### Post by theo-stillwater-sc on 2016-03-21
Dude, you are amazing. Thanks for explaining this stuff, and accumulating all these resources for troubleshooting: it is much appreciated.

I have a call outstanding in the Acer community as well regarding this issue, but have not received any feedback from Acer or its community. I also checked with a service that indicated it has taken over Gateway customer support services, but I can't get a peep out of them either. 

In my AMI bios there is an option to set a password, but it is currently disabled. I will play with that configuration next and report back.

---

