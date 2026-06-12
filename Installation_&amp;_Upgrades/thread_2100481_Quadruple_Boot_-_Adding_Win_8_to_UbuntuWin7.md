---
title: "Quadruple Boot - Adding Win 8 to Ubuntu/Win7"
date: 2013-01-01
forum: Installation &amp; Upgrades
---

### Post by Phil Riegle on 2013-01-01
Hello Folks,
I've tried to make sense of all the info but need to ask for help first instead of just doing it and solving problems later.
Am wanting to add a new partition of Windows 8. I already boot into a GRUB screen for Ubuntu 12.04 and Windows 7. After choosing Win 7 I have choice of a new Win 7 and an old Win 7.
 
It would appear the correct procedure is to use the GPartition tool to crreate a new Win 8 partition and install to that? I think the advice is then to boot into Win 8 a couple of times to let it sort itself out. After that it seems I will have to redo the GRUB to restore the boot to Linux.
 
Not quite sure about the EUFI stuff. I assume that I have a standard BIOS and therefore must do a standard BIOS install of Win 8?
 
Do I have the procedure correct? Thanks for the help in this forum.
Cheers,
Phil R.

---

### Post by oldfred on 2013-01-01
Windows works best from primary partition. But it has to boot from a primary partition formated NTFS with the boot flag or active partition. Second installs will put its boot files into the active partition.

While Vista, still how Windows works.
       To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

    
This also applies if dual booting two copies of Windows.
       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by Phil Riegle on 2013-01-02
Thanks Fred. I've started reading from the UK website and will continue to read and try to decide what to do.:popcorn:
One question: Where will the Win 8 boot from - Grub or Windows booter?

---

### Post by oldfred on 2013-01-03
Grub will only find one Windows partition with the boot files. Windows then will have in the BCD all the other Windows and give you the option to boot them.

If you separately install each copy of Windows to a primary NTFS partition and move boot flag or active partition, then it will have its own boot files. You will not be able to multi-boot from Windows but grub will find boot files in the new & old Windows install and let you directly boot them.

Are you installing all these systems to one drive? Usually once you want this many systems you start adding a drive or two to help keep each separate.

---

### Post by Phil Riegle on 2013-01-03
> **oldfred said:**
> Windows works best from primary partition. But it has to boot from a primary partition formated NTFS with the boot flag or active partition. Second installs will put its boot files into the active partition.
 
While Vista, it still shows how Windows works.
[SIZE=3][COLOR=red]**> [SIZE=3][COLOR=red][B]To get each MS to have its own boot loader**[/COLOR][/SIZE][/B][/COLOR][/SIZE] make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
 
 

 
How does it help for the new Win8 to have its own bootloader? Which Boot loader will get us to this partition?

---

### Post by oldfred on 2013-01-03
Windows has two sets of boot files. One for XP and the other for Vista/7/8. When you install all your Windows with one active partition all the bootmgr & BCD are in one boot partition. Or the last install overwrites all the others and you will not even see bootmgr or BCD in the second or later installs. Grub2's os-prober looks for those files in a partition to know to jump/chain to that PBR to boot, so it normally only finds one set to chain load to.

       Windows Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe

---

