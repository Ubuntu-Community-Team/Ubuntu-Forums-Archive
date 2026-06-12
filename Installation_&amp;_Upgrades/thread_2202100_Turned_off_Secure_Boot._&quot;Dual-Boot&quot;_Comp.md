---
title: "Turned off Secure Boot. &quot;Dual-Boot&quot; Computer will not boot now."
date: 2014-01-27
forum: Installation &amp; Upgrades
---

### Post by Odyssey1942 on 2014-01-27
This is a revolting development. I have a dual (I thought) boot, with 12.04 on a SSD drive, with Win 8 on HDD.

Preparatory to other work to be done, and under guidance, I went into UEFI to turn off Fast Boot and Secure Boot. Fast Boot was already off, and I turned off Secure Boot. Upon exit, and confirmation, it went to the grub loader and I selected Win 8. Then nothing, just a dark screen.

Did hard shut down, and this time selected 12.04. Same result.

Went back into UEFI and turned Secure Boot back on. Will now boot into 12.04, but not Win 8. I have made lots of changes to the computer since installing the SSD and 12.04 over the last couple of weeks without going into Win 8, so am unsure when Win 8 stopped loading (TBH, not entirely sure I ever checked it).Turned off Secure Boot. Computer will not boot now.

How do I get the computer to dual boot with Secure Boot turned off? Thanks.

---

### Post by oldfred on 2014-01-27
There is a bug in newer grub where you cannot boot Windows from grub when secure boot is on. 
But you should be able to boot directly from UEFI menu or one time boot key.

       Unable to chainload Windows 8 with Secure Boot enabled  Also post #11 on using refind
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091464)

Boot-Repair cannot fix Windows issues, you need Windows repair flash drive for most of that. But we can see how you are configured. Do you have separate efi partitions on each drive, so each drive can boot without other?

      
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by Odyssey1942 on 2014-01-27
Good morning Fred,

When "Boot-Info" strarts up, a message comes up that says EFI detected, so I conclude yes on 12.04. 

This is a "stock" HP computer with Win 8 pre-installed, and other than mentioned in the OP, I haven't changed anything. How do I find out if present on Win 8? 

Boot- Info:

[http://paste.ubuntu.com/6827366/](http://paste.ubuntu.com/6827366/)

---

### Post by oldfred on 2014-01-27
It looks like both installs are totally separate or Ubuntu has its own efi partition on sdb.

Can you not directly boot Windows from UEFI menu? It should work with either secure boot on or off. If not those are Windows issues unrelated to grub & Ubuntu.

Entries in grub menu are the old BIOS type and will never boot Windows in UEFI mode. That bug has been fixed only in 13.10 and should be in the 12.04.4 in a couple of weeks.

---

### Post by Odyssey1942 on 2014-01-27
Yes, that worked perfectly, if a bit clunky. Thanks for sorting me out on that.

You mentioned that a fix for this will be included in 12.04 in a couple of weeks. Will that be part of one of the periodic updates, or should one re-install when that version comes out?

What version # will it have, or otherwise how does one identify it separately from the current version? IOW, how does one find it if not part of the pushed updates?

You are pretty familiar with my setup now with the links, etc. If one does re-install, would all of the software installed after the initial installation need to be re-installed, or will some or all of it persevere?

---

### Post by oldfred on 2014-01-27
Not sure if it will be part of a regular update, or you need the enablement stack? Check release notes when it comes out.
 LTS Enablement Stack 12.04.2
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#LTS_Hardware_Enablement_Stack](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop#LTS_Hardware_Enablement_Stack)

I have 12.04 and it says it is 12.04.3. Some posting already say 12.04.4, but it is not.
And since I did not enable the new enablement stack I have the old kernel.

You should also have a one time boot key which is a bit easier than going into UEFI.
And Boot-Repair can add correct Windows entries, but do not let it run the 'buggy' UEFI backup & rename.
Or you can manually add entries to 40_custom. Examples in bug report.
       grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
grub2's os-prober creates wrong style (BIOS) chain boot entry Fixed with 13.10
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)

    
With a total new install, with a separate /home your settings are preserved, but not any hardware changes you may have made that are in /etc. And you need to separately export a list of installed applications. Then you can easier reinstall all software you may have added, if from repository.

My backup is to do a new clean install.
 Oldfred's list of stuff to backup May 2011:
[http://ubuntuforums.org/showthread.php?t=1748541](http://ubuntuforums.org/showthread.php?t=1748541)

---

