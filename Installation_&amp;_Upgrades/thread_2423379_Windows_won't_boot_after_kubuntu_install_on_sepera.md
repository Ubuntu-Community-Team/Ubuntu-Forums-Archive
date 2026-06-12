---
title: "Windows won't boot after kubuntu install on seperate hard drive"
date: 2019-07-22
forum: Installation &amp; Upgrades
---

### Post by gbru316 on 2019-07-22
Windows 10 is installed on 1 hard drive, Kubuntu on another. I tried running boot-repair, output in link below.


[http://paste.ubuntu.com/p/fkH56Ht9Bb/](http://paste.ubuntu.com/p/fkH56Ht9Bb/)


I tried all the options I was provided for booting windows (after boot-repair) from GRUB, no dice.

---

### Post by oldfred on 2019-07-22
Grub only boots working Windows. Or Windows that is not hibernated. Fast start up sets hibernation flag. From report:
>         Metadata kept in Windows cache, refused to mount.
Falling back to read-only mount because the NTFS partition is in an
unsafe state. Please resume and shutdown Windows fully (no hibernation
or fast restarting.)
Could not mount read-write, trying read-only
Windows is hibernated, refused to mount. 
    

       Fast Start up off (always on hibernation), note that Windows turns this back on with updates
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)

You should always be able to directly boot Windows from UEFI boot menu, the same key you use to boot Ubuntu live installer often f10 or f12.

Report shows this.
>        
 /dev/sde1 ends after the last sector of /dev/sde 
    But that looks like just an entry in the gpt protective MBR where the MBR entry is to flag drive is really gpt, so old partition tools do not see drive as unpartitioned.

       
 Use gdisk and verify partitions are correct with p, or v to review issues,  and use w to write the partition table. If not correct just use q to quit. That should update primary, backup & protective MBR. 
      
 sudo gdisk /dev/sde
Command (? for help): 
    
Details:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)
[http://askubuntu.com/questions/446991/gparted-claims-whole-hard-drive-is-unallocated-and-gives-warning-about-gpt-table](http://askubuntu.com/questions/446991/gparted-claims-whole-hard-drive-is-unallocated-and-gives-warning-about-gpt-table)

---

