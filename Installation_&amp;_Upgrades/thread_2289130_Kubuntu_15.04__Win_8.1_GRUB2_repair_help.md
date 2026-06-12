---
title: "Kubuntu 15.04 / Win 8.1 GRUB2 repair help"
date: 2015-08-01
forum: Installation &amp; Upgrades
---

### Post by brohan76 on 2015-08-01
Hello, and thank you for taking a look at this post.  I have an HP ENVY dv7, from my recollection this is one of the earlier systems with UEFI.  I have had dual boot with the original Windows 8 and Kubuntu on for about 2 years now, and everything has worked well.

A few days ago I booted into Windows (which is now 8.1), shut down my system, and tried to reboot into kubuntu. When I did so I had to enter some kind of boot menu that was not GRUB, where it lists a Windows Boot manager, then Ubuntu, and a few other options. When I select Ubuntu, I immediately get dumped out to grub_rescue.  I have tried to repair this with Boot-Repair via a liveUSB, with no luck, Boot-Repair asks me to enable a grub-UEFI repo on my target.  The summary of running the Boot-Repair BootInfo link is below.

In my system BIOS it has an option to turn off UEFI, which I have chosen to do. I'm not certain if it really does this, however in the BIOS it gives me boot order options for UEFI and legacy FWIW.

What are the best steps to take to repair my system. I can boot into Windows just fine. Kubuntu appears to still be available. I have done a full backup of my home directory in my Kubuntu setup.

Thank you again.


Boot-Repair BootInfo Summary:
[http://paste.ubuntu.com/11980205/](http://paste.ubuntu.com/11980205/)

---

### Post by oldfred on 2015-08-01
I am seeing bits of Rescatux in your Windows partition?
I have only seen that used from an external device DVD or flash drive.

I also see burg. I did not even think that worked any more and did not work with UEFI. It has not been maintained for ages.  It also looks like burg added BIOS Windows boot entries to grub menu which will not work. You need the UEFI chain entry into the ESP-efi system partition.

If you want a gui boot with UEFI look into rEFInd. It also is another of the several work arounds for systems like HP that only want to boot Windows.

Both Windows & Ubuntu are in UEFI boot mode, but you have installed a copy of grub2's BIOS boot loader in the gpt protective MBR. Do not change from UEFI boot and only boot in UEFI mode. The grub in the MBR will not work anyway.

HP with UEFI has modified UEFI to boot by description and only valid description was "Windows". That is not per UEFI standard.
But we have many work arounds. Most dual booting use the hard drive default boot which is /EFI/Boot/bootx64.efi. That file is often just a copy of the Windows efi boot file, but we back it up and copy shimx64.efi or grubx64.efi into /EFI/Boot and rename to bootx64.efi. Then the hard drive boot entry will boot grub/Ubuntu.

I would remove the rescatux in Windows, not sure how you have that installed or configured.
I would remove burg as it does not work with UEFI.
I would copy grub & shim into /EFI/Boot and rename one of them to bootx64.efi.
You may have to add a hard drive boot entry to use bootx64.efi with efibootmgr.

I would also make sure Windows fast start up is off. You have left it on, so the Linux NTFS driver cannot see the NTFS partition as it is hibernated.
       Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

If you need details on copying grub to /EFI/Boot they are in link in my signature or I can post more details after you have cleaned up some of the other issues.

Ohter HP's
 HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
      
 HP Envy 700-430QE desktop used bcdedit to dual boot
[URL="http://ubuntuforums.org/showthread.php?t=2260681"]http://ubuntuforums.org/showthread.php?t=2260681
[/URL]
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi
[URL="http://forums.linuxmint.com/viewtopic.php?f=46&t=164076"]http://forums.linuxmint.com/viewtopic.php?f=46&t=164076

http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working[/URL][URL="http://ubuntuforums.org/showthread.php?t=2260681"]
[/URL]

---

### Post by brohan76 on 2015-08-01
Thank you oldfred for the help.

I am very unfamiliar with the booting / grub etc.  Do you have any place you can point me for removing burg and the rescatux?  I will turn off Windows fast start right away.

---

### Post by oldfred on 2015-08-01
Did Boot-Repair's script just pick up a rescatux ISO in your Windows install or is it more than that?
If just in Windows as an ISO, you can keep it, but I normally have all ISO in an ISO subfolder.

Not sure about burg. How did you install it? It is not in repository, so not as easy to uninstall.
I might try Boot-Repair's advanced mode to fully uninstall grub & reinstall grub (be sure to be in UEFI mode). And in the middle of that see if you can also uninstall burg. But it may have added files & settings in various places like grub does.

---

### Post by brohan76 on 2015-08-01
I have disable the fast start-up.  The Rescatux iso was on my windows partition to try and use it, however I was never able to get it to work as a bootable usb.  I don't know how, or even if it's possible to boot into my installed kubuntu, so I have been using a liveUSB for everything but looking at windows settings.  I believe I installed burg shortly after I dual booted windows in an attempt for a dual boot gui, never did get it to work. While I don't mind the GRUB menu (text of kubuntu, recovery, and then all the old installed kernels), I would like to try rEFIND.

In my BIOS should I enable the UEFI again?

---

### Post by brohan76 on 2015-08-01
I need to clarify:

My BIOs allows for "Legacy mode" which turns Secure Boot off, and then allows me to specify what boot order for legacy and secure boot. If I disable legacy, then Secure Boot is on, and I may change only that boot order. I have legacy boot enabled. What do you recommend I do with the BIOS?

---

### Post by oldfred on 2015-08-01
There should be three ways. UEFI with secure boot, UEFI and CSM/Legacy/BIOS. Some have several switches and others combine them. If in BIOS mode secure boot is always off.
But Microsoft required vendors to allow users to turn off secure boot but boot in UEFI mode.

But one user posted this:
 HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)

