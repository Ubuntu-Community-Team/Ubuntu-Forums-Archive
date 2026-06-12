---
title: "dual boot with win7 on asus h87m-e mobo not working"
date: 2016-07-06
forum: Installation &amp; Upgrades
---

### Post by tonymoloney on 2016-07-06
I have actually installed 16.04 on the above computer, but when I reboot all I can get is the win7  system.
I can't find any way to get around the eufi bios.

any help?

Tony

---

### Post by ajgreeny on 2016-07-06
Are you certain Windows 7 was installed using UEFI as it normally used BIOS.

Whichever is the case, both OSs must be installed in the same mode.

Run the Boot-info-script from Boot-Repair in my signature below and copy the pastebin link back here so we can see what is going on. Do not at this stage accept the default repair; just run the boot-info-script.

---

### Post by tonymoloney on 2016-07-10
Hi ajgreeny
Sorry for the delayed response. Australia is so far away!

the address you want is http;//paste2.org/JPh207JM

I hope this helps

Thanks 

Tony

---

### Post by tonymoloney on 2016-07-10
Sorry

This should be [http://paste2.org/JPh207JM](http://paste2.org/JPh207JM)

My bad

---

### Post by oldfred on 2016-07-10
I think the real problem is that you are already tomorrow where we are stuck on today. :)

You now have a gpt partitioned drive.
But Windows 7 default install is normally BIOS and Windows then has to have MBR(msdos) partitioning to boot in BIOS mode.
Windows can only boot in UEFI mode from gpt partitioned drives.

Lots of instructions for UEFI in link in my signature.

And it looks like you converted the Windows 100MB boot partition to a bios_grub.
Windows in BIOS mode has two partition as default with some boot files  in the first partition which is normally 100MB. A bios_grub partition  only has to be 1 or 2 MB.

I do not know how much data or effort you have in systems installed so  far. But easiest fix is to start over. Be sure to backup any data or  configurations you have.

You can choose either BIOS/MBR or UEFI/gpt.

[http://www.eightforums.com/tutorials/13326-downgrade-windows-8-windows-7-a.html](http://www.eightforums.com/tutorials/13326-downgrade-windows-8-windows-7-a.html)
  How to Create a Bootable UEFI USB Flash Drive for Installing Windows 7, Windows 8, or Windows 8.1 - Also command line install of files to efi partition uses rufus
[http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html](http://www.eightforums.com/tutorials/15458-uefi-bootable-usb-flash-drive-create-windows.html) 

If you want BIOS/MBR, you need to use Linux tools to erase gpt. Windows in installing in BIOS mode to gpt does not totally erase gpt data and you need another Linux tool fixparts to erase backup gpt table.
      
 FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/) 
            GPT fdisk Tutorial - user srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/) 
    
Use Windows 7 to shrink the NTFS partition and reboot so it can run chkdsk, and create all Linux partitions as logical in one extended partition. The extended counts a one of the 4 allowed primary partitions.

 Install screen shots:
[http://www.ubuntu.com/download/desktop/install-ubuntu-desktop](http://www.ubuntu.com/download/desktop/install-ubuntu-desktop)

---

### Post by tonymoloney on 2016-07-11
Hi Oldfred

Thanks for all that info.

I'll work thru it over the next couple of days and let you know how I go.

Tony

---

### Post by tonymoloney on 2016-07-13
Hi again
Thanks. I've taken your advice and gone all the way back to the start and reinstalled everything. Now it all works!
Tony

---

