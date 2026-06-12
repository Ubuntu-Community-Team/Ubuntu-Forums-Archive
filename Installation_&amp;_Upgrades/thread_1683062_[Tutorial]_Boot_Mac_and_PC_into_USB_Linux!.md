---
title: "[Tutorial] Boot Mac and PC into USB Linux!"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by Neds Moar Salt on 2011-02-06
Nobody say this isn't possible because I will shoot you.  After writing two somewhat-wrong guides, I have finally corrected my process.  In this post is the instructions to create a linux USB drive and boot Ubuntu from it (and also refit on macs).

[CENTER][B][SIZE=5][SIZE=4]Step 1 - USB Linux[/SIZE]
[/SIZE][/B][LEFT]This is the step where we make a usb drive that we can run linux off of.  In order to boot your usb drive, your pc bios must support it.  Mac's bios (not the efi) doesn't support this, however mac users can use refit, which is discussed later.

Get yourself some of these:

[LIST=1]
[*]A USB key (at least 1GB if you want to run Ubuntu)
[*]Fdisk (this comes with ubuntu, but not debian)
[*]grub-pc (this is also a default ubuntu package)
[*]The tools necessary to create fat filesystems (this comes with ubuntu but not debian)
[/LIST]

[CENTER][B][SIZE=4][SIZE=3]1.1 - Formatting[/SIZE]
[/SIZE][/B][LEFT]This will delete all your USB data.

Firstly, unmount all partitions on your USB drive.

Open your terminal and:```
sudo -s
fdisk <usb name>
```Now you will be at the fdisk prompt, about to edit the partition map on your usb drive.  Now enter these commands:```
c
u
```What these do should be pretty obvious once you have entered them.

