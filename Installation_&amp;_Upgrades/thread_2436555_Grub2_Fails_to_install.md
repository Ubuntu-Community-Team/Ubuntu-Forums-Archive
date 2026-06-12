---
title: "Grub2 Fails to install?"
date: 2020-02-08
forum: Installation &amp; Upgrades
---

### Post by dustyt on 2020-02-08
The laptop is a Lenovo Ideapad 320-15IAP with 8gb ram

The Flavor is Ubuntu Budgie 19.10

I am installing to dual boot with windows 10.

Secure boot is off in the bios if you want to call it that. Fast boot is not enabled in windows 10 either.

The OS installs but at the end grub fails to install. I have reinstalled twice to see if it was a fluke. I have installed selecting dev sda and also dev sda1 Windows boot manager. I have tried booting from the laptop boot menu which lists ubuntu. But I get the grub bash like editing deal. I have double checked to see that everything is EFI, usb and install and also made sure that the hard disk was actually sda not the live usb. I have confirmed the OS is installed on the hard disk sda. I have tried using the live usb again to boot up and then done did stuff at the command line to get boot-repair. Followed those instructions. The top button on that recommended. This does not work either. It says it needs to be a live session? But I'm booting a live usb, lol.

I have tried many ways to manually install grub by terminal. This also fails with an error can't find EFI directory, both using sda and sda1 no difference. I have checked GUI and terminal and can see the EFI directory no problem. Like I said I can select ubuntu from the laptop boot menu from F12. I can see ubuntu in the file. 

Inside EFI is Boot - Insyde - Microsoft - ubuntu
 Inside ubuntu is BOOTX64.CSV - grub.cfg - grubx64.efi - mmx64.efi shimx64.efi
There's very little text in grub.cfg but it does say root is hd0, gpt7 which is where I installed it, so that is correct.

I can't fix it. I have spent 2 nights running all sorts of fixes, and every one I can find anywhere just ends in a road block. I have tried so many that I have forgot the list of what all I have tried and failed at this point. I need some additional help here and can't find any. Im totally lost now.

Is it a permissions issue? drwxr-xr-x

Is it something specific to this laptop. I have found a couple other threads on it marked solved but they aren't really solved.

Is there a way I can just fix what I have so I can use F12 to go to the boot menu to select the OS and actually have it boot?

---

### Post by oldfred on 2020-02-08
Are you installing in UEFI boot mode?
Have you updated UEFI and if SSD, SSD firmware?

