---
title: "My 2TB Hard Drive Wont Boot in Ubuntu 10.04"
date: 2012-06-11
forum: Installation &amp; Upgrades
---

### Post by alexandr frei on 2012-06-11
Hai,

I am Alexander from Indonesia.
I've been stressed out 4 days before to now, because my boss give me 2x2TB Harddrive and ask me to RAID 1 in Ubuntu 10.04.

I created : 
150 MB for reserved BIOS Grub boot OFF
15GB swap area boot OFF
/ 2TB boot on

The Installation went well, until I rebooted the system after installed. My IBM x3400 Server cannot boot from the Ubuntu i've just installed.

Please help me.

---

### Post by darkod on 2012-06-11
Is this hardware raid or software raid?

Also, why don't you use the latest 12.04 LTS version? The 10.04 LTS will be out of support in less than a year.

---

### Post by alexandr frei on 2012-06-11
i already used 12.04 LTS ubuntu server,
but same result, still cannot boot after fresh install.

I tried software Raid in ubuntu.

my Harddrive is IBM Internal Harddrive

---

### Post by darkod on 2012-06-11
OK, so this is a server version? You didn't specify that also.

When it asked you where to install the bootloader, did you select the disk MBR (like /dev/sda, /dev/sdb, etc) or the raid array device? You might be missing the bootloader on the correct place. That would definitely prevent it booting.

You can also try running the boot-repair utility which in most cases can fix bootloader issues. Or just use that utility to create the boot info results and post the link it provides, so we can see more details.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by alexandr frei on 2012-06-11
> **darkod said:**
> OK, so this is a server version? You didn't specify that also.

When it asked you where to install the bootloader, did you select the disk MBR (like /dev/sda, /dev/sdb, etc) or the raid array device? You might be missing the bootloader on the correct place. That would definitely prevent it booting.

You can also try running the boot-repair utility which in most cases can fix bootloader issues. Or just use that utility to create the boot info results and post the link it provides, so we can see more details.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)


i didnt set RAID directly, 
i attached 1 Harddrive 2TB for the first time, because the last time I set software RAID with the both 2TB hard drive didn'n boot also.

How can I set boot loader on /dev/sda ?
I remembered when at finishing the installation of ubuntu server, it asked me to install MBR and i chose yes.

I will try the bootrepair also tommorow. I will update the answer soon, thanks

---

### Post by darkod on 2012-06-11
When was the last time you tried the raid, recently or long time ago?

If you tried long time ago, I think you should try again now. Trying with only one disk will not do much good since you need it to work with raid, not with a single disk.

Try the boot-repair and lets see. I will also do a test in virtual box for this setup and I might find something.

---

### Post by oldfred on 2012-06-11
If you have only one drive, you should not turn RAID on. And if you did it may have written meta-data onto drive that interferes with the install as it will then only install in RAID mode.

If you are sure you do not want RAID, the alternative installer is not a liveCD, so you will also need a liveCD to run these commands:
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

The newer version of Ubuntu automatically converts to gpt with drives somewhat over 1TB, I do not think the old version did that, but if you tried 12.04 first, you may have converted to gpt?

With very large hard drives and  a default install, grub had a bug, where it just seems to get lost when some files may be near the beginning of the drive and others near the end. Often a smaller system partition of 25GB or separate /boot and make the rest of the drive /home or a data partition(s) then works well.

Do you want new gpt or MBR. With 2TB you can use either. Only drives over 2TB have to be gpt.  But with gpt and booting from BIOS have to have a separate 1MB bios_grub partition.

From Boot-Repair post the link it creates when you run the Boot-Info from advanced options.

---

### Post by alexandr frei on 2012-06-12
> **oldfred said:**
> If you have only one drive, you should not turn RAID on. And if you did it may have written meta-data onto drive that interferes with the install as it will then only install in RAID mode.

If you are sure you do not want RAID, the alternative installer is not a liveCD, so you will also need a liveCD to run these commands:
Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

The newer version of Ubuntu automatically converts to gpt with drives somewhat over 1TB, I do not think the old version did that, but if you tried 12.04 first, you may have converted to gpt?

