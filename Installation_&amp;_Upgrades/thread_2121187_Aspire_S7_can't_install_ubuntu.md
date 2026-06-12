---
title: "Aspire S7 can't install ubuntu"
date: 2013-03-01
forum: Installation &amp; Upgrades
---

### Post by Seborreia on 2013-03-01
Hello,

I have been trying to install ubuntu on a recently acquired notebook: Acer Aspire S7. I have followed the instructions on ubuntu website to try and install it but have failed.

I am simply trying to replace windows 8 with ubuntu. I ran the boot-repair and still I haven't had any luck. 

following is some information that could help you help me (and other people): [http://paste.ubuntu.com/5575807/](http://paste.ubuntu.com/5575807/)

Any help is welcome.

Cheers,

Seborreia

---

### Post by oldfred on 2013-03-01
I cannot recommend totally erasing Windows as some computers need Windows to correctly work or fix UEFI. That should not be the case but some have not correctly designed UEFI.

Is this an UltraBook. You are showing /mapper which is RAID (or LVM) and that is usually Intel SRT which is UltraBook. Standard Desktop installer does not have RAID drivers.

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)

            Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)

    
 > Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.

      
 You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

   
       Acer V5-571P-6815 secure boot off worked
[http://ubuntuforums.org/showthread.php?t=2081311](http://ubuntuforums.org/showthread.php?t=2081311)

---

### Post by Seborreia on 2013-03-07
Worked beautifully!! Thank you very much!!

After a couple weeks trying to understand what was going on inside my computer it worked. Yes it is an Ultrabook.

What I did was:

1. Run Ubuntu 12.04.2 LTS on the live USB

2. Enter the commands you gave me on terminal.

3. Reinstalled Ubuntu with partitions for EFI boot, root, and swap

And Voilà!

I removed windows though... If I have any future problems I'll post on this thread :)

Thanks again!! Wooohooo!!

---

### Post by oldfred on 2013-03-07
Glad it worked. :)
You can post solved, but it is a work around currently. See my signature.

---

### Post by Cypher32 on 2013-04-01
I'm sorry to post on this dead thread but how do I enable raid after using those commands I cant boot into windows help!

---

### Post by oldfred on 2013-04-01
I assume it is BIOS/UEFI setting & using the Intel SRT screens to reactivate the SRT.

Others have posted these, Intel SRT should be the same regardless of computer brand:
 Intel SRT - Dell XPS Screen shots of Intel SRT screens & lots of details 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
      
 Dell XPS Intel SRT issue on hibernating post #25
[http://ubuntuforums.org/showthread.php?t=1932965](http://ubuntuforums.org/showthread.php?t=1932965)
Some info on re-instating  details in post #9 Dell 14z
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)

---

### Post by Cypher32 on 2013-04-01
I'm not sure what you mean. All i did was run those commands. Any ideas how to "undo" them.

---

### Post by oldfred on 2013-04-01
No idea what commands you ran.

Did you follow links above on how to enable Intel SRT. They posted some screen shots to help explain it.

---

