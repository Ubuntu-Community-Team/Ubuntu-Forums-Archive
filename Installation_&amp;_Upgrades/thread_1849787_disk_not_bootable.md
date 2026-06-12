---
title: "disk not bootable?"
date: 2011-09-25
forum: Installation &amp; Upgrades
---

### Post by aarsalankhalid on 2011-09-25
I had a single hard drive in my PC with Windows 7 on it. Then I got another Hard Drive for ubuntu. Now I have removed windows hard disk and my PC says that it can't find any bootable disk. Is there something that needs be done with the ubuntu hard drive?

---

### Post by MG&amp;TL on 2011-09-25
Have you installed Ubuntu on said hard disk? Sorry, v.simple question, but I've done this myself.

---

### Post by aarsalankhalid on 2011-09-25
> **MG&TL said:**
> Have you installed Ubuntu on said hard disk? Sorry, v.simple question, but I've done this myself.
yes, ubuntu is on the only hard drive which is now in my PC.

---

### Post by MG&amp;TL on 2011-09-25
So you've:

1. Inserted new disk.

2. Booted from CD/USB.

3. Installed onto hard disk.

4. Installed successfully with no errors.

5. Removed CD/USB.

6. Rebooted.

And you get a system beep and a BIOS error like : found no boot device?

I'm just checking to see if I've got the story right. Try schecking to see if IDE/SATA cable hasn't come undone, and that the power lead for hard disk is in.

If there WAS two, and now there's only one, the MBR will probably be on the other disk.

---

### Post by aarsalankhalid on 2011-09-25
It's like this:
1. I had Windows 7 on disk A
2. I got a disk B, installed ubuntu on it (dual boot)
3. Disk A is no longer available, it had to be removed.
4. Ever since Disk A was removed, rebooting the system produces "No bootable disk found"
5. All the cables and connections are working

And now I booted the system from a live USB and it's loading the Disk B just fine. 
So your theory is MBR (master boot record?) is on other disk? But I don't have that disk any more. So do I have to do a clean installation again? I've been using ubuntu for a while now and I would prefer not to install clean. Can't I somehow repair it or write MBR on this disk?

---

### Post by MG&amp;TL on 2011-09-25
Right:

1. Remove all other hard disks from machine.

2. Install (via USB) Ubuntu onto Hard Disk.

3. Reboot. Done.

The MBR, as I understand it, tells GRUB (the bootloader) where to go, and where the partitions are. If there is no MBR on the hard disk(s) that you install Linux on (i.e. a new hard disk) it SHOULD write the MBR.

If BIOS can't find an MBR, it fails. Installing Ubuntu again should work. :)

Your problem was that the MBR was on the windows HDD, then you removed it. BIOS didn't know where to go.

---

### Post by Awareness on 2011-09-25
follow the chroot tutorial to install grub2 in mbr with a live cd... it has fixed it to me so many times ;)
[https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2#ChRoot](https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2#ChRoot)

---

### Post by andlinux on 2011-09-25
Also take a look in your BIOS, there you can select what hard drive is your first drive that will boot. It's possible that your BIOS selected something else to start off.

---

### Post by Hakunka-Matata on 2011-09-25
+1 on Awareness' post# 7 advice, shouldn't be a problem.

---

### Post by oldfred on 2011-09-27
A few BIOS (mostly Intel motherboards) will not even let the boot process start unless there is a boot flag on a primary partition. Grub does not use a boot flag and one would not normally be set. 

If an Intel motherboard add a boot flag to any primary partition.

If not post this from liveCD:
Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

