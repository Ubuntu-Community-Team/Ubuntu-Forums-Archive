---
title: "Install 9.10 with WinXP using NTLDR as bootloader"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by chaicl on 2010-01-14
I am new to Ubuntu and Linux in general.

I first installed 9.10 from 9.10 Live CD to my Thinkpad X200 selecting not to install its bootloader thinking I could use NTLDR.  That did not work at all.  Tried bootpart, starting 9.10 from LiveCD to reinstall grup... I gave up and in WinXP, deleted the 9.10 partition and its SWAP partition.

I reinstall 9.10 again into the now freed space.  This time I selected to install the bootloader but to /dev/sda5.  After completing the installation, I rebooted to WinXP and used bootpart to create the necessart ubuntu.bin and instructions in boot.ini.  That did not work.  I went into 9.10 live CD again and use dd command to extract the fir 512bytes from /dev/sda5 and place it in a USB drive as ubuntu.bin.  Rebooted into WinXP and put this new ubuntu.bin into C:\.  All I get when booting into Ubuntu is a blank screen...

have I don;t something stupid somewhere?  Thanks

---

### Post by Geffers on 2010-01-14
> **chaicl said:**
> I am new to Ubuntu and Linux in general.

I first installed 9.10 from 9.10 Live CD to my Thinkpad X200 selecting not to install its bootloader thinking I could use NTLDR.  That did not work at all.  Tried bootpart, starting 9.10 from LiveCD to reinstall grup... I gave up and in WinXP, deleted the 9.10 partition and its SWAP partition.

I reinstall 9.10 again into the now freed space.  This time I selected to install the bootloader but to /dev/sda5.  After completing the installation, I rebooted to WinXP and used bootpart to create the necessart ubuntu.bin and instructions in boot.ini.  That did not work.  I went into 9.10 live CD again and use dd command to extract the fir 512bytes from /dev/sda5 and place it in a USB drive as ubuntu.bin.  Rebooted into WinXP and put this new ubuntu.bin into C:\.  All I get when booting into Ubuntu is a blank screen...

have I don;t something stupid somewhere?  Thanks

I think your problem is the Windows bootloader, I would suggest using GRUB, the Linux bootloader, unfortunately V 9.10 is using a new BETA version and I am not sure of the new commands.

If you do the Ubuntu install and allow it to install GRUB to the main hard drive at boot time you will get a menu allowing you to boot your XP partition.

If you had a problem with GRUB you can always get the original windows boot sector back using fdisk /mbr which, judging by your post, you seem familiar with.

geffers

---

### Post by darkod on 2010-01-14
No offense, but the only stupid thing you did is stubbornly trying to use windows bootloader which doesn't support booting ubuntu (by default).

I recommend to delete the ubuntu partitions again, reinstall again but this time let grub2 install on /dev/sda (the MBR of the hdd) and not the ubuntu partition as last time. This is the default way and it will work straight away, provided your XP boot files are not corrupted.

You could have had your system working long time ago, forget about windows booting linux. At least until MS decides to implement that in windows.

---

### Post by chaicl on 2010-01-14
Thanks for the suggestion.  But afraid I don't want to use Grub as the main bootloader.  My Thinkpad as configured by office has two booth option, WinXP and recovery console.  I want Ubuntu to be the third :-)  Otherwise, I will need to go through two bootloader just to start up my WinXP which is the one that is used 99% of the time...

Regards,

---

### Post by chaicl on 2010-01-14
> **darkod said:**
> No offense, but the only stupid thing you did is stubbornly trying to use windows bootloader which doesn't support booting ubuntu (by default).

I recommend to delete the ubuntu partitions again, reinstall again but this time let grub2 install on /dev/sda (the MBR of the hdd) and not the ubuntu partition as last time. This is the default way and it will work straight away, provided your XP boot files are not corrupted.

You could have had your system working long time ago, forget about windows booting linux. At least until MS decides to implement that in windows.

No offence taken :-)  My issue is that WinXP is the main O/S that I use on my notebook :-) while Ubuntu is my experiment O/S for the moment....

---

### Post by darkod on 2010-01-14
I assume grub2 would also give you option for the recovery console, but I can not tell you that for 100% without even seeing the laptop.

I've seen situation where both the OS and the recovery partition are shown in the grub boot menu and people were even confused why does it show two windows in there.

I don't know how to add this to XP bootloader, and in honesty, that's windows question for a windows forum. You're asking about specifics for a windows bootloader.

---

### Post by chaicl on 2010-01-14
> **darkod said:**
> I assume grub2 would also give you option for the recovery console, but I can not tell you that for 100% without even seeing the laptop.

I've seen situation where both the OS and the recovery partition are shown in the grub boot menu and people were even confused why does it show two windows in there.

I don't know how to add this to XP bootloader, and in honesty, that's windows question for a windows forum. You're asking about specifics for a windows bootloader.

When I looked into the ubuntu.bin that I created using LiveCD, I noticed that it is blank.  Is the procedure to create ubuntu using dd the same for grub2? i.e the first 512bytes of the linux partition?

