---
title: "Can't Dual-Boot w/Win7 anymore (UEFI)I"
date: 2014-10-19
forum: Installation &amp; Upgrades
---

### Post by cubdukat1968 on 2014-10-19
I'm not sure what happened, but for the past couple days, I have been able to boot into Ubuntu. It no longer goes into the GRUB menu and boots straight into Win7. 

One other thing I've noticed is that there is not an /EFI folder on my Win7 partition. I'm not entirely sure if it got deleted or whether it was ever there to begin with, but it definitely isn't there now.

Is that something I'm going to need to recreate, and if so, how would I go about that?

I finally got my system set up just how I want it, and I would really like to avoid reinstalling both Ubuntu and Kali Linux in order to get them back. 

I have the Boot Repair DVD, but I am hesitant to use it, because it was responsible for borking my system earlier this year.

---

### Post by TheFu on 2014-10-20
I got patches from MS this week on a dual-boot Win7/Ubuntu Server laptop.  It wasn't using Ubuntu and hadn't in over a month.  The MSFT patches needed a reboot and I was left staring at a GRUB RECOVERY> prompt.

Fortunately, that machine isn't UEFI and boot-repair corrected whatever the issue was ... at least for grub and booting into Win7.  I don't know if Ubuntu works - it really isn't an Ubuntu machine ... have 8 other boxes and about 30 VMs for that already.

So ... I'd say be careful, but try boot repair.  If you like - just use it to post the system data to the web and provide that link back here so someone smarter than me can help with the exact grub-install or grub-update/update-grub command necessary for your specific situation.  Sorry I can't be more helpful bsides a "me too". ;(

---

### Post by oldfred on 2014-10-20
+1 on TheFu's suggestion for just running the summary report from Boot-Repair. 

Usually Boot-Repair works but sometimes it get confused with complicated UEFI/BIOS mixed systems.

       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Penguin360 on 2014-10-20
Not providing any solution here, but I have found that dual-boot on PC with new hardware technology causes more hassle, so I have stopped doing dual-boot. Instead I have a stand-alone Ubuntu PC with VirtualBox installed for Windows OS.

---

### Post by cubdukat1968 on 2014-10-21
I'm going to try Boot Repair later on today. I'm hoping there's a way to back up my original UEFI sed up tup as it stands now, so that if it gets borked I can reinstall it. Admittedly, I'll have to reinstall both Ubuntu and Kali, but at least I'll still have Windows. Unfortunately I don't have enough HD space on any of my externals to do a proper backup of Win7, so if something goes wrong, I'm screwed. 

Earlier this year, I ended up killing both my previous Win7 install and the restore partition trying to get Ubuntu to boot, so needless to say I'm leery of using Boot Repair again...

---

### Post by Vladlenin5000 on 2014-10-21
The suggestion was to use Boot Repair to get its report only.
> (...) just use it to post the system data to the web and provide that link back here (...)

You don't need and this point you shouldn't try the actual repair, the recommended one or any other.

---

### Post by cubdukat1968 on 2014-10-21
My apologies. I misread that.

Here's whar BootInfo had to say:

[http://paste.ubuntu.com/8621999/](http://paste.ubuntu.com/8621999/)

---

### Post by cubdukat1968 on 2014-10-21
One other thing: The boot options for Ubuntu and Kali are available in BIOS when I went to select the USB stick that had Boot-Repair on it. I can boot into both OS's, but Windows Boot Manager no longer brings up GRUB and goes straight into WIndows.

---

### Post by oldfred on 2014-10-22
I think what you call windows boot manager is the UEFI menu.

It looks like your original install was in BIOS mode as you have a grub in the gpt protective MBR. And then you used Boot-Repair to "fix" booting on a system that would not boot ubuntu entry in UEFI. Whether you needed that fix or not is not yet determined. And now other alternatives exist. Also back then grub2's os-prober would not create a correct UEFI boot entry for Windows and only the Boot-Repair entry would work.

The fix that was done was a rename of the Windows efi file, copy grub to be the Windows efi file, and create boot stanza just for the renamed Windows file in 25_custom. Vendors that modified UEFI to only boot Windows then would sill boot the Windows file but it really was grub and you booted to grub menu.

 Boot-Repairs rename copies this /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi
Actual Windows boot file, originally bootmgfw.efi, becomes this:
/EFI/Microsoft/Boot/bkpbootmgfw.efi

But then Windows does an update and copies a new bootmfgw.efi that is the real  Windows file not grub/shim. And now the renamed bkp... file is an old version of bootmfgw.efi that may not work to boot Windows. If you do the undo with Boot-Repair it may restore the older version of bootmfgw.efi from the bkp backup file. And you want to keep the newer version that your Windows update just ran. 

Most systems will boot the hard drive entry from UEFI menu. So instead of renaming bootmfgw.efi we rename the bootx64.efi file which is a hard drive boot entry in the UEFI menu and make it to be a grubx64.efi or shimx64.efi.

Best to do a full backup of the efi partition, it is not large.

I would not run the undo in Boot-Repair that I often suggest. As that may copy back the old bootmfgw.efi and overwrite the newer version from Windows.

I would manually copy grubx64.efi into the /efi/Boot folder and rename bootx64.efi to a backup name and rename grubx64.efi to be bootx64.efi. Then in UEFI boot menu see is you can boot an entry for your hard drive.

run this after booting:
sudo update-grub

If that all works we may want to clean up grub menu, efi partition, and UEFI menu.

---

### Post by cubdukat1968 on 2014-10-22
Yeah, that was a difficult install. As I wrote previously, I tried to install Ubuntu 13.10, but I ended up wiping not only the previous install, but also Asus' restore partition. I used it as a Linux laptop for about four months, and as much as I enjoyed it, I ultimately downloaded a new ISO of Win7 and put it back on there, then I re-installed Trusty and Kali Linux. You were correct when you stated that it looked like I had used Boot Repair on a previous issue. At the time I installed it, Kali wasn't UEFI-friendly, so it wouldn't show up in the boot menu. 

I'm not sure what happened with GRUB that it doesn't show up anymore. The last time the menu worked was the day of Apple's big announcement. I got frustrated with trying to trick Chrome into letting me watch, so I did a normal shutdown and reboot. Ever since then, it refuses to boot to the menu. I thought it might be some kind of divine punishment :)

If I could grab a screenshot of what the menu looks like, you'd see it's a bit of a mess. One entry just loops back in on itself and doesn't go anywhere.

How would you go about accessing the EFI partition? Is that accessible from within either Win7 or Ubuntu?

---

### Post by oldfred on 2014-10-22
Your UEFI is your new BIOS, often f2 or del key, but initial screen should say. If you have fast boot in in UEFI it may be very quick. And if fast boot in UEFI is on (may be separate from Windows fast boot), you may only be able to get back into UEFI with a full power down and reset. Then it may do one normal boot.

Windows does not normally mount efi partition.
In Ubuntu is is mounted via fstab:
UUID=101A-7AF1 [COLOR=#ff0000]   /boot/efi [/COLOR]   vfat    defaults    0    1

And then the folders inside that:
/EFI/Boot
/EFI/Microsoft/Boot
/EFI/ubuntu

So depending on whether you are in your install or booting from Live installer may determine where it is at.

---