Lenovo may have some other UEFI settings.
UEFI update required for USB-C port issues 2017 thru 2019 models
ThinkPad models including the ThinkPad X1 Carbon (5th Gen to 7th Gen), X1 Yoga (2nd Gen to 4th Gen), and P-series 
[https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/](https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/)
Lenovo Thinkpad 430s UEFI update 19.10 install
[https://ubuntuforums.org/showthread.php?t=2432688](https://ubuntuforums.org/showthread.php?t=2432688)
Lenovo x390 'optimized os set up' must be off

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by dragonfly41 on 2020-02-08
This does not answer why your grub configuration does not work .. but as a separate "get out of gaol" card I would try installing rEFInd which is described in [post #8 in this recent thread.]("https://ubuntuforums.org/showthread.php?t=2436339")

---

### Post by dustyt on 2020-02-08
> **oldfred said:**
> Are you installing in UEFI boot mode? **YES**
Have you updated UEFI and if SSD, SSD firmware? **YES**

Lenovo may have some other UEFI settings.
UEFI update required for USB-C port issues 2017 thru 2019 models
ThinkPad models including the ThinkPad X1 Carbon (5th Gen to 7th Gen), X1 Yoga (2nd Gen to 4th Gen), and P-series 
[https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/](https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/)
Lenovo Thinkpad 430s UEFI update 19.10 install
[https://ubuntuforums.org/showthread.php?t=2432688](https://ubuntuforums.org/showthread.php?t=2432688)
Lenovo x390 'optimized os set up' must be off **DOES NOT HAVE THIS SETTING**

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) &  
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/) **I HAVE TRIED THIS SEVERAL TIMES. FOLLOWED STEP BY STEP. DOES NOT WORK. TOOL STATES IT NEEDS TO BE IN A LIVE SESSION, WHICH OF COURSE I AM IN BY THE LIVE USB? I DON'T UNDERSTAND? I CAN DO IT AGAIN AND TRY TO RUN THE REPORT.**

During install grub2 will not install in the first place. Fails to install after the OS is installed.
ubuntu is a UEFI boot option via F12 at startup. But it can't boot because grub isn't installed due to failing.
The repair tool refuses to work saying it needs a live session which I am in while trying to run it.
Manual install of grub by booting live USB and setting up to chroot into my install in terminal errors out saying cannot find EFI directory, but the directory is there?

None of it makes any sense to me. That is why I was trying to ask if there was some way the laptop was blocking the whole EFI partition? Or if the file permissions might be preventing installation. But none of it seems to be the case because there is an ubuntu directory in the partition and there are some files within it.

---

### Post by oldfred on 2020-02-08
Boot-Repair bug from 2014, supposedly fixed. But not sure exactly what issue was.
[https://bugs.launchpad.net/boot-repair/+bug/1281815](https://bugs.launchpad.net/boot-repair/+bug/1281815)

Try dosfsck on the ESP. Change from example with sda1 to your ESP.
dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities

Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

Post this:
sudo parted -l

---

### Post by dustyt on 2020-02-08
Interesting because that is exactly what is happening to me trying to run boot repair. Fixed 6 years ago but I am experiencing it now.

I will peck along on this and post what I find in a bit.

---

### Post by dustyt on 2020-02-08
**Results of sudo parted -l **

Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  274MB   273MB   fat32           EFI system partition          boot, esp
 2      274MB   290MB   16.8MB                  Microsoft reserved partition  msftres
 3      290MB   489GB   489GB   ntfs            Basic data partition          msftdata
 6      489GB   505GB   16.0GB  linux-swap(v1)
 7      505GB   537GB   32.0GB  ext4
 8      537GB   837GB   300GB   ext4
 9      837GB   972GB   135GB   ext4
 4      972GB   999GB   26.8GB  ntfs            Basic data partition          msftdata
 5      999GB   1000GB  1049MB  ntfs            Basic data partition          hidden, diag

**See anything good or bad here that I'm not catching?**


Model: PNY USB 2.0 FD (scsi)
Disk /dev/sdb: 124GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  124GB  124GB  primary  fat32        boot, lba

---

### Post by dustyt on 2020-02-09
sudo dosfsck -t -a -w /dev/sda1
fsck.fat 4.1 (2017-01-24)
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupt.
 Automatically removing dirty bit.
Performing changes.
/dev/sda1: 241 files, 9388/65536 clusters

**Also done.**

---

### Post by dustyt on 2020-02-09
OK... and to thicken the plot here :) and cover a bit of my night's work... I think I will blame Lenovo for this issue.

I went through this stuff, then decided to blow it out again, then but the live usb, run the stuff, then install for a 3rd time, because 3rd time is the charm right? ;)

Well maybe not... same dang thing.

I got really mad and this made me go through with trying it on my work laptop, although I had been very hesitant to do anything on it at all, not wanting to deal with a broken work computer. It all installed just fine. In fact I am on it typing this. What made me really do it is my work laptop is an HP and also has bios from Insyde.

So it is something for sure related to her Lenovo laptop bios crap, or something I am unaware of in her install of Windows 10. I am going to more closely compare the two bios versions. Maybe hit up Lenovo for some complaining and see if there is a flash I can do or anything? 

Typing this makes me remember something else. Her dang laptop refuses to "keep" the UEFI boot order I select. Specifically, I have moved USB to the top several times and saved it for the obvious reason of a lot of usb booting to let her test different distros and all this work I have done trying to get things working. It keeps moving Windows 10 back to the top of that list. I don't know if this offers a key clue in my grub install issue or not?

---

### Post by dustyt on 2020-02-09
Here is a copy of my last try at reinstalling grub manually, hoping there's some clues within...

ubuntu-budgie@ubuntu-budgie:~$ sudo mount /dev/sda7 /mnt
ubuntu-budgie@ubuntu-budgie:~$ sudo mount /dev/sda1 /mnt/boot/efi
ubuntu-budgie@ubuntu-budgie:~$ for i in /dev /dev/pts /proc /sys /run; do sudo mount -B $i /mnt$i; done
ubuntu-budgie@ubuntu-budgie:~$ sudo chroot /mnt
root@ubuntu-budgie:/# grub-install /dev/sda
Installing for x86_64-efi platform.
grub-install: warning: Cannot set EFI variable Boot0000.
grub-install: warning: vars_set_variable: write() failed: Interrupted system call.
grub-install: warning: _efi_set_variable_mode: ops->set_variable() failed: No such file or directory.
grub-install: error: failed to register the EFI boot entry: No such file or directory.

