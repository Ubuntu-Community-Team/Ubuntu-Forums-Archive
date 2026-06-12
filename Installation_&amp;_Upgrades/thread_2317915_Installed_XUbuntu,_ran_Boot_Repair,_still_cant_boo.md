---
title: "Installed XUbuntu, ran Boot Repair, still cant boot"
date: 2016-03-21
forum: Installation &amp; Upgrades
---

### Post by larry_hale2 on 2016-03-21
Installed Xubuntu but couldn't boot into it, so ran Boot Repair. Previously had Ubuntu but installed over it. This machine is a XUbuntu only machine. I initially get a "No bootable device found" message but if I hit 'Enter' key, it brings up the old ubuntu grub menu.  I think I found the problem in the Boot Repair log. 
Boot Info Script e7fc706 + Boot-Repair extra info      [Boot-Info 9Feb2015]


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99-2.00) is installed in the MBR of /dev/sda and looks at sector 
    38228 of the same hard drive for core.img,[B] but core.img can not be found 
    at this location.[/B]
 => Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sdb.


Complete log at [http://paste.ubuntu.com/15455320/](http://paste.ubuntu.com/15455320/)


Thanks in advance for your help.

---

### Post by oldfred on 2016-03-21
You have an UEFI system.
The grub in MBR is for BIOS/CSM/Legacy boot. Was old install BIOS boot?
You still show Windows efi boot files in ESP - efi system partition and ubuntu folder for UEFI boot.

You also show rEFInd, which I have not used but plan to try. Many seem to have good luck with it.

But it seems that you have an Acer?
If so you need to set a supervisory password in UEFI and set trust on ubuntu/grub and probably rEFInd's boot files.
Have you updated to latest UEFI from Acer?

 Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912) 
      
 Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[http://ubuntuforums.org/showthread.php?t=2291335](http://ubuntuforums.org/showthread.php?t=2291335)
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)

---

### Post by Edison_James on 2016-03-21
@ oldfred, this is invaluable information for my Acer computer, Thank you:D

---

### Post by larry_hale2 on 2016-03-21
Here's what I've done still have the same problem.
1. While running from USB stick, using Gparted deleted both the boot partition and the Xubuntu partition on the HD.
2. Made sure supervisor password was set in UEFI
3. Made sure that UEFI was active
4. Reinstalled Xubuntu
5. Went back into UEFI and selected GRUB_x64 as trusted.
6. Rebooted.

---

### Post by fantab on 2016-03-21
post a fresh BootInfo...

---

### Post by larry_hale2 on 2016-03-21
> **fantab said:**
> post a fresh BootInfo...

Sorry, Forgot to post it! [http://paste.ubuntu.com/15464452/](http://paste.ubuntu.com/15464452/)

---

### Post by fantab on 2016-03-21
In the UEFI menu choose 'ubuntu' as first boot order... have you checked?


```
BootOrder: 0002,2001,2002,2003
Boot0000* Unknown Device: 	HD(1,800,100000,50bd73c2-3571-41af-8f2b-8dc9a06966ec)File(EFIubuntushimx64.efi)RC
Boot0001* USB HDD: SanDisk Cruzer Glide	ACPI(a0341d0,0)PCI(14,0)USB(2,0)USB(1,0)HD(1,373a340,40021bf,000919e3)RC
[COLOR=#008000]Boot0002* ubuntu	HD(1,800,100000,50bd73c2-3571-41af-8f2b-8dc9a06966ec)File(EFIubuntushimx64.efi)[/COLOR]
Boot0005* rEFInd Boot Manager	HD(1,800,edf11,aed219b0-f442-4477-88a2-d362bc245a57)File(EFIrefindrefind_x64.efi)
Boot2001* EFI USB Device	RC
Boot2002* EFI DVD/CDROM	RC
Boot2003* EFI Network	RC

```

---

### Post by larry_hale3 on 2016-03-22
Here's the latest on my problem.  In UEFI, when I select Grub_x64 under Trusted UEFI files, it doesn't show up in the boot order list.   When I boot up, I get "Default boot device missing or boot failed" message.If I hit the Enter key, it takes me to the Boot Manager. If I hit Enter again, it takes me to the Ubuntu menu. If I hit Enter again it boots into Xubuntu. Boot Repair has left me in this condition. Where do I go from here?

Here is the last log file from Boot Repair:  [http://paste.ubuntu.com/15469016/](http://paste.ubuntu.com/15469016/)


Additionally, the computer is freezing during use. As much as I like Xubuntu, I may have to switch to mint.

---

### Post by oldfred on 2016-03-22
I do not know why you have an unknown?

But you need to see shimx64.efi and grubx64.efi to set as trusted.
And efibootmgr output does not show / or \ between folders.

```
 BootOrder: 0002,2001,2002,2003
Boot0000* Unknown Device: 	HD(1,800,ee000,15924155-7b44-4b10-aaee-240c6809bc82)File(EFIubuntu[COLOR=#ff0000]shimx64.efi[/COLOR])RC
Boot0001* USB HDD: SanDisk Cruzer Glide	ACPI(a0341d0,0)PCI(14,0)USB(2,0)USB(1,0)HD(1,373a340,40021bf,000919e3)RC
Boot0002* ubuntu	HD(1,800,ee000,15924155-7b44-4b10-aaee-240c6809bc82)File(EFIubuntu[COLOR=#ff0000]shimx64.efi[/COLOR])
Boot0005* rEFInd Boot Manager	HD(1,800,edf11,aed219b0-f442-4477-88a2-d362bc245a57)File(EFIrefind[COLOR=#ff0000]refind_x64.efi[/COLOR]) 


```

---

### Post by fantab on 2016-03-22
If re-installing XUbuntu is an option then I suggest you do so. 
Only this time you will 'delete the partiton table' on the HDD, '[create a new partition table]("http://www.dedoimedo.com/computers/gparted.html#mozTocId555890")', GPT, using gparted... then the usual partitions and install.

***BACK UP your data before you delete the partition table.

If you want a UEFI boot then create a Fat32 Efi System Partition of about 300mb with 'boot'flag.
Set your UEFI menu to boot in UEFI only.. 

Reinstall Xubuntu...

---