With very large hard drives and  a default install, grub had a bug, where it just seems to get lost when some files may be near the beginning of the drive and others near the end. Often a smaller system partition of 25GB or separate /boot and make the rest of the drive /home or a data partition(s) then works well.

Do you want new gpt or MBR. With 2TB you can use either. Only drives over 2TB have to be gpt.  But with gpt and booting from BIOS have to have a separate 1MB bios_grub partition.

From Boot-Repair post the link it creates when you run the Boot-Info from advanced options.



I know RAID need 2 or more harddrive.
I just want to test where the problem was. Because last time (3 days ago) i tested installing ubuntu server 10.04 with 2x2TB Harddrive attached, won't boot after fresh install.

So I tried with 1 harddrive first with the capacity 2TB, reinstalled ubuntu server 10.04 again and same problem happened . Still cannot boot.

I really dont understand gpt and MBR, where can i see if i use gpt or MBR?

so what should i do next?
what about my partition before?
> 
I created : 
150 MB for reserved BIOS Grub boot OFF
15GB swap area boot OFF
/ 2TB ext4, boot ON


i haven't tested the boot-repair, because now i am not in my office. 3 hours from now i will be there at my office.

---

### Post by darkod on 2012-06-12
One easy way to check for gpt or msdos (mbr) partition table, is with parted. In terminal, from live mode or from an installed system, run:
sudo parted /dev/sda print

That will print data about disk /dev/sda. You can also do it for /dev/sdb, etc.

In the details, towards the top part, it will say if the partition table is gpt or msdos.

If you use gpt the disk will need to have a small partition without any filesystem and with the bios_grub flag set, so that grub2 can install properly. Maybe this is stopping it install correctly. With msdos table you don't need this partition.

---

### Post by alexandr frei on 2012-06-12
> **darkod said:**
> One easy way to check for gpt or msdos (mbr) partition table, is with parted. In terminal, from live mode or from an installed system, run:
sudo parted /dev/sda print

That will print data about disk /dev/sda. You can also do it for /dev/sdb, etc.

In the details, towards the top part, it will say if the partition table is gpt or msdos.

If you use gpt the disk will need to have a small partition without any filesystem and with the bios_grub flag set, so that grub2 can install properly. Maybe this is stopping it install correctly. With msdos table you don't need this partition.


i arrived at my office now, and will try all of your and  oldfred suggestion,
i will update soon

---

### Post by oldfred on 2012-06-12
Some general info on MBR(msdos) & gpt(GUID).

