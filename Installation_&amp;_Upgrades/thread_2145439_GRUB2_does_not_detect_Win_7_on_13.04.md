---
title: "GRUB2 does not detect Win 7 on 13.04"
date: 2013-05-15
forum: Installation &amp; Upgrades
---

### Post by Kestreln8144 on 2013-05-15
I've installed Ubuntu on a second drive, sdb, and Windows 7 is installed on sda. I put GRUB on sdb, which BIOS boots to.

Problem is, there is no Windows 7 entry in GRUB. Running sudo update-grub gives me this:
```
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.8.0-19-generic
Found initrd image: /boot/initrd.img-3.8.0-19-generic
done
```

I tried running Boot Repair, which placed GRUB on all disks, which is not what I wanted. I used it to repair the MBR on sda, and place it on sdb like I wanted. But there is still no Windows entry.

Here's the most recent pastebin from Boot Repair: [http://paste.ubuntu.com/5667946/](http://paste.ubuntu.com/5667946/)

My PC has UEFI, which I didn't realize it had when I installed Ubuntu. I've since disabled it, and Ubuntu runs fine. I can access my Windows partitions from Ubuntu and they seem fine, as well.

Is there any way to generate a Windows entry without having to do so manually?

---

### Post by oldfred on 2013-05-15
I do not know encryption and if that is part of the issue.

BootInfo report does see the Windows boot files, so I would think os-prober would see them, or did you unencrypt Windows before running BootInfo report.

If nothing else you should be able to add a chain load entry back to the Windows MBR.

       #Add menu entry to 40_custom
gksudo gedit /etc/grub.d/40_custom
#Turn off prober
gksudo gedit /etc/default/grub
#Add this line
GRUB_DISABLE_OS_PROBER=true
#update grub menu
sudo update-grub


 menuentry "Windows on sda (When from sdb) Chainboot" {
set root=(hd1)
chainloader +1
}

When you boot from BIOS that drive is hd0, so even if Windows is sda, from BIOS or grub it will be hd1 not hd0.
If Windows complains you may need this after the set root commmand as BIOS will still have sdb as hd0.


 drivemap -s (hd0) ${root}

---

### Post by Kestreln8144 on 2013-05-15
sda3 is my encrypted storage partition that holds files, but my OS is not encrypted.

