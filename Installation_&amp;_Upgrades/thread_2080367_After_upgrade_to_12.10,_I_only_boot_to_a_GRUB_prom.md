---
title: "After upgrade to 12.10, I only boot to a GRUB prompt (&quot;GRUB4DOS&quot;)"
date: 2012-11-03
forum: Installation &amp; Upgrades
---

### Post by mjpatey on 2012-11-03
Hi, all-
 
I have a Win 7 / Ubuntu dual-boot setup on my laptop, so to simplify things (so I thought!), instead of doing a fresh install of Ubuntu as I prefer to do, I decided to try the upgrade route this time. But let me back up a bit... when creating the dual-boot setup initially, I followed the tutorial at this link:
 
[http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/2/](http://www.linuxbsdos.com/2012/05/17/how-to-dual-boot-ubuntu-12-04-and-windows-7/2/)
 
To summarize the interesting setup succinctly, I used the Windows program recommended in the link (EasyBCD) to add an entry for Ubuntu in Windows 7's bootloader. So when I boot the laptop, I see the Windows bootloader showing the choices of Win7 and Ubuntu. If I choose Ubuntu, it then loads GRUB 2 which has worked perfectly until the upgrade.
 
Now when it gets to GRUB 2, instead of the usual GRUB menu of OS options, I get a GRUB prompt. The screen shows:
[INDENT]GRUB4DOS 0.4.5b 2011-11-27, Mem: 592K/2357M/1408M, End: 35560D
 
[ Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of a device/filename. ]
grub> _
[/INDENT]I've tried poking around a bit, but absolutely don't know my way around this little GRUB environment.
 
Any Ubuntu entry I create in the Windows bootloader app simply links to GRUB 2, which was obviously broken by my upgrade. I'm thinking it's a simple matter of changing the list entry for Ubuntu to its new name, kernel, etc., but I don't know how to do that... and doesn't Ubuntu normally do that on its own during an upgrade?
 
Thanks in advance for any light you may be able to shed!
 
-Mark

---

### Post by oldfred on 2012-11-04
I do not know EasyBCD, you may do better in their forums. 

I think Easy used the grub4dos as that is a Windows version of grub.

Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)


[http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

---

### Post by mjpatey on 2012-11-04
Thank you, oldfred! I should have noticed that GRUB4DOS was a Windows version of GRUB and not our beloved original. :-)

Here' the pastebin link:

[http://paste.ubuntu.com/1333156/](http://paste.ubuntu.com/1333156/)

Again, thanks!

-Mark

---

### Post by darkod on 2012-11-04
You seem to have a working installation of grub2 on the other disk, /dev/sdb. Just go into BIOS and change it so that it boots from the other (second) disk.

You should get a fully working version of ubuntu's grub menu with entries for both ubuntu and win7.

---

### Post by mjpatey on 2012-11-04
Darko,

I will try that right now. Posting from the Live CD... let's see how this works! Thanks!

-Mark

---

### Post by mjpatey on 2012-11-04
Well, the laptop's BIOS settings don't get quite granular enough, unfortunately. It's an "Insyde H2O" BIOS, and when I get into its setup, I see both hard drives listed (they're actually SSDs), but when looking at the boot order, it only lists:

External Device
Optical Drive
Hard Disk
Network Boot

...only one mention of a hard drive, and no way to specify which one. I kept rebooting and trying different F keys, because sometimes there's a separate utility for making a one-time boot drive selection , but I couldn't find one.

Any idea how to specify the second drive in this setup?

---

### Post by mjpatey on 2012-11-04
I just noticed the boot info output doesn't show a boot sector type for the second hard drive... could this be what's causing the BIOS to skip over it in the list of bootable drives?

-Mark

---

### Post by darkod on 2012-11-04
> **mjpatey said:**
> I just noticed the boot info output doesn't show a boot sector type for the second hard drive... could this be what's causing the BIOS to skip over it in the list of bootable drives?

-Mark

No, that's OK. If you look, none of the linux partitions have a boot sector type. And that's only the partition boot sector, not the MBR of the disk. The bootloaders on the MBR are at the top.

The HDD order is usually a separate setting, but it depends on the BIOS. If you can't change it, you will need to decide whether you want to install grub2 to the MBR of /dev/sda.

---

### Post by mjpatey on 2012-11-04
And doing that will hopefully allow me to boot into both OSes... but I seem to remember the reason I installed Ubuntu in this strange way (using a Windows utility to setup and manage booting) was because installing Ubuntu after Win 7 (and thereby using GRUB2 to handle the booting) either caused Windows not to boot, or Windows automatically "repaired" what Ubuntu had done and reverted to its own bootloader, which of course doesn't detect Ubuntu.

Does this sound correct, or do you think I should be OK installing GRUB2 to the MBR of sda?

---

### Post by oldfred on 2012-11-04
I found this which seems to be the same BIOS. But I think they used the UEFI.

Sony Vaio dual UEFI boot with manual copy of files to efi partition
[http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/](http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/)

---

### Post by mjpatey on 2012-11-04
@oldfred-

This looks pretty complex, and maybe hard to manage as time goes on. I miss the simple dual-boot days of yore!

I'm considering just wiping what I have and starting from scratch. If I were to do that, what would you recommend as an approach that would be the most straightforward in the long run? I.e. Ubuntu can be upgraded or re-installed without having to manually edit and copy files, no need to ever deal with GRUB other than its menu, etc.

I'm also considering not using Ubuntu on this laptop at all... the software I most need to run on it is Windows-only, unfortunately. But if it can be done without too much hacking, I'd really like to, and wouldn't mind starting from scratch if that's simpler than hacking around my current setup.

Thanks for your input, and again, your advice is greatly appreciated!

-Mark

---

### Post by mjpatey on 2012-11-05
OK, I revisited the way I originally setup the dual-boot. It turns out oldfred's very first response to my post here led to the simplest answer: check the EasyBCD forums!

I did, and the answer is here:

[http://neosmart.net/forums/showthread.php?t=10801&goto=newpost](http://neosmart.net/forums/showthread.php?t=10801&goto=newpost)

The latest version of the EasyBCD software (Windows bootloader customization app) allowed me to specify a partition to find the upgraded Ubuntu installation. The older version which I had installed was only letting me see the Windows partition, for some reason.

All is well now. Thanks to everyone for your effort and advice!

-Mark

---

### Post by 2defmouze on 2012-11-06
> **mjpatey said:**
> OK, I revisited the way I originally setup the dual-boot. It turns out oldfred's very first response to my post here led to the simplest answer: check the EasyBCD forums!

I did, and the answer is here:

[http://neosmart.net/forums/showthread.php?t=10801&goto=newpost](http://neosmart.net/forums/showthread.php?t=10801&goto=newpost)

The latest version of the EasyBCD software (Windows bootloader customization app) allowed me to specify a partition to find the upgraded Ubuntu installation. The older version which I had installed was only letting me see the Windows partition, for some reason.

All is well now. Thanks to everyone for your effort and advice!

-Mark

Just wanted to drop a thank you for posting the solution here after you found it! Was having the exact same issue on the exact same setup, lol. Everything working great now, thanks again! :)

---

### Post by mjpatey on 2012-11-06
You're very welcome. Glad it worked for you too!

---

