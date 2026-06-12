---
title: "grub boot-repair fails - dual boot Windows 10 - Ubuntu 17.10"
date: 2018-03-07
forum: Installation &amp; Upgrades
---

### Post by choinul on 2018-03-07
Hi everyone,

I need help concerning dual boot issues (I can only boot on Windows 10, not on Ubuntu). I think the issue
came after an update from Windows or from BIOS not so sure, what was the trigger...

Here is my boot-info result :
[http://paste.ubuntu.com/p/6WSm25Pfqs/](http://paste.ubuntu.com/p/6WSm25Pfqs/)

I can boot with a boot-repair on usb stick and I launched boot repair from terminal as follows : ```
sudo boot-repair -d
```

The boot-repair seems stuck after I launch "Recommended Repair".
The last thing I can see in terminal is :
[debug] End fix /mnt/boot-sav/sda8/etc/grub.d
and after that a thousands of pulse that refresh the graphical message. (after 15-20 minutes, I stopped the process).

The last message on the interface is : unhide boot menu. This may require several minutes... 

Anyone have an idea on what I can do?

Many thanks,

---

### Post by oldfred on 2018-03-07
HP has typically not been dual boot friendly.
And it looks like your UEFI boot entry is gone. And normally Boot-Repair would at least add that back.
But with HP and all its system files as .efi, Boot-Repair adds a lot of entries into grub menu with 25_custom in grub.d folder. You can often delete most or all of them if desired. But if Boot-Repair has not run, then you do not yet have those entries.

I do not know if your SK hynix UEFI entry is UEFI or BIOS or would do either depending on what you have.
But that is your hard drive and typically the hard drive is a fallback boot entry and uses /EFI/Boot/bootx64.efi which is usually just a copy of Windows .efi boot file.
We have made bootx64.efi file the grub boot file shimx64.efi. 
Boot-Repair has automated the backup & copy of shim to bootx, but before we used to suggest the manual copy and then boot hard drive entry.
You could try in Boot-Repair's advanced options the 'Use the standard efi file' option. If you only check that it may work?

       HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi, delay of a so called "Express Multiboot menu"
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP Probook 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

In link in my signature below I have specific terminal commands for manually creating /EFI/Boot (for those who do not have it, you already do) and the copy of shim to bootx64. See section on systems that only boot Windows.

---

### Post by choinul on 2018-03-07
Thanks for the help, I  just tried 'Use the standard efi file' option. It was already checked in advanced options. I tried to deactivate other options (unhide,...) but boot-repair stays stuck again when applying changes...

What else can I test?

Edit : I just realised with gparted that partition /dev/sda2  (128 MiB) appears damaged : unable to detect file system. Any idea if it is linked to my problems?

---

### Post by oldfred on 2018-03-07
Its not damaged, but is unformated which is required.
The Windows system reserved (and grub_bios, if BIOS on gpt) are unformatted partitions which gparted says are error, since not formatted.
But those partitions are assigned specific GUIDs in gpt partitioning and are ok.

I would then try the manual copy of shimx64.efi to bootx64.efi and see if then hard drive entry works.

---

### Post by choinul on 2018-03-07
OK but where can I find these 2 files, should I copy the text of shimx64 to bootx64? Or replace the files?

---

### Post by oldfred on 2018-03-07
You replace the file.
I do not think you can open either file, as they are compiled, not text files.

Best to back up current bootx64.efi, or even better back up entire ESP - efi system partition.
I regularly include in some of my normal backup the entire ESP.

But you can restore boot files with reinstall of boot files.
But with ESP, you typically can do a full reinstall of grub's UEFI version and it will totally restore the /EFI/ubuntu folder in the ESP.
I believe the same with Windows, but never have had to do that.

---

### Post by choinul on 2018-03-08
Thanks for this information, but where can I find these files?

---

### Post by oldfred on 2018-03-08
Specific terminal commands are in link in my signature. Make sure not already mounted.
/EFI/Boot/bootx64.efi is the file you want to backup & replace with
/EFI/Ubuntu/shimx64.efi and you may want to copy all of /EFI/Ubuntu to /EFI/Boot, some have had issues where grub64.efi is missing.

If from live installer you have to mount the drive so path has to include that also.
If auto mounted with Nautilus the path will include /media/$USER/....
To see which partition the ESP - efi system partition(FAT32) is:
sudo parted -l

---