It's 5am, I am fried.... nap time.

---

### Post by dustyt on 2020-02-09
Unbelievable!!!!!

So I went to close everything out on both laptops. I had the grub folders open on both graphically and "my" grub.cfg open as there wasn't one on hers. 

In a grumble command type just to see what kind of dang error I would get, I ran update-grub after the above.

It ran and spit an input-output error at the end, and I decided to shut down after and try it again via the uefi boot menu.

Would you believe it worked? Grub came right up and I booted right in. 

Self-solved out of frustration.

So the fix is run the above commands to mount (sub your root directory)(mine was sda7) and then run update-grub anyways. Reboot, hit key to bring up uefi boot selection menu, select ubuntu and see if it works.

---

### Post by dustyt on 2020-02-09
All in all it continues to work and boot up, etc. 

But after a bit I realize this is not really solved. It's just a work around. I mean grub works and all. But the root problem that caused grub install issues still persists. 

It was apparent when I ran updates. I saw some grub related errors in the update activity

---

### Post by coley9225 on 2020-02-16
I also have a Lenovo ideapad 320, and I think your right, it's a lenovo issue. It took me 2 years to get lubuntu18.04 install, same issues your having. My work around my not work, as they changed the installer. With ubiquity( the installer for lubuntu 18.04) I used terminal command ubiquity -b, and that runs the install without installing bootloader, BEFORE restarting computer, I installed and ran bootrepair. the install worked and boot repair got me so I cpild boot into windows or lubuntu. I did have to boot lubuntu and purge and reinstall grub to end error messages. I hope there is a way to do the same process with the new installer because I'm having trouble installing 19.10 as well. If you find a way to install with this method, it may get you up and running. Good luck.

---

### Post by vidtek on 2020-02-16
Coley-

I have had similar experiences with my Asus bios, it seems to do it's own thing on a random basis, there seems no logic to it.

Occasionally when I have need to access Windows 10, (rare event now), I use the Grub2  entry to do so.

Sometimes when leaving the Windows 10 (always use the restart option otherwise linux can't access my other ntfs drives and I have to reset the dirty bit) the bios takes me straight back to the Windows boot bypassing the grub2 menu altogether.  
I look in the bios boot order list and ....no sign of any linux entry.  ..........Weird.

I then have to do the chroot thing to re-install grub as here:[https://ubuntuforums.org/showthread.php?t=2436958&p=13932625#post13932625]("https://ubuntuforums.org/showthread.php?t=2436958&p=13932625#post13932625")

I could almost do this blindfolded now....

Cheers Tony.

---

### Post by dustyt on 2020-02-18
Yeah, I installed 19.10 and did that workaround and it is still rocking along.

I think I am done doing business with Lenovo. I don't like the UEFI Bios they are using, and I don't like the fact Windows can walk right in there and cause issues. Particularly with windows updates. 

I am sure you can imagine having a daughter away at college end up in a new area of campus, end up connecting to a new network that isn't set to metered, so an automatic update occurs, and then she is calling you freaking out because her keyboard stopped working and she has work due the next day.... and all you know going in is keyboard quit and work is due. Real fun. I just had to make the trip and figure it out. It's happened twice now.

I'm proud. She sat down with me and had a look at Linux one weekend and now she is turning into a dyed in wool linux girl. 

I think I am going to file a complaint with Lenovo rather it does any good or not. And if nothing can be done I may replace it with an HP similar to mine. It sucks though because I have a TB drive and 8gb of ram in that Lenovo, and I am pretty sure that memory is a different type than HP uses.

---

### Post by oldfred on 2020-02-18
In Ubuntu you can turn off the auto updates. But it wants to apply security based updates.
Then when computer connected to the Internet at home or someplace with higher limits, updates can be run.

Some vendors now are starting to support UEFI update from Linux. Dell started a while back as it offered Ubuntu systems.
Others now adding newest systems.

[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist) & 
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)

---

