---
title: "[SOLVED] Installing Ubuntu to an external USB drive hosed RAID 0 XP Install"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by ryanhull76 on 2008-04-02
I've got an XP Pro (SP2) installation on my PC. It's running from a Promise Fasttrak 100 PCI Card.

XP works fine, as it's my work computer. NO problems until I tried to install Ubuntu onto an external USB drive.

I ran this Live CD (I'm actually writing this from the Live CD) and clicked the install icon.

On the Prepare disk space screen, I chose Guided - Use entire disk. Then I clicked on the 320GB WD hard drive radio button as the destination. 

(It's listed as SCSI5 (0,0,0) (sdd) - 320.1 GB etc....

However, there are my 3 other Hard Drives that are part of my RAID0 for XP. They are listed above the 320GB WD Drive, and they all look like this...

SCSI3 (0,0,0) (sda) - 30 GB
SCSI3 (0,1,0) (sdb) - 30 GB
SCSI4 (0,0,0) (sdc) - 30 GB
SCSI5 (0,0,0) (sdd) - 320.1 GB

But I did choose the last one's radio button, since I did not want to hose my XP installation. I still have to have it for work and stuff. I'm just checking ubuntu out for S&G.

So I clicked on the 320GB radio button and then clicked the Forward button in the bottom right of the screen.

Then I entered my name, etblah blah blah and clicked forward and it shows me a list of things it will do, and I clicked "Install"

It appeared to be partitioning the USB drive, formatted it, copied stuff for awhile, and then told me to shutdown and remove the Live CD so it could reboot.

Well, here's where I'm pooched. When it rebooted, I'm getting a GRUB 21 error, and it's just stuck there.

I've even tried to remove the USB drive to see if it will boot back into XP, but no. Nothing. Just that GRUB error. 21 and it halts.

So it looks like Ubuntu installed GRUB on top of my XP boot drives. And from what I've read, linux doesn't like these FakeRaid controllers.

My question is this. How can I remove GRUB from my RAID partition? And did this ubuntu hose my RAID? i.e. did it format my xp install? I would imagine that it should have left it alone, seeing as how I chose the external drive as the install destination.

I've tried to use various boot discs, xp install cd's etc, and I cannot access the RAID partition. The BIOS shows the RAID existing, but can't boot to it, due to the GRUB error 21.

So any help would be appreciated. I'll stick around here and wait for any responses. Perhaps the only way to fix this is to remove / modify GRUB here from this LIVE cd.

Thanks in advance for your assistance. I really need to get this pc back up and running for work.

Ryan

---

### Post by ryanhull76 on 2008-04-02
Also, as a side note. I've dropped to a terminal window on this LIVE CD, and ran...
Sudo fdisk -l

Here's the resulting information. Maybe this will help...

ubuntu@SCITECH-LINUX:~$ sudo fdisk -l

Disk /dev/sda: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf4f2f4f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       10948    87939778+   7  HPFS/NTFS

Disk /dev/sdb: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000201

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 30.0 GB, 30020272128 bytes
255 heads, 63 sectors/track, 3649 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x24e02d8b

Disk /dev/sdc doesn't contain a valid partition table

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000c25c3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       38156   306488038+  83  Linux
/dev/sdd2           38157       38913     6080602+   5  Extended
/dev/sdd5           38157       38913     6080571   82  Linux swap / Solaris
ubuntu@SCITECH-LINUX:~$

---

### Post by dstew on 2008-04-02
> So it looks like Ubuntu installed GRUB on top of my XP boot drives.That appears to be the case. The Ubuntu live CD does not recognize RAIDs, unless you install extra software. The grub boot loader was written to the first sector of track 0 of your first hard disk, which is its default behavior. It seems your RAID setup used non-standard partition tables, which are intact in sdb and sdc, but in sda the partition table now looks "normal" to fdisk, meaning it was de-RAIDed by the grub install.

You will have to try to recover your RAID using whatever RAIDtools you have available. If you have a Windows CD, maybe you can use that. Ubuntu has RAID software. The most user friendly is [mdadm]("http://linux.die.net/man/8/mdadm"), which you can install into a Live CD system using the synaptic package manager. You can install software in the live CD system, just like in a hard disk system, but it disappears when you shut down. The other RAID software is [dmraid]("http://linux.die.net/man/8/dmraid").

If you want to boot your hard-disk Ubuntu, you can probably do that using the grub program on the Live CD, without installing grub to any of your hard disks. Let me know if you want to try that.

---

### Post by ryanhull76 on 2008-04-02
At this point, I just need to get the pc back up and running XP. 

What's the way to just remove GRUB completely? That way I can run WINXP recovery tools to get the XP bootloader reinstalled.

Thanks.

Ryan

---

### Post by dstew on 2008-04-02
You can replace the grub boot loader with the Windows boot loader by using the fixmbr command from the Windows CD Recovery Console. I don't know if this will help you, but at least grub will go away.

---

### Post by ryanhull76 on 2008-04-02
I'll give that a shot and see if ti works. I'll report back when done.

Thanks again. 

Ryan

---

### Post by ryanhull76 on 2008-04-02
WHEW!

OK, I fixed it. Recovered the RAID0 array and am back in XP.

Dear God that was a pain in the ***!

Ok, If anyone else has this issue, the following is what I did to recover the RAID 0 array.

I accessed the Promise fast trak tx2 card's BIOS and noted the sector size, drive order, etc... etc...

I deleted the array. (This actually does not erase the disk, just deletes the MBR and reserve sector that tells the card which drives do what and the order...)

I restarted the pc so that it would write/erase the MBR and reserve sector and went back into the RAID bios. From there I recreated the array, using the values I had noted previously. I set the array to be the primary (boot) and exited to save.

I rebooted the PC with a Windows Setup CD, and hit F6 to add my RAID card drivers. Chose the Promise Fast Trak TX2/TX4 drivers, and continued to load the XP setup.

When it came to the window where it asks if you want to install or repair console, I chose the repair console.

From there it asks which Windows installation you want to use, and I chose #1 (it was the only choice.)

It then logged me in and asked for Administrator password. I typed that in, and Viola'! I had a C:\Windows prompt.

I ran the 2 utilities mentioned by dstew...

fixboot
    Accepted the choices and it ran no problems.

fixmbr

    When I ran this, it told me about a non-standard Master Boot Record, blah blah blah and I told it to go ahead and fix that too.

Done.

Ok, I restarted. Pulled the CD and Floppy out of the drives, and it went right back into my XP installation. Everything works fine, as if this whole dark nightmare never happened.

So thanks to everyone that has helped me out. From here in the forums to the Ubuntu IRC channel and nameless other google search results...

perhaps someday i will attempt to install Ubuntu again.......
Ryan Hull

---

