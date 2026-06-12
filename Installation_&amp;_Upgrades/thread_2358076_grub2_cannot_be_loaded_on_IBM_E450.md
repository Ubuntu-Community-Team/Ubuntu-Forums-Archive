---
title: "grub2 cannot be loaded on IBM E450"
date: 2017-04-09
forum: Installation &amp; Upgrades
---

### Post by shahsumit on 2017-04-09
[FONT=arial]I had Windows 10 installed on an [IBM E450]("http://www3.lenovo.com/in/en/laptops/thinkpad/thinkpad-e-series/E450-Sub-Series/p/22TP2TEE450") and want to put Ubuntu 16.04. Installation went fine for the most part but grub 2 could not be added to the target.[/FONT]
[FONT=arial]
[/FONT]
[FONT=arial]So far I have tried [/FONT]
[FONT=arial]
[LIST]
[*]delete and re-create the EFI partition - didn't seem to make a difference
[*]tried boot repair - this puts grub into the startup option list and starts laptop into the grub> prompt. Not sure where to go from here
[*]I have made sure that Boot option is Legacy and EFI, with Legacy first in priority list
[*]The EFI partition size is 512mb as shown in the report and has boot, esp flags
[/LIST]


[/FONT]
[FONT=arial]Please let me know if you have any suggestions, here is the is the boot info report - [https://pastebin.com/AvNtNWqf](https://pastebin.com/AvNtNWqf)[/FONT]

---

### Post by oldfred on 2017-04-09
I did not think IBM still made laptops, it is a Lenovo.
And Lenovo is one that seems to only like to boot "Windows Boot Manager". Many vendors violate UEFI standard and use description as part of boot.

Since only booting Ubuntu you have several choices of the typical work arounds.
I would do both the fallback/hard drive and just change the Windows description entry to actually boot grub or shim file. It does not check actual boot file, just description.

Boot-Repair now creates  bkpbootx64.efi and copies shimx64.efi as bootx64.efi. This is a hard drive default or fallback boot entry in UEFI
    'Use the standard EFI file' in advanced options. (It looks like that may have been done.)

But Boot-Repair does not create an UEFI boot stanza to boot the fallback as many systems already have that.

To see current UEFI entries & details:
sudo efibootmgr -v
 sudo efibootmgr -c -g -w -L "UEFI hard drive" -l '\EFI\Boot\bootx64.efi' 

And you can delete the current "Windows" entry and create your own:
      
 sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr 
You may want to delete the other older entries you added (redhat & grub). Entry has GUID and if ESP if reformatted it gets a new GUID.

You are not showing shimx64.efi which is just for UEFI Secure Boot. Most use shimx64.efi even if Secure boot is off. 
      
 
 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\grubx64.efi" 

Check entries, if needed you can reorder with efibootmgr or from inside your UEFI.
sudo efibootmgr -v

Both hard drive & Windows boot entry then should boot grub, but with one install you will not get grub menu by default, it just goes to booting. Use escape key right after UEFI screen. Make sure UEFI fast boot is off, or you may not have time to press a key. If you have optional video chip you may need boot parameter in grub boot stanza.

---

### Post by ubfan1 on 2017-04-09
You should install Ubuntu in the same mode as Windows 10.  If Windows 10 is in UEFI mode, setting "legacy before UEFI" in the settings will force the Ubuntu intall media to boot and install in legacy mode (wrong), since it has both boot capabilities.  Change your mode order to "UEFI before legacy" and try the install again.  My Lenovo W520 does not check any boot item labels or filenames, so that may not be a problem.

---

