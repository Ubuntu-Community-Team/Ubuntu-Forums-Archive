---
title: "Having problems installing Ubuntu 20.04 Alongside Windows 10 Acer E5-532"
date: 2020-08-28
forum: Installation &amp; Upgrades
---

### Post by sirwill on 2020-08-28
Hey,
I Have an acer e5-532
intel celeron n3050 cpu
it says 
Insyde Corp is my bio
Baseboard manufacturer Zoro_BA
Type:Mobile
PCR7 Binding not possible
....
I'm running Windows 10 currently.
I Could not successfully install Windows 7 either... Which sucked.
When I install it alongside windows I get the common error I've seen around here.
Cannot unmount /CDROM
...
When I try to create the partitions manually. After installation, when I reboot it just goes directly into Windows 10 as if Ubuntu was never installed,
And I can see the partition it's on but have no access to it within my windows.
Thanks for any advice in advance.


Update : So I accidentally wiped my hard drive and it wouldnt read my ubuntu usb I created off of my laptop having the issues. So it got me thinking.. I decided to plug the USB into a Mac PC and create a bootable ubuntu USB.
And bam. Problem solved. USB read and Ubuntu installed.
But when I reboot it says boot device manager is missing. 
I Am going to try turning secure boot on and installing and see if that allows grub installer to install if not I will try and create a grub loader usb installer and see if that works as it seems ubuntu is installing but grub loader isn't

---

### Post by ActionParsnip on 2020-08-28
Windows 7 is no longer supported so it not installing isn't such a bad thing. There are no updates for it so you will have a vulnerable OS to all sorts of nasties.

Did you MD5 test the ISO you downloaded?
If you are booting CD, did you burn as slowly as possible?

---

### Post by sirwill on 2020-08-28
I'm booting from usb. I just wiped the hard drive using disk part. Now my usb device isn't recognized on UFEI only on legacy boot.... help :/

I'm trying to install Ubuntu LTS 20.04

However if I put windows 10 on the usb the harddrive reads the usb in ufei ...... how do I solve this

---

### Post by CelticWarrior on 2020-08-28
The way to solve this is to make a proper USB installation media.
Likely you used Rufus with the standard settings that good only for BIOS/Legacy. You must change it to UEFI/GPT. Or use Balena Etcher instead.

And you nay need to set a supervisor password in UEFI in order to be able to trust external media. NEVER loose/forget that password.

---

### Post by sirwill on 2020-08-28
I set supervisor Password  nothing.. and the usb media is fine works on other devices. Thanks for tip tho

Also am i am in ufei mode...

I now have a computer for the garbage I guess..

I'm wondering if it might be the Verbatim USB itself?

---

### Post by oldfred on 2020-08-28
Acer's typically require UEFI update and some settings.
Some older threads may mention downgrading UEFI, but newer UEFI fixed many issues.
Acer issues are common across many models. Similar UEFI used, but differences only for options of system.

Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E3-112-C0MQ - Bay Trail Issue Boot Parameter required
[http://ubuntuforums.org/showthread.php?t=2326162](http://ubuntuforums.org/showthread.php?t=2326162)
[SOLVED]Acer Nitro 5 (with Ryzen 7 2700U, RX 560X) Ubuntu 18.10  
[https://ubuntuforums.org/showthread.php?t=2413504](https://ubuntuforums.org/showthread.php?t=2413504) &
[https://ubuntuforums.org/showthread.php?t=2412117](https://ubuntuforums.org/showthread.php?t=2412117) &
[https://community.acer.com/en/discussion/555251/unable-to-install-ubuntu-in-my-nitro-an512-42](https://community.acer.com/en/discussion/555251/unable-to-install-ubuntu-in-my-nitro-an512-42)
Acer Nitro 7 Missing AHCI mode Ctrl + S in UEFI
[https://ubuntuforums.org/showthread.php?t=2429951&p=13900969#post13900969](https://ubuntuforums.org/showthread.php?t=2429951&p=13900969#post13900969)
Acer Cloudbook shows screen for selecting trust, shows typical screens for all Acer
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[https://community.acer.com/en/categories/predator](https://community.acer.com/en/categories/predator)

---

### Post by sirwill on 2020-08-28
None of this helps me sorry. I've been through all those form and none of them apply to me. I have tried flashing my bio to the latest available version it didnt change any settings or anything I dont even think it properly flashed new bio I could be wrong though .

Also if you read I tried to completely erase hard drive and install ubuntu and now it wont read any usb installs except windows 10...

Also I just took pc apart I do not see any write protect screws that could be preventing operating system over rides unless I missed its location

---

### Post by sirwill on 2020-08-29
Update. I Have made a new Ubuntu usb with a Mac pc and now my laptop read the USB and installed Ubuntu properly to my clean hard drive. 
Anyone having issues it seems you cannot create install USBs off of this pc. There is some kind of protect on the pc that prevents it ...

---

### Post by sirwill on 2020-08-29
Any suggestions would be great still no success. This is dumb garbage acer.

---

### Post by sirwill on 2020-08-29
It seems the grub loader isn't loading with my bootloader possibly? Is there a fix for this using live USB

---

### Post by oldfred on 2020-08-29
Did you set the ubuntu entry as "trusted" in UEFI?
Details in links above.

If grub issue:
Lets see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste the pastebin link to the Boot-info summary report ( do not post report), do not run the auto fix till reviewed.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by sirwill on 2020-08-29
I dont have options in my ufei for trusting anything.

I can run the live test off my usb..

Initframs is what I'm having problems with I believe

The repair summary.
[https://pastebin.ubuntu.com/p/y8bwjN4BFR/](https://pastebin.ubuntu.com/p/y8bwjN4BFR/)

---

### Post by oldfred on 2020-08-29
You have many of these entries which are your Ubuntu entry.
But you have to set "trust". This is typical of an entry with Acer that does not have trust.

> Boot0000* Unknown Device:     

And you should delete all the duplicates.

If you do not have trust setting after you enable the UEFI password which will open more settings, then you need to update UEFI. Did you already update UEFI which you normally should do anyway.
Never lose UEFI password or when done go back and reset to blank. If you lose that password you convert PC to a brick.

To delete duplicates:
# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr
[http://linux.die.net/man/8/efibootmgr](http://linux.die.net/man/8/efibootmgr)
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)

---

### Post by sirwill on 2020-08-29
Incorrect problem was solved by adding Ubunti efi from the boot sector of hard drive to the trusted secure boot setting or else it wouldnt show up in my bios. Ubuntu is now running.

---

### Post by sirwill on 2020-08-29
Boot-repair helped me solve this issue telling me to add it to my secure boot device list or it wouldnt appear

---

