---
title: "Ubiquity Crashing In Lucid 3"
date: 2010-03-18
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by danben on 2010-03-18
Ive got a new HP Envy 15 and am trying to get some distribution of Linux running on it.  I made a boot stick out of the Lucid 3 ISO using Unetbootin.  I can run it without much problem, but trying to install it to disk hasn't worked so well.

My setup is as such:  the machine came with 4 partitions, 3 of which I can't remove as long as I still want Windows to work on the machine (which I do as long as its the only functional OS; I plan on removing it as soon as I can).  I removed the fourth partition; it's currently listed as an unallocated block.

The first time through the installer, it crashed at the partition-choosing step with "ubi-partman crashes with error 141".  I got past this by apt-get installing libparted0 and ubiquity.  Now it crashes on the last step, right after confirmation.  The error message isn't very descriptive, and I'm not sure where to look to get more info (if there is any).

I don't have any previous Linux experience, so I'm a little frustrated as I don't know what the next step should be.  All I can think of is to try booting from different ISOs, but that seems like a time-consuming process.  Additionally, other users claim that 10.4 causes less problems on the Envy than 9.10.

Any advice or help would be much appreciated.

Thanks,
Dan

---

### Post by spcwingo on 2010-03-18
Have you tried running it from a terminal emulator to see if you get more informative error messages?  To do that just issue this command from your terminal:

```
ubiquity
```

---

### Post by danben on 2010-03-18
Yep - thought of that right after posting.  I ran ubiquity in debug mode and got the following output (sorry it's so long, but it all looks pretty scary and I can't tell what's relevant and what isn't):

