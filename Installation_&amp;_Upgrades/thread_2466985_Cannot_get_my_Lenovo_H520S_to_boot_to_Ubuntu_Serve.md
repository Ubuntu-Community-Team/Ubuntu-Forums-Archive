---
title: "Cannot get my Lenovo H520S to boot to Ubuntu Server 20 LTS"
date: 2021-09-12
forum: Installation &amp; Upgrades
---

### Post by cakebaker67985 on 2021-09-12
Hello there,

I have been stuck on this for months, I recived an old computer for free and I wanted to install ubuntu server on it. 

The computer is a Lenovo H520S, and the bios date is 05/08/2012. 

I have installed ubuntu server on its hard drive, it previously had windows on it which worked just fine, and all I get is a message saying no OS could be found, however I can boot off the drive in my main PC. I ran the boot repair tool: [http://paste.ubuntu.com/p/5kpfc7bd4d/](http://paste.ubuntu.com/p/5kpfc7bd4d/)

This didn't fix the issue, I have no idea where to go from here, any help is appreciated.

---

### Post by MAFoElffen on 2021-09-14
And it will boot from a USB Key, such as an Ubuntu 20.0.04.3 Desktop LiveCD (USB)?

I looked at your report... And saw it error'ed out bad.

I see that it is UEFI... and I belive that it may have UEFI firmware updates for it, if you want to check that.It could use them. It was early UEFI.

Next, I see that you still have SafeBoot turned on, because it is trying to install grub-efi-amd64-signed... That should be okay with 20.04. But make sure to turn off the fastboot setting in the BIOS.

It is erroring out on the other drives? What is on the other drives you have in that machine? Especially this one:
```
Boot0003* WDC WD5000AAKX-083CA1	BBS(HD,,0x0)AMBO
```

---

### Post by cakebaker67985 on 2021-09-14
It will boot from a USB key, its booted off every live distro I have tried no problems there, 

Interestingly when I installed ubuntu server 18.04 LTS the restart after the installation went fine, and the OS worked perfectly, however when I turned the tower off and back on it came back with the OS not found error.

Is safeboot something I should turn off? if so how would I go about that? in the BIOS quickboot is disabled, im guessing thats the fastboot your referring to.

So that drive is the only drive in the system the WDC WD5000AAKX, its a 500Gb western digital hard drive that came with the pc. I haven't tried any other drives in the machine but I could pull an empty SSD out my main computer if it would help.

---

### Post by MAFoElffen on 2021-09-14
No.Wait. Trying to get an idea of what is there... You said 
> So that drive is the only drive in the system

But I see more drives in this system (in that report) than just that one...
```

===================================== UEFI =====================================

BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.

efibootmgr -v
BootCurrent: [COLOR=#FF0000]0001[/COLOR]
Timeout: 1 seconds
BootOrder: 0001,0000,0005,0003,0004
[COLOR=#ff8c00]Boot0000* ubuntu    HD(1,GPT,867f021e-bde0-4ba6-9bf3-780f6f7899ed,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
[COLOR=#ff0000]Boot0001* proxmox    HD(2,GPT,aebc9c90-0c59-4729-9178-84b8bade1696,0x800,0x100000)/File(\EFI\proxmox\grubx64.efi)[/COLOR]
Boot0003* WDC WD5000AAKX-083CA1    BBS(HD,,0x0)AMBO
Boot0004* SanDisk    BBS(HD,,0x0)AMBO
[/COLOR][COLOR=#008000]Boot0005* UEFI: SanDisk    PciRoot(0x0)/Pci(0x1d,0x0)/USB(1,0)/USB(1,0)/HD(1,MBR,0x2c534026,0x3c4,0x1340)AMBO
[/COLOR]This session has been detected as 'live' because /proc/cmdline contains (boot=casper)
This session has been detected as 'live' because df -Th / contains overlay
```

In most of it, I see sda and sdb, where sda is the wdc hdd that you installed Ubuntu to... with 3 partitions... sda1 is the EFI. sda2 is the /boot. sda3 is the root partition with LVM. SDB is the USB LiveCD you booted from.

I see two big problems. sdc is a mystery... Because there is no "sdc" and for some reason sometimes it thinks there is... Look at lines 403-405, and intermitterntly from Lines 102-153. That will cause problems, but it not the problem stopping you from booting... I'll go over that one after I go over resolving your main problem first, because I think that one is a really easy fix and is an additional/sideline issue....

*** The main problem is sort of two-fold. It looks as if the Server previously... Maybe before you had it, had Promox installed 'somewhere'. It no longer exists 'anywhere', except for the UEFI boot menu file in the EFI partition.
```

# Snip from lines 208-213
BootCurrent: [COLOR=#ff0000]0001[/COLOR]
Timeout: 1 seconds
BootOrder: [COLOR=#ff0000]0001[/COLOR],0000,0005,0003,0004
[COLOR=#ff0000]Boot0001[/COLOR]* proxmox    HD(2,GPT,[COLOR=#ff8c00]aebc9c90-0c59-4729-9178-84b8bade1696[/COLOR],0x800,0x100000)/File(\EFI\proxmox\grubx64.efi)

```
That EFI memu item is still there, and your UEFI BIOS Firmware is still set to boot the orphaned menu item to boot from...Instead of booting from your Ubuntu UEFI menu entry
```
Boot0000* ubuntu    HD(1,GPT,867f021e-bde0-4ba6-9bf3-780f6f7899ed,0x800,0x100000)/File(\EFI\ubuntu\shimx64.efi)
```

Recommendation:


[LIST=1]
[*]A soon as you get into your UEFI BIOS, on BIOS post, it should see that it only has one drive connected, and resolve thinking that it has anohter drive connected... 
[*]Go to the UEFI boot order and select the Ubuntu EFI menut item as the first in the order. 
[*]Turn off FastBoot. That will skip over most of the POST boot order chacks, which makes the booting faster... But has a big drawback, that it will disable the keyboard and mouse until POST is over... Sometimes "you need" that input interaction to do things on boot. 
[*]For now, leave SecureBoot enabled. That is how you installed 20.04 and should be working with that. If you still had 18.04 installed, I would tell you to turn it off. (That didn't support that yet.) 
[*]Then save, and reboot. It should boot. 
[/LIST]
 
Afterwards... Delete that promox efi menu item file and remove it from the EFI menu, using 'efibootmgr'. it has no place there anymore. You could delete this whole directory and files recursively: /dev/sda1/EFI/proxmox/.

With that, you should be running again in a matter of minutes.

---

### Post by cakebaker67985 on 2021-09-15
So that proxmox was my installation, I installed it on the WD hard drive. There used to be a CD drive in the system but I've taken it out for now just for easy access to the hard drive. 

So unfortunately before I saw your message I installed windows back on the machine, to try and run some lenovo UEFI diagnosis software, windows installed just fine and worked perfectly, unfortunately I couldn't get the diagnosis software to work.

Next I booted the computer into a live Kali and used Gparted to delete all the partitions on the hard drive, then reflashed a USB with Ubuntu server 20.04 LTS installer and installed that, it didn't boot again so I ran another boot repair [https://pastebin.ubuntu.com/p/cX6MX7SjQ8/](https://pastebin.ubuntu.com/p/cX6MX7SjQ8/). 

That sdc drive is still there, and for some reason the windows boot manager is still in the boot order bit, I went into the BIOS and updated by boot order so its now: USB, SATA1: WD drive, And nothing else.

For some reason it still isn't booting.

---

### Post by MAFoElffen on 2021-09-15
I'll talk you through it.

Boot from a USB LiveCD...

Please post the results of 
```
sudo efibootmgr
```

I see you are online. I will check this to get you through changing the order after I see what it returns...

---

### Post by cakebaker67985 on 2021-09-15
Thank you,

Sorry for the wait I had to flash a new USB, I booted into a live ubuntu 20.04 desktop, ran the command and got

```
sudo: efibootmgr: command not found
```

EDIT:

Sorry I realised you have to install it, so after installing it I get 

```

BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000, 0002, 0005, 0003, 0004
Boot0000* ubuntu
Boot0002* Windows Boot Manager
Boot0003* WDC WD5000AAKX-08CA1
Boot0004* KingstonDataTraveler 3.00000
Boot0005* UEFI: KingstonDataTraveler 3.00000

```

---

### Post by MAFoElffen on 2021-09-15
While still running the LiveCD, just install it...

```

sudo apt install efibootmgr

```
Trying to jump between doing a cert for work, release a Script for the Forum, and you...

---

### Post by cakebaker67985 on 2021-09-15
So I ran it and it came back with this:

```

BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000, 0002, 0005, 0003, 0004
Boot0000* ubuntu
Boot0002* Windows Boot Manager
Boot0003* WDC WD5000AAKX-08CA1
Boot0004* KingstonDataTraveler 3.00000
Boot0005* UEFI: KingstonDataTraveler 3.00000

```

Thank you, I really appreciate this

---

### Post by MAFoElffen on 2021-09-15
> **cakebaker67985 said:**
> So I ran it and it came back with this:
```

[COLOR=#ff0000]BootCurrent: 0000[/COLOR]
Timeout: 1 seconds
[COLOR=#ff0000]BootOrder: 0000[/COLOR], 0002, 0005, 0003, 0004
[COLOR=#ff0000]Boot0000* ubuntu[/COLOR]
Boot0002* Windows Boot Manager
Boot0003* WDC WD5000AAKX-08CA1
Boot0004* KingstonDataTraveler 3.00000
Boot0005* UEFI: KingstonDataTraveler 3.00000

```


It says it's pointing to the right Menu file now... It does not boot?

If not.... Get into your UEFI firmware and just try it with Secureboot disabled, and see if that makes a change...

---

### Post by cakebaker67985 on 2021-09-15
So I don't have a Secureboot option in my BIOS, I also don't have a option to switch between UEFI and Legacy, its always seemed a bit strange to me

---

### Post by cakebaker67985 on 2021-09-15
So I dont have a Secureboot option in my BIOS, I dont have a option to switch between uefi and legacy either, which always seemed weird

---

### Post by MAFoElffen on 2021-09-15
What is your MotherBoard? Would you be willing to run a little test on a Forum's Sponsored script called system-info? Does nothing but collect support type of system information... You can download and run it while booted from the LiveCD.

But would also tell me allot about the BIOS, How it was booted, If it does have a SecureBoot setting, etc. Just pick the option at the end to upload it to a Pastebin... and post the link to it from a post.

I'm just about to push updates to the Forum's GitHub...

---

### Post by cakebaker67985 on 2021-09-15
So it's an OEM build and the only markings on the motherboard I can see are "CIH61MIV1.1" yeah I dont mind running a test, is it on my main pc or the server you want it running? only issue is not sure how I'd run it on the server

---

### Post by cakebaker67985 on 2021-09-15
I ran the script the link to the pastebin is [https://paste.ubuntu.com/p/gjSV2XKxBw/](https://paste.ubuntu.com/p/gjSV2XKxBw/)

---

### Post by MAFoElffen on 2021-09-15
Dang. You were right. I do not see SecureBoot showing up there. I do not see anything about a /dev/sdc device. I see no Firmware updates for it at Lenovo. And it is old/very Early UEFI.

Question... When you installed and partitioned... Did you notice where it said it was installing Grub to?

---

### Post by cakebaker67985 on 2021-09-15
Yeah it is almost a relic at this point XD. I can't say I did, tend to do something else and let the installer do its thing, is there a way to check on the live boot?

---

### Post by MAFoElffen on 2021-09-15
if you reboot it... For Lenovo,the EFI Boot Menu is usually <F12> or <Fn><F12>... Can you try to boot from the menu to the Hard disk menu item and sdee if that works? If not, then try the Ubuntu one... 

I'll wait. There is wasy to check from the LiveCD, but I need to check in my Dev notes... I'll look those up while I wait for your response...

---

### Post by cakebaker67985 on 2021-09-15
So when I go into the boot selection menu, the only option I have is the hard drive or to enter setup, if I select the hard drive It still comes up with the OS not found error

---

### Post by MAFoElffen on 2021-09-15
Did NOT try the boot-repair LiveCD again...

Let me go through your posts and your reports and come up with instructions for you... Something is off there somewhere.

You said you did not have SecureBoot anywhere in your settings right?

When you ran the script, did it mention that mokutil was not installed?

---

### Post by MAFoElffen on 2021-09-15
If mokutil is not installed on your Ubuntu Desktop LiveCD... Install it and ...
```

sudo apt update
sudo apt install mokutil
mokutil --sb-state

```
Tell me what it said on the last command...

---

### Post by cakebaker67985 on 2021-09-15
Yes, theres no secure boot option anywhere. No, it mentioned curl and pastebinin weren't installed, but I installed them and it seemed to run fine

---

### Post by MAFoElffen on 2021-09-15
Please tell me the output of 
```

mokutil --sb-state

```

---

### Post by cakebaker67985 on 2021-09-15
So the command ```
 mokutil --sb-state
```

returned 

```
 This system doesn't support Secure Boot 
```

---

### Post by MAFoElffen on 2021-09-15
For some reason (I am the author of the Forum's system-info script), my script skipped reporting that in the report... That command is in there and should have shown up right after the other BIOS information in that report... Dang, I'll debug that later. LOL

And there is a confirmation of the problem... Both the install and Boot-repair misread something. If you look at all the boot-repair reports, it installed grub-efi-amd64 signed and configured it as if it was... well here is what it used for a command (you will see it yourself)...
```
grub-install --efi-directory=/boot/efi --target=x86_64-efi [COLOR=#ff0000]--uefi-secure-boot[/COLOR]

```
You reinstalled with LVM again right?

---

### Post by MAFoElffen on 2021-09-15
Post the results of these and I will talk you through it manually...
```

fdisk -lu
pvscan
vgscan
vgchange -a y
lvscan

```

---

### Post by cakebaker67985 on 2021-09-15
Haha if it helps I saw the "This system doesn't support Secure Boot" come up somewhere as the script was running XD.

I believe I did reinstall with LVM, I left everything as default which I think puts it in an LVM

---

### Post by MAFoElffen on 2021-09-15
To help me debug that script... You say it showed up when you viewed it in 'less'? But somehow when it prepared the written report, it skipped over it in and didn't include it... Hmmm. That was an important key to your problem. LOL

---

### Post by MAFoElffen on 2021-09-15
As soon as I get that info from those commands, which has a litle different output for the LVM names, then I will post instructions to mount the filesystem of your installed, chroot into it, to purge the signed version and install the regular EFI version of grub.

---

### Post by cakebaker67985 on 2021-09-15
So the fdisk -lu one might be a struggle to copy out.

pvscan

```

/dev/sdc: open failed: No medium found
PV /dev/sda3 VG ubuntu-vg           lvm2 [<464.26GiB / <264.26 GiB free]
Total: 1 [<464.26 GiB] / in use: 1 [<464.26GiB / in no VG: 0 [0    ]

```

vgscan

```

/dev/sdc: open failed: No medium found
Found volume group "ubuntu-vg" using metadata type lvm2

```

vgchange -a y

```

/dev/sdc: open failed: No medium found
/dev/sdc: open failed: No medium found
1 logical volume(s) in volume group "ubuntu-vg" now active

```

lvscan

```

/dev/sdc: open failed: No medium found
ACTIVE                    '/dev/ubuntu-vg/ubuntu-lv' [200.00 GiB] inherit

```

---

### Post by cakebaker67985 on 2021-09-15
Yeah it showed up in less, I figured you would see it in the report so I didn't mention it XD

---

### Post by MAFoElffen on 2021-09-15
Just for my own info... start the file manager and look at the 1GB /dev/sda2 and see if that is the boot partition or what is there...

---

### Post by cakebaker67985 on 2021-09-15
For fdisk -lu are just the names okay?

```

Disk /dev/loop0: 2.1 GiB,

Disk /dev/loop1: 55.45 MiB,

Disk /dev/loop2: 219 MiB,

Disk /dev/loop3: 65.1 MiB,

Disk /dev/loop4: 32.3 MiB,

Disk /dev/loop5: 50.98 MiB,

Disk /dev/sda: 465.78 GiB,
Disklabel type: gpt

Device    Type
/dev/sda1    EFI System
/dev/sda2    Linux filesystem
/dev/sda3    Linuxfilesystem

Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 200GiB,

Disk /dev/sdb: 28.98 GiB,
Disklabel type: dos

Device    Type
/dev/sdb1    Empty
/dev/sdb2    EFI
/dev/sdb3    Linux

```

---

### Post by cakebaker67985 on 2021-09-15
Inside that 1GB /dev/sda2 there is efi grub and grub.bak and some config files, system maps and vmlinuz files

---

### Post by MAFoElffen on 2021-09-15
From there...
```

sudo su
mount /dev/ubuntu-vg/ubuntu-lv /mnt
mount -o bind /dev /mnt/dev
mount -o bind /proc /mnt/sys
mount -o bind /sys /mnt/proc
mount /dev/sda2 /mnt/boot
mkdir /mnt/boot/efi
mount /dev/sda1 /mnt/boot/efi
chroot /mnt

```
Tell me when you get to that point...

---

### Post by cakebaker67985 on 2021-09-15
Running the first mount command came back with 

```
mount: /mnt: special device /dev/ubuntu-vg/root does not exist
```

---

### Post by MAFoElffen on 2021-09-15
Edited my last post from the bottom of your Post #19...

---

### Post by cakebaker67985 on 2021-09-15
Ah Thank you, I got to 

```
mount -t bind /sys /mnt/proc
```

and got back 

```
mount: /mnt/proc: unknown filesystem type 'bind'
```

---

### Post by MAFoElffen on 2021-09-15
Change the t to an o...
```

mount -o bind /mnt/proc/

```

---

### Post by cakebaker67985 on 2021-09-15
ah, I thought that might be the case but I didn't want to assume XD. I'm up to the last command, when I tried to make the efi directory it said it already exists so I just mounted it, is that okay?

---

### Post by MAFoElffen on 2021-09-15
Yes... Just wanted to make sure it was there...

Are you chrooted into it yet?

---

### Post by MAFoElffen on 2021-09-15
Once you are chrooted into your own installed system, then if still in a root prompt (if not, add sudo to these)
```

apt purge grub-efi-amd64-signed
apt install grub-efi-amd64
grub-install --efi-directory=/boot/efi --target=x86_64-efi
 
```
Tell me how that goes...

---

### Post by cakebaker67985 on 2021-09-15
So it all went okay up until the last line there was a load of "No such Device" errors for /dev/sda1 through sda3, then grub-install error "failed to register the EFI boot entry: Operation not permitted

---

### Post by MAFoElffen on 2021-09-15
Remount the drives via this
```

mount -a

```
Then retry that last command...

---

### Post by cakebaker67985 on 2021-09-15
The 

```
mount -a
``` 

goes through okay, but the same errors come up

```
Unknown device "/dev/sda1": No such device
```

---

### Post by MAFoElffen on 2021-09-15
If you look at sda1 with the file manager, that should be the EFI drive with the Ubuntu directory with it's efi menu and shim files right?

Try to post the fstab from /etc/fstab...

---

### Post by cakebaker67985 on 2021-09-15
I cant actually see sda1 in the file program, but its file type under fdisk is EFI

---

### Post by MAFoElffen on 2021-09-15
yes... as it should be... and it should be mounted to /boot/efi (from inside the chroot)
```
mount | grep '^/dev' | sort
```

---

### Post by cakebaker67985 on 2021-09-15
Running that gave me 

```

mount: failed to read mtab: No such file or directory

```

---

### Post by MAFoElffen on 2021-09-16
This is getting weirder...

Okay...
```

ls -l /boot/efi

```

---

### Post by cakebaker67985 on 2021-09-16
so that came back with 

```

total 4
drwxr-xr-x 4 root root 4096 Sep 15 19:28 EFT

```

---

### Post by MAFoElffen on 2021-09-16
EFT? What the Heck? What is in that directory?

---

### Post by MAFoElffen on 2021-09-16
Okay. New plan.

```

exit
exit
sudo unmount /mnt

```
Start up gparted... give that disk a new gpt partition table.

Download an Ubuntu Server 18.04 LTS ISO. 18.04 was the old server installer system and was before they started supporting SecureBoot again, so the Grub with be the correct flavor.
Burn it to a USB.
Install it.
Reboot.
On reboot
```

sudo apt update
sudo apt dist-upgrade
sudo do-release-upgrade

```
That is simpler and less time on a new install. There is just strange things going on there. And this is simpler at this point. WOW.

---

### Post by cakebaker67985 on 2021-09-16
Sorry for taking so long to get back. 

So I used gparted to delete all the partitions, then created 1 big new etx4 partition. I installed Ubuntu server 18.04 LTS, and here's where it gets interesting... it installs just fine, the first reboot where it asks you to take the media out and hit entre works and it boots into ubuntu server and everything works, I run the first two commands and they work, then when I try the last command it says the system needs to reboot after the 2 command, now when I do this I get the dreadful "No operating system found" error...

---

### Post by MAFoElffen on 2021-09-16
Aaaaaa.... It is UEFI only... it has to create at least a 256MB Minimum (usually 500MB - 1GB) partition marked as EFI/ESP for UEFI to boot. So if you had left it blank, with just the GPT partition table, it would have created that... Or if you have created a 500MB - 1GB EFI partition, formatted as Fat32, again marked as EFT/ESP, it would have used that as, and done the rest with the unallocated spaced on it's own.

One of the big bug's that I have found with the new (20.04 and newer) Server Live Installer, it that it doesn't play well with pre-partitioned drives. Not the EFI partition, but with any other's. It likes the drive to be empty/barren.

Up to try that again?

---

### Post by cakebaker67985 on 2021-09-17
Yeah I'm definitely up for trying that! I really wanna get this working XD

 I used gparted on a live boot to delete all the partitions, and left the drive unallocated. Then I installed Ubuntu server 20.04 LTS, the install went fine, but It didn't reboot into the system it came back with no OS found again. So I went back into the live boot and looked at the partitions, it seems to have done everything right.

There is 

```
/dev/sda1 fat32 512MB boot, esp 
/dev/sda2 ext4 1GB 
/dev/sda3 lvm2 pv ubuntu-vg 464.26GB
unallocated 1.02MB
```

Now I did run another boot repair, BUT this time I went into advanced and unchecked the secure boot option, and as far as I can tell it installed grub with secure boot disabled. [https://pastebin.ubuntu.com/p/dPNCHnq3mR/](https://pastebin.ubuntu.com/p/dPNCHnq3mR/)

Sadly it still didn't boot

---

### Post by MAFoElffen on 2021-09-17
I can see that you installed 20.04 Server again (Instead of what I asked you to try with trying to install Server 18.04)... The boot-repair was running 18.04... I can see that it created everything correctly, and all the pointers were correct. It's still a mystery of the why it is not booting.

I can see that it purged and installed grub-efi-amd64-signed, instead of grub-efi-amd64... but it did configure it as:
```

grub-install --efi-directory=/boot/efi --target=x86_64-efi --no-uefi-secure-boot
Installing for x86_64-efi platform.
Installation finished. No error reported.
df /dev/sda1
mv /mnt/boot-sav/mapper/ubuntu--vg-ubuntu--lv/boot/efi/EFI/Boot/bootx64.efi /mnt/boot-sav/mapper/ubuntu--vg-ubuntu--lv/boot/efi/EFI/Boot/bkpbootx64.efi
cp /mnt/boot-sav/mapper/ubuntu--vg-ubuntu--lv/boot/efi/EFI/ubuntu/grubx64.efi /mnt/boot-sav/mapper/ubuntu--vg-ubuntu--lv/boot/efi/EFI/Boot/bootx64.efi

grub-install --efi-directory=/boot/efi --target=x86_64-efi --no-uefi-secure-boot
Installing for x86_64-efi platform.

```
And finished without errors...

One thing I did notice is that the Boot-repair disk is still 18.04 and you haven't tried to install Server 18.04 yet right?

---

### Post by cakebaker67985 on 2021-09-18
So I wiped the disk with gparted again, let it unallocated, I installed 18.04 again and had the same weird issue as last time where it rebooted after the install into the Operating system and worked, but When I rebooted it again it came back with no OS found. 

I ran another boot repair and unchecked the secure boot option again: [http://paste.ubuntu.com/p/mnHBkR3KB7/](http://paste.ubuntu.com/p/mnHBkR3KB7/)

I did notice something interesting in there

```
[COLOR=#BB4444][FONT=monospace]Disks info: ____________________________________________________________________
[/FONT][/COLOR] 
[COLOR=#BB4444][FONT=monospace]sda    : is-GPT,    no-BIOSboot,    has---ESP,     not-usb,    not-mmc, has-os,    2048 sectors * 512 bytes[/FONT][/COLOR]
```

The no-BIOSboot, is that something to be worried about?

---

### Post by MAFoElffen on 2021-09-19
This is how I setup my GPT disks (prepartitioned) here, no matter what they are going into...
```

GPT partition table
1MB unallocated before anything
1-5MB Partition, unformatted, Labeled boot_grub, type EF02 (bios_grub flag)
500mb-1G, fat32, Labeled EFI, type EF00 (ESP/EFI flag)

```
That way if can go into Legacy or UEFI machines.

"bios_boot" is for Legacy BIOS boot Machines to be able to boot GPT disks. The BIOS-boot partition is a container for GRUB 2's core. It is necessary if you install Linux on a GPT disk, and if the firmware (BIOS) is set up in Legacy (not EFI) mode. It must be located at the start of a GPT disk, and have a "bios_grub" flag.

This is NOT yours. Yours is UEFI only.

---

### Post by MAFoElffen on 2021-09-19
Please... Do this...
```

sudo fdisk -l | sed '/\/dev\/loop/,+3 d' 2> /dev/null | uniq

```
I want to see if anything there (partitons on sda) is marked as bootable...

---

### Post by cakebaker67985 on 2021-09-19
Ah okay thank you that's good to know.

So I ran that command and it came back with: 

```


Disk /dev/sda: 465.78 GiB
Disk model: WDC WD5000AAKX-0
Disklabel type: gpt

Device          start        end           Sectors      size    type
/dev/sda1     2048        1050623    1048576   512M   EFI system
/dev/sda2     1050624   3147775    2097152   1G       Linux filesystem
/dev/sda3      3147776  976771071 973623296 464.3G Linux filesystem


Disk /dev/mapper/ubuntu--vg-ubuntu--lv: 200 GiB

Disk /dev/sdb: 28.89 GiB,
Disk model: DataTraveler 3.0
DiskLabel type: dos

Device         Boot           Start             End             Sectors            Size              Id             Type
/dev/sdb1     *              0                  5999871      5999872          2.9G             0              Empty
/dev/sdb2                     5271500       5279499      8000                3.9M             ef             EFI (FAT-12/16/32)
/dev/sdb3                     6000640     60538880       54538241         26G             83            Linux


```

On sdb there is a Boot column but not on the sda drive, is this the issue?

---

### Post by MAFoElffen on 2021-09-19
Yes...

I looked through your posts last night and when I reviewed the result of your system-info script I noticed that it didn't say that sda1 was flagged with both ESP "AND" boot.

If you boot it up on a Gparted disk, can you make sure that the EFI partition, sda1, has both the ESP and boot flags?

---

### Post by cakebaker67985 on 2021-09-19
In gparted sda1 is showing as having both boot and esp flags. This is from gparted on a live "try ubuntu" distribution, I'm not sure if that would make a difference.

---

### Post by MAFoElffen on 2021-09-19
Everything appears as it should. There is no visible reason from what I can see why this does not find the OS.

Try this ISO an see if it helps. Has a good GUI and some advanced tools... See if it "see's" the OS. If it can see it, it can probably boot it. And if it can boot it, it can probably create and build a workable Grub Boot loader to it.
[https://www.supergrubdisk.org/rescatux/](https://www.supergrubdisk.org/rescatux/)

---

### Post by westie457 on 2021-09-19
Hi just joining in here, freely admitting that I know little to nothing about LVM and what I suggest may be way off target.

To me there are a few items in the last Boot report that seem strange, starting at line #241.

There appears to be something wrong with the fstab.

---

### Post by MAFoElffen on 2021-09-19
@westie457

That is more a "specific" of the boot-repair script of yannubuntu... when it is identifying which of the devices is what, and where things are... it cannot identify the LVM member as having the EFI esp member internally (true before the mount of the LVM). But it has the fstab. file in it. The sda2 is not readable, alone, because it is LVM over it. So it does not see a readable fstab file without using LVM (true). Sda1 is efi/esb and has no fstab on it. (true)...

After it identifies those pieces of the puzzle and activating and the mounting of LVM, it mounts the /efi into the root drive into LVM root, as /boot/efi... Then it is all pieced together in the system filesystem tree. His script inserts fstab entries into a temporary fstab file to do that to facilitate the chroot of the system from a script. Yann and I have talked about what we each do.

But because we haven't seen that ftsab file that resides within the LVM, we cannot confirm that. But if the only problem was a bad fstab entry, it would not say it could not find an OS, it would start to boot and say it had a mount error...

I do the same on my Ama-gi Project support LiveCD. An automated chroot to be able to repair an installed system.

The big difference in this last report from boot-repair, is that this last time, it did have many errors in installing and configuring Grub.

Does that make sense to you now?

---

### Post by westie457 on 2021-09-20
@MAFoElffen

Thank you for the explanation, it sort of makes sense and also makes me realise how little I know about LVM.

---

### Post by cakebaker67985 on 2021-09-20
So, I've run most of the scripts in the "boot" section, the Easy GNU/Linux Boot Fix, Check UEFI Boot, UEFI Partition Status, all of them come back okay all green ticks. Now the partitions the system detects are...

```


sda1 EFI System vfat boot,esp flags

sda2 Windows_/_Data_/_Other ext4

sda3 Cannot_mount LVM2_member

sdb1 Cannot_mount iso9660

sdb2 Windows_/_Data_/_Other vfat

loop0 Debian_GNU/Linux_10_ squashfs

dm-0 Ubuntu_18.04.5_LTS_ ext4


```

I ran the first script on the dm-0 partition which I think is right? it came back all fine

I ran the last script on the EFI sda1 partition and it came back all okay.

THe second script also came back okay.

In "Grub" I ran Restore Grub and it ran all okay as well, and I ran Update Grub Menus this also came back okay.

However... It still wont boot. I'm still confused at to why with 18.04 LTS the first reboot works, and then it stops working, and all the live usbs run just fine but it wont boot off the hard drive.

---

### Post by westie457 on 2021-09-21
@cakebaker67985

In my first post in this thread I stated how little I know about LVM, also I have about the same level of not knowing about server installs.

If you are willing to try a different approach to attempt to resolve this issue it will involve yet another clean install.

If your answer is yes I will post some instructions after.

---

### Post by cakebaker67985 on 2021-09-22
@westie457

Yeah I'm willing to try pretty much anything to get this working, I dont have the money to put together another machine XD

---

### Post by westie457 on 2021-09-22
This is what I would like you to do.

Clean install of your system however you want to set it up. If after the install you are allowed to continue evaluating the OS before rebooting open a terminal and run these commands ```
[COLOR=#333333][FONT=UbuntuMono]sudo add-apt-repository ppa:yannubuntu/boot-repair
[/FONT][/COLOR]sudo apt-get update 
[COLOR=#333333][FONT=UbuntuMono]sudo apt-get install -y boot-repair && boot-repair[/FONT][/COLOR]
```Click the button to generate a report, post the link here.

Reboot into your new install and repeat the above.
when the 2nd report has been posted run ```
sudo apt update
sudo apt upgrade
sudo apt full-upgrade  #this one is just in case some packages were held back
```

Run another Boot-Repair report if you wish.

Now it is hit and hope time.

Reboot (hopefully) into your new system. 

All good hurrah, or complete failure boo!

Grab your installion USB run in try-mode. Please do not use the Boot-Repair ISO.

Run the commands used at the top of this post. DO NOT try any repairs yet, just generate another report. Hopefully there should be enough differences between them to see where things have not gone right.

---

### Post by MAFoElffen on 2021-09-22
LOL. You can try. You have run it 3 times already and it has not given you joy yet. Yann updated his ppa, repo and the boot-repair disk about the same time... I have emails to him about your system specifically, some other things on my Opensource Project, and a few bugs I found in his script on some other tests for him.

Today, just hours ago, I bought a Lenovo T520 Thinkpad, which supposedly has the same BIOS as yours... I am imaging it right now to a 2TB SSD that I want to install in it. 

I did notice a few settings in the firmware setup. Go ahead and do whatever. It will take a while before this finishes imaging.

I had just renewed my Dell Service Engineer Cert's, and was told I need to renew my HP and Lenovo Cert's for 2021, which they scheduled both courses for later this week. I do warranty service on all three brands. So I have been a bit busy lately. LOL.

---

### Post by cakebaker67985 on 2021-09-23
@westie457 @MAF0Elffen

So something interesting happened... before I tried westies solution, for other reasons I pulled the ssd out my main tower, and seeing as it my lying around I thought I would install ubuntu server on it and see if the server would boot off it. For reference I used a USB3.0 to SATA cable to plug it into the server. 


So I tried ubuntu server 18.04 LTS first, but it errored out consistently around when you put your details in like your server name and username and password and stuff, so I updated it and installed ubuntu server 20.04 LTS. The install all went to plan and... IT REBOOTED, now here's the weird part. it rebooted into ubuntu server 18.04.... the hard drive... I turned it off and tired to get it to boot onto the SSD but in the boot menu at the post screen it only showed the hard drive. 

So I unplugged the SSD and turned it on and it booted again... and now as far as I can tell its fixed... I genuinely have no idea what the hell fixed it, if you guys want I'll use boot repair to generate a report on pastebin see if it answers any questions.

---

### Post by MAFoElffen on 2021-09-23
I would like to see a boot-repair and system-info reports on it. 

So maybe a loose connection might have also been what was causing that intermittent phantom reporting of sdc???

After I got through imaging the original drive in my new (to me) Lenovo T520, i Installed that 2TB SSD in it. Then installed Ubuntu 20.04.3 along side Windows 10 Pro. Had no problems, complaints, or hickups at all.

---

### Post by cakebaker67985 on 2021-09-25
Hey, so I generated those reports

The system info one is [https://paste.ubuntu.com/p/Kw9XgSJkK8/](https://paste.ubuntu.com/p/Kw9XgSJkK8/)

and the boot info report is [http://paste.ubuntu.com/p/hC89qhdJTj/](http://paste.ubuntu.com/p/hC89qhdJTj/)

---

### Post by MAFoElffen on 2021-09-26
Your link for the pastebin for boot-repair is broken. I think your link for the boot-repair should have been: [https://pastebin.ubuntu.com/p/hC89qhdJTj/](https://pastebin.ubuntu.com/p/hC89qhdJTj/)

The curiosity now is that you ran both reports while booted from the LiveCD...

You could have installed installed boot-info to your server, and downloaded the ssystem-info script to a directory, then ran both native from your Server OS. The reports would have shown what is going on with your installed/now booting system. So I think those reports are just a bit slighted/Biased.

The reason I think I want to see that. is that the boot-repair report still shows "sdc"... Which is still a mystery to me (???)

---

### Post by cakebaker67985 on 2021-09-26
Ah that was my typo in the link, its fixed now. However when I tried to install anything on the server I had this [issue]("https://askubuntu.com/questions/1040974/ubuntu-server-18-04-apt-get-fails"), I did fix it using the meathod in that discussion but I thought I would mention it.

This is info script [https://paste.ubuntu.com/p/dG2dDRQSqq/](https://paste.ubuntu.com/p/dG2dDRQSqq/)

for the boot-repair script, I cant see a way of running it without a GUI, I have ubuntu server installed so im not sure if it will work?

---

### Post by MAFoElffen on 2021-09-27
Yann's boot-info script is different that his boot-repair script. The boot-info script "was" started year's ago (at least over a decade ago), and has gone many updates, through three groups of Maintainers. Yann is the present Maintainer of the current script. We used to have very many user's who had any kind boot issues run "that script" before Yann made the Boot_repair disk and his Boot-repair script. That is what he based the boot-repair script from. That script will create a report without making changes... Your's is working now. We don't need to repair it, or possibly break it. We just want to see it.

It can be found at and downloaded from: [https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Use the "Download link" there. It comes in a Tar Ball... So what I would do is download it from a browser, unpack it and put it on a USB drive... Be able to use that USB drive, to copy to your server... to run the script...

---