thanks!

---

### Post by darkod on 2010-01-14
It seems the process changed slightly with grub2. Read here from post #8 onwards:
[http://ubuntuforums.org/showthread.php?t=1304667](http://ubuntuforums.org/showthread.php?t=1304667)

---

### Post by chaicl on 2010-01-14
> **darkod said:**
> It seems the process changed slightly with grub2. Read here from post #8 onwards:
[http://ubuntuforums.org/showthread.php?t=1304667](http://ubuntuforums.org/showthread.php?t=1304667)

I saw this but was quite confused with the steps.  Also it seems to require the installation of GRUB to MBR first and then restoring Windows' NTLDR to the MBR... Not quite sure I am ready to take that plunge yet...

A question on grup2.  When I run the 9.1 LiveCD, grub command is not recognised and ask me to install.  Is that normal?  Is grub2 commands the same as that for grub?

Thanks.

---

### Post by darkod on 2010-01-14
> **chaicl said:**
> I saw this but was quite confused with the steps.  Also it seems to require the installation of GRUB to MBR first and then restoring Windows' NTLDR to the MBR... Not quite sure I am ready to take that plunge yet...

A question on grup2.  When I run the 9.1 LiveCD, grub command is not recognised and ask me to install.  Is that normal?  Is grub2 commands the same as that for grub?

Thanks.

The commands are not always identical, depending on the command itself. And restoring grub1 and grub2 is definitely different. Also for grub1 you need to use 9.04 cd or earlier, and for grub2 9.10 cd.

Plus, when running the live desktop from the live cd, not all commands are available as with a system running from your hdd. Don't forget, you are not actually running a full installation, just a live ubuntu from the cd which is almost identical to the full hdd install, but not 100% identical.

---

### Post by chaicl on 2010-01-14
> **darkod said:**
> The commands are not always identical, depending on the command itself. And restoring grub1 and grub2 is definitely different. Also for grub1 you need to use 9.04 cd or earlier, and for grub2 9.10 cd.

Plus, when running the live desktop from the live cd, not all commands are available as with a system running from your hdd. Don't forget, you are not actually running a full installation, just a live ubuntu from the cd which is almost identical to the full hdd install, but not 100% identical.

So far I have seen many instructions for restoring grub.  But have not been able to positively identify those for grub2 from a Ubuntu 9.10 liveCD.  Right now, my HDD Ubuntu can't be used as I couldn't boot it... Will search around more on this... Thanks!

---

### Post by darkod on 2010-01-14
> **chaicl said:**
> So far I have seen many instructions for restoring grub.  But have not been able to positively identify those for grub2 from a Ubuntu 9.10 liveCD.  Right now, my HDD Ubuntu can't be used as I couldn't boot it... Will search around more on this... Thanks!

I wasn't aware you are looking for that. It's here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Make sure you use the instructions for 9.10 for grub2 and by using 9.10 cd. For grub1 use instructions for 9.04 and 9.04 cd.

---

### Post by Geffers on 2010-01-14
> **chaicl said:**
> Thanks for the suggestion.  But afraid I don't want to use Grub as the main bootloader.  My Thinkpad as configured by office has two booth option, WinXP and recovery console.  I want Ubuntu to be the third :-)  Otherwise, I will need to go through two bootloader just to start up my WinXP which is the one that is used 99% of the time...

Regards,

If your laptop can boot to USB install it to an 8 or 16GB USB key and then at boot time select Boot to USB

This way you can use the XP bootloader unless you want ubuntu.

Geffers

---

### Post by chaicl on 2010-01-15
> **Geffers said:**
> If your laptop can boot to USB install it to an 8 or 16GB USB key and then at boot time select Boot to USB

This way you can use the XP bootloader unless you want ubuntu.

Geffers

Yes, that's another option, but will be slower in access :-)

Will try investigate more on GRUB2 first before going that route.

Thanks!

---

### Post by chaicl on 2010-01-15
Managed to resolve the problem using the sledge hammer way. i.e. 

1.  Delete the Ubuntu partitions from WinXP
2.  Install Ubuntu 9.10 from its live CD to the freed partition
3.  (No change to bootloader i.e. let grub2 modify the MBR
4.  Reboot into the Ubuntu:
    a.  plug in a USB drive
    b.  open a terminal
    c.  #sudo -i
    d.  #mkdir /tmp/USB
    e.  #mount /dev/sdb1 /tmp/USB
    f.  #dd if=/dev/sda of=/tmp/USB/ubuntu.bin bs=512 count=1
5.  Reboot and select WinXP in Grub menu
6.  Download repairmbr and use it to reset the MBR to WinXP's
[http://pcsupport.about.com/od/termsf/p/fixmbr.htm](http://pcsupport.about.com/od/termsf/p/fixmbr.htm)
7.  Copy ubuntu.bin from USB drive to C:\
8.  Edit boot.ini and inset the statement c:\ubuntu.bin="Ubuntu" as the last line.
9.  Reboot and you are back to normal WinXP bootloader with option to boot to Ubuntu!

Thanks to all the help.

---