But then be sure to boot in UEFI mode. I think it should try that first and only if it fails try BIOS mode. But with burg in MBR it may try that, which is a BIOS only boot?

I have not tried rEFInd, but it is on the list of things to try.

---

### Post by brohan76 on 2015-08-01
Thank you for your patience and help.

I didn't realize there is a difference with UEFI and Secure boot.  In trying to be preemptive here is what I get when I run efibootmgr, again while running in a liveUSB:

[http://paste.ubuntu.com/11982912/](http://paste.ubuntu.com/11982912/)

---

### Post by brohan76 on 2015-08-01
I removed the rescatux.iso instances from the windows partition, and reran the summary, which can be found here:
[http://paste.ubuntu.com/11983089/](http://paste.ubuntu.com/11983089/)

I didn't see how to remove GRUB from the boot-repair.

---

### Post by yancek on 2015-08-01
You still have Grub code in the MBR per the boot repair output which, as I understand, should not be there if you are using UEFI and you do have an EFI partition. 
It still shows Burg files on the Ubuntu partition with no sign of the /boot/grub files?  The bottom two paragraphs show an option to try to repair and indicate that you selected not to do this.  I don't use UEFI myself so you might wait for oldfred or someone more knowledgeable to post.

---

### Post by brohan76 on 2015-08-01
Correct, Once I removed the rescatux, I wanted to rerun the summary to verify that the iso on windows was the reason that it was showing, without making any changes.

---

### Post by oldfred on 2015-08-01
There is no easy way to remove grub from gpt partitioned drive's protective MBR. But it is not used except for BIOS boot so what is in there does not matter. Just do not try to boot in BIOS mode.

It can be erased with dd, but dd's nickname is Data Destroyer and I try not to use it. Any typo and you may lose a lot of data.

---

### Post by brohan76 on 2015-08-02
What do you recommend as my next step?

---

### Post by oldfred on 2015-08-02
If you have removed burg, I would use Boot-Repair's total uninstall/reinstall of grub. It is in advanced repairs.
Look in grub options and check purge grub before reinstalling. If you do not want or need secure boot un-tick that option. But go thru all the tabs for what it can do.

---

### Post by brohan76 on 2015-08-02
Will do.  I am trying to find help on uninstalling BURG, the threads I am finding all assume that you can boot into your existing system to do so, and some even recommend doing so via Boot-Repair.  I am unfamiliar how to do this while using a LiveUSB.  Do you know of any resources that would shed light on using LiveUSB to do so (be able to possibly purge a package on the system while on liveUSB).

Also I did find the Purge GRUB before reinstalling option in Boot-Repair, for me it is automatically selected, and it grayed out so that it can not be unselected. Leading me to believe that when I had run Boot-Repair before, it had already tried to do this and failed. Would the failure be due to having BURG installed?  The failure was Boot-Repair asking me to enable the amd64-efi package on the target system (sda6 in my case).

Thank you.

---

### Post by oldfred on 2015-08-02
I have only seen one or two Boot-Repair summary reports with burg & do not remember if burg is in grub's folders or has its own. 
The full uninstall/reinstall of grub should in effect overwrite parts of burg, but then you may have to search system for files & folders to delete.

The only way to remove from inside your install using live install is to chroot or CHange ROOT which uses the current kernel from live installer, but then you change to use file system of broken system to update. Boot-Repair does this or a mini version of chroot to do grub updates.

---

### Post by brohan76 on 2015-08-02
When I run Boot-Repair, I get the following error message:
 Please enable a repository containing the [grub-efi-amd64-signed] packages in the software sources of Ubuntu 15.04 (sda6). Then try again.

and when I choose okay, I get the following Konsole pop-up:
[http://paste.ubuntu.com/11989502/](http://paste.ubuntu.com/11989502/)

Here is the most recent Boot Info Summary right after I run Boot-Repair:
[http://paste.ubuntu.com/11989511/](http://paste.ubuntu.com/11989511/)

My system currently has legacy mode enabled on the BIOS, Secure Boot disabled, and the fast start disabled on Windows. As for Boot Repair the advanced options I chose to use the latest GRUB, as well as to purge GRUB before re-installing it. I have tried both with and without the secure boot option selected, and I get the same result.

This is where I currently stand, that Boot-Repair can't do anything, or so it seems to me.  It appears to me that a Ubuntu live CD offers a repair option of sorts, that you can re-install it, and save your data. I don't see that option with Kubuntu, but is it possible? Also I have backed up my home dir, would a fresh install repair this, setting it up with my same username and password, then copy my home directory back?

---

### Post by oldfred on 2015-08-02
Line 43 in sources shows quantal?
Comment that line out as it is blocking all updates, as that is now obsolete.

---

### Post by brohan76 on 2015-08-03
I tried commenting out the line, with both one and two hashes, and I also ran boot-repair from LiveUSB as root. Not sure if that mattered. I received the same result, posted here:

[http://paste.ubuntu.com/11994054/](http://paste.ubuntu.com/11994054/)
[http://paste.ubuntu.com/11994076/](http://paste.ubuntu.com/11994076/)

Would following the instructions here work, or cause any issues:
[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

---

### Post by oldfred on 2015-08-03
Sources looks ok, I think, do you have a ~ at end? 
Some files cannot have extra lines at end, sometimes even a space.

Your link is on chroot.
But it does not show the mount of an efi partition or the sometimes need cp of resolv.conf to get Internet working.

This shows efi mount and reinstall of grub's efi version.
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)

But it does not have the resolve command, may not now be required?
Another user posted this, note his / & efi partitions may not be the same as yours.

 sudo mount /dev/sda2 /mnt #sda2 is my root partition
sudo mount /dev/sda1 /mnt/boot/efi #sda1 is my efi partition
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
sudo cp /etc/resolv.conf /mnt/etc/ #makes the network available after chrooting
sudo chroot /mnt
apt-get install --reinstall grub-efi-amd64

   or alternatively: 
apt-get install --reinstall grub-efi
update-grub

---

### Post by brohan76 on 2015-08-03
The actual file doesn't have an END in it, the konsole that pops up after the error message does have END but no  tilde. When I was able to run my system, I could update the system just fine (except for the message of expired packages).

I currently have BIOS (as it was when this occurred) set to use legacy boot as well, should I change this and enable secure boot before I try chroot?

---

### Post by oldfred on 2015-08-03
Were you booting Windows in UEFI mode and Ubuntu in BIOS mode before? That only works from UEFI or perhaps one time boot key. 
UEFI & BIOS boot are not compatible and once you start booting in one mode you cannot switch. Or from grub menu you can only boot systems installed in the same boot mode.

Best not to have secure boot on.

Better to have Ubuntu in UEFI mode, but HP does not make it easy. And Boot-Repair often adds all the HP efi files into grub menu making it very busy. But those can be manually edited out.

I posted before some other HP threads where users did the work arounds to make HP work with UEIF.

---

