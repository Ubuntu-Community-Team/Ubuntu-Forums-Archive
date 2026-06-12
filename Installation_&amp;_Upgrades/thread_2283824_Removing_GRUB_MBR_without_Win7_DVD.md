---
title: "Removing GRUB MBR without Win7 DVD"
date: 2015-06-24
forum: Installation &amp; Upgrades
---

### Post by imrazor on 2015-06-24
I started with a dual boot laptop that could boot into Win7 or Win8. I then bought a mSATA card to install Ubuntu on. In the process of installing Ubuntu, I didn't pay attention and installed GRUB to the default drive, /dev/sda. Now I cannot boot the Win7 drive at all. I tried to follow the steps here:

[http://askubuntu.com/questions/5748/how-to-restore-windows-7-mbr-without-a-cd](http://askubuntu.com/questions/5748/how-to-restore-windows-7-mbr-without-a-cd)

but both suggestions did not work. I did hit upon a workaround. I used a tool called EasyBCD to create a Win7 entry in the Win8 boot menu. So if I tell my BIOS to boot from the Win8 drive, I can then select Win7 and boot it up. However, the GRUB install on my Ubuntu drive refuses to boot Win7 at all. So is there anything else I can try (without a Win7 DVD) to restore the Win7 MBR? Assuming that's the actual problem, of course.

---

### Post by oldfred on 2015-06-24
With two Windows only one typically has boot files, unless you forced it differently.

Best to see details.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by imrazor on 2015-06-24
As requested, here's the pastebin URL.

[http://paste.ubuntu.com/11771558/](http://paste.ubuntu.com/11771558/)

Hmm, would ```
sudo dd if=/dev/sdb of=/dev/sda bs=512 count=1 
```do the trick?

---

### Post by oldfred on 2015-06-25
Did you run a fix with Boot-Repair as it now shows syslinux in the sda MBR. Syslinux works just like Windows in booting.

But if you originally installed grub to sda, it remembers that and will reinstall on a major update.

       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,tab to ok, spacebar to choose/unchoose drive, enter to accept, do not choose partitions

Do not use dd, just use correct repairCD or live installer to install a new boot loader.
      
 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

---

### Post by imrazor on 2015-06-25
Installing Syslinux to sda was suggested in the article I mentioned in my first post. However, the Syslinux MBR seems unable to boot Win7 for some reason. When I attempt to boot Windows 7 with that Syslinux MBR, I get an "inaccessible boot device" message, as if it's missing a controller driver.

When I realized my mistake in installing GRUB to /dev/sda and the OS to /dev/sdc, I formatted the Ubuntu partition and then correctly installed grub to /dev/sdc. That should have wiped out any GRUB config files pointing to /dev/sda. To be sure I ran "dpkg-reconfigure grub-pc" (since I'm using legacy booting/MBRs), and it was pointing to /dev/sdc.

My issue is that I do not have a Windows 7 DVD to attempt a repair with. I was hoping it would be as simple as writing a Win7 MBR to /dev/sda with dd. I can get a Win7 DVD, but it's going to be a major hassle. I was hoping to avoid that.

---

### Post by oldfred on 2015-06-25
If syslinux will not boot it, then I doubt a standard Windows boot loader will. The issue is probably not Windows boot loader but something inside Windows.
If you have working Windows on sdb, use it to run chkdsk on sda's NTFS partitions.

---

