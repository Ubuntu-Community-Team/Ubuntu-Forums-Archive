---
title: "No grub2 after boot-repair windows 8 hp envy dv6"
date: 2013-04-03
forum: Installation &amp; Upgrades
---

### Post by jalexstark on 2013-04-03
Now solved (with workaround)

a) On this laptop it matters how you boot the liveDVD.  If you do it straight from F9 (alt boot device), it may boot the DVD in non-UEFI mode.  For me, it may have been that I temporarity had legacy support enabled.  Beware of this, since it may affect installation.  Test what is running as per the UEFI ask-ubuntu page before installing.   It may help to move the DVD option above the "OS boot Manager" (original caps) in the BIOS device boot order.  It may also help to restart from Win8.  Use the trick of holding down shift when clicking on "restart", and use troubleshoot / advanced.
b) After install, rebooting F9 could be used to start UEFI-installed Ubuntu.  Then follow instructions for getting and running boot-repair.  The latest version now correctly renames and replaces the Microsoft boot manager efi file.  (This is the unethical "bug" of hard-coding the EFI file so as to boot with Microsoft's.  Not exactly vendor-neutral.)
c) Rebooting should go to grub.  Booting windows from grub does not work correctly if secure boot is enabled.


%%%
Original description:

Common scenario: Ubuntu installed, just boots to windows: tried boot-repair.

Intervening and selecting alternative boot device (Ubuntu goes to grub) brings up the good old grub menu.


Tried following [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI), though not much applied.  I looked for SRT before realizing this is an AMD machine.  (Duh!)  That said, I have not been able to find QuickBoot/FastBoot anywhere.

FYI, on boot F9 is for alternative boot options, F10 for BIOS.  Type carefully.  F11 is for destroy your computer.  (Well, reinstall win 8.)



I actually installed 12.04.2 then tried to boot the secure remix (12.10) from DVD, but it will not.  Perhaps a burning problem.

On reboot I always get windows, unless I press F9, in which case Ubuntu appears as an option.  This way I could ppa / apt-install boot-repair and then run it.

* If FastBoot is the problem, where does one disable it?
* Boot repair warns that the OS is a long way down the disk.  It suggests creating a /boot partition closer to the start.  Could this be the issue?  The advice was incorrect I think for my case for tackling this.  At least in my experience, messing around reconfiguring for a /boot partition is a major pain, and reinstalling the whole of Ubuntu (this is a new machine) quite easy.  Why would the BIOS find Ubuntu under F9 boot?
* I only did recommended repairs (twice), which did not include MBR rewrite.
* Disabling secure boot did not seem to help.

From boot-repair.
[http://paste.ubuntu.com/5672759/](http://paste.ubuntu.com/5672759/)

---

### Post by oldfred on 2013-04-03
The issue of either large / (root) partitions or / far into drive has not really shown itsself with the new UEFI systems. Almost all users have Linux partitions at end of drive and only one so far created a /boot and I do not know if that solved his issue or not. Issue was only with some BIOS. I always thought it was a BIOS setting, but some users had to create /boot or a small / inside the first 100GB. So Boot-Repair still reports it, but I would look at other issues first.

Some others with HP
 HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
Installing Ubuntu on HP Envy-6 
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)

Fast boot may be the Windows setting to always hibernate. I also do not know as some seem to say it is a UEFI setting. It is intended to skip any UEFI/BIOS screens for quicker booting.

If you get an option with one time boot key to select Ubuntu, you should have in UEFI menu an option to set it as the first boot option or default also. 
Does Windows boot from grub menu, when you boot with ubuntu?

HP has a lot of efi files in your efi partition, so Boot-Repair adds a lot of entries to menu. This should boot Windows. Some systems need secure boot on, others work with it on or off.


 menuentry "Windows UEFI bootmgfw.efi" {
search --fs-uuid --no-floppy --set=root C616-56DA
chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}

---

