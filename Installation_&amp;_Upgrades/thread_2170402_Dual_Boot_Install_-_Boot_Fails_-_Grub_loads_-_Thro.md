---
title: "Dual Boot Install - Boot Fails - Grub loads - Thrown to initramfs"
date: 2013-08-26
forum: Installation &amp; Upgrades
---

### Post by ktz84 on 2013-08-26
Hi,

I have Windows 7 installed on custom built pc. I installed Ubuntu 13.04 x64 from a USB stick using unetbootin. Install seem to go smoothly. When I restarted after the install it wouldn't boot in so I set the grub (using e to amend the linux line to take out the quiet splash or whatever it's called and also put in nomodoset in case it was graphics. This is what I end up with:

[IMG]https://dl.dropboxusercontent.com/u/3136192/IMG_20130826_090817.jpg[/IMG]

It boots to grub fine and I can boot into windows without issue. I've no idea what to do now.

Here's the computer specs in case it might be of use.

CPU: AMD Athlon II x4 640
Motherboard: Gigabyte 8800GA-UDH3H Rev 2.1          
Memory:4x4GB DDR3 PC3-10666C9 1333MHz Low-Volt Dual Channel A-Data
Graphics Card: MSI HD 6850 OC 1024MB GDDR5 PCI-Express
Sound Card: Onboard          
Monitor/Display:Samsung 32" TV connected via HDMI @ 1920 x 1080
Hard Drives:
         Intel 120GB SSD[COLOR=#ff0000] (This is where Ubuntu is installed)[/COLOR]
        Samsung 1TB SATA
        Samsung 2TB SATA3
        Maxtor 160GB SATA [COLOR=#ff0000](This is where the Windows 7 System and Install Partitions are)[/COLOR]
        WD Caviar Green 2TB Internal Hard Drive SATA3          
Keyboard & Mouse: USB Logitech s510 Deskset
Network/Internet: Connected via Gigabit Ethernet Connection with Internet Speed at 56MBPS DOWN / 16MBPS UP
USB Connected Devices (currently removed in case any of those were casing problems):
        Canon Pixma MP460 Printer
        Logitech Quickcam Pro 4000 Webcam
Other PCI cards: Really old Leadtek Analog TV Capture Card (can't remember model details) & USB Ports connected to onboard USB header.

---

### Post by oldfred on 2013-08-26
I do not know if AMD has AHCI as a setting, but drives should not be IDE. Check what options you have in BIOS.
You may need another boot option in addition to nomodeset.
Did Ubuntu work in live mode without any issues?

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by ktz84 on 2013-08-26
Olfred,

I've looked at the BIOS and I do see options for AHCI however I have no idea what to set them up as as I wasn't sure if you were saying AHCI was good or bad. The OnChip SATA is set to Native IDE. The other options are RAID and AHCI. There is also an entry for Oboard SATA/IDE Ctrl which is set to IDE and the description reads: Sata ports work as IDE Mode. The other options are: RAID/IDE and AHCI.

I have installed the boot-repair and ran it.

The paste results from the pre boot are:

[http://paste.ubuntu.com/6029369](http://paste.ubuntu.com/6029369) and the post repair is:

[http://paste.ubuntu.com/6029393](http://paste.ubuntu.com/6029393)

Post repair throws the same errors.

---

### Post by Quackers on 2013-08-26
The error message on your screen is saying that it can't find your /dev/sde1 partition (by UUID) 
This can sometimes be caused by that hard drive being slow to spin up and therefore not being ready by the time grub tries to read its files.
If that is the problem a rootdelay=30 (or similar) may get around your problem. What that does is tell it to wait 30 seconds before looking for that drive.
This boot prompt can be entered in the same way (and same place) as the nomodeset option you have already tried.

---

### Post by ktz84 on 2013-08-26
> **Quackers said:**
> The error message on your screen is saying that it can't find your /dev/sde1 partition (by UUID) 
This can sometimes be caused by that hard drive being slow to spin up and therefore not being ready by the time grub tries to read its files.
If that is the problem a rootdelay=30 (or similar) may get around your problem. What that does is tell it to wait 30 seconds before looking for that drive.
This boot prompt can be entered in the same way (and same place) as the nomodeset option you have already tried.

Quackers this is an SSD. Would that still apply?

---

### Post by Quackers on 2013-08-26
I have no idea but I wouldn't have thought so. Having said that it's worth trying a small, one-time boot prompt to see :-)

---

### Post by ktz84 on 2013-08-26
> **Quackers said:**
> I have no idea but I wouldn't have thought so. Having said that it's worth trying a small, one-time boot prompt to see :-)

No problem. I'll give it a go.

---

### Post by oldfred on 2013-08-26
I would also change to AHCI, but you have to install drivers for that into Windows before you change.

Boot-Repairs auto repair installs grub everywhere. I would be better to have the Windows boot loader in sda. You can use Boot-Repair, uncheck auto repair, but then check the update MBR. Then under advanced setting choose to add a Windows boot loader to sda.

Are you booting from sde in BIOS?

---

### Post by ktz84 on 2013-08-26
Dumb question but I take I should enable AHCI on both the Controller and the Onboard SATA/IDE Ctrl?

The initial hard drive priority had the sde last however I changed that 1st when I realised that grub wanted it to run from there. It was initially on the 160GB Maxtor Hard Drive which I think sda.

---

### Post by ktz84 on 2013-08-26
Well sde is sdb which I presume is becuase I changed the boot order in the BIOS. The boot-repair doesn't match what I've been asked to do therefore I'm confused as to what options I should be chosing.

There is only an option to repair or create the boot info report. In Advanced there are 5 Tabs of one (MBR Options is currently greyed out).

The other 4 menus are: Main Options which has OS to boot by Default. As present this is set to sdb1 Ubuntu 13.04. Place Grub in all disks (except USB disks without OS) is checked. The next option is place grub into of which I can chose any drive. Is this where you want me to chose sda

The next tab has GRUB Options and there we have.
Purge GRUB before uninstalling it
Upgrade GRUB to its most version (greyed out)     GRUB Legacy
Reset extra space after MBR (solves the [FlexNet]error)
Uncomment GRUB_GFXMODE (solves the[no-signal / out-of-range] error)
ATA dis support (solves [out-of-disk] error)
Add a kernel option:
Purge kernels then reinstall last kernel
Edit configuration file

Finally Other Options
Place boot flag on (uncheck however I'm thinking this is where you want me to check it and choose sda)
Create a BoofInfo Summary (checked)
Participate to statistics in use (checked)
Check internet connection (checked)

I didn't want to chose the boot flag option as I couldn't work out where do the MBR update.

Can you please advise.

---

### Post by oldfred on 2013-08-26
In advanced unselect install grub and select restore MBR.
Then under MBR options choose sda and restore generic.

---

### Post by ktz84 on 2013-08-26
Unfortunately still the same message. I've tried it by booting the ssd first and booting the windows system disk first. I've tried with or without achi enabled and with and without nomodeset set in grub.

The boot repair page is at [http://paste.Ubuntu.com/6030024](http://paste.Ubuntu.com/6030024)

---

### Post by Quackers on 2013-08-26
I'm not clear on which drive is set to boot first in the BIOS.
Your drive designations keep changing, it seems. 
What was /dev/sde earlier is now /dev/sdb
/dev/sda now appears to have Syslinux installed in the MBR
Your bootable Windows installation is on /dev/sdc which also seems to have grub installed in the MBR of the drive.

I'm not sure how you keep track of all this with regard to setting boot priority in BIOS.

---

### Post by oldfred on 2013-08-26
The syslinux should be on the Windows drive.

As Quacker comments drive order is changing a lot. The order is usually set by BIOS and may be different if drives come up to speed at different times.
On my system they are somewhat consistent. But I skipped one port on motherboard and if I reboot with a bootable flash drive that port then is sdb which then renumbers all the higher drives. Otherwise drives are in port order on motherboard.

---

### Post by ktz84 on 2013-08-26
As I was enabling and disabling AHCI it kept changing the order of the drives. It kept throwing the usb stick that I'm using to boot into a live version of linux to the top. It then goes to Maxtor disk and the SSD where Linux is installed the final drive on the list. I'm unclear myself which drive is supposed to be set as the boot drive. I thought it should be SSD as I wanted to boot into Linux so I kept changing it back to the top of the hard disk priority list. Should I have left it where it was?

I've enabled AHCI in Windows and corrected the registry so it is bootable so I will not need to change those options back and forth anymore so that's one less complication now.

---

### Post by Quackers on 2013-08-26
I think it's probably best to leave the Ubuntu drive at the top of the boot list.
I would also (for the sake of simplicity) disconnect all drives except the Ubuntu drive and the Windows system drive (not the data drives).
That would simplify things a bit.

There still remains the fact that grub can't find your Ubuntu system partition. Now that could be because the wrong drive is attempting to boot (as grub seems to be installed all over the place - even in drives that aren't bootable) so you can't be sure which edition of grub is doing the looking.

---

### Post by ktz84 on 2013-08-26
OK all but two drives now connected. Linux not bootable. Windows still bootable.

---

### Post by Quackers on 2013-08-26
So Windows boots when you select that drive in BIOS but Ubuntu still gives the same error - initramfs with the same UUID missing

---

### Post by ktz84 on 2013-08-26
> **Quackers said:**
> So Windows boots when you select that drive in BIOS but Ubuntu still gives the same error - initramfs with the same UUID missing

I'll check but I'm pretty sure that Windows boots no matter which drive is set as the highest priority in the BIOS. For instance I'm booted into windows at the min and the ssd where linux is installed is at priority 1 in the boot list that's why I'm pretty sure this is the case. Just to be double sure I'll do an F12 which brings up a boot list and chose the linux drive and then in grub chose Windows 7 and see if it boots.

---

### Post by ktz84 on 2013-08-26
Yep chose Linux drive but still booted into windows.

---

### Post by Quackers on 2013-08-26
Ok thanks.  Did you by any chance encrypt Ubuntu on installation?

Please try booting Ubuntu and it will go to that initramfs busybox message.
Leave it showing for 20 or 30 seconds then type exit and hit the enter key - what happens?

---

### Post by ktz84 on 2013-08-26
No encryption. Just done the exit and return. Exit just throws the same error immediately after i hit return.

---

### Post by oldfred on 2013-08-26
I found these that had similar issues, but am not sure if what each did was really the solution.

  SOLUTION: ! /dev/disk/by-uuid/ ...<your UUID>.... does not exist 
[http://ubuntuforums.org/showthread.php?t=1127779](http://ubuntuforums.org/showthread.php?t=1127779)
[http://ubuntuforums.org/showthread.php?t=1565714](http://ubuntuforums.org/showthread.php?t=1565714)
"If the “apt-get upgrade” does not successfully complete then a flag is set and update-initramfs does not get to run, hence grub gets all messed up. You should be able to boot using the old kernel and then run the sudo update-initramfs –u -k command. Then run sudo dpkg –reconfigure. That should clear the upgrade flags and fix any broken packages."

   Gave up Waiting for Root Device? Change from UUID to sdaY
[http://ubuntuforums.org/showpost.php?p=10058668&postcount=2](http://ubuntuforums.org/showpost.php?p=10058668&postcount=2)


 ALERT! /dev/disk ... does not exist." error
Boot the machine and go to BIOS configuration (F2) and change:
Advanced -> SATA Controller Mode
from "AHCI" to "Compatibility"

---

### Post by Quackers on 2013-08-26
Many people have had this error in the past. Some have fixed running the boot repair utility.
Others have run fsck on the affected partition.
Still others have re-installed grub and fixed it.
Yet others have resorted to re-installing Ubuntu completely to fix it.

The quickest way would be to try re-installing grub via chroot from the live cd desktop - maybe even purging grub first (scroll down that page to the chroot section). There is a guide by drs305 that I have always used and the link is given below.
Obviously no guarantees here. I'm not entirely convinced that this will work but it is worth a try.

[http://ubuntuforums.org/showthread.php?t=1581099&highlight=re-install+grub]("http://ubuntuforums.org/showthread.php?t=1581099&highlight=re-install+grub")

Failing that I would suggest that if possible you re-install Ubuntu making sure that you install grub to the drive you are installing Ubuntu to - /dev/sdb in the current circumstances but you can check that at the time. Make sure it doesn't install grub on /dev/sda (the default). You would do this on the partitioning page after choosing "something else" in the appropriate screen.
Obviously if you have a lot of stuff already in your Ubuntu install you would be averse to this option.

EDIT also see oldfred's post above!

---

### Post by ktz84 on 2013-08-27
I've done the reinstall via chroot via grub and that didn't make any difference. Same error. I've reinstalled the whole operating system and made sure the boot drive was set as my SSD where I was intalling ubuntu on. If I boot and set my Windows disk as the first boot device I end up at grub rescue. That sounds good to me as it says grub isn't set up on it. If I set my ssd where linux is installed up as the first boot device then I get the same old error.

I've tried the trick of naming the device rather the UUID that was given above however the instructions are old and grub has changed. There are two search lines therefore not sure which to take out and there is then else statement between them therefore it's not just as easy as removing one as syntax is no longer correct. Anyway all I get is messages by grub when I try that method is that the commands weren't understood.

Here's the latest boot-repair summary:

[http://paste.ubuntu.com/6031828](http://paste.ubuntu.com/6031828)

---

### Post by Quackers on 2013-08-27
Now you've got grub installed on the Windows drive too! You should be able to repair that with a Windows repair disc.
You can't name the device like others can  because your device designations keep changing.
If the re-install hasn't worked I'm running out of ideas here.
Are you installing a 32 bit or 64 bit Ubuntu?

---

### Post by oldfred on 2013-08-27
Set BIOS to boot from SSD.
As an experiment, at grub menu use e for edit and we will change to boot by device.

Change this line:
       set root='hd1,msdos1'
to

 set root='hd0,msdos1'

And then delete the entire search line everything from if to fi
Delete:

 
>  if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root --hint-bios=hd1,msdos1 --hint-efi=hd1,msdos1 --hint-baremetal=ahci1,msdos1  6a7de62b-8809-48ea-bad1-659c2ed84e5d
else
  search --no-floppy --fs-uuid --set=root 6a7de62b-8809-48ea-bad1-659c2ed84e5d
fi


These are one time changes, so nothing permanent is changed.

---

### Post by Quackers on 2013-08-27
How old is this hard drive? Could it be failing?

---

### Post by ktz84 on 2013-08-27
> **Quackers said:**
> How old is this hard drive? Could it be failing?

It's about a year old and it was my primary installation disk for windows before I moved windows off it to a new partition on a new drive as my plan was to use Ubuntu as my primary system hence why I wanted the faster performance that an ssd will give me. I have had no trouble from this disk so I'd be surprised if this was the case. Indeed I have no problem accessing the drive from a live environment or having it recognised by the BIOS and boot-repair.

---

### Post by Quackers on 2013-08-27
Ok, thx. Did you see Oldfred's post previous to my last?

---

### Post by ktz84 on 2013-08-27
Hi Thanks Quackers. Yes I've seen both your and Oldfred's responses. I was testing Oldfred's first as it was the easier of the 2 to accomplish. It was had interesting results I feel. If I change to hd0 I get the same error however if I leave it at its default of hd1 with those search lines also removed I get a message to say that vmlinuz-blahdeblah image is missing. It needs a kernel or words to that effect. That seems interesting to me as it at least suggests that the linux image is seen on hd0 and not hd1.

As to your message I don't need to run a windows repair as windows boots properly form sda2. There are two windows entries listed in grub. One on the system partition of windows which is obviously unbootable and the one on the window installation partition and that one does boot.

It's a 64 bit install.

---

### Post by ktz84 on 2013-08-27
Just whilst I'm booted into the live enviroment and I thought I would take a look at the ubuntu disk and see what I could see on it. I see a shortcut called vmlinuz and the properties shoow this:

Name: vmlinuz
Type: Link to DOS/Windows executable (application/x-ms-dos-executable)
Link target: boot/vmlinuz-3.8.0-19-generic
Location: /media/ubuntu/6a7de62b-8809-48ea-bad1-659c2ed84e5d
Volume: 103 GB Volume
Accessed: Tue, Aug  6 2013 00:00:00

If I go to a terminal and sudo su and then cd into /media/ubuntu I can see that there is an entry for: 6a7de62b-8809-48ea-bad1-659c2ed84e5d

The directory listing for that directory is:
```
root@ubuntu:/media/ubuntu/6a7de62b-8809-48ea-bad1-659c2ed84e5d# ls -l
total 116
drwxr-xr-x   2 root root  4096 Aug 27 08:40 bin
drwxr-xr-x   3 root root  4096 Aug 27 08:41 boot
drwxr-xr-x   2 root root  4096 Aug 27 08:38 cdrom
drwxr-xr-x   4 root root  4096 Apr 24 17:06 dev
drwxr-xr-x 136 root root 12288 Aug 27 08:42 etc
drwxr-xr-x   3 root root  4096 Aug 27 08:39 home
lrwxrwxrwx   1 root root    32 Aug 27 08:40 initrd.img -> boot/initrd.img-3.8.0-19-generic
lrwxrwxrwx   1 root root    33 Aug 27 08:37 initrd.img.old -> /boot/initrd.img-3.8.0-19-generic
drwxr-xr-x  22 root root  4096 Aug 27 08:40 lib
drwxr-xr-x   2 root root  4096 Apr 24 17:02 lib64
drwx------   2 root root 16384 Aug 27 08:36 lost+found
drwxr-xr-x   3 root root  4096 Apr 24 17:01 media
drwxr-xr-x   2 root root  4096 Apr 19 09:03 mnt
drwxr-xr-x   2 root root  4096 Apr 24 17:01 opt
drwxr-xr-x   2 root root  4096 Apr 19 09:03 proc
drwx------   2 root root  4096 Apr 24 17:07 root
drwxr-xr-x  11 root root  4096 Apr 24 17:06 run
drwxr-xr-x   2 root root 12288 Aug 27 08:42 sbin
drwxr-xr-x   2 root root  4096 Jun 11  2012 selinux
drwxr-xr-x   2 root root  4096 Apr 24 17:01 srv
drwxr-xr-x   2 root root  4096 Jan 30  2013 sys
drwxrwxrwt   2 root root  4096 Aug 27 08:42 tmp
drwxr-xr-x  10 root root  4096 Apr 24 17:01 usr
drwxr-xr-x  13 root root  4096 Apr 24 17:08 var
lrwxrwxrwx   1 root root    29 Aug 27 08:40 vmlinuz -> boot/vmlinuz-3.8.0-19-generic
```

And /boot has the following entries:

```
root@ubuntu:/boot# ls -l
total 4386
-rw-r--r-- 1 root root  918868 Apr 17 18:42 abi-3.8.0-19-generic
-rw-r--r-- 1 root root  154942 Apr 17 18:42 config-3.8.0-19-generic
drwxr-xr-x 1 root root      60 Aug 27  2013 grub
-rw-r--r-- 1 root root  176764 Dec  5  2012 memtest86+.bin
-rw-r--r-- 1 root root  178944 Dec  5  2012 memtest86+_multiboot.bin
-rw------- 1 root root 3059890 Apr 17 18:42 System.map-3.8.0-19-generic
```

None of that is probably any use but I'll put there in case it is.

---

### Post by ktz84 on 2013-08-27
Ok I think that grub is confused. The fact that it seems to recognise hd0 has a having a valid kernel yet hd1 as not seems odd as in the boot-repair file I posted above sda1 is hd0,msdos1 and sda2 is hd0,msdos2 yet in the boot summary at the top of that file sda is clearly the windows hard drive given the formatting, size and labelling and sdb the linux ssd and given what I've just posted above the linux kernel referred to in grub and the uuid match everything that is on sdb or hd1. So why does it complain that hd1 doesn't have a valid kernel?

---

### Post by ktz84 on 2013-08-27
Ok had enough of tryign to get Ubuntu to play ball so decided to try and Ubuntu-Gnome 13.04 x64 cd and it installed without a hitch. I do begrude marking this as solved as the actual problem wasn't resolved but just glad to get it closed anyway.

Thanks to those that tried to help me sort this, it was very much appreciated. Boots really quick and opening things really, really fast so happy so far.

---

### Post by oldfred on 2013-08-27
It depends on what drive you set in BIOS to boot from.
Grub always sees from BIOS the boot drive as hd0, and that often used to create this type of issue. But the search by UUID is to override an incorrect device setting if it is wrong. It looks like the original install had grub installed to sda, but Ubuntu was on sdb. So the setting in the grub menu was to hd1 as when BIOS boots hd0 then the other drive is hd1.
The boot from Ubuntu drive and then manually changing hd1 to hd0 and deleting the search as it also has a hint of hd1,  should have been correct on a pure device setting, but did not work?

The suggestion of having Windows boot loader in sda, is if Ubuntu's grub does not load menu from booting sdb then you can reset BIOS to boot sda and direct boot Windows instead of a grub rescue. You get grub rescue from sda now since grub was updated and now that one is not correct.

Started typing while you posted. Did you set grub to install to the Ubuntu drive or sdb when re-installing?

---

### Post by ktz84 on 2013-08-27
Oops, unfortunately I did as that's what I thought I was meant to do and I've experienced the grub resuce when I readded all my drives back in again however adding my ssd back to the top of the list resolved that. I can see how having it on the windows disk as well would help if something went wrong with the ubuntu.

---

### Post by Quackers on 2013-08-27
I'm glad to see that you are up and running, eventually.
I have done some searching about and there are many instances of this problem. However, most are solved by re-installing grub or Ubuntu.
Those that don't get solved that easily tend to be on multi-harddrive systems AND on systems that change disc designations regularly.
As you said earlier, maybe grub gets confused. It would certainly seem so. In your case I'm not even convinced that grub was actually seeing your /boot/grub file at all, though I don't know why that would be.

Anyway, glad to see you're running ok now.

---

### Post by oldfred on 2013-08-27
We like to fix things, maybe to understand what is wrong. And sometimes spend days fixing things when a reinstall is really the quickest & easiest solution. :)

Glad you got it working.

---

### Post by ktz84 on 2013-08-27
Thanks again. Now that I knew that everything should install ok I actually wiped out the Ubuntu-Gnome install and installed Ubuntu again. Same problems returned. Next I decided to install xubuntu 13.04 x64 this time and it installed and booted wthout issue. So there's definitely something about Ubuntu and how it's playing with my system. The only difference between how both Ubuntu-Gnome and Xubuntu were installed was that they were installed from a DVD and Ubuntu was installed from a usb stick. The usb stick is seen as a hard drive so unless that somehow got itself entangled with the physical drives. If unity doesn't play well with xubuntu I could well go back to trying to install again but I'll give it a chance first.

---

### Post by Quackers on 2013-08-27
That is one thing that has also cropped up previously. Installing from a USB stick to a USB drive has also causes this error to appear. You weren't installing to a USB drive were you? 
It's all very curious. I definitely think that the multi-hard-drive systems are somehow messing up grub or its installation.

---

### Post by ktz84 on 2013-08-27
No I had checked that. Just mounted it there again and nothing on there that shouldn't be. I'm all out of dvds (plenty of cds but they are not big enough anymore for ubuntu installs) or I'd love to go back and check by installing from a dvd. If I find one I'll give it a go and report back.

---

### Post by ubfan1 on 2013-08-28
Looks like bug 384633.  Do feel free to add yourself to the "does this bug affect me" list.

---