[http://www.wolframalpha.com/input/?i=3TB+in+TiB](http://www.wolframalpha.com/input/?i=3TB+in+TiB)
MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)
[http://en.wikipedia.org/wiki/Extended_boot_record](http://en.wikipedia.org/wiki/Extended_boot_record)

---

### Post by darkod on 2012-06-12
I did a test in virtual box and it worked fine.
What I did:
1. Created two virtual hdds so I can test raid.
2. Booted into live mode with 12.04 desktop live cd (you can use another version also as long as it's the live cd that can boot live mode).
3. Created gpt tables and needed partitions on both disks (I will post examples only for /dev/sda, it's the same for /dev/sdb):
```
sudo parted /dev/sda
unit MiB
mklabel gpt
mkpart P1 1 2
mkpart P2 2 2050
mkpart P3 2050 10240
```

The P? is a label that is used for partitions on disks with gpt table. Note that your start/end numbers will differ when creating your partitions. I chose to work with MiB and that's why I set the units to that.
The P1 small partition is the bios_grub, so it's only 1MiB starting at 1Mib and ending at 2MiB. P2 is for raided swap, P3 for raided root.
4. While still in parted, set the correct flags to all partitions and exit parted:
```
set 1 bios_grub on
set 2 raid on
set 3 raid on
quit
```

5. After that I rebooted with the server cd and started the install process. I selected manual partitioning. Partition P1 on both disks is already set correctly with the bios_grub flag, you don't need to touch it. This partition should be OUTSIDE the array and is NOT raided.
Don't make changes to P2 or P3 also, simply go into Configure Software RAID. The P2 and P3 are already marked as raid and recognized as raid devices. Create the md devices you want, in my case it was /dev/md0 for swap, created from sda2 and sdb2, and /dev/md1 for root created from sda3 and sdb3.

6. After the raid devices show in the partitioner, set to use one as swap area and the other as ext4 with mount point /.

7. That's it. At the end of the installation, grub2 installed itself automatically on both /dev/sda and /dev/sdb without any need for intervention. The system starts fine. I still haven't tested disconnecting one of the virtual hdds.

I attached a screenshot of df -h and of parted. In df -h you can see /dev/md1 mounted as / because swap doesn't show there. The parted print shows you the partitions with the flags, and that the disks are gpt. They are identical on /dev/sdb.

---

### Post by alexandr frei on 2012-06-12
Hello,

I tried Boot Repair yesterday but it didn't work.

until I reformat the HDD then set the Harddrive :

HDD sda :

Primary : 2TB / ext4, Bootable flag OFF, -> Physical volume for RAID
Logical : 15GB swap area, Bootable flag OFF

HDD sdb :

Primary : 2TB / ext4, Bootable flag OFF, -> Physical volume for RAID
Logical : 15GB swap area, Bootable flag OFF


It all went well booting. I guess this is all because Pri/Log set in the beginning label before create new partition. really strange for me.

But, why the boot flag * below only in my sdb HDD ?
how can i set the both HDDs bootable ?


> 

[SIZE=2]Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d7148

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2046    29296639    14647297    5  Extended
/dev/sda2        29296640  3907028991  1938866176   fd  Linux raid autodetect
/dev/sda5            2048    29296639    14647296   82  Linux swap / Solaris

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

[/SIZE][SIZE=2]Device **Boot      **Start         End      Blocks   Id  System
/dev/sda1            2046    29296639    14647297    5  Extended
/dev/sda2        29296640  3907028991  1938866176   fd  Linux raid autodetect
/dev/sda5            2048    29296639    14647296   82  Linux swap / Solaris
[/SIZE]		    
[SIZE=2]Device **Boot      **Start         End      Blocks   Id  System
/dev/sdb1   *        2046    29296639    14647297    5  Extended
/dev/sdb2        29296640  3907028991  1938866176   fd  Linux raid autodetect
/dev/sdb5            2048    29296639    14647296   82  Linux swap / Solaris[/SIZE]



---

### Post by oldfred on 2012-06-12
Boot flag is not used by grub. Windows uses boot flag and a few BIOS will not let you even start booting unless the BIOS sees a boot flag.

---

### Post by alexandr frei on 2012-06-13
> **oldfred said:**
> Boot flag is not used by grub. Windows uses boot flag and a few BIOS will not let you even start booting unless the BIOS sees a boot flag.


If BIOS cannot see the bootflag in my sda drive (RAID), and plug out my sdb drive (RAID), it won't boot ?

how can i set the bootflag also in my sda drive (RAID)?

---

### Post by oldfred on 2012-06-13
I do not know how to do it with RAID. But if you can use parted.

for details see:
man parted
> set partition flag state
                     Change the state of the flag on partition to state.  Sup&#8208;
                     ported  flags  are:  "boot",  "root",  "swap",  "hidden",
                     "raid", "lvm", "lba", and "palo".  state should be either
                     "on" or "off".


parted /dev/sda set 1 boot on

---

### Post by alexandr frei on 2012-06-14
> **oldfred said:**
> I do not know how to do it with RAID. But if you can use parted.

for details see:
man parted


parted /dev/sda set 1 boot on


ok, i reiinstalled and reformated again my 2x2TB harddrive using ubuntu server 10.04.

set primary/logical to both drive :
logical 15 GB for swap area, bootable flag OFF 
primary 2TB GB for RAID, bootable flag ON

and because of primary/logical of HDDs, the partition automatically create Extended partition.


and the boot works!
you can mark this thread SOLVED.

thank you for all your response and helps.

---

### Post by darkod on 2012-06-14
Glad you got it working.

If you go through my post #12 it might give you some ideas for using gpt in future. The install worked right away for me testing in virtual box.

And only you can mark the thread as Solved because it's yours. You can do that in Thread Tools above the first post.

---

