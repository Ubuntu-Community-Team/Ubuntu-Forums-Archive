---
title: "GRUB, MBR / Boot Problem"
date: 2006-11-09
forum: Installation &amp; Upgrades
---

### Post by GarethMB on 2006-11-09
Hi,

I had dist-upgrade dapper --> Edgy but, I had a lot of Desktop environments installed as well as a lot of applications, I'm a KDE user so booting was becoming rather slow on a 1.3ghz Celeron. As I had a pretty bad partition table arrangement, I decided that it was time for a fresh edgy install.

However when I try to boot now after a HD install I get something like:

Hard disk boot sector invalid, press H to retry hard disk or any other key for floppy.

If I boot to live CD, and then select boot from first hard disk I can boot fine.


Suggestions?
:-k 
Gareth.

---

### Post by bulldog on 2006-11-09
You can try to```
sudo update-grub
``` to see if it changes some thing.

---

### Post by GarethMB on 2006-11-09
Nope didn't do anything.

---

### Post by Sef on 2006-11-10
Read [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub").

---

### Post by GarethMB on 2006-11-10
> **Sef said:**
> Read [Restore GRUB]("http://doc.gwos.org/index.php/Restore_Grub").
Ubiquity won't let me select to install system files such as / /var /boot or /swap without formating that part of the hard disk. ](*,) 

Any ideas? 

I think this is probably because I didn't assign a /boot partition. (I've never had to before, when did this change and why?)

---

### Post by bulldog on 2006-11-10
Don't think that's the case really,I have a / ,a swap and a /home and it runs fine [after some troubles of course :D ]

---

### Post by GarethMB on 2006-11-10
I've fixed. I've searched some pages and it dawned on me that the drive might not have been flagged as bootable. So I did:

```
sudo aptitude install gparted
``` because QTparted is crap and can't handle flags. Aptitude so I can remove everything. Then I just changed the flag to boot.

Thanks for the input guys.:rolleyes:

---

### Post by lowracer on 2006-11-17
> **GarethMB said:**
> Then I just changed the flag to boot.

Holy cats, that tidbit just fixed my edgy booting problem.  Ubuntuforums rock.

---

### Post by markus36fi on 2007-08-23
> **GarethMB said:**
> I've fixed. I've searched some pages and it dawned on me that the drive might not have been flagged as bootable. So I did:

```
sudo aptitude install gparted
``` because QTparted is crap and can't handle flags. Aptitude so I can remove everything. Then I just changed the flag to boot.

Thanks for the input guys.:rolleyes:


I just wanted to explain this last sentence to guys like me :).

After that gparted install type sudo gparted. Then after the GUI starts select the hard drive from which you want the computer to boot from (for example hda1(root)). Then select "Partition" -> "manage flags" and check the boot box. Then just exit from gparted and reboot your system.

At least this worked with my Feisty. :lolflag:

---

### Post by psusi on 2007-08-23
Wow, that is really strange.  The "boot flag" only has meaning to the msdos MBR boot code.  Grub ignores it.  It sounds like you have a retarded bios that was checking for an active partition for some reason, when all it is supposed to do is check that the sector ends in the 0x55 0xAA signature, and jump to the first instruction.

---

