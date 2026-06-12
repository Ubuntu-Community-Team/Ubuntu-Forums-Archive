---
title: "Uninstall Ubuntu 15.04 from dual boot with Windows Starter 7"
date: 2015-06-25
forum: Installation &amp; Upgrades
---

### Post by jerry49 on 2015-06-25
I have installed Ubuntu 15.04 dual boot with W7 Starter on a 5 YO Acer Netbook... has 160 GB HDD and 1 GB RAM.  

All appeared to work well, but over a few light uses the system is bogging down, both when booted Ubuntu and W7S.  I make this comment based on the performance of Firefox run in both environments.  I took the default partition on the HDD wiht approximately 100 GB to W7S and 40 GB to Ubuntu (yes, know it doesn't add up, take as approximate nums, but show enough is allocated).   

I had "heard" from a person who gave a presentation at the Senior Center I participate at that he runs Ubuntu 15.04 on a USB port not double boot as he had problems.  I also read a recent post about dual boot problems, it had a lot of extensive program information and is over my level of understanding.

The above noted, can I uninstall Ubuntu and retain W7S... thus move Ubuntu to the USB rather than a dual boot?  Also welcome advice on how to fix the dual boot so it will run better/normal.

---

### Post by oldfred on 2015-06-25
Were you running full Ubuntu with Unity.
System that old may not run Ubuntu well as Unity needs more RAM and better video than a system that old. I installed fall-back or gnome-panel on my Ubuntu install on a nearly 10 year old laptop with 1.5GB of RAM. It would not run full Ubuntu well, but lighter weight gui worked fine. But if I loaded more than one large app like Firefox and a couple of smaller apps like terminal & Zim then system started to use Swap and got real slow.
Others may suggest Xubuntu or Lubuntu which also are lighter weight gui.

Windows also gets slow if you make the NTFS partition too small. You want to maintain 30% free space for it to work well. Best to houseclean, defrag and run chkdsk regularly.

A USB install typically will be slower. Newer systems with USB3 ports & flash drives work pretty well (but they also have newer video & more RAM). Older systems with USB2 ports and USB2 flash drives are ok, but not speedy. But your RAM & video chip will still limit overall system even more.

---

### Post by jerry49 on 2015-06-26
Thanks, just checked tonight, seems I do not get email notification of activity on a thread I post or contribute to.

I came back because I found a method  on 'howtogeek" to uninstall Ubuntu.   I post a like to that method here - welcome any opinions on this method:
[http://www.howtogeek.com/141818/how-to-uninstall-a-linux-dual-boot-system-from-your-computer/](http://www.howtogeek.com/141818/how-to-uninstall-a-linux-dual-boot-system-from-your-computer/)

The above is rather complicated, but looks doable.... even for me.  I'll check the link you provided too... too late tonight for me to try either.   Your recommendations on a lesser Linux will be considered, then too I have been told by a local "expert" that he runs Ubuntu on a machine similar to my Acer but runs it on a USB HDD boot, not on a dual boot.  Sound like that may not be enough to get 15.04 running on my Acer netbook, and my real target is a Dell Desk Top running XP Media.  This machine has even older hardware.

---

### Post by oldfred on 2015-06-26
Better to install the Windows boot loader and make sure Windows boots before removing Ubuntu partitions. But either way best to have both a installed version Windows repair CD or flash drive and current version Ubuntu live installer to remove the Linux partitions with gparted.

---

### Post by jerry49 on 2015-06-28
Thanks, given I remove installed Ubuntu and run Ubuntu from an external "HDD" am I correct a USB solid state flash drive will perform better/faster than running from a USB connected DVD?  Can the DVD be read only, i.e., doesn't Ubuntu on the DVD still require an HDD partition to store dynamic data, e.g., Thunderbird profile?  Maybe I just concluded the USB run Ubuntu has to be a read/write medium, a flash drive.   Oops, just recalled I ran Ubuntu the first time from the installation DVD.

Edit: I see answer on USB question answered on the first time I submitted via an existing thread...still working to get immediate notifications of thread activity.

---

### Post by oldfred on 2015-06-28
The flash drive installer is just the same as the DVD version. Not intended for updates and you cannot update its system. But since flash drive, you can add persistence which lets you save some data. Or you can do a full install of Ubuntu to a flash drive, as flash drive is just another drive. Many system see flash drive as another small hard drive.

I did see USB3 flash drive in my USB2 ports was about 10% faster. So after that I only purchased USB3 flash drives as I knew eventually I would also have system with USB3 ports.

 Pros & cons of persistence install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=2133067](http://ubuntuforums.org/showthread.php?t=2133067)
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

Brand of flash drive also important for speed.
 pendrive speed tests USB2 & USB3 various brands - user sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)
Includes links to speed tests and lists some that do not work well.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

### Post by girtsz on 2015-06-28
You can try on 1Gb RAM Linux Mint 17.1 Cinnamon with disabled all effects in Linux Mint after installation. You need only to disable effects.

---

### Post by jerry49 on 2015-06-28
Sill lost on dynamic data.  Let's say for example I have Ubuntu (15.04 or otherwise) on a DVD, case one, and Flash Drive case two.  Both are connected via USB.  

So running Ubuntu Thunderbird I download my one or more email accounts, that data being saved in the Ubuntu Thunderbird Profile folder.  Then, I shut down and disconnect the USB (both cases)... what happens to the Thunderbird Profile information on the downloaded email (saved somewhere on the computer internal HDD, somewhere else, lost)?

Second follow up question on the two methods of holding Ubuntu.  I have 15.04 installation version on a DVD.  I used that once to run Ubuntu from the USB, and to load (dual boot) on my Acer Netbook with Windows 7 Starter.  Can I put the same on a Flash Drive by simply copying the DVD to a Flash Drive, i.e., use just Windows copy, or is something lost when that is done?  Of course, I can boot to Ubuntu as I have not yet uninstalled and use Ubunto File Manager to copy from the DVD to the Flash.

---

### Post by oldfred on 2015-06-28
Your Thunderbird profile is gone.
That is actually one of the advantages of the live installer, as those users who do not want Firefox or other history kept can be sure it is not. If you have a swap file on hard drive, some data may be hidden there if swap was used.

You cannot copy or directly extract ISO to flash drive and have it bootable. It does not copy boot loader & configuration to flash drive. But if you want an UEFI only flash drive it does work as UEFI only needs an /EFI folder with boot files. A BIOS install needs boot files in MBR & PBR partition boot sector.

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
 [http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

      
 Most find this works best
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

 Howto help USB boot drives - sudodus
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by jerry49 on 2015-06-28
Thanks, looks like if one wants to maintain history, associated folders for email in Thunderbird operated over USB, one could copy the Thunderbird Profile to the HDD before shutting Ubuntu down.  A bit cumbersome but that would bridge Thunderbird boot-to-boot perhaps Thunderbird van be directed to store the profile on the HDD, "C" drive.  Otherwise, one would have to copy the Profile back into the Ubuntu Thunderbird to pick up where they left off on the last email session.  Here I obviously take the input given to tell me when operating from a USB Flash (drive) we get a fresh start every time we boot up Ubuntu over the USB.  Seems to me something Ubuntu experts might work on is a Flash Drive operation that operates just like a dual boot, thus when one boots to the Flash the computer comes up just like it has Ubuntu loaded... just the BIOS?  That is Windows is never activated.  Here we go, confession on how little I know about BIOS - I understand the BIOS is responsible for setting up the computer to be transferred to a boot address, normally on the HDD, but can be via USB (BIOS runs USB?) to an outboard "drive".

I have a Flash Drive copy of Ubuntu 15.04 as provided via a download from Ubuntu.  I used that via Windows 7 to create the DVD iso installation medium.  I thus think I can reused the Flash download to create another installation on a Flash Drive, the same one?  The subject Flash Drive is at least 16 GB, don't remember the size at the moment.  In any case if I purchase a new Flash memory stick, 8 GB should be more than enough as I'll not be storing anything there beyond the operational installation Ubuntu... less than 4 GB.

---

### Post by oldfred on 2015-06-28
If you want the functionality of a full install, just do a full install to another flash drive. That then is just another install of Ubuntu but on a removeable drive. Needs to be at least 8GB, but if you really want to store some data better to be larger.

An installer can be on a smaller flash drive, if you want.

---