### Post by jalexstark on 2013-04-03
Tried it all again, with [http://paste.ubuntu.com/5674634/](http://paste.ubuntu.com/5674634/).

I don't think it is the far problem.

It might be a "always hibernate" problem.

Windows will not boot from the grub menu.  I have 4 entries, 2 efi entries, 1 (?)disk, and 1 "recovery".  I have tried the first three many times.  The efi entries were added by boot-repair, which (as you mentioned) added a lot of chatter entries.

The main thing is that the BIOS does not provide any option to add the new "ubuntu" grubx64.efi boot choice.  It insists on booting to "OS boot Manager" (the actual capitalization).  Does this mean that I am doomed to mess with BCDedit?

Thanks again,
/Alex

---

### Post by oldfred on 2013-04-03
Some systems have modified UEFI to only boot the Windows efi file. But Boot-Repair has a rename work around. I think you turn secure boot on, and check the secure boot option in Boot-Repair and it renames files.

       Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706 and 711
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)
 Boot-Repair copied /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (in case the BIOS is hard-coded to boot into /EFI/Boot/bootx64.efi or secure boot signed GRUB file shimx64.efi.
Renamed files:
/EFI/Boot/bkpbootx64.efi
/EFI/Microsoft/Boot/bkpbootmgfw.efi 

   To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC to UEFI/BIOS and chose ubuntu,  and please tell us what you observe.
Please enable SecureBoot in your BIOS, then run Boot-Repair --> Advanced Options --> "GRUB options" tab --> tick "SecureBoot" --> Apply.
To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair. 
A user disabled secure boot, and unchecked it in boot-repair. It now bypasses Grub and goes straight in to Windows.

---

### Post by jalexstark on 2013-04-03
Will do.  In the meantime note that F9 boot to grubx64.efi boots to win8.

---

### Post by oldfred on 2013-04-03
Grub2's shim file has the Microsoft key, but grubx64.efi should not be booting Windows?? Or has renaming of files gone beserk?
Might be a good idea to backup efi partition. 
Boot-Repair also has its own backups of files, somewhere on your system.

---

### Post by jalexstark on 2013-04-03
Another (second boot-repair for third install) info file:
[http://paste.ubuntu.com/5674712/](http://paste.ubuntu.com/5674712/)

I didn't understand the options and second-run advice.  The version I have (ppa:yannubuntu/boot-repair for 12.04) has the secure boot checked automatically when enabled, and has the renaming checked automatically.  Is there a workaround to force a renaming?

/Alex

---

### Post by jalexstark on 2013-04-03
Shim file works.  Actually an error (?)from grub flashes up before the menu.  Suggest you pass on need to change message given by boot-repair about BIOS going to shim instead of grub efi file directly.

(This is, of course, only via F9).

---

### Post by oldfred on 2013-04-03
I have not done it, but if you run it a second time does it rename the files?

---

### Post by jalexstark on 2013-04-03
I tried a second time.  The info in [http://paste.ubuntu.com/5674712/](http://paste.ubuntu.com/5674712/) shows the results.  There appears to be a renaming problem (around line 890).  I have send email according to instructions therein.

---

### Post by oldfred on 2013-04-03
There was just another HP user with the locked efi partition. That is an unusual issue which do do not know how it occurs nor a good fix. But Boot-Repair did not report the locked efi issue on your system.
Just as a test can you edit a file name in your efi? As that seems to be the issue Boot-Repair has.

       grub-efi fails to install with Input/output error - locked efi
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1090829)

If you cannot edit a filename, backup entire efi partition delete efi partition with gparted, create new efi partition in same place with gparted, set boot flag to make efi and restore files.

---

### Post by jalexstark on 2013-04-04
Yann provided an updated version to the ppa repo.  This fixed the menu problem.  (Awesome!)
([http://paste.ubuntu.com/5677086/](http://paste.ubuntu.com/5677086/))

Now I cannot boot to windows, since the previous problem persists for booting windows via grub.  Each grub menu item gives an error, such as
file path: ...  /File(\EFI\Microsoft\Boot)/File(bkpbootmgfw.efi) ...
error: cannot load image.

I think that I am nearly there!

---

### Post by jalexstark on 2013-04-04
...but I can get to Win8 via F9 on start-up; choose EFI file as boot device; choose EFI/Microsoft/Boot/bkpbootmgfw.efi.

---

### Post by oldfred on 2013-04-04
This menu entry in grub2's menu should be using the same file in the efi partition?

 menuentry "[COLOR=#ff0000]Windows UEFI bkpbootmgfw.efi[/COLOR]" {
search --fs-uuid --no-floppy --set=root C616-56DA
chainloader (${root})[COLOR=#ff0000]/EFI/Microsoft/Boot/bkpbootmgfw.efi[/COLOR]
}

---

### Post by jalexstark on 2013-04-04
Yes.  Weird.

Full error:
```
/EndEntire
file path: /ACPI(a0341d0,0)/PCI(0,11)/ATAPI(0,0,0)/HD(2,c8800,82000,8342c12b8be64e4c,9e,b0)/File(\EFI\Microsoft\Boot)/File(bkpbootmgfw.efi)/EndEntire
error: cannot load image.
```

Error similar for "Windows Boot UEFI loader":
```
/EndEntire
file path: /ACPI(a0341d0,0)/PCI(0,11)/ATAPI(0,0,0)/HD(2,c8800,82000,8342c12b8be64e4c,9e,b0)/File(\EFI\Boot)/File(bkpbootx64.efi)/EndEntire
error: cannot load image.
```

---

### Post by oldfred on 2013-04-04
Some only boot with secure boot on, others boot with it on or off. Have you tried both?

---

### Post by jalexstark on 2013-04-04
Disabling secure boot seems to have fixed it, as a workaround.  Somewhere in between osprober, grub, chainloader and secure booting it goes wrong.

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)

Thanks for your essential and timely assistance.

---

### Post by oldfred on 2013-04-04
Glad you have it working.

Must be something in the secure boot or UEFI modifications that make it more difficult for some computers that prevents secure boot.

---

### Post by YannBuntu on 2013-04-05
I agree, I also have the feeling that there are several types of SecureBoot, and that Ubuntu (Linux in general) is still not compatible with all of them.

---

