---
title: "Clarifications Please for Dual Boot on Windows 8 Pre-installed Laptops"
date: 2012-11-28
forum: Installation &amp; Upgrades
---

### Post by teastman on 2012-11-28
Thanks to "OldFred" and others I think I almost have this nailed down.  I just have a couple other questions to sweep out of the way. These UEFI and GPT disks don't behave like the dual boot scenario of the MBR days hence my confusion.

Given feedback from other posts we see the 12.10 64bit ISO boots and installs with UEFI toggled on in system setup. SecureBoot needs to be off it seems. So far so good.

Pre-installed Windows 8 Laptop for a Dual Boot - yes there are many posts on this but I am missing just a couple minor points.

Here's where I am befuddled;
Leaving the pre-installed Windows 8 partitions in place (but making room for Linux installation), what would be the recommended partition scenario for the Linux install?
How big to make /home, /, /boot(needed?) 
What other Linux partitions would be recommended in a pre-installed windows8 laptop scenario?

Does the Linux install routine in the UEFI scenario make use of the Windows8 EFI (ESP) partition to write Grub information or do we tell install to write this information in one of the partitions we created? 

Does the Windows Boot Loader point to Grub now or is that Grub info somehow get written to the UEFI system setup? 
How do we set the default OS and timeout (as in grub.cfg days).

Thanks in advance!
tje

---

### Post by oldfred on 2012-11-28
oldfred is back, you also may want opinions from others also. Everyone has an opinion on best partitioning and it really depends on what you want to do with system.

Use Windows to shrink Windows & reboot several times so it can run chkdsk or make other repairs to recognize its new size. Make backups and a repairUSB. With Windows 8 a repair USB has to be FAT32 to give a UEFI boot.

I do not recommend separate /boot, but we have seen some installs where grub seems to get lost. Have not seen the issue with Windows 8 yet. Not sure if issue is a BIOS/UEFI setting issue or just grub cannot find all its files when a / (root) partition is very large or very far into a large drive. I normally have 25GB / partitions with all data in other partitions. 

Ubuntu 12.10 with Grub2 2.00  has the capability to install to secure boot systems. Some have worked, a few have issues and turning secure boot often then works. A few systems have bugs in the UEFI that cannot be worked around, yet.
Grub installs a efi boot loader into the efi partition. Only one efi partition is allowed per hard drive, so both Windows & others are in the same efi partition. Someone posted a multi-boot UEFI system with other boot loaders also

I prefer separate system and data partitions. Both for Windows & Linux. Whether you have a separate /home is another question. For new users I usually suggest a separate /home. For those willing to partition and add a few mount commands to fstab separate data partitions may be appropriate in addition or in place of /home as a separate partition.

I also strongly suggest a separate NTFS data partition with Windows 8. Best to only set the Windows system partition ( c: drive not boot) as read-only.

       WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

You will need Boot-Repair to add a correct Windows boot stanza to boot Windows. The current os-prober only creates BIOS type Windows boot not the new efi boot stanza.  Or you can manually add a boot stanza to 40_custom

---

### Post by YannBuntu on 2012-11-29
Hello
Concerning partitioning, you will find the basics here: [https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

The Ubuntu installer should use the existing EFI partition (as long as you used a recent 64bit disk). See the first paragraph of [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) for an easy approach.

---

### Post by teastman on 2012-12-01
OldFred and Yann. Thank you so much for your clarifications. I am out hunting for two more days and the laptop is home hence my lack of response. I have repartitioned the extra space with gparted (latest flavor). I will post later on the install. Other than this little droid I don't have access to the net.

Thank you both for your replies.

---

### Post by teastman on 2012-12-03
As always - OldFred and YannBuntu - you guys came through once again. Install was with the kubuntu-12.10-desktop-amd64.iso Since the partitions were created ahead of time with Gparted 0.14.0-1 things went pretty flawless as far as install.
The only hitch I had was Boot Repair did not like my EFI and I was told (by Boot Repair) to download the ubuntu 12.10 remix 64bit flavor and run Boot Repair from that. I was concerned when that ISO would not boot without switching my boot from UEFI to Legacy. Didn't have to do that with the kubuntu-12.10-desktop-amd64. But the Boot Repair didn't either. After that dual boot to windows and Kubuntu took right off. I have "Ubuntu" in my bootup menu instead of Kubuntu but who gives a rat's hindquarters. It works and the install went flawless.

You guys are awesome - thanks for patrolling these forums and thanks for all your help!

---

### Post by YannBuntu on 2012-12-03
You're welcome :)  You can use the Thread Tools to mark this one [SOLVED].

---

### Post by oldfred on 2012-12-03
Someone did file a bug on the name issue as he was dual booting flavors of Ubuntu and wanted the different names.  

You may be able to just change name in efi files, but that would be an experiment.

Someone also post this with his UEFI:

> Enter your UEFI menu, select "Boot maintenance manager", then "Boot options", then "Add boot option", then "NO VOLUME LABEL,....Primary,Slave...1, GPT,..", then browse the /EFI/ubuntu/ folder via the UEFI boot menu, and select the grubx64.efi . Give it the name you want (eg "Precise"), then "Commit Changes and exit", then Enter. 

    

---

