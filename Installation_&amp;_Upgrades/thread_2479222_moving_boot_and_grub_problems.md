---
title: "moving /boot and grub problems"
date: 2022-09-18
forum: Installation &amp; Upgrades
---

### Post by dgermann on 2022-09-18
Friends--

In order to update to 22.04.1, I needed more space in /boot, so I moved /boot to a usb stick, following [https://askubuntu.com/questions/539504/moving-boot-to-a-usb-key]("https://askubuntu.com/questions/539504/moving-boot-to-a-usb-key")

All went well.

So now I want to move /boot back to the hdd and eliminate the usb stick. Now it boots to /boot on the hdd, but it will not boot without the usb stick inserted.

What I did to reverse things was this:

```
doug@fire:~$ ls -alh /boot.20220823/ # shows empty--this was the original location of /boot simply renamed with the date appended
doug@fire:/boot$ sudo cp -ax . /boot.20220823 # at this stage /boot was still on the usb stick
doug@fire:/boot$ cd
doug@fire:~$ sudo nano /etc/fstab # here I  switched # markers for boot to the UUID for /dev/sdb1 (the hdd)
doug@fire:~$ sudo umount /boot
doug@fire:~$ sudo mv /boot /boot.20220918
doug@fire:~$ sudo mv /boot.20220823/ /boot
doug@fire:~$ sudo update-grub
remove usb stick and reboot

```

Now when it boots, it goes to grub-rescue.

So here are where things are now:
```
doug@fire:~$ lsblk # showing partial results
sdb                  8:16   0 167.7G  0 disk  # this is the hdd
&#9500;&#9472;sdb1               8:17   0   487M  0 part  /boot
sdd                  8:48   1   7.3G  0 disk  # this is the usb stick
&#9492;&#9472;sdd1               8:49   1   7.3G  0 part

doug@fire:~$ mount |grep boot
/dev/sdb1 on /boot type ext2 (rw,relatime)

```

What I have tried:
```
doug@fire:~$ sudo update-grub
doug@fire:~$ sudo grub-install /dev/sdb1
  Installing for i386-pc platform. # this is a 64-bit system
  grub-install: warning: File system `ext2' doesn't support embedding.
  grub-install: warning: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and their use is discouraged..
  grub-install: error: will not proceed with blocklists.

```

So it seems to boot properly to /dev/sdb1, but grub is looking for something on the usb stick, /dev/sdd or sdd1.

How to get rid of the usb stick, please?

Thank you!

---

### Post by oldfred on 2022-09-18
You should never install grub to a partition like sdb1.
You always install to a drive like sdb.
Rare exceptions, but grub2 does not correctly fit into a partition and has to use blocklists which are unreliable. And you have to have another grub to configfile or chainload as a system cannot boot from a partition. In BIOS mode it only boots from MBR of a drive.

Also now most systems are UEFI, but there you still select a drive, and the installer knows with UEFI to put grub's UEFI boot files into the ESP - efi system partition.

Is /boot a separate partition or part of / (root)?
You may need to update fstab with mount of /boot partition if a separate partition.

You can also use Boot-Repair, but fstab has to be correct first or it will default to a /boot folder in /.

---

### Post by dgermann on 2022-09-19
oldfred--

Thanks for helping me (again!).

After reading through your post a couple of times, it seems I did not give enough info the first time around.

You asked,  > Is /boot a separate partition or part of / (root)?

This machine was originally set up as an ubuntu box in 2015 or so. It has luks/lvm, and looks like this:

```
doug@fire:~$ lsblk
NAME               MAJ:MIN RM   SIZE RO TYPE  MOUNTPOINTS
loop0                7:0    0     4K  1 loop  /snap/bare/5
loop1                7:1    0   114M  1 loop  /snap/core/13425
loop2                7:2    0 114.9M  1 loop  /snap/core/13741
loop3                7:3    0  55.6M  1 loop  /snap/core18/2560
loop4                7:4    0  55.6M  1 loop  /snap/core18/2566
loop5                7:5    0    62M  1 loop  /snap/core20/1611
loop6                7:6    0  63.2M  1 loop  /snap/core20/1623
loop7                7:7    0   177M  1 loop  /snap/firefox/1794
loop8                7:8    0 176.9M  1 loop  /snap/firefox/1810
loop9                7:9    0 140.7M  1 loop  /snap/gnome-3-26-1604/102
loop10               7:10   0 140.7M  1 loop  /snap/gnome-3-26-1604/104
loop11               7:11   0 162.9M  1 loop  /snap/gnome-3-28-1804/145
loop12               7:12   0 164.8M  1 loop  /snap/gnome-3-28-1804/161
loop13               7:13   0   219M  1 loop  /snap/gnome-3-34-1804/72
loop14               7:14   0   219M  1 loop  /snap/gnome-3-34-1804/77
loop15               7:15   0 400.8M  1 loop  /snap/gnome-3-38-2004/112
loop16               7:16   0 346.3M  1 loop  /snap/gnome-3-38-2004/115
loop17               7:17   0   2.5M  1 loop  /snap/gnome-system-monitor/174
loop18               7:18   0   2.5M  1 loop  /snap/gnome-system-monitor/178
loop19               7:19   0  81.3M  1 loop  /snap/gtk-common-themes/1534
loop20               7:20   0  91.7M  1 loop  /snap/gtk-common-themes/1535
loop21               7:21   0  45.9M  1 loop  /snap/snap-store/582
loop22               7:22   0  45.9M  1 loop  /snap/snap-store/592
loop23               7:23   0   284K  1 loop  /snap/snapd-desktop-integration/14
sda                  8:0    0   9.1T  0 disk  
&#9492;&#9472;sda_crypt        253:5    0   9.1T  0 crypt 
  &#9492;&#9472;vgsda-lvsda    253:7    0   9.1T  0 lvm   /backups1
sdb                  8:16   0 167.7G  0 disk  
&#9500;&#9472;sdb1               8:17   0   487M  0 part  /boot
&#9500;&#9472;sdb2               8:18   0     1K  0 part  
&#9492;&#9472;sdb5               8:21   0 167.2G  0 part  
  &#9492;&#9472;sdb5_crypt     253:0    0 167.2G  0 crypt 
    &#9500;&#9472;ubuntu--vg-root
    &#9474;              253:1    0 143.2G  0 lvm   /
    &#9492;&#9472;ubuntu--vg-swap_1
                   253:2    0    24G  0 lvm   
      &#9492;&#9472;cryptswap1 253:3    0    24G  0 crypt [SWAP]
sdc                  8:32   0   9.1T  0 disk  
&#9492;&#9472;sdc_crypt        253:4    0   9.1T  0 crypt 
  &#9492;&#9472;vgsdc-lvsdc    253:6    0   9.1T  0 lvm   /backups2
sdd                  8:48   1   7.3G  0 disk  
&#9492;&#9472;sdd1               8:49   1   7.3G  0 part  
sr0                 11:0    1  1024M  0 rom

doug@fire:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 22.04.1 LTS
Release:	22.04
Codename:	jammy


doug@fire:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
/dev/mapper/ubuntu--vg-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda1 during installation
#####ddg 20220823:

UUID=c06baf8b-1008-485a-8c98-5c406e5ad497 /boot           ext2    defaults        0       2 <<--This is sdb1
#UUID=a26eefb0-361e-41ff-924b-cd15214d83d5 /boot           ext2    defaults        0       2 <<--This is the usb stick
#####

#/dev/mapper/ubuntu--vg-swap_1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
#####ddg20220728:
/dev/mapper/vgsda-lvsda /backups1       ext4    relatime,errors=remount-ro      0       2
/dev/mapper/vgsdc-lvsdc /backups2       ext4    relatime,errors=remount-ro      0       2

#####ddg20220829:
//bach/current    /sam/current       cifs    rw,nobrl,mand,user,credentials=/root/.bachcredentials,uid=doug,gid=data	0	0
//bach/apps	/sam/apps       cifs    rw,nobrl,mand,user,credentials=/root/.bachcredentials,uid=doug,gid=apps	0	0
//bach/personal  /sam/personal	cifs	rw,nobrl,mand,user,credentials=/root/.bachcredentials,uid=doug,gid=doug	0	0


#####ddg20171118:
//192.168.0.204/apps    /sam2/apps       cifs    noauto,rw,nobrl,mand,user,credentials=/root/.earthcredentials,uid=doug,gid=apps	0	0
#//192.168.0.204/client    /sam2/client       cifs    noauto,rw,nobrl,mand,user,credentials=/root/.earthcredentials,uid=doug,gid=data	0	0
//d2/client    /sam2/client       cifs    noauto,rw,nobrl,mand,user,credentials=/root/.earthcredentials,uid=doug,gid=data	0	0

#####ddg20180729:
/dev/sdc1	/media/usb	vfat	defaults,noauto	0	0<<--I will comment out this entry to avoid conflicts.

```

So the original install had /boot on sdb1, with sdb5 having the luks lvm volume. (I have since added sda and sdc for additional space, also encypted.)

As I am reading your post, it seems you are telling me I cannot put /boot back where it was, in sdb1.

If true, then I am seeing three possible alternatives for me:

1. move the boot files back to sdd and let well enough alone;

2. since I don't like that big usb stick protuding, I could do the same thing with a new slimmer usb stick;

3. put /boot under /, but that seems unworkable, since that is part of the encrypted volume.

Am I missing a bigger picture, OldFred?

Thanks for your help!

---

### Post by oldfred on 2022-09-19
You should be able to move it back to a separate /boot partition.
But probably need to totally reinstall grub.
With LVM & encryption you have to be sure to mount /boot, the ESP (if UEFI), and your install. You do need to decrypt the LVM volume so the install can be seen, but do not need any additional data only partitions mounted.

Boot-Repair can walk you thru a minimal chroot. Still have to decrypt LVM volume.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If BIOS, just skip the mount of the ESP.
UEFI chroot, must include ESP - efi system partition
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
 chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)

---

### Post by dgermann on 2022-09-19
oldfred--

Thank you! It is encouraging that I could move it back. But if it is risky, or a lot more work than keeping the boot usb, I lean toward just going back to the usb. What do you advise?

It appears I do not have uefi:
```
doug@fire:~$ ls -alh /sys/firmware/
total 0
drwxr-xr-x  5 root root 0 Sep 19 16:52 .
dr-xr-xr-x 13 root root 0 Sep 19 16:51 ..
drwxr-xr-x  5 root root 0 Sep 19 16:52 acpi
drwxr-xr-x  3 root root 0 Sep 19 16:52 dmi
drwxr-xr-x 22 root root 0 Sep 19 19:23 memmap

doug@fire:~$ sudo efibootmgr
[sudo] password for doug: 
EFI variables are not supported on this system.

```

So it looks like I skip the last two links you gave me.

I am a little nervous about running anything with "repair" in the name! (Because if someone clueless about the repairs--like I am--pushes the recommended repair button, it can be big trouble.) Since you say it is safe, I am willing to try.

Is there any reason not to just install boot-repair to sdb? Or is it better to use a live disk?

Thanks!

---

### Post by oldfred on 2022-09-19
I regularly run Boot-Repair but never used it for a repair. I use its report to document my system.
It really is running standard commands in the background.
I have seen one or two reports where it complained about running from a working system. Not quite sure what that issue was as others have run it without issue.

You  will need /boot in fstab before running Boot-Repair. You may already have an entry, but its UUID would be for the USB drive?
You can probably do it without boot repair, by updating fstab with /boot of internal drive. And doing a full reinstall of grub from withing system.
But if issues then you need live installer to make repairs.

I always suggest users have a flash drive with current version of system to make repairs.
I have multiple as I do minimal (with some extra repair tools) full installs to every flash drive and use flash drives as part of my backup.

---

### Post by dgermann on 2022-09-22
oldfred--

Sorry you had to wait for a response--I had some family matters to attend.

I installed boot-repair to the hard drive and ran it. Here is the pastebin: [https://paste.ubuntu.com/p/6pdSNJqdZH/]("https://paste.ubuntu.com/p/6pdSNJqdZH/")

Two questions:

1. It suggests "The default repair of the Boot-Repair utility would restore the [(generic mbr)] MBR in sda," but sda is encrypted, so I think I cannot boot from there. Originally it was in sdb1, where I would like to restore it. (sdb1 appears to be unencrypted, and the only unencrypted part.) How might that be done with Boot-Repair?

2. It asks for /sdb5 to be mounted with luksOpen, but when I do that, it complains that it is already mounted. Did I do something wrong?

Thanks, oldfred!

---

### Post by oldfred on 2022-09-22
I do not really know LVM.

But you always install grub to a drive like sdb. As that is where BIOS looks to start boot. But MBR is tiny so grub only starts boot and looks for rest of boot files.
Your sdb1 is the /boot partition which then has additional boot info, grub & kernel.

---

### Post by dgermann on 2022-09-22
oldfred--

Many thanks!

Perhaps I am reading it wrongly, but it looks like boot-repair wants to install to sda, and not the sdb that you point to. Is there a way to tell boot-repair to put it in sdb, not sda?

Thanks!

---

### Post by oldfred on 2022-09-22
You can use Boot-Repair's advanced mode.
Choose drive and total re-install of grub. Best to also choose to install newest available kernel.
Be sure that /boot is mounted, it should auto find that, but you may have to mount LVM.

Shows advanced mode screens:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by dgermann on 2022-09-25
oldfred--

"Missing operating system" is what I get now, after following (I think) the instructions.
> Intel Boot Agent GE v 1.3.65
PXE-E53 No boot filename received.


The pastebin from before running boot-repair is [https://paste.ubuntu.com/p/s8kqz3yq3v/]("https://paste.ubuntu.com/p/s8kqz3yq3v/")

The pastebin report from after running boot-repair is [https://paste.ubuntu.com/p/qb7WmBKPTZ/]("https://paste.ubuntu.com/p/qb7WmBKPTZ/")

I chose the advanced option. I left all as is except I changed these two:
```
Restore MBR of sdb (generic mbr)
Partition booted by the MBR: sdb1 [Boot-repair filled this in after I change the first from sda to sdb]

```

When it would not boot, I went to bios (f10 at start) tried each of the boot options. Got the same error each time (or at least it stopped waiting for info on the boot location). Never got to a grub menu.

What next, O wise and experienced one? <grin>

---

### Post by oldfred on 2022-09-25
PXE boot is normally last on the list. That is Internet boot. I always turn that off, just so UEFI/BIOS is not trying it.

Are you sure you have CSM/BIOS/Legacy boot set in UEFI/BIOS to boot sdb drive?

While it looks like Boot-Repair auto found & mounted LVM, but you have to decrypt it manually. I do not know if it asks for that or not?
Then you can see / (root) so it can correctly install grub to MBR, mount /boot partition and fstab is seen.
Does fstab have correct /boot partition?

---

### Post by dgermann on 2022-09-25
oldfred--

That PXE entry appears right after the splash screen on reboot, before it even brings up a grub menu or a request for the luks password. So somehow it seems it is looking for some really basic and early boot sequence. Just rechecked the screen. It says:
> 
Missing Operating System
Initializing and Establishing links
#after running through some things:
Reboot and select proper boot device

The PXE entry is maybe last on the list--it seems to be trying a bunch of things--it first has the client mac address and then the guid. I suspect this is telling us nothing useful.

Decrypting luks for me always comes after the grub menu, so that should not be holding up anything. Now I never even get to the grub menu.

Yes fstab has the correct boot partition, I am 98% sure. fstab is set to a UUID. When I look at the pastebin from after boot-repair, line 16 has the correct uuid for sdb1, the same as what fstab has. Line 222 also looks correct to me. (I was wishing it was a matter that the uuid was wrong in fstab, but appears that is not the problem.)

Is line 66 of the pastebin a problem?

To your question, I went into bios and made sure it was set to boot first to the drive that has hdb on it. (While doing that I saw an entry for UEFI which seems to give me an option to enable that, but I left it disabled, so as not to complicate things.)

Thanks for sticking with me, oldfred!

---

### Post by oldfred on 2022-09-25
Going back to report.
Lines 53 & 54 say its not decrypted. 
So then Boot-Repair could not see the Linux / (root) partition and installed the generic MBR.
The generic MBR is syslinux which is a Windows type boot loader, not grub.

Run Boot-Repair again in BIOS mode, but make sure you have decrypted install, so it installs grub, not generic boot loader.

---

### Post by dgermann on 2022-09-26
oldfred--

It worked! Thank you oldfred!

Here are some of the details, so I can retrace my steps if I ever have to, and so others might avoid my missteps:

1. Most of this is from memory, since I was working on a live usb 22.04.1.

2. boot-repair asks to run :sudo cryptsetup luksOpen /dev/sdb5 myvolume, but I found I also had to do something like:

```
sudo mkdir /mnt/boot
sudo mkdir /mnt/myvolume
sudo mount /dev/sdb1 /mnt/boot
sudo mount /dev/sdb5 /mnt/myvolume
```

before I ran boot-repair.

3. This part was confusing: After choosing the advanced option in boot-repair I tried 3 or 4 times and did not get past the boot-repair screen where it said to say yes to replacing grub. I thought that choosing continue meant it would automagically run those commands. Then I realized I had to copy-paste each command one after the other in order in cli and run them. That made it work for me.

Thank you so much for saving me--again--oldfred!

---