```

r 19 01:45:17 ubuntu ntfsresize: Failed to startup volume: Invalid argument.
Mar 19 01:45:17 ubuntu ntfsresize: ERROR(22): Opening '/dev/mapper/isw_cigaehddaa_RAID-0' as NTFS failed: Invalid argument
Mar 19 01:45:17 ubuntu ntfsresize: The device '/dev/mapper/isw_cigaehddaa_RAID-0' doesn't have a valid NTFS.
Mar 19 01:45:17 ubuntu ntfsresize: Maybe you selected the wrong partition? Or the whole disk instead of a
Mar 19 01:45:17 ubuntu ntfsresize: partition (e.g. /dev/hda, not /dev/hda1)? This error might also occur
Mar 19 01:45:17 ubuntu ntfsresize: if the disk was incorrectly repartitioned (see the ntfsresize FAQ).
Mar 19 01:45:17 ubuntu partman: Error running 'ntfsresize --info'
Mar 19 01:45:18 ubuntu ubiquity[10896]: switched to page partman
Mar 19 01:45:38 ubuntu wpa_supplicant[2299]: CTRL-EVENT-SCAN-RESULTS 
Mar 19 01:45:48 ubuntu ubiquity[10896]: debconffilter_done: ubi-partman (current: ubi-partman)
Mar 19 01:45:48 ubuntu ubiquity[10896]: Step_before = stepPartAdvanced
Mar 19 01:45:48 ubuntu ubiquity[10896]: switched to page usersetup
Mar 19 01:45:57 ubuntu ubiquity[10896]: debconffilter_done: ubi-usersetup (current: ubi-usersetup)
Mar 19 01:45:57 ubuntu ubiquity[10896]: Step_before = stepUserInfo
Mar 19 01:45:57 ubuntu ubiquity[10896]: filtering out /dev/mapper/isw_cigaehddaa_RAID-04 as it is to be formatted.
Mar 19 01:45:57 ubuntu migration-assistant: info: setting ostype from: '/dev/mapper/isw_cigaehddaa_RAID-01:Windows 7 (loader):Windows:chain'
Mar 19 01:45:57 ubuntu migration-assistant: info: got ostype of: 'windowsxp', mountpoint is: '/mnt/migrationassistant'
Mar 19 01:45:57 ubuntu ntfs-3g[15895]: Version 2009.4.4 external FUSE 28
Mar 19 01:45:57 ubuntu ntfs-3g[15895]: Mounted /dev/mapper/isw_cigaehddaa_RAID-01 (Read-Write, label "SYSTEM", NTFS 3.1)
Mar 19 01:45:57 ubuntu ntfs-3g[15895]: Cmdline options: rw,umask=0022,nls=utf8
Mar 19 01:45:57 ubuntu ntfs-3g[15895]: Mount options: rw,nls=utf8,silent,allow_other,nonempty,default_permissions,relatime,fsname=/dev/mapper/isw_cigaehddaa_RAID-01,blkdev,blksize=4096
Error: Could not find the path /mnt/migrationassistant/WINDOWS/system32/config/software
Error: Could not find the path /mnt/migrationassistant/WINNT/system32/config/software
Fatal: Could not find the SOFTWARE registry hive at /mnt/migrationassistant/WINNT/system32/config/software.
Mar 19 01:45:58 ubuntu ntfs-3g[15895]: Unmounting /dev/mapper/isw_cigaehddaa_RAID-01 (SYSTEM)
Mar 19 01:45:58 ubuntu migration-assistant: info: setting ostype from: '/dev/mapper/isw_cigaehddaa_RAID-02:Windows Vista (loader):Windows1:chain'
Mar 19 01:45:58 ubuntu migration-assistant: info: got ostype of: 'windowsxp', mountpoint is: '/mnt/migrationassistant'
Mar 19 01:45:58 ubuntu ntfs-3g[15927]: Version 2009.4.4 external FUSE 28
Mar 19 01:45:58 ubuntu ntfs-3g[15927]: Mounted /dev/mapper/isw_cigaehddaa_RAID-02 (Read-Write, label "", NTFS 3.1)
Mar 19 01:45:58 ubuntu ntfs-3g[15927]: Cmdline options: rw,umask=0022,nls=utf8
Mar 19 01:45:58 ubuntu ntfs-3g[15927]: Mount options: rw,nls=utf8,silent,allow_other,nonempty,default_permissions,relatime,fsname=/dev/mapper/isw_cigaehddaa_RAID-02,blkdev,blksize=4096
profilesdir: /mnt/migrationassistant/Users
profilesdir: /mnt/migrationassistant/Users
Error: Could not find the path /mnt/migrationassistant/Users/Administrator/NTUSER.DAT
Fatal: Could not find the USER registry hive at /mnt/migrationassistant/Users/Administrator/NTUSER.DAT
.Mar 19 01:45:58 ubuntu migration-assistant: error: ma-search-items exited with an error for Administrator.
profilesdir: /mnt/migrationassistant/Users
Mar 19 01:45:59 ubuntu ntfs-3g[15927]: Unmounting /dev/mapper/isw_cigaehddaa_RAID-02 ()
Mar 19 01:45:59 ubuntu migration-assistant: info: setting ostype from: '/dev/mapper/isw_cigaehddaa_RAID-03:Windows Vista (loader):Windows2:chain'
Mar 19 01:45:59 ubuntu migration-assistant: info: got ostype of: 'windowsxp', mountpoint is: '/mnt/migrationassistant'
Mar 19 01:45:59 ubuntu ntfs-3g[15969]: Version 2009.4.4 external FUSE 28
Mar 19 01:45:59 ubuntu ntfs-3g[15969]: Mounted /dev/mapper/isw_cigaehddaa_RAID-03 (Read-Write, label "RECOVERY", NTFS 3.1)
Mar 19 01:45:59 ubuntu ntfs-3g[15969]: Cmdline options: rw,umask=0022,nls=utf8
Mar 19 01:45:59 ubuntu ntfs-3g[15969]: Mount options: rw,nls=utf8,silent,allow_other,nonempty,default_permissions,relatime,fsname=/dev/mapper/isw_cigaehddaa_RAID-03,blkdev,blksize=4096
Error: Could not find the path /mnt/migrationassistant/WINDOWS/system32/config/software
Error: Could not find the path /mnt/migrationassistant/WINNT/system32/config/software
Fatal: Could not find the SOFTWARE registry hive at /mnt/migrationassistant/WINNT/system32/config/software.
Mar 19 01:45:59 ubuntu ntfs-3g[15969]: Unmounting /dev/mapper/isw_cigaehddaa_RAID-03 (RECOVERY)
Mar 19 01:45:59 ubuntu ubiquity[10896]: (10, "migration-assistant/isw_cigaehddaa_RAID-01/users doesn't exist")
Mar 19 01:45:59 ubuntu ubiquity[10896]: switched to page migrationassistant
Mar 19 01:46:01 ubuntu ubiquity[10896]: debconffilter_done: ubi-migrationassistant (current: ubi-migrationassistant)
Mar 19 01:46:01 ubuntu ubiquity[10896]: Step_before = stepMigrationAssistant
Mar 19 01:46:01 ubuntu ubiquity[10896]: switched to page summary
Mar 19 01:46:08 ubuntu ubiquity[10896]: debconffilter_done: ubi-summary (current: ubi-summary)
Mar 19 01:46:08 ubuntu ubiquity[10896]: Step_before = stepReady
Mar 19 01:46:08 ubuntu ubiquity[10896]: progress_loop()
Mar 19 01:46:09 ubuntu ubiquity[10896]: Exception in GTK frontend (invoking crash handler):
Mar 19 01:46:09 ubuntu ubiquity[10896]: Traceback (most recent call last):
Mar 19 01:46:09 ubuntu ubiquity[10896]:   File "/usr/lib/ubiquity/bin/ubiquity", line 468, in <module>
Mar 19 01:46:09 ubuntu ubiquity[10896]:     main(oem_config)
Mar 19 01:46:09 ubuntu ubiquity[10896]:   File "/usr/lib/ubiquity/bin/ubiquity", line 455, in main
Mar 19 01:46:09 ubuntu ubiquity[10896]:     install(query=options.query)
Mar 19 01:46:09 ubuntu ubiquity[10896]:   File "/usr/lib/ubiquity/bin/ubiquity", line 243, in install
Mar 19 01:46:09 ubuntu ubiquity[10896]:     ret = wizard.run()
Mar 19 01:46:09 ubuntu ubiquity[10896]:   File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 498, in run
Mar 19 01:46:09 ubuntu ubiquity[10896]:     self.process_step()
Mar 19 01:46:09 ubuntu ubiquity[10896]:   File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 1098, in process_step
Mar 19 01:46:09 ubuntu ubiquity[10896]:     self.progress_loop()
Mar 19 01:46:09 ubuntu ubiquity[10896]:   File "/usr/lib/ubiquity/ubiquity/frontend/gtk_ui.py", line 937, in progress_loop
Mar 19 01:46:09 ubuntu ubiquity[10896]:     'enable-file-access-from-file-uris', True)
Mar 19 01:46:09 ubuntu ubiquity[10896]: TypeError: object of type `WebKitWebSettings' does not have property `enable-file-access-from-file-uris'
Mar 19 01:46:09 ubuntu ubiquity[10896]: 

