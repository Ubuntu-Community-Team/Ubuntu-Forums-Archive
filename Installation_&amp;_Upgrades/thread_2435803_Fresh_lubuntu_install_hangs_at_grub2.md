---
title: "Fresh lubuntu install hangs at grub2"
date: 2020-01-26
forum: Installation &amp; Upgrades
---

### Post by eatdembeans on 2020-01-26
Hey,
I'm trying to install lubuntu on an acer laptop, disabled secure boot, the installation hangs when it reaches "installing grub2" phase. I found this guide [https://askubuntu.com/a/876153](https://askubuntu.com/a/876153) which works 100% on ubuntu ubuntu-18.04.3-desktop-amd64 but when I try with lubuntu-18.04.3-desktop-amd64 (used latest rufus with both mbr and gpt schemes when making the usb stick), I get an error after 

[COLOR=#242729][FONT=Arial]7. Change root to /mnt and update grub[/FONT][/COLOR]
sudo chroot /mnt
sudo update-grub

sudo: unable to resolve host lubuntu: Resource temporarily unavailable
sudo: update-grub: command not found

When I cd /usr/sbin/  cat update-grub I see this

#!/bin/sh
set -e
exec grub-mkconfig -o /boot/grub/grub.cfg "$@"

What is different on lubuntu compared to ubuntu that it fails this command?
Without it, I cannot install lubuntu. Please help

EDIT: I managed to install lubuntu, it does boot but when I want to sudo apt-get update and then upgrade, I get

[COLOR=#000000]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.[/COLOR]
[COLOR=#000000]and after I run it, this happens[/COLOR]

[COLOR=#000000]Setting up grub-efi-amd64 (2.02-2ubuntu8.14)..[/COLOR]
[COLOR=#000000]Installing for x86_64-efi platform.

[/COLOR]and it hangs again.

I'm checking the same with ubuntu and it updates properly without any problems. Something is wrong in lubuntu.

EDIT: In the end it was impossible to use lubuntu so I installed LXLE 18.04.3 instead, it's also low on resources (260MB idle) and it worked after this guide [https://askubuntu.com/a/876153](https://askubuntu.com/a/876153) (just like how ubuntu works).

---

### Post by oldfred on 2020-01-26
May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by eatdembeans on 2020-01-26
> **oldfred said:**
> May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I tried the recommended repair and it froze at the same thing as the normal installer "Installing for x86_64-efi platform." My previous try with the guide passed this stage. That contained this command "sudo apt-get install --reinstall grub-efi-amd64sudo grub-install --no-nvram --root-directory=/mnt" The --no-nvram has to be the solution here but why is update-grub not working afterwards?

I did try to do the same thing again but it crashed even before it gave me the command, now it just keep crashing. Will format again with sudo ubiquity -b.. I don't get this, the ubuntu stick works fine..

---

### Post by dragonfly41 on 2020-01-26
> [COLOR=#000000]sudo apt-get install --reinstall grub-efi-amd64sudo grub-install --no-nvram --root-directory=/mnt[/COLOR]

This might just be a simple typo error in your post but the two commands should read ..

[COLOR=#000000]sudo apt-get install --reinstall grub-efi-amd64
sudo grub-install --no-nvram --root-directory=/mnt[/COLOR]

---

### Post by eatdembeans on 2020-01-26
yeah that's how I meant it, so the boot-repair gives me this command, I'll post it just in case it freezes again

sudo chroot "/mnt/boot-sav/sda2" dpkg --configure -a
sudo chroot "/mnt/boot-sav/sda2" apt-get install -fy
sudo chroot "/mnt/boot-sav/sda2" apt-get install -y grub-efi-amd64-signed shim-signed linux-headers-generic linux-signed-generic

EDIT: yep, it froze again, at 
"creating config file /etc/default/grub with new version
Installing for x86_64-efi platform."

---

### Post by yancek on 2020-01-26
Is there some reason you do not want to post the details request by moderator oldfred in post 2 above?  You were asked to use the Create BootInfo Summary option and post the link produced when running it.  That will give details needed for someone to help.

---

### Post by oldfred on 2020-01-26
I prefer to have link to report before you run any suggested fixes. While Boot-Repair usually works especially if it really is just a grub reinstall or simple fix, in some cases it can make things worse. 
So best that someone, not necessarily me, at least review details before running fixes or perhaps other fixes.

---

### Post by eatdembeans on 2020-01-27
> **oldfred said:**
> I prefer to have link to report before you run any suggested fixes. While Boot-Repair usually works especially if it really is just a grub reinstall or simple fix, in some cases it can make things worse. 
So best that someone, not necessarily me, at least review details before running fixes or perhaps other fixes.

I thought that there will be a report after the recommended repair finishes but since it crashed for me I didn't have anything...my bad

[http://paste.ubuntu.com/p/V3CKptMnQQ/](http://paste.ubuntu.com/p/V3CKptMnQQ/)

this report is done after I managed to install lubuntu, it boots by itself but when I try to sudo apt-get update then upgrade, I get this
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.
and after I run it, the usual thing happens

Setting up grub-efi-amd64 (2.02-2ubuntu8.14)..
Installing for x86_64-efi platform.
and it crashes.

This is how I managed to install lubuntu and have it boot by itself, but in the end it cannot use sudo apt-get upgrade, because the same error happens, as above "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem."

in windows: download rufus 3.8 -> select lubuntu iso
partition scheme MBR (but this may be irrelevant)
add fixes for old bioses (extra partitions, align, etc) - this also may be irrelevant?
file system fat32 

boot from stick, select try live lubuntu
enable wifi/go online

go to terminal (ctrl alt T)

sudo ubiquity -b

get updates during install
erase disk

when it's done, do not restart, continue testing

in terminal

sudo add-apt-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair && boot-repair

select recommended repair

copy paste the command it gave you into a terminal, this will crash the system, hold power button and restart

go to try live lubuntu from stick

in terminal
sudo mount /dev/sda2 /mnt
sudo mkdir /mnt/boot/efi
sudo mount /dev/sda1 /mnt/boot/efi
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done

sudo modprobe efivars

sudo apt-get install --reinstall grub-efi-amd64
sudo grub-install --no-nvram --root-directory=/mnt

sudo chroot /mnt
sudo update-grub

cd /boot/efi/EFI
sudo cp -R ubuntu/* BOOT/
cd BOOT
sudo cp grubx64.efi bootx64.efi

reboot

it logs into lubuntu, then I enable wifi and try

sudo apt-get update
sudo apt-get upgrade

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem
sudo dpkg --configure -a
setting up grub-efi-amd64 (2.02-2ubuntu8.14)..
Installing for x86_64-efi platform. crash

---

### Post by oldfred on 2020-01-27
Is this an Acer?
```
Boot0000* Linux	HD(1,GPT,4c6e73ea-ae44-4392-b141-4234546dfe35,0x800,0x100000)/File(EFIBootgrubx64.efi)RC
Boot0001* Unknown Device: 	HD(1,GPT,4c6e73ea-ae44-4392-b141-4234546dfe35,0x800,0x100000)/File(EFIubuntushimx64.efi)RC
Boot0002* Linux	HD(1,MBR,0x382dfdd5,0x3f,0x1cea782)/File(EFIBootgrubx64.efi)RC

```

Acer is the only one I have noticed that uses the Unknown Device. Then from within UEFI you have to set "trust" to name the entry. 
Or did you name the Linux entries already?

You have the Ubuntu files in the ESP. So not sure where grub error is.
Most of the errors are related to the installer flash drive. Most installer are configured as hybrid DVD/flash drive and are not a standard partitioned drive. So then report shows various errors which all related to that drive can be ignored.

Try this on ESP.
dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by eatdembeans on 2020-01-27
> **oldfred said:**
> Is this an Acer?
```
Boot0000* Linux    HD(1,GPT,4c6e73ea-ae44-4392-b141-4234546dfe35,0x800,0x100000)/File(EFIBootgrubx64.efi)RC
Boot0001* Unknown Device:     HD(1,GPT,4c6e73ea-ae44-4392-b141-4234546dfe35,0x800,0x100000)/File(EFIubuntushimx64.efi)RC
Boot0002* Linux    HD(1,MBR,0x382dfdd5,0x3f,0x1cea782)/File(EFIBootgrubx64.efi)RC

```

Acer is the only one I have noticed that uses the Unknown Device. Then from within UEFI you have to set "trust" to name the entry. 
Or did you name the Linux entries already?

You have the Ubuntu files in the ESP. So not sure where grub error is.
Most of the errors are related to the installer flash drive. Most installer are configured as hybrid DVD/flash drive and are not a standard partitioned drive. So then report shows various errors which all related to that drive can be ignored.

Try this on ESP.
dosfstools - dosfsck (aka fsck.msdos and fsck.vfat) utilities
Must be unmounted
sudo dosfsck -t -a -w /dev/sda1
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)


Yes it is an Acer Aspire 1. While I waited for help, I tried ubuntu, everything works fine, including updating, so there's something with lubuntu only.

I got a fresh lubuntu, used live usb, did "sudo ubiquity -b" and then installed boot-repair, here's the info without trying to install grub
[http://paste.ubuntu.com/p/4CwXcYKWWR/](http://paste.ubuntu.com/p/4CwXcYKWWR/)

then

lubuntu@lubuntu:~$ sudo dosfsck -t -a -w /dev/sda1
fsck.fat 4.1 (2017-01-24)
/dev/sda1: 40 files, 2047/130812 clusters

then I ran boot-repair again [http://paste.ubuntu.com/p/JsjvHxNJR4/](http://paste.ubuntu.com/p/JsjvHxNJR4/)

now I'm gonna restart and see what happens, will edit this later. This happens when I try to boot from hdd.

error: file '/boot/grub/x86_64-efi/normal.mod' not found
entering rescue modeI 
grub rescue>

EDIT: after this I enter live usb again, and I try what works on ubuntu


[LIST=1]
[*]Mount newly installed file system on /mnt:
  sudo mount /dev/sda2 /mnt
sudo mkdir /mnt/boot/efi
sudo mount /dev/sda1 /mnt/boot/efi
for i in /dev /dev/pts /proc /sys; do sudo mount -B $i /mnt$i; done
[/LIST]
  (where sda2 is the root partition and sda1 is the EFI system partition)
  
[LIST=1]
[*]Load efivars by:
  sudo modprobe efivars

[*]Reinstall grub-install for a 64-bit version
  sudo apt-get install --reinstall grub-efi-amd64
sudo grub-install --no-nvram --root-directory=/mnt

[*]Change root to /mnt and update grub
  sudo chroot /mnt
sudo update-grub

but again the error message is the same

lubuntu@lubuntu:~$ sudo grub-install --no-nvram --root-directory=/mnt
Installing for x86_64-efi platform.
Installation finished. No error reported.
lubuntu@lubuntu:~$ sudo chroot /mnt
root@lubuntu:/# sudo update-grub
sudo: unable to resolve host lubuntu: Resource temporarily unavailable
sudo: update-grub: command not found

[/LIST]
and after this, I ran the boot-repair to make a new report

[http://paste.ubuntu.com/p/qj6rmPBDBx/](http://paste.ubuntu.com/p/qj6rmPBDBx/)

---

### Post by oldfred on 2020-01-27
Report now is not showing the /EFI/ubuntu files & folders?
Everything else looks ok.

Are you using Boot-Repair or manually chrooting without Boot-Repair. Boot-Repair walks you thru the minimum commands to reinstall grub using its advanced options.

If chroot:
UEFI chroot
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

---

### Post by eatdembeans on 2020-01-27
> **oldfred said:**
> Report now is not showing the /EFI/ubuntu files & folders?
Everything else looks ok.

Are you using Boot-Repair or manually chrooting without Boot-Repair. Boot-Repair walks you thru the minimum commands to reinstall grub using its advanced options.

If chroot:
UEFI chroot
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

I only used boot-repair to generate the error link. If I try to do recommended boot repair, it will hang on the usual 

[COLOR=#000000]"creating config file /etc/default/grub with new version[/COLOR]
[COLOR=#000000]Installing for x86_64-efi platform."

This efi platform can only be installed if this command is used, [/COLOR]sudo grub-install --no-nvram, there is something with the bios of this laptop that requires this, that's what I read and I know that it passes every time --no-nvram is used.

[COLOR=#000000]next, when I try the link you posted, this happens:

[/COLOR]### Mounting ###

sudo mount /dev/sda# /mnt            #Mount root (/) partition
sudo mount /dev/sda# /mnt/boot       #Mount boot (/boot) partition 
                                      (if separate from root partition)
sudo mkdir -p /mnt/boot/efi          #Create EFI partition mount point
sudo mount /dev/sda1 /mnt/boot/efi   #Mount EFI partition

sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys

sudo chroot /mnt                     #Chroot to your installation

### Installing ###

apt-get install grub-efi-amd64  #Install grub EFI bootloader

after this I get, "[COLOR=#000000]E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem." and it hangs again at "installing for x86_64-efi platform.. so I cannot go further.
[/COLOR]

[COLOR=#000000]at this stage, if I try to boot from hdd, I get GNU GRUB version 2.02 Minimal bash-like line editing...
[/COLOR]

---

### Post by oldfred on 2020-01-27
You have to mount your install partition as part of chroot. 
The example /dev/sda# is replace # with the number of your /(root) partition or in your case sda2.

Is Internet not working?
As it has to download package.

Do you get grub> or grub rescue>
If grub> you can try this:
configfile (hd0,gpt2)/boot/grub/grub.cfg

---

### Post by eatdembeans on 2020-01-27
> **oldfred said:**
> You have to mount your install partition as part of chroot. 
The example /dev/sda# is replace # with the number of your /(root) partition or in your case sda2.

Is Internet not working?
As it has to download package.

Do you get grub> or grub rescue>
If grub> you can try this:
configfile (hd0,gpt2)/boot/grub/grub.cfg

Yes I replaced with sda1 as /mnt/boot and sda2 /mnt (this is the big partition)

I am online while I'm doing this

I get grub>
I typed what you said, it simply clears the entire screen and only grub> is showing, did a restart, and I'm back at grub> again

---

### Post by oldfred on 2020-01-27
You would not do a restart. 
The configfile should load the grub.cfg file & start boot after 10 seconds.
If some issues, boot could be slow. Or if video issues you could be booting, but not to gui. Or try Escape during 10 sec to see if menu appears.

---

### Post by eatdembeans on 2020-01-27
> **oldfred said:**
> You would not do a restart. 
The configfile should load the grub.cfg file & start boot after 10 seconds.
If some issues, boot could be slow. Or if video issues you could be booting, but not to gui. Or try Escape during 10 sec to see if menu appears.

There is nothing happening after I wrote that command, the screen simply cleared and showed grub> I waited about a minute, nothing happened.

In the meantime I tried this lubuntu-18.04-alternate-amd64.iso wrote it with rufus 3.8, MBR (with gpt it failed to boot), this iso has a dos-like installer, it was very slow (3 times slower than the ubiquity) but it finished without any problems. It booted up, everything was fine, I was so happy, after trying to get lubuntu on this machine for 3 days straight, finally it was working... and then I'm doing sudo apt-get update & upgrade, it was updating for like 30 minutes, until it hits this:

setting up secureboot-db (1.4~ubuntu0.18.04.1)..

and it hangs again... hard reset it
it boots again, trying to upgrade again, and the good old sudo dpkg --configure -a message appears again, when I run it,
setting up secureboot-db (1.4~ubuntu0.18.04.1).. and hangs

I don't know what else to do, I tried every lubuntu versions, they all fail at the same point while ubuntu works fine. Is there a way to reduce ubuntu's graphics or whatever uses that extra 6-700mb of ram constantly?

---

### Post by oldfred on 2020-01-27
If you are using BIOS/MBR, you cannot have UEFI Secure Boot on.


Graphics are based on your hardware.

Lots of details on install to Acer.
Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

---

### Post by eatdembeans on 2020-01-28
> **oldfred said:**
> If you are using BIOS/MBR, you cannot have UEFI Secure Boot on.


Graphics are based on your hardware.

Lots of details on install to Acer.
Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

Up till now I only tried with secure boot disabled because it didn't boot at all when that was enabled, now I'm trying with mbr and gpt partitioned usb sticks with or without secure boot but it's all the same, always hangs on the same thing when trying to sudo dpkg --configure -a

I do not have this what the guy in the link has
[COLOR=#242729][FONT=Arial]"Use the right cursor key to highlight "Security" and use the down cursor key to highlight "Select an UEFI file as trusted for executing" and press Enter."

I only have this [/FONT][/COLOR]https://imgur.com/a/0DVaDsz bios is the latest, I'm thinking to downgrade bios but the problem that most guys on the net are having is actually booting from the hdd, I can boot, I can enter linux np but as soon as I do the upgrade, it's dead. That means I can't even download any programs because dpkg is not working properly. Also, if the bios was the issue, how come ubuntu 18 is working properly after manually fixing the grub? (which cannot be done on lubuntu because :
[COLOR=#000000]
lubuntu@lubuntu:~$ sudo chroot /mnt[/COLOR]
[COLOR=#000000]root@lubuntu:/# sudo update-grub[/COLOR]
[COLOR=#000000]sudo: unable to resolve host lubuntu: Resource temporarily unavailable[/COLOR]
[COLOR=#000000]sudo: update-grub: command not found

BTW, Aspire ES1-533 is the machine model

---

### Post by eatdembeans on 2020-01-28
I read somewhere that sudo apt-mark hold secureboot-db helped a guy bypass this problem, indeed it did, I was able to run sudo apt-get upgrade properly until it reached to Installing for x86_64-efi platform. and it hangs again...

---

### Post by oldfred on 2020-01-28
Some other ES1 threads which may have a bit more info?

Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)
Details on password & trust setting:
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi)

Acer Aspire ES1-512: ubuntu 14LTS USB install over Windows 8.1  Set shim as secure in UEFI
black list some drivers for shutdown issues - post #9 link to Mint
[http://ubuntuforums.org/showthread.php?t=2256083](http://ubuntuforums.org/showthread.php?t=2256083)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)
Acer E1-531 UEFI menus.
[http://www.tomshardware.com/forum/65627-63-body](http://www.tomshardware.com/forum/65627-63-body)

---

### Post by eatdembeans on 2020-01-28
> **oldfred said:**
> Some other ES1 threads which may have a bit more info?

Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044)
[http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot](http://acer--uk.custhelp.com/app/answers/detail/a_id/27071/~/how-to-enable-or-disable-secure-boot)
[http://acer.custhelp.com/app/answers/detail/a_id/29349/](http://acer.custhelp.com/app/answers/detail/a_id/29349/)
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)
Details on password & trust setting:
[http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi](http://askubuntu.com/questions/597213/bootable-device-not-found-after-clean-install-of-ubuntu-14-04-uefi)

Acer Aspire ES1-512: ubuntu 14LTS USB install over Windows 8.1  Set shim as secure in UEFI
black list some drivers for shutdown issues - post #9 link to Mint
[http://ubuntuforums.org/showthread.php?t=2256083](http://ubuntuforums.org/showthread.php?t=2256083)
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)
Acer E1-531 UEFI menus.
[http://www.tomshardware.com/forum/65627-63-body](http://www.tomshardware.com/forum/65627-63-body)

Thanks a lot for trying to help but I gave up on this, everyone has a similar problem but they all solve it with efi trusted file (which my bios doesn't have, even when using older bios) and the main point is that everyone who has this problem they cannot boot ubuntu, I can manage that easily with the first guide that I posted in the OP but no matter what I do, even if I boot lubuntu (with the alternative iso, non-graphical installer) after the apt-get upgrade, it crashes. Now I'm checking if I can switch to lubuntu's desktop from a fresh ubuntu install, if that lowers ram usage I'll use it, if not, I'll try, LXLE or arch.

---