Now, lets create a new mbr table:```
o
```Next, let's make some partitions.  4MB for grub and the rest for ubuntu and other things:```
n
p
1
<enter>
+4M
n
p
2
<enter>
<enter>
w
```Now we need to create the filesystems.  Open up your favorite disk manager and format the 4MB partition as ext2 and the other one as fat32.  Then mount them both.

[CENTER][B][SIZE=4][SIZE=3]1.2 - Linux on USB[/SIZE]
[/SIZE][/B][LEFT]
Note: Grub may not run correctly when used with computers with grub installed on the internal hard drive, especially mac computers.

Now we need to install grub onto the usb drive.  Use this command:```
cd <mountpoint>
sudo grub-install --root-directory=. <usb device, mine is /dev/sdc>
```Now open up that disk manager again and set the bootable flag on the 4MB partition.

[CENTER][SIZE=5][B][SIZE=4]Step 2 - Ubuntu on your USB Drive[/SIZE]
[/B][/SIZE][LEFT]Now we will add ubuntu to your flash drive.  This will allow you to boot into ubuntu live from your flash drive.  Grab the following:

[LIST=1]
[*]An Ubuntu live cd iso
[*]About 700MB free space on your fat partition
[/LIST]
[CENTER][B][SIZE=4][SIZE=3]2.1 - The Files[/SIZE]
[/SIZE][/B][LEFT]Do this:

[LIST=1]
[*]Mount your fat partition
[*]Copy the iso to the root of your fat partition
[*]Name the iso "Ubuntu.iso"
[/LIST]
We now have the iso copied to the fat partition.  Brilliant.

[CENTER][SIZE=3]**2.2 - The Bootloader**[/SIZE]
[LEFT]Do this now:

[LIST=1]
[*]Mount your 4MB ext2 partition
[*]Check if you have write permissions for the partition.  If not, run the next step as superuser
[*]Run "gedit" in terminal
[*]Enter the following:
menuentry "Ubuntu Live from ISO" {
insmod fat
search.file /Ubuntu.iso root
loopback loop /Ubuntu.iso
linux /casper/vmlinuz boot=casper iso-scan/filename=/Ubuntu.iso
initrd /casper/initrd.lz
}
[*]Save this file as <mountpoint>/boot/grub/grub.cfg
[/LIST]
[CENTER][SIZE=4]**Step 3 - USB Linux for Macs**[/SIZE]
[LEFT]You will need:

[LIST=1]
[*]Access to Mac OS 10.4.6 or later with elevated permissions
[*]To format your flash drive with an additional partition at the end (16MB should do)
[/LIST]
Here are the steps to make the flash drive bootable on EFI Macs

[LIST=1]
[*]Download rEFIt from [here]("http://refit.sourceforge.net/").  You should grab the one packaged as a gzip
[*]Format that third partition on your flash drive as hfs+.  This can be done in disk utility by formatting it as "Mac OS Extended".  You can pretty much choose any of those, but I would recommend not choosing a case sensitive file system.
[*]Copy the "efi" folder you just downloaded into the hfs+ partition (it's inside the refit-bin-x.xx folder you downloaded from the above link)
[*]Open up a terminal
[*]Execute the efi/refit/enable.sh file.  This needs to be the one on the flash drive, not the one on the disk.  What this does is blesses rEFIt so the Mac's equivalent of a BIOS can find it.
[*]Reboot your computer holding the option key.  You should know what to do then.
[/LIST]
Once in the rEFIt menu:

[LIST=1]
[*]You will need to boot linux from HD (it will have the red/orange flash drive icon)
[*][COLOR=Red]IMPORTANT: if you have a non-default MBR on your internal HD #1, the last step will fail.  There is no way around it.  The only way it will not fail is if your MBR is default of if you already have grub installed on the internal HD.  For example: if you have windows installed on the internal HD and push boot from HD (flash drive), windows will boot.  Yes, I know, Apple did a ****** job emulating a BIOS.[/COLOR]
[/LIST]
[/LEFT]
 [/CENTER]
[/LEFT]
[/CENTER]
[/LEFT]
[/CENTER]
[/LEFT]
[/CENTER]
 [/LEFT]
[/CENTER]
[/LEFT]
[/CENTER]
[/LEFT]
[/CENTER]

---

### Post by BMacK1311 on 2011-02-07
Thanks again Neds.

I'm going to try this today but while you're working on the "coming soon" portion, Is it possible to create a fork that uses grub2 (1.99) efi for the macs? Your last thread works for newer hardware, but not for older MBP's. Any insight will be appreciated.

---

### Post by Neds Moar Salt on 2012-01-02
> **BMacK1311 said:**
> Thanks again Neds.

I'm going to try this today but while you're working on the "coming soon" portion, Is it possible to create a fork that uses grub2 (1.99) efi for the macs? Your last thread works for newer hardware, but not for older MBP's. Any insight will be appreciated.

Yes.  You won't need an ext2 partition for grub.  You just need to compile it yourself and shove the hfsplus driver into the image with grub-mkimage.  Then you stick it on the hfs+ partition (or, if you have a newer mac, just put the image as /EFI/boot/bootx64.efi, assuming you have a 64-bit computer) and bless it instead of rEFIt.

See: [https://help.ubuntu.com/community/MactelSupportTeam/EFI-Boot-Mactel](https://help.ubuntu.com/community/MactelSupportTeam/EFI-Boot-Mactel)

---

### Post by windfix on 2012-01-02
I have only tested on one MacBook Pro (about 2 years old), but for booting a Mac from USB drive this works like a charm:

[http://www.plop.at/en/bootmanagerdl.html](http://www.plop.at/en/bootmanagerdl.html)

Burn the .iso to a CD.  Insert a live Ubuntu (or other) USB drive in the Mac.  Boot holding the C key - to boot from the CD.  Plop will give you a menu of disks and partitions to boot from, including USB... and the USB drive takes it from there.

Update:  This only worked from a few MacBook Pro models, failed on other MBP's.  Dangit.

---

### Post by reachcontrol on 2012-03-08
> **Neds Moar Salt said:**
> 
[*][COLOR=Red]IMPORTANT: if you have a non-default MBR on your internal HD #1, the last step will fail.  There is no way around it.  The only way it will not fail is if your MBR is default of if you already have grub installed on the internal HD.  For example: if you have windows installed on the internal HD and push boot from HD (flash drive), windows will boot.  Yes, I know, Apple did a ****** job emulating a BIOS.[/COLOR]


I don't quite understand this.  Does this mean that this will fail on a dual-boot (bootcamp) Macbook?  I tried this method:

[http://mac.linux.be/phpBB3/viewtopic.php?f=2&t=88](http://mac.linux.be/phpBB3/viewtopic.php?f=2&t=88)

similar in purpose to yours, and in the final USB rEFIt menu I get my OS X, my Windows 7, and an old windows logo that says "Legacy OS on HD" with the tiny orange USB icon in the bottom corner.  

When clicked it boots to Windows 7.

-Rob

---

### Post by HowDidIGetHere? on 2012-03-10
I must be really stupid because I just can’t get Ubuntu to boot from an external USB HD or flash drive with either my old MacBook or my MacBook Pro. I have been trying to find out how to do this for weeks now but absolutely none of the guidance that I have found works. Often the instructions either do not match what I see therefore I cannot follow them or, if manage to follow them they just don’t work. I have successfully managed to get Ubuntu running on a partition of my MacBook but I can’t get it to work from an external HD.

Is there a way to achieve this that has simple instructions for a thicko like me to follow? I do not understand why the developers have not made this a straightforward task. It is very frustrating and I am sure that it puts many Mac users off trying Ubuntu. If I weren’t so determined I would have given up ages ago.

---

### Post by reachcontrol on 2012-03-11
If you're stupid than I am as well.  I tried everything I could find, every variant of code, hard drive manipulation, rEFIt, Bootcamp, etc.

The only thing I haven't tried is the information in this thread, or the information in the link from my post above (a variant of this thread) WITHOUT my computer being configured with BootCamp for dual boot.  That may be the issue as I can get to the last step here before my computer will only boot to Windows.  

But, my hard drive crashed two days ago (too much screwing around?) and I'm now running off an Oneiric liveCD till my new drive comes in the mail.

Before I put Windows back on in Bootcamp, I'm going to try this thread again and see if I can get it to work.  

I'll post my results, probably sometime Tuesday evening (PST).

There has to be a way.  If I can find it I'd be willing to confine Windows to a Virtual Machine install.  

-Rob

---

### Post by pierro78 on 2012-03-11
I must confess I am stupid as well. I could boot my usb drive using a plop boot manager CD and I wanted to get rid of the plop CD so I tried this method but unfortunately I couldn't get it to work for me ... I ended using a simple [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation) with the /home partition on my (fast ssd) usb drive.

---

### Post by reachcontrol on 2012-03-11
>  I ended using a simple [https://help.ubuntu.com/community/Ma...elInstallation]("https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation") with the /home partition on my (fast ssd) usb drive. 	

Can you explain this a bit further?  There are a lot of variants in there.

-Rob

---

### Post by pierro78 on 2012-03-11
I took the "single boot variant" except that I installed windows and then ubuntu (linux mint lxde) on my internal hard drive (I used gparted first to create 3 partitions : one ext4, one swap & one ntfs partition) (I first cloned my mac osx partition to another usb hard drive ... mac osx is booting like a charm from this usb drive ;D)

---

### Post by HowDidIGetHere? on 2012-03-11
OK so I’m not the only ’stupid’ person here but am I really stupid? Surely people should not be having to go through such convoluted routes to achieve what should be a relatively simple task. Come on Ubuntu developers! Sort this out!

---

### Post by pierro78 on 2012-03-18
actually now that grub has been installed on the internal drive I can boot from my usb drive ... I realized that once there was an "sdb" entry in my boot menu after I've updated the kernel in my internal drive OS (I think there was an "update-grub" while my "sdb" usb drive was connected or sthg like that ...)

---

### Post by HowDidIGetHere? on 2012-03-19
> **pierro78 said:**
> actually now that grub has been installed on the internal drive I can boot from my usb drive ... I realized that once there was an "sdb" entry in my boot menu after I've updated the kernel in my internal drive OS (I think there was an "update-grub" while my "sdb" usb drive was connected or sthg like that ...)
I have almost no idea what you are talking about. ;)

I still can't get Ubuntu to boot from an external HD or flash drive. My point is that this should not be difficult. The installer should do everything for me without me having to scour the Internet for a solution. It puts people off trying Ubuntu.

---

