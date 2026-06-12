---
title: "Is it possible to retroactively change from legacy boot to UEFI Boot? 14.04.04"
date: 2023-04-12
forum: Installation &amp; Upgrades
---

### Post by jmssr13 on 2023-04-12
Hello,

I am currently in the midst of a very lengthy EOL hardware upgrade and am having issues with booting from EFI.
Pastebin: [https://paste.ubuntu.com/p/FKYBT6hMmN/](https://paste.ubuntu.com/p/FKYBT6hMmN/)

Background: I have a complicated program setup that I am not allowed to change that currently runs on an embedded computer. The current computer supports both legacy/uefi boot options. I can no longer purchase this board, and the latest revision supports only EFI. I cannot switch to another style of embedded computer at this time due to size/port constraints (a proprietary design was chosen before I could have a choice). I did not realize that the current system image doesn't support efi boot, and wasn't set up to do so until it failed to boot (lol)

I would like to know if it is possible to add the ability to boot via efi since everything is already set up for legacy. I do not care if the new image is only able to boot via efi, as I have many copies of the current legacy image. I created a fat32 partition of 512mb in gparted (sdb4), I also created a directory to store the efi information (/boot/efi) although I'm not incredibly familiar with ubuntu or linux and when I tried to use the advanced options in the Boot Repair tool I could not see sdb4 in the "Separate /boot partition" dropdown.

I could use any help at this point, I will provide as much detail as I can as quickly as possible. I can follow instructions fairly well, but if there are particular commands please type the exact command wherever possible instead of describing the action.

Thank you so much,
Justin

---

### Post by MAFoElffen on 2023-04-12
First, my disclaimer: Ubuntu 14.04 reached EOL on April 30th 2019. ESM (Extended Support Maintenance) extends that lifecycle to April 2024.

Embedded devices usually have the OS flashed in ROM. If there was a way (there is for traditional systems) are you able to make changes to the image so that there could be the addition of an EFI partition and Grub2 changes in the image? And I am assuming that the image may be specific to the hardware on that embedded board... So the chances for success for something like that might be slim. (Unless you found an image for that board that already has that.)

On normal systems, as I remember for LTS 14.04, you create an EFI partition of at least 512MiB and mark it as EFI/CSM, format the partition as Fat32, then you install 'grub-efi-amd64'  using the flags to point it to that new EFI partition... So that it creates the correct directory structure and installs the EFI files that the UEFI BIOS is going to look for. This all is also going to depend on if you can boot and chroot into the device, to be able to even attempt any of those changes. 

Or boot from an old image (also hinges on if changes can be persistent) and make the changes, and apply all the updates.

But that is not how embedded systems work. They exist on an embedded static OS image, that is usally compiled into an image. 

I just talked with Online Support Chat for Canonical Ubuntu Core- Embedded. My questions were above their support tier. They are finding someone for me to talk with. LOL (But they did ask me to apply for a position there.)

Instead of generalizations, abstracts and guesses, it might help if you  told me what the embedded device board was. Then I could research what  might be possible.

---

### Post by ubfan1 on 2023-04-12
To your fstab, add after the /boot line the ESP line:
UUID=7B61-9FD7  /boot/efi       vfat    umask=0077      0       1

Your (new) ESP appears empty, either populate it from copying another or run grub-install (from the grub-efi package, not the grub-pc one)
The link from the ESP to your root is in the ...EFI/ubuntu/grub.cfg file.  It is a 3 line stub to bring in the maintained grub.cfg from your root.  You need to change the UUID (if you copied it from another system) to match the UUID of your root: 67f5c402-b648-486d-88d4-5f86446ed4ec  and fix any explicit disk/partition hints like (hd?/msdos? ) . If the hints use (hd0,gptx), since you are leaving MSDOS partitioning, change the gpt to msdos.

That's about it, the root differences between an UEFI and legacy install are nothing that prevent booting or running.  Adding the /boot/efi and mounting the ESP allow updates to grub and shim, but that doesn't stop boot/run.  I ran two disks in a Lenovo, one booting UEFI and the other booting legacy, and would occasionally try cross booting, which always worked (maybe with some delays).

You should consider redoing the partitioning to gpt, just for future compatibility. Adding a small grub-bios partition to support legacy boot might be advisable just in case, or for testing. The msdos to gpt is pretty easy, without Windows complicating things.

---

### Post by MAFoElffen on 2023-04-12
I looked at you boot-repair report and I have questions.

You booted it in legacy boot mode, but your target is UEFI. WHY? That is why it didn't recommend any changes to convert it to EFI.

What is the partition hex type for /dev/sdb4? For UEFI as EFI, it should be set to ef00.

What is the CPU and Arch of the device? Back when, there were 32bit EFI systems, but they are not well supported.

---

### Post by oldfred on 2023-04-12
The only difference between UEFI boot & BIOS boot is the version of grub2. You now use grub-pc for BIOS and grub-efi-amd64 for 64 bit PC systems. There are other versions of grub for just about everything from Raspberry PI to IBM mainframes.

But you do have to have an ESP - efi system partition for UEFI boot. It is FAT32 with esp,boot flags.

While huge proponent of gpt and started using gpt in 2010, you may be the exception. If doing new install & restoring data you probably can convert. But if data is image of a partition, you cannot restore a MBR partition to a gpt partition.
Windows requires gpt for UEFI boot, but Ubuntu does not. It will boot in UEFI mode from MBR(msdos) partitioned drives.

Some tools to convert from MBR to gpt totally  erase a drive.
You can use this, but grub has to be reinstalled & any entry in fstab or elsewhere using UUID has to be updated. Better to convert only data drives.
Converting to or from GPT - must have good backups.
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

---

### Post by jmssr13 on 2023-04-13
H[SIZE=2]i MAFoElffen,

I guess that "Embedded PC" might not quite be the correct term, although it is what the manufacturer calls them. All of our currently deployed boards are these: [/SIZE]https://www.ieiworld.com/en/product/model.php?II=150
[SIZE=2]I am using this board from IEI for my current system image: [/SIZE]https://www.ieiworld.com/en/product/model.php?II=119.
I am upgrading to this board, which I was able to pre-order through IEI directly: [https://www.icp-deutschland.de/en/industrial-pc/cpu-boards-cpu-cards/embedded-boards/epic-nano/nano-ehl-j6412c-r10.html](https://www.icp-deutschland.de/en/industrial-pc/cpu-boards-cpu-cards/embedded-boards/epic-nano/nano-ehl-j6412c-r10.html)

Although the current ULT3 board is available through their website, their customer service team told me that the ULT3 board would be ending production due to the silicon shortage and that they could not fulfill my order, although I was able to get their only board left in stock. I am essentially picking up the pieces from a very sloppily done implementation that had no forethought into anything whatsoever. I have about 35 deployed, but we have no spares left.

If you would like any more information, I'll try my best to supply it. Thank you for the quick response.
Justin

---

### Post by jmssr13 on 2023-04-13
Hi MAFoElffen,

So in the BIOS for the board that supports legacy and efi, should I now attempt to boot using uefi mode? I will attempt to do so in the morning.
I will check the hex type in the morning and get back to you asap.
The current cpu is an intel skylake i3 6100u.
The new CPU is an intel Elkhart lake Celeron J6412.
Truthfully, I have no idea if the cpu will be compatible with 14.04. Also, these boards do not connect to the internet when deployed. I have the ability to connect them to download software for testing. 

I apologize if I am not describing things correctly, I am still learning.

---

### Post by MAFoElffen on 2023-04-13
I looked up the specs on that board. Yes is 64bit x86.

It still comes as pre-compressed images for Core ([http://cdimage.ubuntu.com/ubuntu-base/releases/14.04.1/release/](http://cdimage.ubuntu.com/ubuntu-base/releases/14.04.1/release/)), but since already installed... You are changing the installed system. 

Nice board. It most likely supports newer than 14.04 LTS but Ubuntu Core for Embedded Versions are supported for 10 years. So your directed limitation is still supported for another 2 years(?) Canonical had announced that starting with 14.04, that they would support Core Versions for 10 years.

What 'all' have suggested would work. On the Lubuntu LiveCD you used, if you started GParted and modified the EFI partition so that it says has Boot and ESP flags... Or used fdisk and changed the type to "1" for EFI... If you used gdisk, then the type code for ESP is "EF00"... 

Then mounted the system root, and mounted the EFI directory into /boot/efi/... chrooted into it, and installed grub-efi-amd64, then did
```

grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck --no-floppy

```
Then did 
```

lsblk -o NAME,SIZE,FSTYPE,LABEL,MOUNTPOINT,MODEL  # to see what to modify the partitIon in red in the next line
echo -e "/dev/disk/by-uuid/$(blkid -s UUID -o value [COLOR=#ff0000]/dev/sda4[/COLOR]) /boot/efi vfat defaults 0 0" >> /etc/fstab

```
To add the mount to the fstab file...

Then 
```

sudo update-initramfs -c -k all

```
That should do it.

EDIT: I spun up a 14.04.6 image to verify the commands, I couldn't find online man pages that old to ensure what was current for 14.04. LOL

---

### Post by jmssr13 on 2023-04-13
Hi MAFoElffen,

I have successfully added the flags to /dev/sdb4 in gparted, and my fdisk -l shows the following now: [https://imgur.com/a/Xp3sTf1](https://imgur.com/a/Xp3sTf1)[COLOR=#FFFFFF][FONT=&quot]
[/FONT][/COLOR]
What does "[COLOR=#000000]mounted the system root, and mounted the EFI directory into /boot/efi/... chrooted into it"[/COLOR] mean?

I'm not exactly sure how I would mount the system root. I know that you'd use mount /dev/sda4 ____ but do you know where the root would be? Would that just be doing "mount /dev/sda4 /boot/efi?"

I think I can do the grub install on my own, but I want to make sure this is getting mounted to the right place.

The help is very much appreciated,
Justin

---

### Post by ubfan1 on 2023-04-13
Mount the hdd root wherever you want, typically some empty dir under /mnt: /mnt/xxx.  Then chroot to that location,...

---

### Post by jmssr13 on 2023-04-13
So I've edited the /etc/fstab file to include the following:[COLOR=#000000]UUID=7B61-9FD7 /boot/efi vfat umask=0077 0 1[/COLOR] 

From my understanding that will allow the sda4 partition to automatically mount to /boot/efi upon every startup (which is appears to do upon reboot). Does that mean that I am ready to chroot to /boot/efi? Or should I do this: mount /dev/sda4 /mnt/esp and then: chroot /mnt/esp

Thanks for the help,
Justin

---

### Post by ubfan1 on 2023-04-13
I think the order is mount your root at /mnt/esp, then chroot there ( and do whatever else setup needed to fake a system), then mount the esp partition in your new root's /boot/efi, then run the grub-install.  But I've never done that myself, seems like a lot work just to set up a new directory and copy three files onto your esp.  (/boot/efi)/EFI/ubuntu directory, and grubx64.efi, shimx64.efi, and a three line grub.cfg stub with the new root's UUID and some edited disk/partition hints (hd0,msdos2) or whatever (copy an existing one and do your edits). I also copy shimx64.efi to .../EFI/Boot/bootx64.efi so the device will boot (without any nvram entries).  If I want nvram entries, just run the efibootmgr.
One thing to watch out for, is a 32bit bootloader required?  The preceding uses the 64 bit names.  I too still run 14.04 on a little Intel Compute Stick, getting the ESM updates, but I've set up other sticks with Debian/Lubuntu/Antix with a 64 bit UEFI boot without problem.

---

### Post by jmssr13 on 2023-04-14
I do not know if I need a 32 or 64bit bootloader. However, the only grub installation on the computer is i386-pc, but when I attempted to download the grub-efi it could not find the ip address to download the files from us.archive.ubuntu.com and aborted the install. (Yes, I have internet connectivity). I'm feeling a bit stuck now.

---

### Post by ubfan1 on 2023-04-14
Take a look at [https://askubuntu.com/questions/1417698/how-to-install-ubuntu-on-a-pc-with-a-32-bit-uefi](https://askubuntu.com/questions/1417698/how-to-install-ubuntu-on-a-pc-with-a-32-bit-uefi)  or github [https://github.com/hirotakaster/baytail-bootia32.efi/blob/master/bootia32.efi](https://github.com/hirotakaster/baytail-bootia32.efi/blob/master/bootia32.efi)  maybe one of those would work.  But first determine the 64 bit versions do not work, much simpler if they do.

---

### Post by jmssr13 on 2023-04-14
Thanks. I'll let you know how it goes. The grub install failed with a 404 error, I think I need to update my url lists. It couldn't grab any of the files, lol. it hasn't seen any updates or internet connectivity since 2016.

---

### Post by MAFoElffen on 2023-04-14
> **jmssr13 said:**
> Hi MAFoElffen,

So in the BIOS for the board that supports legacy and efi, should I now attempt to boot using uefi mode? I will attempt to do so in the morning.
I will check the hex type in the morning and get back to you asap.
The current cpu is an intel skylake i3 6100u.
The new CPU is an intel Elkhart lake Celeron J6412.
[COLOR=#ff0000]Truthfully, I have no idea if the cpu will be compatible with 14.04.[/COLOR] Also, these boards do not connect to the internet when deployed. I have the ability to connect them to download software for testing. 

I apologize if I am not describing things correctly, I am still learning.
On the partition output that you posted, Could you describe what each partition "is" or what each contains, and I will come up with some more details instructions for you.

I am downloading the manual from here: [https://download.ieiworld.com/?model=WAFER-EHL](https://download.ieiworld.com/?model=WAFER-EHL)

In the meantime, create a directory on the system for the EFI to mount to...
```

mkdir /boot/efi

```
That folder did not exits when it was installed as Legacy boot...

Then download the Ubuntu Desktop 14.04.6 amd64 iso and create a GPT UEFI bootable LiveUSB... Change the BIOS to UEFI and boot from that USB Media. Use Try. This will test if the New CPU will boot from that old of a sys. And be used to complete the conversion... 

If that is test successful, then we will go on.

---

### Post by MAFoElffen on 2023-04-14
What that vendor said in it's download was it's manual, and that parts of the manual was incorporated into an ISO file... After a painstakingly hour long download... Was a waste of time. The manual was not in that ISO file. That is a driver disk, that only works for installing drivers for Windows 10.

Since we do not have info on the device, let's get that information. Let's do something else.
While booted as Legacy in the BIOS, do this
```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/system-info/raw/main/system-info && \
chmod +x system-info && \
./system-info --details

```
Run the script. Ignore where it says it is missing anything (Choose C to continue). Upload the report to a pastebin and post the URL.

Then change the BIOS to UEFI boot and boot from the EFI LiveUSB and do this from the Live Environment:
```

sudo add-apt-repository ppa:mafoelffen/system-info
sudo apt update
sudo apt install system-info
system-info --details

```
Run it the same way...

Running it both ways will tell us everything we should need to see to come up with some detailed instructions and commands for you to follow.

---

### Post by jmssr13 on 2023-04-14
Hi MAFoElffen,

> [COLOR=#000000]Run the script. Ignore where it says it is missing anything (Choose C to continue). Upload the report to a pastebin and post the URL.[/COLOR]
I am getting the following result: 

2023-04-14 16:00:11 112MB/s - system-info saved [82334/82334] in 0.001s

No command ' chmod' found, did you mean:
 Command 'chmod' from package 'coreutils' (main)
 chmod: command not found
$

If removing the space between \ chmod, result: 

2023-04-14 16:01:31 100MB/s - system-info saved [82334/82334] in 0.001s
chmod: changing permissions of 'system-info': Operation not permitted

The script then ends and I cannot upload anything.
Thank your extended help, I am still fairly new to linux and ubuntu but your instructions are very helpful. This installation does not have a desktop environment either, so I am cli only.
Justin

---

### Post by MAFoElffen on 2023-04-14
Dang. Core is missing a lot of basic utils, but chmod is a 'core utility' from package 'coreutil'... LOL. I don't want to install a bunch of things that your approved "embedded system" is limited to, that is later going to be hard to unisntall the dependencies that might be pulled in by that. It's embedded, so your system is meant to remain small and compact.

If you do not mind temporarily installingthe script to your environment, use the install from the PPA. When we are through, if not a go approval to leave it there in your company IT infrastructure, you can uninstall it via
```

sudo apt remove --purge system-info
sudo add-apt-repository -r ppa:mafoelffen/system-info

```
I am the author and Project Lead. I gave the script to the Forum, and it was reviewed and approved by the Ubuntu Forum Admin Counsel... That GitHub is the Forum's GitHub. The Debian package installs the script to /usr/bin with the correct permissions already set...

The script is not just for diagnostics, but also good for routine maintenance, systems inventories, and to plan for system migrations. I think you will see better once you see what the reports contain.

EDIT: We tested and certified it on current supported Ubuntu Core (for all arches), releases 18.04 through 23.04. Thinking now, that yours would actually be the first for "Embedded Ubuntu Core." And for Release 14.04.

---

### Post by jmssr13 on 2023-04-14
It really doesn't matter too much to me, whatever we need to do to get this working is fine by me. Originally everything was stripped down as much as possible so that the computers could be spec'd with 4GB mSATA drives. Everyone who made these decisions has left, so I really don't care how large the drives are. The newest board doesn't have msata anyways and storage is much cheaper now. Once the board has a working image they won't be connected to the internet for the foreseeable future so I'm frankly not worried. I'll be out of the office until Monday, I'll let you know how this goes as soon as I'm back.

Thanks for the help, here's the project it'll be deployed in if you're curious: [https://en.wikipedia.org/wiki/Morgantown_Personal_Rapid_Transit](https://en.wikipedia.org/wiki/Morgantown_Personal_Rapid_Transit)
Thanks,
Justin

---

### Post by jmssr13 on 2023-04-17
Hello,
I added the repository with no issues. (ppa:mafoelffen/system-info)
However, when installing the system-info package, I get the following error:

E:Unable to locate package system-info
I've checked and everything is spelled correctly, is there a particular reason for this error or anything else I can try?

Also, I successfully uefi booted from a "vanilla" 14.04 live usb on the new board, so I think we will be able to get this to work.
Thanks

---

### Post by MAFoElffen on 2023-04-17
I believe, for you, you are going to have to install 'coreutils'
```

sudo add-apt-repository -r ppa:mafoelffen/system-info
sudo apt install core-utils
chmod +x ./system-info
mv ./system-info /usr/bin/
system-info --details

```
Why? Because I just remembered, that for releases, I don't have any releases built there anything older than 18.04, because that is what is currently in support.

---

### Post by jmssr13 on 2023-04-17
Sounds good.

Installed 'coreutils' and it finished just fine, shows in my apt list of installed packages.

doing sudo apt install system-info gives the following error:

Reading package lists ... Error!
E: Problem parsing dependency Depends
E: Error occured while processing libboinc-app7 (NewVersion2)
E: Problem with MergeList /var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_trusty-backports_universe_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
$

Any idea what I should do from here?
Thanks

---

### Post by MAFoElffen on 2023-04-17
Oh dang...

Do not try to install system-info. I don't have a package for it build for 14.04 Trusty Tahr.

And you just reminded me that the 14.04 packages are no longer located at "us.archive.ubuntu.com"... After they left support, they were move to "old-releases.ubuntu.com"...

You are going to have to repoint it to where the repo's were moved so tha you "can" install 'core-utils'.
```

sudo sed 's/us\.archive/old-releases/g' /etc/apt/sources.list

```
Then 
```

sudo apt update
sudo apt install core-utils

```
Then change to the folder where you downloaded the script from the github using wget...
```

chmod +x ./system-info
mv ./system-info /usr/bin
system-info --details

```

---

### Post by MAFoElffen on 2023-04-18
Any update?

---

### Post by jmssr13 on 2023-04-18
I am currently waiting for apt update to complete, it is taking quite a bit longer than I'd expected.

When I went to change the us.archive.ubuntu.com links to the old-releases.ubuntu.com yesterday afternoon, doing a sudo apt update could not find the ip addresses of any of the packages. So this morning, I went back and restored the image to before I tried to change the package urls.

I will get back to you as soon as that finishes so I can install coreutils and run the script.

Sorry for the delay, I did not realize this would take so long.

---

### Post by jmssr13 on 2023-04-18
Update:
coreutils is installed/updated successfully.

I ran the wget command, it worked. It couldn't upload the report for some reason even though it has internet access, so I will have to upload it myself to a pastebin here once I copy the file to a different machine.

Pastebin: [https://pastebin.ubuntu.com/p/Vgpx2t9btJ/](https://pastebin.ubuntu.com/p/Vgpx2t9btJ/)

Please note: I was having trouble with apt update taking hours at a time, so I decided to rollback the source.list files to contain the original us.archives.ubuntu.com URLs.

Thanks

---

### Post by MAFoElffen on 2023-04-19
Going through it now...

---

### Post by MAFoElffen on 2023-04-19
Okay, from what I see there.

First you still need to create a FAT32 filesystem in the EFI partition. Later, you will need the UUID from that filesystem (after it is created, to add to your fstab file for the mount.
```

sudo apt install --yes dosfstools

mkdosfs -F 32 -s 1 -n EFI ${DISK}-part1
echo "/dev/disk/by-uuid/$(blkid -s UUID -o value /dev/sda4) /boot/efi vfat defaults 0 0" >> /etc/fstab

```
If for some reason you cannot install dosfstools then boot off an installation LiveUSB and use GParted to format that partition.

You could also get the UUID manually by just doing
```

blkid -s UUID -o value /dev/sda4

```
Copying that number down, then adding the line to the fstab file.

Then start putting all the pieces together. I would do it booted from an Ubuntu install LiveUSB drive... From a terminal session (Using Try)...

If you did lsblk, that would verify that the system's drive is most likely /dev/sdb

Verify the mode the LiveUSB boot in.
```

[ -d /sys/firmware/efi ] && echo "Booted in UEFI mode" || echo "Booted in Legacy mode" 

```
You want UEFI mode...

Then you are ready
```

sudo -i
mount /dev/sdb2 /mnt/
mount /dev/sdb1 /mnt/boot
mount /dev/sdb4 /mnt/boot/efi
mount /devsdb5 /mnt/var
mount /dev/sdb /mnt/home
mount /dev/sda7 /mnt/data
mount --make-private --rbind /dev  /mnt/dev
mount --make-private --rbind /proc /mnt/proc
mount --make-private --rbind /sys  /mnt/sys
mount --make-private --rbind /run  /mnt/run
cd /mnt
chroot .

```
Then
```

apt update
apt install --yes grub-efi-amd64 grub-efi-amd64-signed linux-image-generic shim-signed
# I don't remeber if the 14.04 repo's had package 'grub-efi-amd64-signed. If it complains that it cannot find that, redo the command wihout that package
update-initramfs -c -k all
grub-install --target=x86_64-efi --efi-directory=/boot/efi --bootloader-id=ubuntu --recheck --no-floppy
# if no errors, then 
exit
umount -a
reboot

```
Crossing fingers.

---

### Post by jmssr13 on 2023-04-19
Ok,

Mostly so far so good.

I got the UUID for dev/sda4 and added it to /etc/fstab

EFI boot from an efi liveusb was successful with result : Booted in uefi mode

chroot working properly.

apt update worked with the us.archives.ubuntu.com 

However, when installing the grub-efi-amd64 the packages are found but the URLs show error 404. Ok, no biggie just change the sources.list file to old-releases.ubuntu.com and retry.

However, now I get error:

Package grub-efi-amd64 is not available, but it is referred to by another package.
This may mean that the package is missing, has been obsoleted, or is only available from another source
However, the following packages replace it:
   grub2-common grub-pc grub-common
E: Package 'grub-efi-amd64' has no installation candidate
E: Unable to locate package linux-image-generic
E: Unable to locate package shim-signed

Output of dpkg -l | grep grub:
grub-common                    2.02beta2-9ubuntu1.7
grub-gfxpayload-lists          0.6
grub-pc                             2.02beta2-9ubuntu1.7
grub-pc-bin                       2.02beta2-9ubuntu1.7
grub2-common                  2.02beta2-9ubuntu1.7

Do I try to install one of the other grub packages?

Thanks

***Update***
Reverting my sources.list file back to the original configuration, I was able to:

apt install --yes grub-efi-amd64 linux-image-generic

linux-image-generic installed successfully, however the grub-efi-amd64 error 404 url not found still exists. Trying to install grub2-common brings up that the package is updated to the most recent version, then closes.

---

### Post by MAFoElffen on 2023-04-19
I just PM'ed a friend, a Moderator here who keeps a personal archive of information on old issues and is the person I feel know the most about UEFI.

I can't find old package information online for 14.04.x. It stops at 18.04. So having a problem resolving the package names. Hopefully he can help with what that "was" for 14.04.

In the meanwhile... I am sill looking, for just in case.

---

### Post by jmssr13 on 2023-04-19
Thank you very much!

Looking on the launchpad website, would something like this be what I am needing?

[https://launchpad.net/ubuntu/trusty/amd64/grub-efi-amd64-bin/2.02~beta2-9ubuntu1.17](https://launchpad.net/ubuntu/trusty/amd64/grub-efi-amd64-bin/2.02~beta2-9ubuntu1.17)

[https://launchpad.net/ubuntu/+source/grub2/2.02~beta2-9ubuntu1.17](https://launchpad.net/ubuntu/+source/grub2/2.02~beta2-9ubuntu1.17)

Thanks

---

### Post by MAFoElffen on 2023-04-19
I spun up a 14.04 image and installed it as UEFI... Then searched the installed packages, so that I could resolve the package names.
```

apt install grub-common grub-efi-amd64 grub-efi-amd64-bin grub-efi-amd64-signed grub2-common

```

---

### Post by jmssr13 on 2023-04-19
Ok. Reverted my sources.list file back to the original us.archives.ubuntu.com url:

executing:
apt install grub-common grub-efi-amd64 grub-efi-amd64-bin grub-efi-amd64-signed grub2-common

There are multiple issues. They all stem from dependencies:

grub-efi-amd64 requires grub2-common and grub-efi-amd64-bin

grub-efi-amd64-bin requires grub-common and efibootmgr, which efibootmgr says "but it is not installable"

trying to standalone apt install efibootmgr gives this error:

E: Package 'efibootmgr' has no installation candidate

The versions of the grub2-common and grub-common are slightly different but say that they 'could' install if the dependencies were fixed. I believe that everything will install correctly if I can get efibootmgr package installed. Is this a good assumption?

Thanks so much as always

---

### Post by MAFoElffen on 2023-04-19
That is what I think. 

Let me look at this 14.04 VM. Yes, it says that it is installed on it..
```

Listing... Done
efibootmgr/trusy-updates,now 0.5.4-7ubuntu1.2_amd64 [installed,automatic]

```

---

### Post by MAFoElffen on 2023-04-19
I stand corrected on the repo URL's (us.archive) in sources.list, This VM kept bugging me on updates, so I went ahead and let it go. It went fine.

---

### Post by ubfan1 on 2023-04-19
The grub packages on my Ubuntu 14.04 under esm:
$ sd grub
ii  grub-common                                           2.02~beta2-9ubuntu1.21                               amd64        GRand Unified Bootloader (common files)
ii  grub-efi-amd64                                        2.02~beta2-9ubuntu1.21                               amd64        GRand Unified Bootloader, version 2 (EFI-AMD64 version)
ii  grub-efi-amd64-bin                                    2.02~beta2-9ubuntu1.21                               amd64        GRand Unified Bootloader, version 2 (EFI-AMD64 binaries)
ii  grub-efi-amd64-signed                                 1.34.24+2.02~beta2-9ubuntu1.21                       amd64        GRand Unified Bootloader, version 2 (EFI-AMD64 version, signed)
ii  grub2-common                                          2.02~beta2-9ubuntu1.21                               amd64        GRand Unified Bootloader (common files for version 2)
ii  ubuntu-recovery-grub-hotkey                           1.1kittyhawk3                                        all          Ubuntu Recovery Grub Hotkey Configuration

$ apt-cache policy grub-efi-amd64
grub-efi-amd64:
  Installed: 2.02~beta2-9ubuntu1.21
  Candidate: 2.02~beta2-9ubuntu1.21
  Version table:
 *** 2.02~beta2-9ubuntu1.21 0
        500 [https://esm.ubuntu.com/ubuntu/](https://esm.ubuntu.com/ubuntu/) trusty-infra-security/main amd64 Packages
        100 /var/lib/dpkg/status
     2.02~beta2-9ubuntu1.17 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
     2.02~beta2-9ubuntu1.6 0
        500 [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) trusty-security/main amd64 Packages
     2.02~beta2-9 0
        500 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages

---

### Post by jmssr13 on 2023-04-20
Do you think there might be a conflicting issue with the fact that my system is i686 in uname -m? That it just can't install the 64 bit applications? Is there a 32 bit efi package for 14.04?
Is there any other way to install efibootmgr to allow myself to install grub? Can it be done manually or offline?

---

### Post by MAFoElffen on 2023-04-20
> **jmssr13 said:**
> Do you think there might be a conflicting issue with the fact that my system is i686 in uname -m? That it just can't install the 64 bit applications? Is there a 32 bit efi package for 14.04?
Is there any other way to install efibootmgr to allow myself to install grub? Can it be done manually or offline?
Yes... You are right. That sort of throws another wrench into it...

**i686?** How could I have missed that? (Because that is not the current nowadays normal.)

Dang...
```

Original Installation Media: Ubuntu-Server 14.04.4 LTS "Trusty Tahr" - Release i386 (20160217.1)

```
The board you bought is 64bit. It may boot 32bit Legacy. It will run 32bit app's from a 64bit install, because back in that release there where 32bit libraries available. But I don't think the new board will boot 32bit EFI, because there were only a few years and even less machines that ever booted as 32bit EFI... I just happen to own "one".... An old MAC ProBook Notebook. For something "new" to be able to boot as 32bit EFI would be very rare.

What app's are you stuck to that are 32bit? I am assuming these are controls, that were probably written in Python 2? Or what are we looking at if there were a migration to a 64bit version of 14.04?

I'm thinking of many possibilities of how to adapt to this... Or this new board can actually boot as 32bit EFI, I'll dig into my MACBook and see what Grub2 Packages are installed for it... But is would still be different, as "it" is a 64bit OS, booting off 32bit EFI.

Let's put our heads together and come up with something that will work for this. There is an possibility here somewhere.

---

### Post by MAFoElffen on 2023-04-20
This may work for this...
> 
Use rEFInd to boot 64-bit EFI-mode OSes and your 32-bit BIOS-mode OS

(User had 14.04 installed...)
RE: [https://askubuntu.com/questions/749306/installing-32-bit-ubuntu-side-by-side-with-64-bit-ubuntu-on-uefi-system](https://askubuntu.com/questions/749306/installing-32-bit-ubuntu-side-by-side-with-64-bit-ubuntu-on-uefi-system)

oldfred knows about rEFInd, but he told me he is busy today, will PM him again tonight...

---

### Post by oldfred on 2023-04-20
Oldfred is back. Golfed ok, not great, but good to get out and get exercise & fresh air.

I use rEFInd for emergency UEFI boot. I used to use Supergrub, and still keep a current copy,which I believe still works for booting when grub has issues.

Have not really dealt with 32 bit systems as almost everything now is 64 bit. There were a few UEFI systems that used 32 bit UEFI but system was 64 bit. Those were an attempt to lock in Windows as it had 32 bit and Linux originally did not. But thne a 32 bit UEFI boot was created. Those systems also are now old.

First post's Boot-Repair says this, so system is 64 bit, but using 32 but Ubuntu:
> CPU architecture: 64-bit
Live-session OS is Ubuntu 32-bit (Boot-Repair-Disk 32bit 20211212, bionic, i686)


---

### Post by jmssr13 on 2023-04-20
Hey to answer both of your posts, as far as I am aware there shouldn't be any application compatibility issues with 64 bit. I don't know what language the application is written in as it isn't something I have looked into. I am definitely interested in going down either converting the existing image to 64 bit or like a boot loader/manager that would allow the default system to boot being the 32 bit image. Either of those options would be fine for me, because I will still just hopefully need something that could boot and load the application.

---

### Post by oldfred on 2023-04-20
I do not know the AMD processor used in old board.
EPIC SBC supports AMD® Embedded G-Series SoC

New board uses Intel I-series chips which are 64 bit.
EPIC SBC supports Intel® 14nm 6th Generarion Mobile Core&#8482; i7/i5/i3 and Celeron® on-board Processor (ULT)

My current desktop is Intel z170 Skylake or 6 series Intel.

---

### Post by MAFoElffen on 2023-04-20
(I know this is a restoration project.)

I wish I had more info on the application... Then I could create two KVM VM's with both 32bit and 64bit 14.04 installed... and see what can be done with each and still have your application run. Instead of just hoping what I am suggesting will work.

I have VM machines created for this to replicate the board you have now... But with 14.04 64bit installed to it.

Then I could see if there was a fresh installed 64bit 14.04 system installed to the new board (that part would be easy), what would need to be done to migrate the existing application to it, to ensure it still ran okay.

That would be 'clean' and go on with the least problems. Ubuntu Core 14.04 loses support in 2 years. So there is a shelf life there. If it can be migrated to a 64bit 14.04, then there might be a possibility that it can go on to newer, still supported Core in the future... Although with "Embedded", that is not as much of a concern.

Sorry, you got my mind going on this.

---

### Post by jmssr13 on 2023-04-20
> [COLOR=#000000]I wish I had more info on the application... Then I could create two KVM VM's with both 32bit and 64bit 14.04 installed... and see what can be done with each and still have your application run. Instead of just hoping what I am suggesting will work.[/COLOR]

I am not sure how I could send it to you, but I would be open to such a thing. I could send you the files somehow for the application, then go from there? I was never given any sort of installation package or installer for it, it just "happened" to be on the image that we were given at the end of the project. (well before I was hired.) Either way, it will need to be 64 bit compatible for the future anyways, I'm assuming. Let me know what you'd like me to do and I'll help you to help me as much as I can. I greatly appreciate all the help so far since I'm still a linux novice.

---

### Post by jmssr13 on 2023-04-20
oldfred, I will explore the rEFInd option and get back to you as soon as I can.

Thanks.

---

### Post by MAFoElffen on 2023-04-20
> **jmssr13 said:**
> I am not sure how I could send it to you, but I would be open to such a thing. I could send you the files somehow for the application, then go from there? I was never given any sort of installation package or installer for it, it just "happened" to be on the image that we were given at the end of the project. (well before I was hired.) Either way, it will need to be 64 bit compatible for the future anyways, I'm assuming. Let me know what you'd like me to do and I'll help you to help me as much as I can. I greatly appreciate all the help so far since I'm still a linux novice.
I created a shared folder for you and PM'ed you with my contact information...

---

### Post by MAFoElffen on 2023-04-21
Success so far. See attachment.

---

### Post by MAFoElffen on 2023-04-22
I'm making copies of the drive to make changes too. I think i found a way to install and configure 'grub-efi-amd64-signed', where it may boot the 32bit OS...

Crossing fingers.

Why keep it as 32bit? I looked into the two applications that they are locked into using. They are both compiled for i386. In fact: <ediited for security>
```

gate@unnamed-gate:/data/install$ file /data/install/[FILTERED]
/data/install/[FILTERED]: ELF 32-bit LSB  executable, Intel 80386, version 1 (GNU/Linux), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=0c4b541db766cbe7198c5d700ddfdbade4789c7d, not stripped
gate@unnamed-gate:/data/install$ file /data/install/[FILTERED]/[FILTERED]
/data/install/[FILTERED]/[FILTERED]: ELF 32-bit LSB  executable, Intel 80386, version 1 (SYSV), dynamically linked (uses shared libs), for GNU/Linux 2.6.24, BuildID[sha1]=ac8854dbc71edfae8460d1d064b47fe1950401b7, not stripped
gate@unnamed-gate:/data/install$

```
I am thinking that, if they do not have the original source code, and can try to compile it as 64bit, they are locked into it being run on 32bit. This may be the case, as I see two versions of one of the executables present on the device.

My plan is:
1. To get 14.04.4 i386 (their existing OS) to boot from UEFI. Ubuntu Core 14 is supported until April 2024.
2. Install Ubuntu Core 18 i386 and see if the application will run on it. If so, they that will buy them another 4 more years of a supported OS. (Then dead-ends.)

If the source code exists still, then maybe the University could acquire it, and take on converting it to 64bit (In their Computer Science Department) as a (real world) project(?) Or come up with their own form of it in their curriculum.

---

### Post by jmssr13 on 2023-04-24
As far as needing to modify the existing drive partition sizes to accommodate any new updates, it won't be a problem. I'm anticipating on using at minimum a 64GB or 128GB m.2 ssd in the NANO-EHL board. 

While you are testing the uefi boot, I will continue the conversion process from 32 to 64 bit kernel on one of my test images. If it can run successfully it will be a big relief. If not, I'll begin the process of inquiring the source code and go from there. I'll keep everyone updated with how things go, if anyone needs anything else from me they are free to pm or comment in this thread.

Thanks!

---

### Post by MAFoElffen on 2023-04-24
The image you sent me was 64G. 

I used GParted to format /dev/sda4 (EFI) as vfat (FAT32), added that partition to the fstab file and it mounts fine now.

I added amd64 to the arch of dpkg, so it is seeing amd64 packages now... I also added some pinnings and such in an apt preference file. But it was still getting "no installation candidate" on grub-efi-amd64.

Per oldfred's advise, I changed the sources.list to a Mirror. Is taking forever to update the APT cache from it. Once it updates, I will upgrade it from 14.04.4 to 14.04.6, before I retry to install grub-efi-amd64.

I'm thinking that is the problem with installing that package. It see's the version of Grub installed is lower than the newer package, so is a depends problem that it is having a problem resolving getting passed.

I'm keeping a terminal log to document would I do, so i can post what the process actually turns out to be.

Will tell you how it goes.

---

### Post by MAFoElffen on 2023-04-25
Success. In a round-about way...
```

mafoelffen@lunar-lander-01:~$ ssh gate@192.168.122.225
gate@192.168.122.225's password: 

  System information as of Tue Apr 25 23:28:18 EDT 2023

  System load:    0.36             Processes:           131
  Usage of /home: 0.4% of 9.49GB   Users logged in:     0
  Memory usage:   1%               IP address for eth0: 192.168.122.225
  Swap usage:     0%

  Graph this data and manage this system at:
    https://landscape.canonical.com/
****************************************

THALES WVU PROJECT
PRT Entry Fare Gate

Install instructions:
1) edit /etc/network/interfaces
   replace the ip of the device
2) edit ~/install/AccessGate.ini
   change [Local_DSU]/Device_ID to the proper device ID
Last login: Tue Apr 25 23:28:18 2023
gate@unnamed-gate:~$ lsblk -o name,mountpoint,size,UUID
NAME   MOUNTPOINT   SIZE UUID
sda                 128G 
&#9500;&#9472;sda1 /boot/efi    750M 
&#9500;&#9472;sda2 /boot          1G 
&#9500;&#9472;sda3 /           34.2G 
&#9500;&#9472;sda4 /var        1000M 
&#9500;&#9472;sda5 /home        9.8G 
&#9492;&#9472;sda6 /data        9.8G 
sr0                14.3M 
gate@unnamed-gate:~$ [ -d /sys/firmware/efi ] && echo "UEFI Firmware mode" || echo "Legacy mode (alias CSM alias BIOS mode)"
UEFI Firmware mode
gate@unnamed-gate:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.4 LTS
Release:    14.04
Codename:    trusty
gate@unnamed-gate:~$ uname -a
Linux unnamed-gate 4.2.0-34-generic #39~14.04.1-Ubuntu SMP Fri Mar 11 11:39:00 UTC 2016 i686 i686 i686 GNU/Linux

```
Partition table is GPT. Tried to install as Grub's grub-efi-amd64... I had it installed, but it didn't want to boot, so Installed rEFInd... It still had challenges, until I figured out that SecureBoot was enabled in the Machine's BIOS, Disabled it and it boots fine now. LOL.

I had an idea on it running on Ubuntu Core 64bit... and running those 32bit compiled applications. It should work it you install Core up to Ubuntu Core 18, then do"
```

sudo dpkg --add-architecture i386
sudo apt-get update
sudo apt-get install libc6:i386 libncurses5:i386 libstdc++6:i386 multiarch-support

```
That would add the 32bit libraries to 64bit, and give it the ability to run 32bit applications.

---

### Post by MAFoElffen on 2023-04-26
Now I have 2 images working with 64Bit UEFI and 32bit Ubuntu 14.04. One with grub-efi-amd64, and the other with rEFInd.

Now trying to install a 64bit version of Ubuntu Core try to get if to boot as UEFI...

---

### Post by jmssr13 on 2023-04-26
Awesome!

Thank you very much. Once they're ready, if you wouldn't mind tossing them on the google drive folder and I'll see if I can boot them on my machine.

Let me know how the 64 bit core installation goes!

---

### Post by MAFoElffen on 2023-04-26
Here is the summarized instructions for both. Both are on a GPT disk. 

To create the GPT disk, I started with a new VM Disk file. Then attached both disks to a machine, which was booted from an Ubuntu 14.04.6 Live Installer media. On the new disk, created the needed number of partitions. On the first partition, labeled it as EFI, flagged it as bootable, ESP (gdisk type ef00), fomratted as FAT32.

Then I mounted the partitions from the original MBR disk to /media and the new GPT disk to /mnt, and used rsynch to copy everything over to the new disk, which preserving the permissions and such, using this command:
```

sudo rsync -axHAWXS --numeric-ids --info=progress2 /media/sourcePart/ /mnt/destPart

```
The difference in the number of partitions is one less. The original disk was MBR, which partition 4 was the extended partition, which the logical partitions were within...

After I had created a GPT disk, then it differs on making it bootable via UEFI. Of course, then I had to update the /etc/fstab file with the new UUID's of the GPT disk. I had Labeled all the partitions of the Disk, so using this command, it was easy to ID the partitions and update the fstab file:
```

sudo lsblk -o name,mountpoint,label,size,UUID

```

Option #1: Bootable via 'grub-efi-amd64'

While still booted via UEFI BIOS with the Ubuntu 14.04.6 Live installer 
```

# become root
sudo su
# mount the root partition
mount /dev/sda3 /mnt 
mount  /dev/sda2 /mnt/boot
mkdir /mnt/boot/efi
apt update
apt upgrade
apt install reinstall grub-efi-amd64 grub-efi-amd64-signed shim-signed
for i in /dev /dev/pts /proc /sys; do mount -B $i /mnt$i; done
modprobe efivars
apt-get install --reinstall grub-efi-amd64-signed
grub-install --no-nvram --root-directory=/mnt
chroot /mnt
update-grub
cd /boot/efi/EFI
mkdir ./BOOT
cp -R ubuntu/* ./BOOT/
cd ./BOOT
cp grubx64.efi bootx64.efi
reboot

```
* Ensure SecureBoot is disabled. Booted the 32 bit OS, with the 64bit UEFI.

Option #2

Download the rEFInd boot media. Create the boot media from the files. Boot from the fEFInd media. Install the boot loader to the disk. After booted modified the refind.conf file timeout from the default 20 seconds, to 2 seconds.

What size do you want the disks? Have to drop off my wife to babysit the grandkids. Will PM you later...

---

### Post by jmssr13 on 2023-04-26
That's awesome, thank you so much!

32GB would be nice for now, the 64GB drive I currently use is more along the 60GB line. Is 32GB big enough? I'm assuming so.

Thanks!

---

### Post by MAFoElffen on 2023-04-26
As it is now, it would fit comfortably on an 4GB storage disk. The storage used between all the partitions is only  2176MB.

But I like to set ESP directories at 750MB and Boot directories at 1GB, by my own rule-of-thumb to help prevent maintenance and upgrade out-of-space challenges. I see the most active partition for reads and writes being /var, as all the logging, and log rotations that is going on there.

I will PM you on the format's to send to you, based on what might be easiest for both of use. What I usually do is shrink down the partitions to just above what is used, then store as raw IMG. That way it can just be burned onto whatever, then the partitions expanded to whatever sizes you need.

---

### Post by jmssr13 on 2023-04-27
Good news and bad news,

Good news: Works perfectly on the ULT3 board. It boots via uefi only, all the way to the os, and the program runs great! 

Also boots to GRUB on the NANO-EHL board. The grub menu loads, and shows the ubuntu selection. Awesome!

Bad news: Looks like the graphics driver doesn't work with Intel 10th gen integrated graphics. After making the grub/refind boot selection, the screen goes blank and stays blank. Trying to edit the kernel boot line seems to generate no difference in results.

On the ULT3 image, the whole time I was always getting i915 errors, but didn't really know what to make of them. Since the original system was created for an AMD cpu/gpu, I don't know if intel drivers were ever properly loaded. I'll start looking into this, now.

---

### Post by MAFoElffen on 2023-04-27
I added this to /etc/default/grub file
```

GRUB_CMDLINE_LINUX_DEFAULT="nomodeset"

```
Remember, after saving and exiting the editor, to do 
```

sudo update-grub

```
To pick up the changes. See attached...

Since you are live hardware and me doing VM, your hardware shows through, so using "i915.modeset=0" might work as well.

Interesting note- I noticed that the original install image was done with Ubuntu 14.04 Server ISO, on VirtualBox, on a host that had a 5th Generation Intel i7. It would have had the video shielded in that VBox VM.

---

### Post by jmssr13 on 2023-04-28
Unfortunately, no dice. Still a blank screen after grub. 

I'm going to poke around and see if there is any driver package I could install, and then if that doesn't work we'll see about moving to 16.04. I don't know of any packages that would break for that upgrade as of now.

---

### Post by MAFoElffen on 2023-04-28
Look at /var/log/Xorg.0.log to see that XServer started okay with no errors...

Hmmm. I didn't changed anything in the system. Just installed the bootloader. That is the only change there.

---

### Post by jmssr13 on 2023-04-28
I don't think anything you did broke anything. It still boots via uefi-only just fine on the ULT3 (i3 6100u) board. It does have some firmware errors upon startup but the driver works enough for what we use it for. Display totally functional in the cli environment as well as the Gate Application. No worries there at all! Everything is still functioning just as before.

I'm thinking the issue is with the 10th gen integrated gpu, that it just isn't supported by the 4.2 kernel, or perhaps that it doesn't support a 32bit OS at all. I'd like to try stepping to 14.04.05 (4.4 kernel), seeing if the updated kernel seems to increase support or fix things, then going from there to 14.04.6, and then to 16.04...etc. At this point I don't think I have another choice. If neither of the upgrades work, I might end up migrating from 32 to 64 bit and seeing what works from there, although at that point the gate application might not work.

---

### Post by MAFoElffen on 2023-04-28
The KVM host I am hosting the VM on right now has Intel i9 10900.

I created a Ubuntu 18.04 Server amd64, which I added i386 multi-platform support for. Am trying to set it up to run it with how the old image is configured. Running into some challenges. LOL.

That is the first Ubuntu release that had systemd (completely), instead of INIT... and the last that support i386 libraries, before it got dropped. Then the Tab Window Manager (twm) that is installed on the original image, just wants to be a black screen. I'm thinking maybe "that piece" there (the windows manager)  is what may not like the intel graphics.

Have to leave for work soon. Tomorrow, I may uninstall twm and replace it with OpenBox and get a working minimal, lightweight desktop first, before trying to test dev2scada and AccessGateMain again.

---

### Post by jmssr13 on 2023-05-01
Looks like i386 16.04 is no bueno. Same boot result on the NANO-EHL board amd64 grub bootloader functions as normal, but doesn't boot afterwards. And yeah, I'm also running into issues on 16.04 with the window manager not working correctly. 

Let me know if you have any success!

---

### Post by MAFoElffen on 2023-05-02
I have been getting a black screen right after the login of the user. I  have enough tried creating a new user to see if it was something with  the user profile, but that wasn't it. I had everything all at once,  assuming it would just work. Which was a bad idea.

I am  reinstalling fresh to add the applications in after I know I have a  stable desktop and Windows Manager. There is something in the original  install that is "wonky." 

I haven't identified what that was yet.  But if I add it in one by one, I should be able to identify what piece  of the puzzle is causing the trouble.

---

### Post by MAFoElffen on 2023-05-04
I Installed Ubuntu Server 18.04 amd64 and added the basic libraries to make it multi-arch between amd64 and i386. Added LXDE and Lightdm.

Had a stable desktop.

Here is where I broke it. With both dev2scada then with AccessGateMain, when starting each, it would get errors where it was not finding symbolic links for link libraries. I followed each one to find that there was amd64 versions of the links... and installations of amd64 bit versions of the packages, that I then installed i386 version of the packages. On some, where the name of the symbolic link implied an outdated version of the package, I then created a newly named symbolic link to point to that link library.

All was going well in that methodology until I got to package  'libobject' where the package is compiled as multiarch deb package / ending in '_all'... But the link and package says it's only amd64...
```

wrong ELF class: amd64

```
I hit a dead end there. Sorry.

Next idea? Install Ubuntu Server 16... Upgrade to 18.04... Why? Because there was not i386 Server ISO... Then try it again with pure i386.

---

### Post by MAFoElffen on 2023-05-04
I instead cloned the one I had working and unlocked the pinning on the upgrades. Then I upgraded it to 14.04.6(i386). That still worked. (see attachments.)

Then I cloned again and did a do-release-upgrade to 16.06 (i386). After taking care of bugs still present on letting a non-root user start xserver-xorg... Then I deadended at a blackscreen with xserver, txm, and AccessGateMain.

---

### Post by jmssr13 on 2023-05-08
Yep, that's about where I got. Thank you for all the help, I greatly appreciate it. Looks like I'll have to reach out to see what can be done about the software itself.

---