After some ill-given advice, I reinstalled Ubuntu on the second drive, so this is where I sit now: [http://paste.ubuntu.com/5668902/](http://paste.ubuntu.com/5668902/)

It still does not see Windows:
```
=================== blkid:
/dev/sda1: LABEL="SYSTEM" UUID="305C371B5C36DAF4" TYPE="ntfs"
/dev/sda2: LABEL="OS" UUID="468CEF828CEF6ABF" TYPE="ntfs"
/dev/sdb1: UUID="7b6d6813-8cdf-4528-b909-26e76d1e0d8c" TYPE="ext4"
/dev/sdb2: UUID="6ef644e4-66e3-4637-9dcb-bb67a902d703" TYPE="ext4"
/dev/sdb3: UUID="a458404f-88b9-4bba-852c-14af851b27e5" TYPE="swap"


1 disks with OS, 1 OS : 1 Linux, 0 MacOS, 0 Windows, 0 unknown type OS.

Windows not detected by os-prober on sda2.
```

I tried your advice nonetheless, but it still doesn't show GRUB on boot. I would probably run Boot Repair again, but frankly I'm too tired by now, so I'll just wait for instructions.

---

### Post by oldfred on 2013-05-15
Are you hibernated in Windows? As now it shows it cannot mount the NTFS partitions and that is why it cannot see any Windows boot files.
Also if NTFS needs chkdsk the Linux NTFS driver will not mount the NTFS to avoid more damage that chkdsk might not be able to fix.

---

### Post by Kestreln8144 on 2013-05-15
No, I wasn't hibernated in Windows. I can't think of anything that might've been using the partitions, unless it was Ubuntu itself. The partitions sometimes show up automatically in the launcher.

I'll run chkdsk and see if it finds anything.

---

### Post by Kestreln8144 on 2013-05-16
Alright. I've slept, I've got my coffee, and I'm ready to work on this again.

I ran chkdsk on my C: partition with no errors. I'm going to boot back into Ubuntu and see if I can't mount the Windows partitions so Boot Repair can read them. If nothing else chainloading should work, since booting to my first drive loads Windows without a problem. But first I'm going to run Boot Repair so GRUB shows up when I boot to the second.

Something I found that might be the issue, in this thread: [http://ubuntuforums.org/showthread.php?t=1758396&p=10815865#post10815865](http://ubuntuforums.org/showthread.php?t=1758396&p=10815865#post10815865)

This poster mentions RAID metadata. I've seen messages is Windows, Boot Repair and even BIOS about RAID. Apparently my system shipped "RAID ready," although it *doesn't* have a RAID. I've always wondered about how to disable and/or remove this RAID nonsense, but it hasn't caused me any real trouble in Windows and I've feared doing something that would sabotage my system.

Would you recommend I follow the steps in that post? There's also the following that I've found in BIOS: Under the menus Storage -> Storage Options it has "SATA Emulation," which is currently set to RAID. The other options are AHCI and IDE. Should I change this? (I can change it back, but I'm not sure if this would damage my systems.)

Thank you for the help. This is very frustrating for me, but may it serve as a useful learning experience. :P

**UPDATE:** I ran Boot Repair so GRUB loads, restarted, and surely enough your earlier solution worked! It boots to Windows. Here is the log: [http://paste.ubuntu.com/5670846/](http://paste.ubuntu.com/5670846/)

It appears to have mounted them this time, but still can't find the OS.

Even though it is working now, I would still like to resolve this issue of my OS not being found. At the very least, I'd like to know if it has to do with this RAID setup on my PC.

---

### Post by oldfred on 2013-05-16
You should not have RAID on in BIOS, the best setting now is AHCI or second choice LBA which may be called large for large block allocation. You also definitely do not want IDE. If you have not used AHCI you have to install drivers in Windows first or it will not boot. Ubuntu usually boots either way.
Normally Ubuntu did not install to a drive with RAID meta-data, but now it is just grub does not install. But if you add drivers to the desktop version you can easily work with RAID systems.

---

### Post by Kestreln8144 on 2013-05-17
> **oldfred said:**
> You should not have RAID on in BIOS, the best setting now is AHCI or second choice LBA which may be called large for large block allocation. You also definitely do not want IDE. If you have not used AHCI you have to install drivers in Windows first or it will not boot. Ubuntu usually boots either way.
Normally Ubuntu did not install to a drive with RAID meta-data, but now it is just grub does not install. But if you add drivers to the desktop version you can easily work with RAID systems.

I've been discussing how to switch to AHCI mode on a Windows 7 forum, since that is a Windows issue.

However, I did discover this by running dmraid -r:
```
/dev/sda: pdc, "pdc_bbhjjee", stripe, ok, 1953124992 sectors, data@ 0
```

So my Windows drive *does* have RAID metadata. Windows won't boot, even after enabling the drivers and changing modes, and I wonder if this is why.

As per the link I posted, I could try removing this metadata, but I don't know if that would prevent Windows from booting, and I wouldn't know how to repair it if it did aside from a factory reset, which I *don't* want to do.

Is there a way I could back up the metadata to replace it if Windows fails to boot afterwards? Maybe with dd?

---

### Post by oldfred on 2013-05-17
I do not know details on RAID meta-data. I think it can easily be recreated as many with the new UEFI Windows systems that are UltraBooks use Intel SRT which has similar RAID meta-data. Users said to get Ubuntu to install they had to remove the meta-data install grub and then restart Intel which worked.

But it is always a good idea to have a full backup of Windows.
       Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710](http://ubuntuforums.org/showthread.php?t=2137439&p=12611710#post12611710)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Was this an UltraBook or were the two drives mirrored before. A few systems are set up that way. We have seen a few systems where they claim 500GB for instance, but user complains they only have 250GB. It turns out drives were mirrored with two 250GB drives in RAID.

---

### Post by Kestreln8144 on 2013-05-17
> **oldfred said:**
> Was this an UltraBook or were the two drives mirrored before. A few systems are set up that way. We have seen a few systems where they claim 500GB for instance, but user complains they only have 250GB. It turns out drives were mirrored with two 250GB drives in RAID.
Strangely enough, this is an HP desktop that came with a *single* drive. (My second drive I installed myself later.) It was advertised as "RAID Ready" even though it didn't come with a RAID array.

That said, I've solved my problem. So, for posterity, I did the following:

Turns out, like [this thread]("http://ubuntuforums.org/showthread.php?t=1758396&p=10815865#post10815865"), it was the RAID metadata on my first drive. I backed up the metadata (just in case removing it prevented me from booting Windows) and saved it to a flash drive:
```
dmraid -D -r
```
That command creates some files in the current directory containing the metadata. [dmraid(8)]("http://linux.die.net/man/8/dmraid") explains that as well as how to "repair" it if needed.

Then I did the following from my Linux installation on the second drive:
```
dmraid -an
dmraid -si
dmraid -E -r
update-grub
```

GRUB was finally able to see my Windows installation, and Windows still boots.

An important note/disclaimer: My drive was apparently set up to be RAID 0, or a striped array. Since it was only *one* drive, it obviously wasn't striped, so from what I read it was safe to do this. **Had it come as an *actual* RAID array, it wouldn't have been so simple.** Furthermore, I don't know if it would be safe to do with other kinds of arrays. So let the next person with this problem beware.

Thank you for your help oldfred, I appreciate it.

---

### Post by oldfred on 2013-05-17
Glad you got the issues resolved. :)

---

