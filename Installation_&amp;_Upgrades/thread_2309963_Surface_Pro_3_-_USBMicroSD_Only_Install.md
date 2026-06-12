---
title: "Surface Pro 3 - USB/MicroSD Only Install"
date: 2016-01-14
forum: Installation &amp; Upgrades
---

### Post by Tom_S. on 2016-01-14
**SOLVED:  **[Part 1]("http://ubuntuforums.org/showthread.php?t=2309963&p=13424796#post13424796")   [Part 2]("http://ubuntuforums.org/showthread.php?t=2309963&p=13424798#post13424798") 

Hello! I am trying to install Ubuntu 15.10 onto a MicroSD card on my Surface Pro 3, so I can switch from Windows 10 to Ubuntu simply by putting in the card, disable Secure Boot, and boot from USB. To switch back to Windows, just remove the card, re-enable secure boot. Best of both worlds, eh?

The problem is, every time I install Ubuntu (or reinstall grub) it simply can't resist putting grub on the Surface Pro 3 internal SSD, rather than keeping everything on the MicroSD card. I had the same problem trying to install it to a USB drive instead.

This is what I've been doing:

[LIST]
[*]In Windows, use Universal-USB-Installer-1.9.6.3.exe to install ubuntu-15.10-desktop-amd64.iso onto a USB drive. 
[*]On the Surface, plug that USB drive and mouse into a hub, put a blank MicroSD card into the Surface, and boot into Ubuntu install. 
[*]Don't set up networking, updates, or any additional programs (the install hangs if I do) 
[*]Select "Something else", and create the following partitions:
EFI System Partition, 200 MB
Root: 46000 MB, Ext4
Swap: Everything else (it's a 64 GB card) 
[*]Specify the EFI partition for the boot loader install 
[/LIST]
 
And despite doing this, the installer sticks grub on the internal SSD, making Windows unusable until I go through Windows Recovery to remove it. I tried manually installing grub (couldn't get it work) as well as using boot-repair (it stuck grub on the internal SSD again despite telling it to put it on the USB drive only - argh!)

Other people have had this problem and recommended disconnecting the internal drive while installing - I can't, it's a sealed Surface.
Some others have suggested just using the Ubuntu setup drive and setting up persistent space - that is insufficient for me, I need a full install so I can install Steam and run a game that requires Linux.

Any ideas? Or will I have to relegate Ubuntu to an old laptop?

Thanks!

---

### Post by haoz2 on 2016-01-15
That's exactly what I'm trying to do these days. Failed though :(
Check this out: [SIZE=2][COLOR=#333333][FONT=Ubuntu]Installation from a compressed image file in windows. [/FONT][/COLOR][/SIZE][h=1][COLOR=#222222][FONT=Verdana]https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#in_Windows[/FONT][/COLOR][/h]
Just two steps and perfectly works. However Surface keyboard won't.
It is Ubuntu 14.04, and for some reason it's impossible to upgrade kernel for Live USB.

So I'm hoping there were compressed image for SP3 we can download :)[h=1][/h][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu][/FONT][/COLOR]

---

### Post by Tom_S. on 2016-01-15
Thanks, I looked into the compressed images, but they aren't up-to-date - the only way to have any chance at reasonable Surface support (like the type cover) is to use the absolute latest version of Ubuntu available.

I keep searching around about how to do a USB-only install of Ubuntu and there's always some key thing missing from the instructions, such as:

[LIST]
[*]BIOS instead of UEFI
[/LIST]

[LIST]
[*]casper / persistent file / etc. - I need more than that
[*]Instructions say to use a ready-made image - those images are older, I need instructions how to do it from the standard latest ISO. I am already looking forward to the April 2016 release so I can use the latest TypeCover instead of pulling out my old one.
[*]Missing instructions about creating the EFI partition on the USB drive
[*]Setup created the EFI partition, but grub didn't install to it even though I specifically told setup to do so
[*]Setup or grub-install modified the internal SSD when it shouldn't have
[/LIST]

This is frustrating, what I am trying to do shouldn't be so hard, and should really be a common use case - take your Ubuntu box with you anywhere you go on a USB drive.

---

### Post by kurt18947 on 2016-01-16
I have no experience with UEFI or the latest lightest portables so take this for what it is. Is there any way to disable the internal SSD in BIOS settings? I'm thinking the firmware equivalent of unplugging a drive. The Ubuntu installs I've done have a screen when installing to place GRUB in a partition rather than in the disks' root. I use that in conjunction with a boot manager I use to overcome the 4 primary partition limit. I don't think I've ever tried placing GRUB on different drive.

---

### Post by Tom_S. on 2016-01-16
There isn't a way to disable the internal SSD in the BIOS. (technically, UEFI) There's options to disable every other piece of hardware except the internal SSD.

The odd thing is, I told the Ubuntu installer to place the boot loader on the MicroSD or USB drive, and it put it on the internal SSD anyway. That shouldn't happen. I tried yanking the drive from an old laptop and told it to install to a USB drive - it just skipped installing GRUB altogether. And I tried the install both as a full auto-install, as well as manual partitioning with space for EFI, Root, and Swap.

What's really odd is before I yanked the drive in the old laptop, I just tried disabling it in the BIOS, but somehow Ubuntu saw it anyway and at that point I was like 'No! Hands off, I need that laptop for media capture' then shutdown and pulled the drive.

I might give it a try with 14.04.3 LTS just to see if there's a problem with 15.10. Or maybe Ubuntu simply can't be used this way, which would be a real shame.

---

### Post by ubfan1 on 2016-01-17
Copy the /EFI/ubuntu from the internal disk to the USB's EFI partition.  The grub.cfg file will then be in the correct place, /EFI/ubuntu.  The bootloaders will be there too, but think of them as backups, they are ignored.  On the USB, copy /EFI/ubuntu/shimx64.efi to /EFI/Boot/bootx64.efi and copy /EFI/ubuntu/grubx64.efi to /EFI/Boot/grubx64.efi.  This will work with secure boot enabled or disabled.  The USB should be bootable on a UEFI machine now.
  The bad part left is possibly having to fix the nvram boot entry for selecting a bootloader off the hard disk.  There is no reason for the install to have messed with any of these nvram entries, but ...  Use efibootmgr to repair, reorder, or re-add the hard disk boot entry.  Put the USB first in the boot order in UEFI settings.  Getting late, I'll check in tomorrow.

---

### Post by Tom_S. on 2016-01-17
Thanks for the info; I will try this and if it works, I'll see if I can do a writeup so others may benefit or improve upon the process.

It worked! I'm working on writing up a full procedure.

**Installing Ubuntu onto a microSD card (or USB drive) on a Surface Pro 3**
 
**Part I - Preparation**
 
**Overview**
 
This procedure will install Ubuntu onto a microSD card or USB drive, on a Surface Pro 3. And I mean ***really*** install it:

[LIST]
[*]You'll get a real, complete install, where you can use the entire USB drive. You won't be limited by "Try Ubuntu" / 4 GB casper persistent file, etc. 
[*]Nothing related to Ubuntu will be left on the Surface SSD after it's cleaned up, so Windows will be able to start up smoothly.
 (no GRUB screen in the way - the Surface being what it is, you might not even have a keyboard attached to use the arrow keys or press Enter!) 
[*]You can use the latest version of Ubuntu right off [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) which is required for the best Surface support.
Ready-made images are easier to use, but aren't always up-to-date. 
[/LIST]
  One done, you'll be able to switch back and forth between Windows 10 and Ubuntu by following just a few steps.
 
This procedure might be useful for other computers that use UEFI, where you want to run Ubuntu exclusively off a USB drive.
 
**Things you will need:**
 

[LIST]
[*]Surface Pro 3, running Windows 10. This procedure *might *work on Windows 8.x as well, but I developed and tested it on 10 only. 
[*]Power supply for Surface Pro 3 - best to do this on AC power 
[*]USB hub - I was able to get away with an unpowered hub since all I had was one slow USB drive and a mouse, but if you have two USB drives, a mouse, and a keyboard, go powered. 
[*]USB mouse 
[*]Surface Pro 3 Type Cover OR a USB keyboard - see note below 
[*]USB drive for the Ubuntu installer, 2 GB or greater. It can be an old slow one. Note - all existing files will be erased. 
[*]MicroSD card or USB drive that you want to install Ubuntu onto. See "Storage Media Selection" below. Note - all existing files will be erased. 
[*]BitLocker Drive Encryption Recovery Key - very important! 
[*]Windows 10 Recovery Drive - also very important 
[/LIST]
  Also:

[LIST]
[*]A fresh backup of your Surface Pro 3 in case it gets hosed 
[*]Second computer with a microSD card reader, to work with the microSD card if needed, and to look stuff up if something goes wrong 
[*]Plenty of time 
[/LIST]
  Optional:

[LIST]
[*]Bluetooth mouse 
[/LIST]
 
**Notes about hardware compatibility:**
 
SP3TC = Surface Pro 3 Type Cover. No spaces between the keys
SP4TC = Surface Pro 4 Type Cover. Spaces between the keys, nicer feel, works on a Surface Pro 3 as well as the newer Surface Pro 4.
 
At the time of this writing (January 2016), Ubuntu 15.10 at supports the SP3TC, but not the SP4TC. Support for the SP4TC might be added in Ubuntu 16.04 LTS.
Ubuntu 14.04.3 LTS does not support the SP3TC nor the SP4TC, so if you  want to install that version, you'll need to use an external USB  keyboard.
It is possible to add support for any Type Cover to any version by recompiling the kernel, but that is additional complexity I did not want to get into for a procedure that's already long.
 
The touchpad on any Type Cover won't work regardless of which version is installed. A Bluetooth mouse seems to be a reasonable workaround.
 
**Storage media selection:**
 
Regardless of whether you install to a USB stick or a microSD card, you'll want one that has good performance on small random reads/writes, and good durability for frequent writes.
 
If you're installing to a USB stick, the SanDisk Extreme USB 3.0 might be the best choice at the moment, it seems to include SSD-grade flash memory. Unfortunately it's rather large hanging off the side USB port of a Surface.
 
I like installing to a microSD card, as it frees up the USB port. Unfortunately, there aren't any standout microSD cards, they all seem to be optimized for large sustained writes (eg GoPro) or large block writes (eg Android cell phone camera), but not the small random reads/writes that an OS will do. The benchmarks out there only test the first two cases, not the last case which is what we're interested in.
 
That said, I am using a Samsung EVO 64 GB microSD card, because that is what I had on hand already, based on recommendation from The Wirecutter ([http://thewirecutter.com/reviews/best-microsd-card/](http://thewirecutter.com/reviews/best-microsd-card/)). It seems like the Samsung 64GB PRO or PRO+ might be even better choices, but I couldn't find any reviews or benchmarks that covered small random reads/writes. Maybe the Raspberry Pi folks would know what's best, as they run their systems off microSD cards.
 
**Terminology:**
 
I will assume you're installing to a microSD card rather than a USB drive, but the same procedure applies to both.
 
The thing that appears when you hit a special key combination on bootup used to be the BIOS screen, but now it's UEFI firmware, not BIOS. Therefore I will refer to it as the "UEFI firmware screen", even though I still think of it as a BIOS screen after tinkering with computers for years.
 
**My Background / My Goal:**
 
Though my desktop operating system has always been some version of Windows, I've used Unix-like systems for years, primarily for web hosting / web development. So this means that either someone else set up the box and I'm using it, or I'm running Linux as a VM and don't have to worry much about setup. This is the first time in years that I'm running Linux directly on hardware.
 
My goal was to install Steam and run a game that runs only on Linux, which is what got me into this procedure. Having wasted time in the past due to installation procedures missing steps, missing information, or just plain out missing, that is why this is a bit long and verbose.

**Installing Ubuntu onto a microSD card (or USB drive) on a Surface Pro 3**
 
**Part II - Procedure**

At various points during this procedure, and after you're done, you'll have to switch between Windows and Ubuntu. Here's the steps to do it, so they aren't repeated numerous times below.
 
**Switch to Ubuntu**
Shut down Windows - a full shutdown, not sleep, not hibernate.
Insert the microSD card (or USB drive) with Ubuntu
Boot into the the UEFI firmware screen by holding Volume Up, press Power for 2 seconds and release. Keep holding Volume Up until the UEFI screen appears.
Secure Boot Control - Change to **Disabled**
Configure Alternate System Boot Order - change to **USB -> SSD**
Exit Setup
Save configuration and reset.
 
Remember to switch to the original SP3 Type Cover if you normally use the SP4TC.
 
**Switch to Windows**
Shut down Ubuntu.
Remove the microSD card (or USB drive) with Ubuntu
Boot into the the UEFI firmware screen by holding Volume Up, press Power for 2 seconds and release. Keep holding Volume Up until the UEFI screen appears.
Secure Boot Control - Change to **Enabled**
Configure Alternate System Boot Order - could change it to **SSD only**, or leave it as **USB -> SSD**
Exit Setup
Save configuration and reset.
 
You can switch back to the new SP4TC if you have it.

**Disclaimer**

I am not an Ubuntu or Linux expert, in fact I'm quite a newbie at this type of installation. I cannot offer support, and you do this at your own risk. Please make backups and don't do this if you need your Surface for anything important anytime soon!

**Step 0 - Get everything together**
 
Make sure you have everything listed above, **especially a fresh backup of your Surface, the BitLocker Key, and the Windows recovery drive.**

**Step 1 - Prepare the Install drive**
 
Download Universal-USB-Installer-1.9.6.3.exe from [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
Download the latest version of Ubuntu from [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
Run the Universal USB installer.
Install to the USB drive. Let it reformat it. Don't worry about a persistent file.
 
**Step 2 - Prepare the MicroSD card or USB drive**
 
This is optional, you can do this later during the Ubuntu install, but I prefer to do it ahead of time.
 
Use Windows Disk Management to delete all partitions on your target microSD card or USB drive.
(Right-click Computer, Manage, Storage, Disk Management (Local))
 
Be careful! A wrong move here and you could erase a drive with data on it.
 
If there's a partition that won't delete, try this:
 
Start
**diskpart**[INDENT][B]list disk
select disk 99 (use whatever drive number it is)
recover
clean
exit[/B]
[/INDENT]
 
**Step 3 - Prep the Surface**
 
Follow instructions above to Switch to Ubuntu.
Before starting, plug in your USB hub, Ubuntu install drive, USB mouse, target microSD card or USB drive, and a USB keyboard if you don't have a Surface Pro 3 Type Cover.
 
**Step 4 - Install Ubuntu**
 
After it boots, you'll see the GNU GRUB screen.
Select Install Ubuntu.
Select language
DO NOT connect to a network right now - sometimes it hangs install
DO NOT install third-party software right now - sometimes it hangs install
Installation Type - Something Else (very important, don't overwrite anything)
 
**Step 5 - Partitioning**
 
**Identify the drives:**

*sda *is normally the Surface built-in SSD. *sdb *is usually the microSD card. You could have more drives, or they could be labelled something else. Take a close look at them and verify which is which. I know my Surface has a built-in 250 GB SSD, I'm installing to a 64 GB microSD card, from a 16 GB USB drive, so I can use the size to verify which is which. Also the built-in SSD has lots of partitions for Windows, whereas the microSD card has none because I blanked it in Step 2. Be careful!
 
On *sdb *(or whatever your USB drive or microSD card is), create the following partitions:[INDENT]200 MB, Primary, Beginning, EFI System Partition
46000 MB, Primary, Beginning, Ext4, Mount Point: /
17822 MB, Primary, Beginning, Swap Area
[/INDENT]
 
100 MB is usually enough for a boot partition, but everyone's pushing for 200 MB nowadays so I went with that.
A rule of thumb for Swap is that it should be twice your RAM. My Surface has 8 GB RAM so approximately 16000 MB is enough.
In reality I just typed 46000 MB for the root partition and used the rest of the available space for swap.
We'll decrease swap usage later to hopefully extend the life of the flash media.
 
**Boot Loader:**
 
This is where the install program fails. You'd think this would be sufficient:[INDENT]Device for boot loader installation: /sdb/sdb1         (or wherever you created the EFI System Partition)
[/INDENT]
  
But in reality, Setup completely ignores what you put in and sticks it on /dev/sda2 anyway, hosing Windows 'till it's cleaned up. I am not the only one with this problem; see [http://ubuntuforums.org/showthread.php?t=2309806](http://ubuntuforums.org/showthread.php?t=2309806) This action is what made this whole procedure necessary. There's steps below to clean up this mess. (which is the whole point of this guide)
 
Verify which partitions the installation will change, and proceed if correct.
 
**Step 6 - Continue Install**
 
Time Zone - Select your local time for now. This will require an adjustment later on.
 
Who are you - enter info.
 
Sit back and wait for Ubuntu to install.
 
Let Ubuntu reboot. Be sure to remove the USB drive you used for the installation.
 
Boot GRUB menu - Ubuntu
 
After reboot, welcome to a fresh install! Well, maybe not. At this point if you pulled the card and turned secure boot back on, Windows wouldn't start up anymore. So…
 
(well, first I go into Settings and turn the screen brightness down! Then…)
 
**Step 7 - Clean up after install, Part I - put the files where they should have gone**
 
Log into Ubuntu. Open a terminal.[INDENT]**sudo su**
[/INDENT]
List mounted drives:[INDENT]**df**
[/INDENT]
In my case, /dev/sda2 is mounted as /boot/efi. That's where the GRUB files went.
The microSD card EFI partition isn't mounted.
(from [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB))
List drives available for mounting:[INDENT]**fdisk -l**
[/INDENT]
In my case, it's /dev/sdb1. That's where the GRUB files should have gone. (I can tell by the drive size and description - it's the EFI drive, and it's about 200 MB as set above)
Create mount point:[INDENT]**mkdir /media/microsdefi**
[/INDENT]
Mount the drive. You should look up which uid and gid to use, but 1000 seems to be the default for the first user on a fresh install:[INDENT]**mount -t vfat /dev/sdb1 /media/microsdefi -o uid=1000,gid=1000,utf8,dmask=027,fmask=137**
[/INDENT]
Create directories and copy files. The goal is to get all the files
in /boot/efi/EFI/ubuntu/
into /media/microsdefi/EFI/ubuntu
(THANK YOU **ubfan1** for a clear explanation of what was required)
(Resident expert **oldfred** also notes this: [http://ubuntuforums.org/showthread.php?t=2310318&p=13424975#post13424975](http://ubuntuforums.org/showthread.php?t=2310318&p=13424975#post13424975))[INDENT][B]cd /media/microsdefi
mkdir EFI
cd EFI
mkdir ubuntu
cd ubuntu
cp /boot/efi/EFI/ubuntu/* .[/B]
[/INDENT]
Then, copy /media/microsdefi/EFI/ubuntu**/**shimx64.efi
to /media/microsdefi/EFI/Boot**/**bootx64.efi (note - file name change!),
and /media/microsdefi/EFI/ubuntu**/**grubx64.efi
to /media/microsdefi/EFI/Boot**/**grubx64.efi (note - same file name)[INDENT][B]cd ..
mkdir Boot
cd Boot
cp ../ubuntu/shimx64.efi bootx64.efi
cp ../ubuntu/grubx64.efi .[/B]
[/INDENT]
 
**exit**,** exit**, and shut down Ubuntu.
 
**Step 8 - Clean up after install, Part II - remove GRUB from the SSD**
 
Plug in the Windows recovery drive.
Follow instructions above to Switch to Windows. Ensure Windows will boot from USB first.
Restart.
 
(this is based on [http://askubuntu.com/questions/443637/how-to-remove-grub-without-access-to-windows](http://askubuntu.com/questions/443637/how-to-remove-grub-without-access-to-windows))
 
Windows Recovery
Choose keyboard layout.
Troubleshoot
Advanced options
Command Prompt
Type in your BitLocker recovery key if required.[INDENT][B]diskpart
list disk[/B]
[/INDENT]
You'll want to select the boot drive. In my case it's Disk 0.[INDENT]**select disk 0**
[/INDENT]
Show the partitions[INDENT]**list partition**
[/INDENT]
Find the EFI partition. In my case it's 100 MB so it's easy to spot. Select it.[INDENT]**select partition 99**     (use whatever number it is for you)
[/INDENT]
Assign the partition to a drive[INDENT]**assign letter=u**
[/INDENT]
Exit diskpart[INDENT]**exit**
[/INDENT]
 
You can take a look at the offending directory one last time:[INDENT][B]u:
cd efi
dir[/B]
[/INDENT]
Now, get rid of the GRUB files:[INDENT]**rd /s u:\efi\ubuntu**
[/INDENT]
Fix the Windows boot record:[INDENT][B]c:
cd \windows\system32
bootrec/fixmbr
bootrec/fixboot[/B]
[/INDENT]
All done![INDENT]**exit**
[/INDENT]
 
Select Turn off your PC.
Unplug the Windows recovery drive.
Start up, verify you can get back into Windows.
 
**Step 9 - Have a bit of fun switching back and forth!**
 
There's still some work to be done, but you can follow the steps above to "Switch to Ubuntu" and "Switch to Windows".
 
**Step 10 - Decrease swappiness**
 
(remember to Switch to Ubuntu)
 
Normally Ubuntu swaps files to disk frequently. Since the disk is a microSD card that's a bit slow and has limited write cycles, it's best to reduce swapping to only when needed.
 
(from [http://askubuntu.com/questions/103915/how-do-i-configure-swappiness](http://askubuntu.com/questions/103915/how-do-i-configure-swappiness))[INDENT]**sudo nano /etc/sysctl.conf**
[/INDENT]
Then, find this line and change it from 60 to 10, or add it to the file:[INDENT]**vm.swappiness = 10**
[/INDENT]
Reboot to make it take effect.
Verify the changes stick after reboot:[INDENT]**cat /proc/sys/vm/swappiness**
[/INDENT]
 
**Step 11 - Clock**
 
When I go into Windows, the clock is wrong. It turns out this is a common problem. See [http://askubuntu.com/questions/169376/clock-time-is-off-on-dual-boot](http://askubuntu.com/questions/169376/clock-time-is-off-on-dual-boot) for possible solutions. I agree that the clock really should be set to UTC, but given that the Surface is primarily a Windows machine, I'll take the heretic's solution and let it be local as Windows wants. In Ubuntu:[INDENT]**sudo nano /etc/default/rcS**
[/INDENT]
Find UTC=yes and change it to[INDENT]**UTC=no**
[/INDENT]
Reboot if you'd like.
 
**Step 12 - Updates**
 
You're done!
Follow the procedures above to switch between Ubuntu and Windows whenever you'd like.
NOW it's okay to connect to a network and install updates in Ubuntu.
You might want to set up the Bluetooth mouse now if you have one, so you'll have a neater setup.
 
**Final Notes**

I recommend taking your BitLocker key with you if you're travelling, as it's possible to trigger a protection mechanism that will require your to re-enter your key. That happened to me only once before I got the above procedure figured out, but it's a good precaution anyway. Take along your Windows recovery drive as well.

**Acknowledgements**
 
Major thanks to **ubfan1 **for providing the crucial file-moving instructions in Step 7 to make this work.
 
Raspberries to the Ubuntu installer for doing something other than what I told it to do, making this process a lot harder than it should be.

> **haoz2 said:**
> That's exactly what I'm trying to do these days. Failed though [IMG]http://ubuntuforums.org/images/smilies/icon_sad.gif[/IMG]
Check this out: [SIZE=2][COLOR=#333333][FONT=Ubuntu]Installation from a compressed image file in windows. [/FONT][/COLOR][/SIZE]**[COLOR=#222222][FONT=Verdana]https://help.ubuntu.com/community/Installation/UEFI-and-BIOS#in_Windows[/FONT][/COLOR]**


Just two steps and perfectly works. However Surface keyboard won't.
It is Ubuntu 14.04, and for some reason it's impossible to upgrade kernel for Live USB.

So I'm hoping there were compressed image for SP3 we can download [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

You'll need at least 15 for Surface Pro 3 Type Cover support, 14 LTS won't work. (unless you want to recompile the kernel) The procedure I wrote up lets you use 15 instead of 14. It won't support the Surface Pro 4 Type Cover, but maybe the upcoming version 16 will.

---

### Post by haoz2 on 2016-01-18
Awesome! Can't wait to give a try.:popcorn:

---

### Post by sudodus on 2016-01-18
@*Tom_S.*,

You have written  a nice tutorial for installing Ubuntu onto a microSD card (or USB drive) on a Surface Pro 3. I think it explains what to do quite well :-)

-o-

I went along another path and made a system by installing in UEFI mode into a pendrive with an MSDOS partition table and two partitions, with FAT32 for the EFI (boot) partition, and with ext4 for the root partition. I skipped the swap partition, but it is easy enough to add, if you wish. After the installation I remade the booting (re-installed grub twice, once for UEFI and once for BIOS, and with the option --removable, which I think makes it less vulnerable to attacks from Windows or from the UEFI system.

You can also install from [Compressed image file with a live Ubuntu 14.04.2 and an installed Ubuntu 15.10](http://ubuntuforums.org/showthread.php?t=2213631&page=4&p=13426191#post13426191) into a pendrive and try various patches and tweaks for the Surface Pro 3.

---

### Post by Tom_S. on 2016-01-19
*sudodus*, thank you for working on an updated disk image. I am sure that will help people - going through all those steps could be a bit much for new folks!
If there are any improvements that could be make to the process I wrote up, please let me know so I can edit it so others may benefit.
When you say your image makes it less vulnerable to attacks, are you referring to Windows overwriting the bootloader, or are you referring to being able to use Secure Boot to improve security and reduce the chance of bootloader attacks?

---

### Post by sudodus on 2016-01-20
I meant that the UEFI system or Windows should not tamper with the linux system. But I found that the system I made a day or two ago is vulnerable and can get damaged. (I noticed that after posting in your thread.) Yesterday I made another system with an installed Ubuntu 15.10 64-bit system, that I will test today, and I think it has better chances to survive attacks and mistakes. If successful I will upload it as another compressed image file and describe it in my tutorial thread.

I think secure boot is mainly a method for Microsoft to lock the computer to only use Windows, or at least to make it very difficult to use other operating systems.

---

### Post by sudodus on 2016-01-20
I made a system with a stable booting mechanism. I think it will work well in your Surface Pro 3 computer. See this link:

[Compressed image file with a live Ubuntu 14.04.2 and an installed Ubuntu 15.10](http://ubuntuforums.org/showthread.php?t=2213631&page=4&p=13426191#post13426191)

---

### Post by ankov on 2016-06-01
Actually lads, the whole procedure can be simplified significantly. Simply install it via a virtual machine and then fix file paths in the EFI image...

Instructions: [http://ankov.blogspot.bg/2016/06/ubuntu-uefi.html](http://ankov.blogspot.bg/2016/06/ubuntu-uefi.html)

---

### Post by alessio-cpt on 2017-04-11
Hello guys, sorry to revive an old thread.

I am following the guide posted by ankov, but whenever i plug the usb stick with ubuntu, I get the following error: "system bootOrder not found. Initializing defaults".
Then, the system reboots.

I tried to turn off and on secure boot and trusted platform module, ubuntu 16.04 and ubuntu mate, 2 different usb sticks; but I have always got the same result.
I would try the guide by Tom_S. but it looks quite complex and I have a feeling that I would get again the same result.

Do you have any idea how can I fix this or why is it happening?

---

### Post by ubfan1 on 2017-04-11
Use efibootmgr to set the bootOrder variable.  See the man page (man efibootmgr) for more details. Get the items with  
sudo efobootmgr -v  
Then use the -o switch to set the order to what you want  
sudo efibootmgr -o 0,3,4    or whatever order you want them.
If that doesn't work, that's a bug in the firmware.  Are you at the latest firmware revision?

---

### Post by alessio-cpt on 2017-04-13
**Solved**, I booted the usb pen drive from a virtual machine and installed boot repair ([https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)). I launched with the following custom options: force delete grub, update grub, hard-coded efi. This cleaned the efi partition and created three folders inside /EFI: Boot, Microsoft and Ubuntu.  At this point, I could still not boot. The Boot folder contained only bootx64.efi and bkpbootx64.efi. I deleted bootx64.efi and copied grubx64.efi, grub.cfg and shimx64.efi from the ubuntu folder to the boot folder. Then I renamed shimx64.efi in bootx64.efi. After that I could finally boot the system. I am not sure why it was not working before or why it is working now, but I hope it can help someone.


> **ubfan1 said:**
> Use efibootmgr to set the bootOrder variable. See the man page (man efibootmgr) for more details. Get the items with 
sudo efobootmgr -v 
Then use the -o switch to set the order to what you want 
sudo efibootmgr -o 0,3,4 or whatever order you want them.
If that doesn't work, that's a bug in the firmware. Are you at the latest firmware revision?


I am not really sure how I can do this. I could not boot in the ubuntu system until I solved this problem except using a virtual machine. Of course, I could change the bootorder in the virtual machine but it would not have any effect on the surface. Also, I think the problem here is that the bootOrder is hardcoded in the firmware, that's why I had to play with the files.


My firmware version is 3.11.2050.


If you have a similar problem, I would advice to launch the virtual machine and play with the files there. In a VM you have access to the uefi shell, and that helps a lot when you are looking for the missing files. Also, you do not have to reboot thousand of times to test different .efi files.

---

