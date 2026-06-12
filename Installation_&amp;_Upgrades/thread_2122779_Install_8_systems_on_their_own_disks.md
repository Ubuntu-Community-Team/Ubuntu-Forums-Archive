---
title: "Install 8 systems on their own disks"
date: 2013-03-06
forum: Installation &amp; Upgrades
---

### Post by Alf Stockton on 2013-03-06
My client needs me to install Ubuntu 12.04 or later on their workstations.
There are 8 workstations each already running Windows 7 and the requirement is to install Ubuntu on its own seperate HDD. ie Each Workstation will therefore have two HDD and would need to be dual bootable(either Linux or Windows).
Would it be possible to do the install, with all the needed applications(including Maya), on one workstation and then use dd if=??????? of=??????? to clone this HDD to the other seven(one HDD at a time)?
Would dual booting still work on all eight?

-- 
Regards,
Alf Stockton                 [www.stockton.co.za](www.stockton.co.za)

---

### Post by darkod on 2013-03-06
It should be possible. I don't like dd since it will copy the partitions with UUIDs, but since all disks are installed in separate machines that should not affect you. You can't put two disks with same UUIDs in the same system.

I prefer copying it with fsarchiver or clonezilla but that would mean editing /etc/fstab after that and reinstalling grub2 since the copied UUID will not match the UUID on the new disk.

So, in this case and for your purpose, dd might be the best option.

---

### Post by prodigy_ on 2013-03-06
I'd use Acronis TrueImage (they give you a 30 day free trial).

---

### Post by darkod on 2013-03-06
Does Acronis support linux fully now, or it's still like earlier that it does sector by sector image? That would take long, you might as well do it with dd.

---

### Post by prodigy_ on 2013-03-06
They added support for ext 4 in [v2011](http://en.wikipedia.org/wiki/Acronis_True_Image#Supported_file_systems).

---

### Post by oldfred on 2013-03-07
I do not know if this is still current. You copy will have the same userID and require change.
 OEM mode so user can add name & password later:
[https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview](https://help.ubuntu.com/community/Ubuntu_OEM_Installer_Overview)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

dd will not be particularly fast is it also copies empty space. So even if install only uses 10GB of a new 1TB drive, it will have to copy 1TB.

---

### Post by Alf Stockton on 2013-03-11
If I do as originally suggested will I still be able to dual boot all machines? Does the boot run from the Ubuntu HDD? If so my question is answered.

---

### Post by oldfred on 2013-03-11
You will have to go into BIOS and change boot order to the second drive on every system.

Ubuntu will be fully on your second hard drive. But from Ubuntu you will have to run this on every system to find the Windows on the other hard drive.

sudo update-grub

Depending on version of Windows be sure to leave Windows as the first drive that BIOS enumerates. 

XP is hard coded to the drive it uses and would have to be changed if not still first. Newer Window seems to be more flexible like Ubuntu in using something like Linux UUIDs so drive order is less important, but keep it first also. Or make sure to plug into a higher port number if SATA. 
Some really old IDE systems may only boot from the primary master in the IDE chain (those with jumpers on hard drive for master & slave). Those IDE with cable select offer BIOS boot options.

---

