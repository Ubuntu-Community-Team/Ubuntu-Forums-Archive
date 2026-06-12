---
title: "Can we install ubuntu on an external disk and boot on it?"
date: 2018-08-21
forum: Installation &amp; Upgrades
---

### Post by cimmerian-iter on 2018-08-21
Hi guys, i've got a hp probook x360 11 g1 ee intel celeron and hd intel graphics with 4G of ram. This pc was known to block any attempt to boot on an external storage. Such as grub. You can find a report her at this link : [https://lists.gnu.org/archive/html/bug-grub/2017-12/msg00010.html](https://lists.gnu.org/archive/html/bug-grub/2017-12/msg00010.html)

When i tried to boot it give me that [COLOR=#000000][FONT=Arial]Selecting this just causes the screen to go black with a blinking cursor and... that's the end."[/FONT][/COLOR]

But by chance, i booted with a ubuntu 18 iso key and i succeded to boot on grub bootloader (what a miracle) i though that freedom was acheived but no. At the ubuntu installation it stuck at "installing grub 2 package". Meh too bad (unless you have an idea) so my question is can i install ubuntu on a external drive and boot in as it was a usb key? (i think it's the only way for me to make ubuntu work) thanks in advance.[COLOR=#000000][FONT=Arial]

[/FONT][/COLOR]

---

### Post by oldfred on 2018-08-21
HP violates UEFI spec that says NOT to use description as part of boot. And of course only valid description is "Windows Boot Manager". But many work arounds.

Also is Windows UEFI? If system is less than 5 years old and Windows installed by HP, it will be UEFI.
Some with newer HP have said updating UEFI from HP has helped withsome of the issues.

I have full installs of Ubuntu to external flash drives & an SSD using USB3 ports. Flash drives are slow to write to and it takes about 45 minutes to install. My install to SSD was only slightly longer than install to internal SSD or just over 10 minute.

You have to partition in advance. And if UEFI must have an ESP on external drive.
New installs now use swap file, so swap partition not required. 
       UEFI/gpt partitioning in Advance:
[http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu](http://askubuntu.com/questions/743095/how-to-prepare-a-disk-on-an-efi-based-pc-for-ubuntu) 
    
Issue with UEFI external installs is that UEFI only boots from an ESP - efi system partition on external drive using /EFI/Boot/bootx64.efi. That is on Ubuntu and Windows installers (but obviously different files).
And Ubuntu's version of grub only installs UEFI boot loaders to ESP on internal drive. My work around is to copy /EFI/ubuntu from internal drive's ESP to external drive's ESP twice. Once to /EFI/ubuntu as full install of grub expects to find that. And then copy a second time to /EFI/Boot and rename shimx64.efi to bootx64.efi.

       [https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312](https://askubuntu.com/questions/786986/boot-ubuntu-from-external-drive/942312#942312)
[https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration](https://askubuntu.com/questions/913716/dual-boot-on-seperate-drives-best-configuration)
[http://linuxbsdos.com/2015/10/31/how-to-dual-boot-windows-10-and-ubuntu-15-10-on-two-hard-drives/](http://linuxbsdos.com/2015/10/31/how-to-dual-boot-windows-10-and-ubuntu-15-10-on-two-hard-drives/)

---

### Post by cimmerian-iter on 2018-08-22
Wow nice, thanks for the full tuto i'll try out that

---

### Post by C.S.Cameron on 2018-08-22
I have had success making BIOS/UEFI Full install external drives starting with a mkusb Persistent install to external USB drive.
The mkusb OS and casper-rw partitions are deleted and Ubuntu is installed on a ext4 partition in their place.

It is also possible to place the OS on the internal drive, (which should be faster than a USB for opening and running programs), and keep the boot and /home partition on the external drive.

---

### Post by cimmerian-iter on 2018-08-22
Woa impressive, but i think it's kinda hard to do that. And with the locked bios of my pc i don't know if it would work.

---

### Post by oldfred on 2018-08-22
A lot of users have installed to HPs, but work arounds usually required.

 HP UEFI boot order change with efibootmgr does not stick, but change in HP's UEFI does work
[https://ubuntuforums.org/showthread.php?t=2390309](https://ubuntuforums.org/showthread.php?t=2390309)
HP 11m reinstall Windows & dual boot with Ubuntu 16.04
[https://ubuntuforums.org/showthread.php?t=2389104](https://ubuntuforums.org/showthread.php?t=2389104)
Probook G4 470 Ubuntu works fine with UEFI and secure boot. 
[https://ubuntuforums.org/showthread.php?t=2381663](https://ubuntuforums.org/showthread.php?t=2381663)
HP 8470p 
[https://ubuntuforums.org/showthread.php?t=2379728](https://ubuntuforums.org/showthread.php?t=2379728)
HP Z240 Tower Workstation XEON E5 UEFI & hard drive issues, manual chroot & reinstall of grub-efi-amd64
[https://ubuntuforums.org/showthread.php?t=2376227](https://ubuntuforums.org/showthread.php?t=2376227)
HP - escape + F9 for boot menu, F10 for bios setup
[http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453](http://askubuntu.com/questions/870453/live-boot-usb-install-of-16-04-fails-on-hp-pavilion-23?noredirect=1#comment1349777_870453)
[http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook](http://askubuntu.com/questions/666631/how-can-i-dual-boot-windows-10-and-ubuntu-on-a-uefi-hp-notebook)
Some HP will not boot a flash drive that is gpt partitioned. Some only boot from the USB2 port not USB3 ports.
[http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&p=13468260#post13468260)
HP Check if Customized UEFI settings available like this  HP ProBook 4340

---

### Post by cimmerian-iter on 2018-08-24
Hi guys I'm back with some news informations. So I found grub bootloader in my PC, it's called windows boot manager in my uefi loading menu (dunno why) and when I choose to boot in I arrive in grub minimal bash like so with that is there a way to install Ubuntu on my PC and use this to boot on it?

---

### Post by oldfred on 2018-08-24
One of the old work arounds was to make the Windows boot file really be a copy of grub or shim to boot Ubuntu, but then Windows updates would overwrite it.
Another work around was to name the Ubuntu UEFI boot entry to be "Windows Boot Manager", but best to leave that as Windows as grub only boots working Windows. If only installing Ubuntu that is a good work around.
Often HP has a fallback or hard drive UEFI boot entry, and we make that be a copy of grub or shim to boot Ubuntu. 

Did you review links in previous posts, those are some of those with HP that made it work.

       Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by cimmerian-iter on 2018-08-24
Hi yes I read them I'll try this soon as I have everything prepared. Also in this grub mode I tried to boot by setting the root and running Linux. But it ended up in a kernel panic because VFS : cannot open root device "hd0,gpt4. And I'm sure hd0,gpt4 is Ubuntu partition
I tried to launch boot repair but same it just take forever to install grub.

---

### Post by cimmerian-iter on 2018-11-15
Ok so i tried multiple way, load grub from an external device and try to load ubuntu that is installed on my pc. load initramfs with grub (so i boot to a busybox black screen). But neither of them worked. Is there any other way?

---

### Post by oldfred on 2018-11-15
With UEFI, you do not need to install grub to external drive to boot an internal install.

UEFI only boots from /EFI/Boot/bootx64.efi for external devices. My full installs of Ubuntu to flash drive or external SSD required me to copy /EFI/ubuntu twice to ESP - efi system partition on flash drive with second copy going into /EFI/Boot. Then I had to rename shimx64.efi to bootx64.efi. You have to have the /EFI/ubuntu as the full version of grub seems to be hard coded to look in that path for more boot files.

       May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Please attach link to the summary report, the auto fix sometimes can create more issues.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by cimmerian-iter on 2019-01-26
Ok got it, so now i leave the grub installation and made my way out using Refind and now it works. I can load my Ubuntu detoskop. Now small problem, i've got some problems with grub again. When i do the sudo apt full-upgrade, it will attemp to configure grub  grub-efi-amd64-signed (1.110+2.02+dfsg1-5ubuntu8) ...
Iand install it for x86_64-efi. And it stuck on this level. So is there a way to avoid updating grub package or not? Because now, my dpkg is often interumpt and i wan't install any apps from ubuntu store. Thanks

---

### Post by oldfred on 2019-01-26
run these:
sudo apt update
sudo apt upgrade

And if error messages, post exact message, if longer use code tags.

---

### Post by cimmerian-iter on 2019-01-26
It's not that there is an error code. But rather when i do apt upgrade, it does a lot of things until it come to 
Setting grub-efi-amd64-signed (1.110+2.02+dfsg1-5ubuntu8)
Installing for x86_64-efi.

And it kinda freeze at this step, it does not pass this installation

Other thing is that when i boot, ubuntu tells me that an error occured and that i can report it (though it doesn't give me a log)
dpkg is interrupted, so i had to manually launch it using 
cd /var/lib/dpkg/updates sudo rm *

So the thing would be to prevent apt upgrade from trying to install grub so it can complete the upgrade.

---

### Post by oldfred on 2019-01-26
Grub's UEFI install, expects to find an ESP that it can write into on first drive, usually sda, or NVMe first drive.
If that is not found you then get errors or perhaps a hang as it cannot finish writing into ESP.

If you use Boot-Repar, it normally shows some detail of the grub install steps & errors.

Advanced mode screens:
       [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by cimmerian-iter on 2019-01-27
Ok thanks, i will run boot repair.


Also something that i notice, when i boot REFIND, it show 2 ubuntu, One grub menu that boot into bash minimal editing, and the other one that boot into ubuntu shell. Maybe this grub mess everything?

---

### Post by cimmerian-iter on 2019-01-27
here is the log that boot repair provide 
[http://paste.ubuntu.com/p/jsmdhPKDtg/](http://paste.ubuntu.com/p/jsmdhPKDtg/)

---

### Post by oldfred on 2019-01-27
It is normal to have two ubuntu entries, one is shimx64.efi and other is grubx64.efi.
Shimx64.efi is for UEFI Secure boot but will boot with secure boot off.
Grubx64.efi for for normal boot, but since shim works for both not sure why we still have both.

If you are able to use rEFInd, that is one of the work arounds for systems that do not follow UEFI standards.
HP supposedly is better than it was, but you need to update UEFI to see if you get some of those fixes.
       HP Envy 17 - 18.04.1 works See post #3
[https://ubuntuforums.org/showthread.php?t=2392797](https://ubuntuforums.org/showthread.php?t=2392797)
HP Pavillion X360 13-a220nw
[https://ubuntuforums.org/showthread.php?t=2359510](https://ubuntuforums.org/showthread.php?t=2359510) & 
[https://ubuntuforums.org/showthread.php?t=2407615](https://ubuntuforums.org/showthread.php?t=2407615)
[https://ubuntuforums.org/showthread.php?t=2406993](https://ubuntuforums.org/showthread.php?t=2406993) 
    
Do not really see anything in Boot-Repair's summary report.
HP used to not allow any UEFI entry other than "Windows Boot Manager" by description.
But you did use a Windows entry for rEFInd, so you now have two Windows entries. We used to do that for grub also, but Windows updates would rewrite Windows UEFI boot entries, erasing the grub entry.
We normally use the fallback or hard drive entry which is at /EFI/Boot/bootx64.efi and usually something like UEFI: hard drive in UEFI boot menu. You do not show that file. Grub now creates it as a copy of shimx64.efi and Windows normally creates it as a copy of Windows boot files. Not sure if UEFI boot entry then created or not.

Have you updated UEFI from HP to most current UEFI?

---

### Post by cimmerian-iter on 2019-01-27
I see, thanks for the info. also yep i had updated to the latest UEFI version for my pc.
Yes my uefi allow to boot on other bootloader than "windows boot manager" as it show REFIND.

But anyways i found the solution. It was to delete the grub bootloader that was still there in EFI partition, so now apt upgrade works fully (and brightness works again)

Thanks for all your help now i can begin my linux adventure. :KS

---