```So, my setup is as follows:  the machine came with Windows 7, a System partition, a Recovery partition, and an HP_TOOLS partition on 2 SSD drives with RAID0 (though it may be fake raid, I'm not totally sure how to tell).  I removed the HP_TOOLS partition, but I'm trying to avoid blasting the Windows partitions as my exit plan is to sell the machine if I can't get Linux running.

As you can see from those messages, the Windows partitions are RAID-0[1-3], and RAID-04 is the partition that I'm trying to format and mount as root.  What I don't understand is why its doing anything at all with those other partitions.

One other thing - the error block at the very top (ntfs-resize) was actually happening continuously throughout the configuration steps.

---

### Post by danben on 2010-03-18
Update - I opened up GParted to find that it doesn't seem to recognize any of the existing partitions.  I am able to mount the Windows partition and the System partition through the File Browser, but GParted just shows me both of the SSDs separately (which probably means I do have software raid) and says they are both unallocated.  

The fakeraid guide says 9.10 loads dmraid automatically, so the partitions should show up.  Wouldn't it follow that this would be in 10.4 also?

---

### Post by spcwingo on 2010-03-18
It almost sounds like a bad disk image from the get-go.  I would try formatting the USB boot disk and then downloading and check-summing the downloaded ISO.  Only after doing that would I use unetbootin to recreate the USB boot disk.

---

### Post by VMC on 2010-03-19
> **danben said:**
> ...
The first time through the installer, it crashed at the partition-choosing step with "ubi-partman crashes with error 141". ...

That [***partman***]("https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/535630") crash bug was fixed a week ago. 

Make sure you have the latest [daily-live]("http://cdimage.ubuntu.com/daily-live/current/").

---

### Post by danben on 2010-03-19
Finally got this working - I had to boot from a 9.10 image so that GParted could create the new partition, then booted from a 10.4 image to install.  No grub problems or anything like that.

---

