---
title: "SOLUTION TO /bin/sh: can't access tty; job control turned off"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by dannyboy79 on 2007-04-24
UPDATED FIX!!! I removed the old suggestion that I had written and pasted the new fix from the main thread of this problem...... Credit to this goes to 
hbjason as these are his exact words. It appears as though it's a combination of some of my suggestions that I found on the internet etc etc.


f you are getting this error (and you have a SATA harddrive); this is the fix:

At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

You will now boot into the LiveCD normally.

If you choose to install from the LiveCD, you must make the following modifications (or else your installed system will not be able to boot, just like the LiveCD):
o Make note of the device id of the partitions that were used to install (such as /dev/hda1)
-- if you choose to install the '/boot' mount from a different partition make note of it as well (this would be done from the manual partition selection); just a side note -- if you do this, make sure the boot partition is at least 50MB or the install will error at grub setup
o When the install is complete do not reboot -- stay in the LiveCD
o Open a terminal (Applications->Accessories->Terminal)
o You must now mount the installed partitions by typing the following (assuming the install was to /dev/hda1; otherwise replace '/dev/hda1' with the install partition) commands:

mkdir target
sudo mount /dev/hda1 target

*if you also created a boot partition issue (replace /dev/hda2 with the boot partition) the command: 
sudo mount /dev/hda2 target/boot

sudo chroot target

o You will now be in a 'chroot' command prompt for your new ubuntu system (be careful here, you are editing with root access!)
o You must edit the /etc/initramfs-tools/modules file; adding a line with the word: piix
-- you should do this with your favorite unix editor; or simply type the command:
echo piix >> /etc/initramfs-tools/modules
o After modifying the file you must update the system with the command
update-initramfs -u
o When complete, type 'exit' to exit the chroot env; you can now close the Terminal and reset your system.

Now when you boot you will be in your new shinny Ubuntu system!

---

### Post by Ipsissimus on 2007-04-27
My upgrade from Edgy to Feisty encountered several problems, but this one the most gruesome.  

1. The update-manager upgrade stalled at the very end. I could not figure out why, and on reboot Feisty did not start.
2.  The Feisty i386 install CD would not boot because I have an ATI card. So I had to manually mount and install xorg-driver-fglrx drivers.
3.  Tried installing Feisty from the 'Alternate CD'. But that failed on some kind of hard drive driver issue.

My system was installed, but I had this same TTY error everyone had. And the above fix did NOT fix my system. This did:

Having searched/read countless feisty bugs I found this: [[COLOR="Blue"]boot on md raid drives fails[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/79204")

I booted from the 'Alternate CD' using the 'Recover Damaged System' option, mounted my hard drive (/dev/sda7) downloaded the initramfs-tools package: [[COLOR="Blue"]http://people.ubuntu.com/~scott/packages/initramfs-tools_0.85eubuntu10_all.deb[/COLOR]]("http://people.ubuntu.com/~scott/packages/initramfs-tools_0.85eubuntu10_all.deb")

After installing this I rebooted, and Feisty worked! And it seems the upgrade did in fact install correctly. Seems that my settings/programs from Edgy are still in place.  Still having an issue with WPA and my ipw3945 wireless card though.

If the above doesn't fix your system, perhaps this will.

-- Ipsissimus

---

### Post by hal8000 on 2007-04-27
Well done DannyBoy, after reading your post and Shevins blog and Ben Collins I managed to fix my Feisty install without unplugging any cables.  I booted from the live feisty cd, change rooted into my Feisty root partition and appended piix to /etc/initramfs-tools/modules

(previously I have been booting Feisty with a 2.6.18 kernel so update-initramfs -u failed for me.)
However I simply created a new inintramfs and modified grub

cd /boot
mkinitramfs  initramfs-2.6.20-15-generic

(Above lines created a new initramfs in /boot to match the feisty kernel, and I modified /boot/grub/menu.lst to point to the new initramfs)

To confirm:
 uname -a
Linux orac 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

lsmod | grep piix
ata_piix               15492  0 
libata                125720  2 ata_piix,ata_generic
piix                   10756  0 [permanent]


The piix module is now used.
I have a PATA (UDMA 100 HD on IDE0 as master and LS120 drive on IDE0 as slave. A cdwriter and dvdwriter on IDE1. Motherboard is Asus P4P800E , there is an onboard Promise SATA controller but mine is disabled in BIOS as I dont use SATA drives.

[COLOR="Blue"]
_More Verbose instructions:_[/COLOR]
First install Feisty and make a note of your partitions, my Feisty / is /dev/hda11 and Feisty /home is /dev/hda12

Boot with the live Feisty 7.04 CD.
When at the desktop create a mountpoint for the Feisty / partition, I have called mine feistyroot

[COLOR="Blue"]mkdir feistyroot[/COLOR]

Now as root mount the Feisty / partition:

[COLOR="Blue"]sudo mount /dev/sda11 feistyroot[/COLOR]
(watch out as Feisty will now rename hda partitions as sda)


Now change root into the Feisty system
[COLOR="Blue"]chroot feistyroot[/COLOR]

Now modify /etc/initramfs-tools/modules

[COLOR="Blue"]sudo echo piix >> /etc/initramfs-tools/modules[/COLOR]

Create a new initramfs in /boot
(Make sure initramfs name refelects the Feisty kernel name)

[COLOR="Blue"]cd /boot
mkinitramfs -o  initramfs-2.6.20-15-generic[/COLOR]

Final step,  check your /boot/grub/menu.lst file and make sure you are booting
the new initramfs, 

Extract from my grub menu.lst:
title Ubuntu Feisty
    splash =(hd0,10)/boot/splash.tar.gz
    kernel (hd0,10)/boot/vmlinuz-2.6.20-15-generic root=/dev/hda11 vga=791 ro splash
    initrd (hd0,10)/boot/initrd.img-2.6.20-15-generic

Remember grub counts from 0 so hd0,10 is partition 11.
Hopefully this solution works for you also.

---

### Post by dannyboy79 on 2007-04-27
This is great news!!!! Hopefully newbies converting from other's os's will be able to follow and perform your above mentioned fix. So jjust to be clear for other newbies, can you maybe edit your post and be super duper specific as to how you created a new initramfs and possibly update any other instructions you wrote so that you make it totally newbie friendly. For example, does this fix work if you haven't installed feisty at all, can you chroot into the live cd to fix it before it get's put onto your hard drive? I guess I am not totally aware of what happens to people when you try to boot the livecd and they get dropped to this busybox prompt. I know that when I had an issue with my ATI card on my P4P800-E Deluxe, I couldn't for the life of me get Dapper LiveCD to boot, no matter what I would get dropped to busybox, so the solution was to add break=bottom to the boot line, then at the busybox prompt, I chrooted into the live cd (i thought?), changed the xorg.conf from ati to vesa, saved xorg.conf, and hit control d at the busybox prompt and it continued booting the livecd and it worked. (see this post for total story: [http://ubuntuforums.org/showthread.php?t=386688](http://ubuntuforums.org/showthread.php?t=386688)
post #5)

I am glad to hear that it works for that specific hardware as I mentioned above I too own the P4P800-E Deluxe. That is the last box that I haven't converted from Win XP Pro that exists in my house. All other's are running some form of ubuntu. at least when I convert that box I'll know what to do unless of course ubuntu developers fix this issue in the next release. cough cough cough.

thanks for posting your additional solution but if you could do as I asked that would be so awesome!

---

### Post by hal8000 on 2007-04-27
> **dannyboy79 said:**
> 
thanks for posting your additional solution but if you could do as I asked that would be so awesome!


Ok, post edited to reflect changes, code I typed in blue for easier reading, remember that the credit is for the original threads, mine is a modification of ideas, Regards, Hal/:)

---

### Post by dannyboy79 on 2007-04-27
> **hal8000 said:**
> Ok, post edited to reflect changes, code I typed in blue for easier reading, remember that the credit is for the original threads, mine is a modification of ideas, Regards, Hal/:)

alright hal, you might have not read my question but I asked what do people do when they get the busybox prompt (initramfs) straight away, they don't even make it far  enough to even install Feisty??? Can you fix it from the busybox prompt if you don't even have feisty installed yet??? can't you chroot into the livecd or the ramfs. Like I said, I don't know, I am merely trying to help out those people that can't even get to the stage that they installed feisty on their computers because most people have been getting busybox immediately before even getting the livecd to boot fully so that they can then chose hte instal option. thanks for more clarification if you could.

---

### Post by hal8000 on 2007-04-27
> **dannyboy79 said:**
> alright hal, you might have not read my question but I asked what do people do when they get the busybox prompt (initramfs) straight away, they don't even make it far  enough to even install Feisty??? Can you fix it from the busybox prompt if you don't even have feisty installed yet??? can't you chroot into the livecd or the ramfs. Like I said, I don't know, I am merely trying to help out those people that can't even get to the stage that they installed feisty on their computers because most people have been getting busybox immediately before even getting the livecd to boot fully so that they can then chose hte instal option. thanks for more clarification if you could.


No, the solution will not work for everyone. In my case I could load the live cd, install Feisty, but on reboot it would halt with the cant access tty error.
To use chroot you must have a bootable system; either on a live cd or loaded on a partition. If the busybox prompt is displayed from a live cd then there is no way (that I can see) around this problem.....
having said that, it may be possible to install 6.10 Edgy first, then do apt-get distro upgrade to update to Feisty, but I think some people have had problems with this method of install.

---

### Post by ifinishwhatistar on 2007-04-28
Hi Hal

I had roughly the same problem as you.  In my case, I upgraded from edgy to feisty from within the update-manager, but then found I couldn't reboot.  I eventually figured out that I could boot into an older kernel (I'm currently running feisty on the 2.6.17-11 kernel) but just not the 2.6.20-15 one.

I tried what you said (added piix and remade the initramfs for 2.6.20-15), but I still have the same problem:
the computer hangs for about 3-5 minutes and then finally I get the tty error, that my root partition (/dev/mapper/nvidia_bfcfchfc4) doesn't exist.

From the shell that it drops me to, if I ls /dev/mapper, I CAN see nvidia_bfcfchfc, just not the four partitions that the controller should list (1 (windows), 2 (swap), 3 (boot), 4 (root)).

I think I can confirm that I did this properly because when I lsmod | grep piix from feisty (under 2.6.17-11), it says "piix  11780  0 "

Can you remember if there was anything else you did to get it recognize your root partition?

Otherwise I suppose that I somehow have a different problem...

BTW my hardware is as follows:
HDD: 2x120gb Maxtor SATA drives in RAID0 through NVIDIA raid controller through dmraid
MB: Gigabyte GA-8N-SLI rev 1.1 (nforce4 chipset)
CPU: Pentium D 940
RAM: 2gb ddr2
GeForce 7900GT

---

### Post by hbjason on 2007-04-28
> **hal8000 said:**
> 
[COLOR=Blue]
_More Verbose instructions:_[/COLOR]
First install Feisty and make a note of your partitions, my Feisty / is /dev/hda11 and Feisty /home is /dev/hda12

Boot with the live Feisty 7.04 CD.
When at the desktop create a mountpoint for the Feisty / partition, I have called mine feistyroot

[COLOR=Blue]mkdir feistyroot[/COLOR]

Now as root mount the Feisty / partition:

[COLOR=Blue]sudo mount /dev/sda11 feistyroot[/COLOR]
(watch out as Feisty will now rename hda partitions as sda)


Now change root into the Feisty system
[COLOR=Blue]chroot feistyroot[/COLOR]

Now modify /etc/initramfs-tools/modules

[COLOR=Blue]sudo echo piix >> /etc/initramfs-tools/modules[/COLOR]

Create a new initramfs in /boot
(Make sure initramfs name refelects the Feisty kernel name)

[COLOR=Blue]cd /boot
mkinitramfs -o  initramfs-2.6.20-15-generic[/COLOR]

Final step,  check your /boot/grub/menu.lst file and make sure you are booting
the new initramfs, 

Extract from my grub menu.lst:
title Ubuntu Feisty
    splash =(hd0,10)/boot/splash.tar.gz
    kernel (hd0,10)/boot/vmlinuz-2.6.20-15-generic root=/dev/hda11 vga=791 ro splash
    initrd (hd0,10)/boot/initrd.img-2.6.20-15-generic

Remember grub counts from 0 so hd0,10 is partition 11.
Hopefully this solution works for you also.

This is basically the same thing I did to get my install to work... just remember that you need to add the option [COLOR=Blue]break=top[/COLOR] to the LiveCD boot options (using F6) and start booting, when you are kicked out of the boot and into a command prompt type:
[COLOR=Blue]modprobe piix
exit[/COLOR]

You will then be booted into the LiveCD where you can run the install.

After the install open a terminal (Applications->Accessories->Terminal); in the terminal follow hal8000's instructions (above) after install (remember not to select continue using the LiveCD after install).  If you attempt to reboot at this point you will not be able to boot the ubuntu system; if you do reboot, just boot back into the LiveCD and start where you left off (no need to reinstall).

Just to simplify a little, however, after the command (in the chroot env):
[COLOR=Blue]sudo echo piix >> /etc/initramfs-tools/modules[/COLOR]
all I needed to do is issue the command
[COLOR=Blue]sudo update-initramfs -u[/COLOR]
to update the initramfs (thus correcting the system) and then
[COLOR=Blue]exit[/COLOR] 
to leave the chroot env; you can now close the Terminal window and reboot from the LiveCD to your new install.

---

### Post by ifinishwhatistar on 2007-04-28
Right...sorry I think I wasn't clear--my initial upgrade to feisty was successful (i.e. I can boot into Feisty) but only if I use the older kernel.  I think that's the situation hal described as well?

update:

OK so I tried booting from the Feisty live CD to see if I couldn't isolate the problem.  I installed dmraid from the liveCD, and tried listing the partitions.
Here's the problem.  dmraid indeed finds the raid controller, and it shows /dev/mapper/nvidia_bfcfchfc, which is the control node, but doesn't show any of the partitions.  BUT, if I run fdisk -l /dev/mapper/nvidia_bfcfchfc, I CAN see all of my partitions!

How is this possible?

In any case, if I do exactly the same thing from the Edgy live CD, all my partitions show up in /dev/mapper...
Did dmraid break since edgy :)?

---

### Post by hal8000 on 2007-04-28
> **ifinishwhatistar said:**
> Hi Hal
I tried what you said (added piix and remade the initramfs for 2.6.20-15), but I still have the same problem:
the computer hangs for about 3-5 minutes and then finally I get the tty error, that my root partition (/dev/mapper/nvidia_bfcfchfc4) doesn't exist.

From the shell that it drops me to, if I ls /dev/mapper, I CAN see nvidia_bfcfchfc, just not the four partitions that the controller should list (1 (windows), 2 (swap), 3 (boot), 4 (root)).

I think I can confirm that I did this properly because when I lsmod | grep piix from feisty (under 2.6.17-11), it says "piix  11780  0 "

Can you remember if there was anything else you did to get it recognize your root partition?

Otherwise I suppose that I somehow have a different problem...

BTW my hardware is as follows:
HDD: 2x120gb Maxtor SATA drives in RAID0 through NVIDIA raid controller through dmraid
MB: Gigabyte GA-8N-SLI rev 1.1 (nforce4 chipset)
CPU: Pentium D 940
RAM: 2gb ddr2
GeForce 7900GT

OK, you have a different drive configuration from me, I'm running Solaris, FreeBSD and 7 linux installs on a single 160G HD. Because of gparted's inability to work with FreeBSD and Solaris partitions, I had to load feisty in text mode from the alternate CD.

One thing you have proved is that your system boots from an alternate kernel, so this definately looks like a problem with kernel 2.6.20 or maybe just a kernel module missing from the initial ramdisk..
What I would do is boot with your alternate kernel and  print a list of every module that is loaded.

To solve this you will have to  booting from the live cd, chrooting and add other modules to /etc/initramfs-tools/modules and update initramfs. You may need the modules for your raid controller, for example but these could  already  be compiled into the Ubuntu kernel.
You will have to look at the kernel config, I dont have much experience with RAID, so maybe someone else reading your post may have an answer. Hope that helps.

---

### Post by brutal_deluxe on 2007-04-29
> **ifinishwhatistar said:**
> Right...sorry I think I wasn't clear--my initial upgrade to feisty was successful (i.e. I can boot into Feisty) but only if I use the older kernel.  I think that's the situation hal described as well?


Hi ifinishwhatistar
I have basically the same problem (not able to see any partitions when booting from the 2.6.20 kernel) and have been booting the 2.6.17 kernel since upgrading to feisty.  However I think my little bundle of joy is related to a PCI IDE controller which has 2 PATA hard drives plugged into it. (is there any crossover between the modules loaded for a raid array and those loaded for an ide controller card?)

All the solutions I've seen on the forums which revolve around adding entries to */etc/initramfs-tools/modules* seem to be posted by people with SATA driver problems. 

Whatever my problem, it seems to be related to the new kernel.  I've logged a bug report on launchpad but I can't imagine there are too many people with a setup similar to mine so I'm resigned to just waiting for the next kernel revision and hoping for improvement :( .

---

### Post by dannyboy79 on 2007-04-30
> **brutal_deluxe said:**
> Hi ifinishwhatistar
I have basically the same problem (not able to see any partitions when booting from the 2.6.20 kernel) and have been booting the 2.6.17 kernel since upgrading to feisty.  However I think my little bundle of joy is related to a PCI IDE controller which has 2 PATA hard drives plugged into it. (is there any crossover between the modules loaded for a raid array and those loaded for an ide controller card?)

All the solutions I've seen on the forums which revolve around adding entries to */etc/initramfs-tools/modules* seem to be posted by people with SATA driver problems. 

Whatever my problem, it seems to be related to the new kernel.  I've logged a bug report on launchpad but I can't imagine there are too many people with a setup similar to mine so I'm resigned to just waiting for the next kernel revision and hoping for improvement :( .


UPDATED FIX!!!!!!!!

f you are getting this error (and you have a SATA harddrive); this is the fix:

At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

You will now boot into the LiveCD normally.

If you choose to install from the LiveCD, you must make the following modifications (or else your installed system will not be able to boot, just like the LiveCD):
o Make note of the device id of the partitions that were used to install (such as /dev/hda1)
-- if you choose to install the '/boot' mount from a different partition make note of it as well (this would be done from the manual partition selection); just a side note -- if you do this, make sure the boot partition is at least 50MB or the install will error at grub setup
o When the install is complete do not reboot -- stay in the LiveCD
o Open a terminal (Applications->Accessories->Terminal)
o You must now mount the installed partitions by typing the following (assuming the install was to /dev/hda1; otherwise replace '/dev/hda1' with the install partition) commands:

mkdir target
sudo mount /dev/hda1 target

*if you also created a boot partition issue (replace /dev/hda2 with the boot partition) the command: 
sudo mount /dev/hda2 target/boot

sudo chroot target

o You will now be in a 'chroot' command prompt for your new ubuntu system (be careful here, you are editing with root access!)
o You must edit the /etc/initramfs-tools/modules file; adding a line with the word: piix
-- you should do this with your favorite unix editor; or simply type the command:
echo piix >> /etc/initramfs-tools/modules
o After modifying the file you must update the system with the command
update-initramfs -u
o When complete, type 'exit' to exit the chroot env; you can now close the Terminal and reset your system.

Now when you boot you will be in your new shinny Ubuntu system!

---

### Post by markoloka on 2007-04-30
I tried this:
"At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit"

it starts going further but  30 seconds later i'm back in busyprompt again. 
Damn.

---

### Post by ifinishwhatistar on 2007-04-30
In my case, this is irrelevant because I can load into the live CD just fine, but I can't actually see my partitions once in the live CD--dmraid fails to find them.  Yet FDISK finds them just fine, they don't show up anywhere else--they don't show up via dmraid.  Filed a launchpad report here [https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/111030](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/111030)

---

### Post by mach777 on 2007-04-30
> **markoloka said:**
> I tried this:
"At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit"

it starts going further but  30 seconds later i'm back in busyprompt again. 
Damn.

Adding **irqpoll** to boot options (F6 / menu.lst) helped me get my system to boot. Something to do with modules not loading in correct order and messing up irq's I believe.

---

### Post by xyphur on 2007-05-01
Okay, so I'm having the same issues - being dumped to a BusyBox prompt. My hardware config sounds quite different from what the rest of you are dealing with though, which makes me wonder what's causing it. The following system boots, installs and runs Edgy without issue, but cannot boot the Feisty Final LiveCD:

IBM eServer xSeries 232 (8668-27X)
Dual P3 1.13, 1GB ECC PC133
6 x 18.2GB u160 SCSI connected to an integrated Adaptec controller (via a hotswap backplane)
IDE DVD-ROM (the only IDE device in the system)

Like I said, it boots the Edgy LiveCD no problems, installs without fault to a SCSI-connected hard drive, runs flawlessly, and after manually mounting them, sees the remaining 5 hard drives on the SCSI interface as well... so this really came as a surprise when first booting the Feisty CD... something's gotta be broken or otherwise-borked since Edgy.

Anyone have any ideas? I'd try the above-mentioned fix if I wasn't almost positive it has nothing to do with my hardware setup... If it helps, the mainboard in this server is based on a ServerWorks chipset, not that it should matter really, since it apparently had no problems with it in Edgy...

I'm doing a dist-upgrade now after having backed up the entire drive to another empty one... we'll see...

---

### Post by gn2 on 2007-05-01
> **xyphur said:**
> Okay, so I'm having the same issues - being dumped to a BusyBox prompt. My hardware config sounds quite different from what the rest of you are dealing with though, which makes me wonder what's causing it. The following system boots, installs and runs Edgy without issue, but cannot boot the Feisty Final LiveCD:

IBM eServer xSeries 232 (8668-27X)
Dual P3 1.13, 1GB ECC PC133
6 x 18.2GB u160 SCSI connected to an integrated Adaptec controller (via a hotswap backplane)
IDE DVD-ROM (the only IDE device in the system)

.
I had similar problem with very different hardware- Portege 3440CT -and solved it by installing (X)ubuntu 7.04 from the Alternate CD using these instructions:
[https://help.ubuntu.com/community/InstallingXubuntu](https://help.ubuntu.com/community/InstallingXubuntu)

---

### Post by xyphur on 2007-05-01
> **gn2 said:**
> .
I had similar problem with very different hardware- Portege 3440CT -and solved it by installing (X)ubuntu 7.04 from the Alternate CD using these instructions:
[https://help.ubuntu.com/community/InstallingXubuntu](https://help.ubuntu.com/community/InstallingXubuntu)

I shall give that a go, should the dist-upgrade fail as I'm fairly sure it will... I do have a backup of my current Edgy install, after all.

Thanks for the tip.

---

### Post by Muffins on 2007-05-04
> **dannyboy79 said:**
> UPDATED FIX!!!!!!!!

...
o You must now mount the installed partitions by typing the following (assuming the install was to /dev/hda1; otherwise replace '/dev/hda1' with the install partition) commands:

mkdir target
sudo mount /dev/hda1 target



To this action it get fine (and my install is making on entire disk : hda), but the next command -> 'sudo mount /dev/hda target/boot' return me this erros message : ' mount point target/boot not exist'

For information, hda already exist (a hard disk icon with a cross over) in directory /dev.

---

### Post by dannyboy79 on 2007-05-04
QUOTE=Muffins;2590059]To this action it get fine (and my install is making on entire disk : hda), but the next command -> 'sudo mount /dev/hda target/boot' return me this erros message : ' mount point target/boot not exist'

For information, hda already exist (a hard disk icon with a cross over) in directory /dev.[/QUOTE]

what do you mean hda already exists? you mean that you have more than 1 hard disk? 
during the install did you create a boot partition or did you just put your install and your boot contents into 1 partition? if you answer this question I can help. also, so I understand clearly, please post back the results of this command

sudo fdisk -l

and please inform me where you installed ubuntu to and what all the partitions are for. just put it along with the output from the above command. so an example would be this (notice the bold info that I added):

Disk /dev/hdc: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1               1           6       48163+  83  Linux **[boot partition]**
/dev/hdc2           29421       36483    56733516    7  HPFS/NTFS** [windows install]**
/dev/hdc3              7        1281    10241437+  83  Linux** [ / for ubuntu]**
/dev/hdb4           29421       36483    56733547+   f  W95 Ext'd (LBA)
/dev/hdc5           1282        1472     1534207+  82  Linux swap / Solaris
/dev/hdc6           1473        2434     7727265   83  Linux** [home partition]**

---

### Post by Cannaregio on 2007-05-07
Happened to me too once.
The followjng solution worked for me, so I'll bump it here as well. It could work for you too.

This error "BusyBox /bin/sh can't access tty" and so on is imho mostly due to the fact that you have a XP partition and dual boot _**and you just pulled off a USB stick without due ejecting either in your XP partition or in Ubuntu itself.**_

Solution is to live boot from a feisty live cd, and then terminal, and then (not really necessary) check with system --> administration --> gnome partition editor, if you want to check it's a sda1 and see what happens, but the important life-saving command is:

```
sudo e2fsck -y /dev/sda1
```

the corrupted drive will be checked and healed.

It worked for me, your mileage may vary.

---

### Post by hobs0n on 2007-06-10
I also have the same error, I seem to have very different hardware, a MSI K9AGM2-FIH, AMD 690G+SB600 MB and I have a 80Gb HDD that is completely empty and I deleted the old Longhorn partition so I have no partition with any windows install left.

My thread about this is: [http://ubuntuforums.org/showthread.php?t=469735](http://ubuntuforums.org/showthread.php?t=469735)

please help ;)

---

### Post by xyphur on 2007-06-10
I can't remember exactly what fixed this for me, or where I happened upon the solution, but I believe hitting F6 and adding 'acpi=off noapic' to the end of the boot line, as well as making sure that the HDD is the only device on the primary IDE bus, and the optical drive is the only one on the secondary IDE bus... if that doesn't work, try it again but with the optical drive as slave on the primary... I know I found a way to get the LiveCD to boot without throwing this error, but like I said, I can't really remember exactly how... Also, it was doing it on both Ubuntu 7.04 and Xubuntu 7.04 on the same two machines. One was a dual P3 IBM eServer xSeries with 6 SCSI drives, and the other an old P3 733 machine built around an Asus CUSI-FX mainboard with nothing but an IDE CDROM and HDD.

Lemme know if that works though, so I can append it to a 'workaround' file I have saved. :)

---

### Post by hobs0n on 2007-06-11
Yay it worked! Im in the Xubuntu installation now :) Spanks for helping

---

### Post by WebDrake on 2007-06-15
I'm having this problem with a new Lenovo ThinkPad R61, with only Windows Vista installed.  I'm trying to install Kubuntu 7.04.

None of the solutions proposed above permit the LiveCD to boot.  The basic solution presented by dannyboy79 (F6 at startup, adding break=top and entering modprobe piix in the command shell) results in the error,

[75.664000] hda: error code 0x70 sense_key: 0x03 asc: 0x02 ascq: 0x00
[75.664000] Buffer I/O error on device hda, logical block ..........

with many more following.

Doing the same but adding irqpoll to the options does not alter the situation although I also get a SQUASHFS error.

If in addition to all the above I add acpi=off noapic to the end of the boot options, I get the error messages,

[   0.158788] PnPBIOS: Resource structure does not contain an end tag.
[   0.158881] PnPBIOS: build_devlist: Node number 0x0 is out of sequence following node 0x0.  Aborting.
Loading, please wait...
Spawning shell within the initramfs

... and am dumped back into the BusyBox / initramfs command prompt.

The hardware spec for the R61 can be found here: [http://www5.pc.ibm.com/uk/products.nsf/$wwwPartNumLookup/_NA01EUK?OpenDocument]("http://www5.pc.ibm.com/uk/products.nsf/$wwwPartNumLookup/_NA01EUK?OpenDocument")

I note that the Fedora 7 LiveCD also fails to boot in a similar manner, dumping me into a command prompt, although I haven't tried any solutions.  So it looks like it's more than just an Ubuntu issue.

Earlier Ubuntu versions don't seem to like the R61 at all which I'm guessing is a driver/hardware issue---it's a quite new model.

Any advice?

---

### Post by bluknight on 2007-06-15
I tried another way - copy the old kernel from edgy (2.6.17-11-generic), initrd, /lib/modules/2.6.17-11 as well as /lib/firmware/2.6.17-11 to my installed target locations. Then generate the new initramfs as you've outlined to the old kernel and it booted on the old kernel!

Risky but works for me - now I can upgrade the faulty kernel in fiesty. which repaired my grub and Im in fat city.

:p:p

---

### Post by ben::zen on 2007-06-16
So, I could'nt load the Feisty LiveCD to install, and then, following the instructions to load with --noacpi, it ran fine. I've gotten it installed, and it runs beautifully. So, that's my story about a Feisty install.

---

### Post by hobs0n on 2007-06-16
I had a bit of a problem with getting my new OS HDD being discovered by the servers BIOS, I had to reset the CMOS and after that all my problems disapeared. The Xubuntu install just worked right away with the default settings :up:

---

### Post by weemooseus on 2007-06-18
Didn't work at all, may start trying an xp install. I am running 7.04 on a very old laptop, installed perfectly and works great, was going to try an install on a computer that I am donating to charity.

Carl

> **dannyboy79 said:**
> UPDATED FIX!!! I removed the old suggestion that I had written and pasted the new fix from the main thread of this problem...... Credit to this goes to 
hbjason as these are his exact words. It appears as though it's a combination of some of my suggestions that I found on the internet etc etc.


f you are getting this error (and you have a SATA harddrive); this is the fix:

At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit

You will now boot into the LiveCD normally.

If you choose to install from the LiveCD, you must make the following modifications (or else your installed system will not be able to boot, just like the LiveCD):
o Make note of the device id of the partitions that were used to install (such as /dev/hda1)
-- if you choose to install the '/boot' mount from a different partition make note of it as well (this would be done from the manual partition selection); just a side note -- if you do this, make sure the boot partition is at least 50MB or the install will error at grub setup
o When the install is complete do not reboot -- stay in the LiveCD
o Open a terminal (Applications->Accessories->Terminal)
o You must now mount the installed partitions by typing the following (assuming the install was to /dev/hda1; otherwise replace '/dev/hda1' with the install partition) commands:

mkdir target
sudo mount /dev/hda1 target

*if you also created a boot partition issue (replace /dev/hda2 with the boot partition) the command: 
sudo mount /dev/hda2 target/boot

sudo chroot target

o You will now be in a 'chroot' command prompt for your new ubuntu system (be careful here, you are editing with root access!)
o You must edit the /etc/initramfs-tools/modules file; adding a line with the word: piix
-- you should do this with your favorite unix editor; or simply type the command:
echo piix >> /etc/initramfs-tools/modules
o After modifying the file you must update the system with the command
update-initramfs -u
o When complete, type 'exit' to exit the chroot env; you can now close the Terminal and reset your system.

Now when you boot you will be in your new shinny Ubuntu system!

---

### Post by weemooseus on 2007-06-18
Cute, this one got me a crc error and --System halted

Carl

> **xyphur said:**
> I can't remember exactly what fixed this for me, or where I happened upon the solution, but I believe hitting F6 and adding 'acpi=off noapic' to the end of the boot line, as well as making sure that the HDD is the only device on the primary IDE bus, and the optical drive is the only one on the secondary IDE bus... if that doesn't work, try it again but with the optical drive as slave on the primary... I know I found a way to get the LiveCD to boot without throwing this error, but like I said, I can't really remember exactly how... Also, it was doing it on both Ubuntu 7.04 and Xubuntu 7.04 on the same two machines. One was a dual P3 IBM eServer xSeries with 6 SCSI drives, and the other an old P3 733 machine built around an Asus CUSI-FX mainboard with nothing but an IDE CDROM and HDD.

Lemme know if that works though, so I can append it to a 'workaround' file I have saved. :)

---

### Post by weemooseus on 2007-06-18
Ahhh, re-read post, pulled 2nd cd drive off and it still did not install, but this time I got to the very end of the install before it dropped out to a text screen and gave me more cryptic statements -- I feel like I am in a time warp and its 1984 and I am using my C64 and VI on the university server.

First message reads: "you are missing a dpkg-statoverride on /var/run/hplip. Fix it, otherwise you risk silent breakage on upgrades. If you have no idea what to do, just reinstall hplip and it will fix itself" Sorry, I am even more clueless. There was a whole bunch of other junk including three or more error messages.

132: Can't open /usr/share/hotkey-setup/key-constants
/bin/sh: can't open chgrp
/etc/rc2.d/s20nvidia-kernel: 40: seq: Permission denied
cant start powernowd
update-binfmts: permission denied ...fail! (OMG, I flunked!)
/bin/sh: Can't open grep (ahh, the old can't get a grep on the problem)

Carl, (now known as clueless in NM)

> **xyphur said:**
> I can't remember exactly what fixed this for me, or where I happened upon the solution, but I believe hitting F6 and adding 'acpi=off noapic' to the end of the boot line, as well as making sure that the HDD is the only device on the primary IDE bus, and the optical drive is the only one on the secondary IDE bus... if that doesn't work, try it again but with the optical drive as slave on the primary... I know I found a way to get the LiveCD to boot without throwing this error, but like I said, I can't really remember exactly how... Also, it was doing it on both Ubuntu 7.04 and Xubuntu 7.04 on the same two machines. One was a dual P3 IBM eServer xSeries with 6 SCSI drives, and the other an old P3 733 machine built around an Asus CUSI-FX mainboard with nothing but an IDE CDROM and HDD.

Lemme know if that works though, so I can append it to a 'workaround' file I have saved. :)

---

### Post by smilinmonki666 on 2007-06-28
Ok peeps, I've tried to do this for several hours.

Got it installed, so thank you for everyones help on that part.

I've tried to mount hd0 via the mounting code in Terminal but with no luck.

when I boot, the screen shows

Starting up

then boots to the following:

/bin/sh: cant access tty; job control turned off.
(initramfs)

so, i try the following command as suggested:


/bin/sh: cant access tty; job control turned off.
(initramfs)modprobe piix
(initramfs)exit


This does the trick, Ubuntu starts up fine, and smoothly.

Now, the problem is I don't like messing with things I don't know about, yet I still do... I've tried to edit the syntax for the boot option but it still persist's to boot to the previous shell screen.

Question is, could it be to do with my bios? I've set it to default, tried changing boot options, and various other things. This was a hand down PC, but only a smaller spec than my Dads which I was using, still my more recent PC is a P4, its 2.40GHz, only 256 RAM whic i admit is not great & an ATI Graphics Card. 

That doesn't seem to be the problem in my eyes, but the Bios does concern me, I was thinking of resetting it, but I feel as if I'm moving away from the problem.

I've tried to find a way to change the code but again, not 100% confident. I really like this OS, its fantastic. Just wish it start on its own.

My other problem is that I can not use Desktop Effects, any suggestions there? Probably my card to be fair!?

Also, would like to get the machine to use PHP/ MySQL/ Apache I have the 7.04 server edition installation disk, but that also buggers up.

Any help is greatly appreciated...

Smilinmonki666

---

### Post by tommytabib on 2007-06-30
Hi,

Im having the exact same "cant access tty, job control.......ect" and nothing is working for me, plus im having the exact same problem with gutsy gibbon.

My question is: when i get to the "cant access tty........" error i only have about 3sec to type stuff in the i cannot type anything and the computer effectivly stops - ctrl+alt+del does nothing and i have to press reboot on my tower.

Is this happening to everyone?

**smilinmonki666  ** you said that when the error came up you typed "modprobe piix" then "exit", did you have to type fast???

Thanks

---

### Post by tommytabib on 2007-07-01
Alright heres what comes up after i type in "modprobe piix"

> FATAL: module piix not found

Any ideas?

---

### Post by Funky Drummer on 2007-07-05
Well first of all this is my first post to the Forums...and after so much great help over the past couple of years I thought I would try and offer some extra info based around this thread...

First of all - I installed Ubuntu Studio and on boot I was getting
the "ata....failed to set xfer mode....0x4" (not exactly this, but its in an earlier post in this thread) message coming up...
So anyway I was so grateful for Dannyboy79s solution...

> Just to simplify a little, however, after the command (in the chroot env):
> sudo echo piix >> /etc/initramfs-tools/modules
> all I needed to do is issue the command
> sudo update-initramfs -u
> to update the initramfs (thus correcting the system) and then
> exit
>

(THANKS THANKS THANKS!)
However, this works for the "low latency" kernel but not for the "generic" kernel...
I boot into  "generic" kernel 
then attempt...

> cd /boot
> mkinitramfs -o initramfs-2.6.20-15-generic
when I do sudo update-initramfs -u
it will keep updating the low latency kernel but not the generic one - I have tried -k all etc
No dice.

Anyway I had another problem last night which MIGHT be related...and might of help...
Besides this SATA related problem (I use IDE) I also had a  "sound problem" - 
My system sound went off for no reason, after working fine...

Basically after spending all night ******* around - I thought "I'll just check the BIOS" - in the BIOS onboard sound was set to AUTO, as was SATA...
I DISABLED both..BINGO.
The two sound cards were creating havoc...
I thought that turning off SATA detection auto - would fix original problem...it didn't

(Not much help - granted) But I thought that perhaps having SATA autodetect on in the BIOS maybe part of the original "ata....failed to set xfer mode....0x4"  problem...

A lot of people have had sound card problems of various kinds so I thought I would add this in case anyone was doing a search - like I was all night...

FD (I hope that this post is in appropriate place - excuse me, a neophyte etc)

---

### Post by Jhongy on 2007-07-05
I'm getting the same BusyBox / can't access TTY error message -- but it's intermittent. I have a fully working Feisty install, and the error appears on rebbot -- one in every two or three reboots.

So how do I follow these instructions in my case, with a fully working install? Can I just add piix to the end of the file, then generate a new initramfs? I assume I also need to do modprobe piix???

All partitions seem to be working fine -- /boot is on a separate partition.

Thanks in advance.

J

---

### Post by s_raghu20 on 2007-07-07
Hi,

I tried to follow the instructions here, but my 6710b compaq failed again.


After putting in the initial break=top at boot options and later modprobe piix stuff.. it worked for some more time...

but later on, it failed agin with a text based message. And gave me the command prompt.

Saying..

```

Message from sysload@ubuntu at <date>
ubuntu kernal: [    107.536000] wmi_add device=c221d000

Message from sysload@ubuntu at <date>
ubuntu kernal: [    107.536000] calling WQBA

```

Later on, when I tried to startx the system, if failed with 
```

FATAL Server error: 
no screens found
X10: fatal IO 104 (Connection reset by peer) on X server "":0.0"

```


help...

---

### Post by s_raghu20 on 2007-07-10
Well, Finally I managed to get it done....Install Feisty on 6710b... 

Here is my experience..

[http://mytwu.blogspot.com/2007/07/how-i-installed-ubuntu-feisty-fawn-on.html](http://mytwu.blogspot.com/2007/07/how-i-installed-ubuntu-feisty-fawn-on.html)

thanks to everyone 

regards
raghav..

---

### Post by cvmostert on 2007-07-28
I have a LG E500 and also get the same error for wich this page is supposed to be the sollution. I type in break=top after F6, and it does the same.. brings me to a wierd prompt. not the normal command prompt.. when i load the piix module, it seems to load, but when i exit, it wants to start ubuntu... but returnes to this wierd command prompt.

? is this still the sata hard drive?

---

### Post by dracomordag on 2007-07-28
alright, to get my wireless working, i had to updrage to kernel 2.6.22-8. i still get the initramfs error at boot up, but modprobe piix returns "FATAL: module piix not found". upon typing "exit", ubuntu boots into a command prompt, where i login, get an X-server error, so i "sudo dpkg-reconfigure xserver-xorg", choose the VESA driver, it boots normally.

then i have to stop the xserver, sh NVIDIA-LInux-x86-100.14.09-pkg1.run, go through all the configuration, and then start the xserver again.


any idea how i can not have to do this every goddamn startup? it takes at least 5 minutes to go through all those command prompts.

---

### Post by commonplace on 2007-08-09
I have a question. The modprobe piix fix works for me, but a student helper (I work at a school) did the installation and didn't follow all the instructions. So, the installation went fine, but now every time the system boots up, I have to enter 'modprobe piix' and then 'exit' in order for the system to boot.

How can I retroactively make it so that piix loads each startup without me having to modprobe it each time? I went ahead and tried following the remainder of the instructions (mkdir target, sudo mount /dev/hda1 target, echo piix >> /etc/initramfs-tools/modules, and update-initramfs -u) but when I reboot, I still have to do 'modprobe piix' and 'exit' in order to boot each and every time.

Please help! Unfortunately, they setup 20+ computers the same way, and each and every one of them requires that I type 'modprobe piix' and 'exit' to boot the rest of the way. (The five systems I setup myself all work perfectly.)

---

### Post by cyb3rj on 2007-08-13
100% failed to work for me.  "break=top" would break me out of the startup, but my keyboard would not work.  I tried with a USB and a PS/2 keyboard.

What did work was putting a floppy in the drive.  There was nothing special from it, and I still booted from the CD.

I *think* the problem is partly due to having another IDE device attached.  This is complete speculation.  Whatever the case, I'm running the LiveCD and now have the ability to partition and install to my SATA drive.

My next recourse was going to be to try the 7.10 LiveCD.  I sure hope this is fixed in Gutsy; this is a pretty significant issue.

---

### Post by xyphur on 2007-08-15
A typical 1.44mb 3.5" floppy drive isn't an IDE device. The only 'floppy'-type device that's IDE would be a Zip or LS120 drive.

This is a guess, but I think that having the floppy disk in your drive and being able to successfully boot without the BusyBox error was pure coincidence. Once the system has determined that there's no viable operating system located on the floppy disk, the BIOS moves along to the next boot device in sequence, which would've been your CDROM. By doing this, whatever was on the floppy (or wasn't) was ignored by the Linux bootloader on the CD. (again, I'm guessing here - I'm unaware whether or not an Ubuntu LiveCD will attempt to load anything from a floppy device upon bootup - but I would assume not, it seems highly unlikely unless you actually told it to do so at kernel init)

At any rate, seeing as this reply is a couple days since yours, I hope everything worked out and you have a functioning install now. I certainly hope whatever is causing this is figured out by the time Gutsy goes final. Average end-users looking to get away from Microsoft typically wouldn't be too thrilled to be dumped to a console with an error line staring them in the face. ;)

---

### Post by wing25 on 2007-08-20
i went though this thread and tried everything but failed. as far as i know, when i started using PC i used MS-DOS and all other windows based OS. Therefore, i have no idea on LINUX.  I got my Ubuntu fiesty fawn 7.04 CD via snail mail. tried to install but got this error msg. 
ive been searching for any solution till i came to this thread. tried everything but again failed. i suspected my ati radeon 9250 video card and my dial up modem(i am not using).. i tried to remove both and install ubuntu but again failed. i really need your help. step by step if its ok.. and i am sorry for this. I just want to learn new things, and hope to install my ubuntu after this.

Axion Sapphire(VIA chipset) motherboard
celeron D 2.4Ghz(133Mhz)
512mB DDr
Ati radeon 9250 128mB
1 40gB Barracuda (IDE) ----- primary master
1 6gB quantum fireball(IDE) --- from my amd k6 PC ----- secondary master
SONY internal COMBO cdrom drive --- primary slave
intex firewire card
CNET 56k dial up modem.
WINXP prof. SP2

weak PC...

HELP HELP..

want to try ubuntu on my 6gB hardisk.

---

### Post by pairojte on 2007-08-20
Hi,
In my case, I change my BIOS setting by enable SATA control. ( My M/B is Asus P5VD2-VM. I had disable it, because my hard drive is IDE, not knowing that doing this it will make my computer unable to run live ubuntu). Maybe, some of you make the mistake. I believe this is easier to fix the thing.
bye,
pairojte

---

### Post by xyphur on 2007-08-20
wing25: Ideally, you want non-disc IDE devices on the secondary port, and hard drives alone on the primary. Try removing the 6GB drive altogether (for now) and set the cdrom as secondary master. Leave the 40GB as primary master. This should work.

After you're all set up and istalled, you can plop the 6GB drive onto the primary as a slave, which would leave you with an ideal IDE device setup; Hard drives alone on primary, non-disc devices on secondary.

Good luck!

---

### Post by wing25 on 2007-08-21
xyphur<======= Thanx so much.. have to try it tonight... another sleepless night for me just to learn linux...

---

### Post by wing25 on 2007-08-28
Finally i was able to install UBUNTU on my PC. Im on dual boot, windows2k prof sp4 and ubuntu. I pu[B][B]t
break=top[/B][/B but did not use modprob piix, type exit and there goes my ubuntu.  But i have another issue, can i update my copy without hooking in the internet since my pc is not hooked up? or can i update my ubuntu by downloading fixes and run it to my PC? i am having trouble with my display, my resolution is at 800X### and 640x### only and the desktop is too large for my 15" AOC monitor. how can I add 1024x768 on my resolution?

---

### Post by todak on 2007-08-28
This appears to be some sort of goofy kernel-related issue (Issue? I prefer problem). I have no problem at all with ANY distro so long as I use kernel 2.6.20.xx. If I use a kernel 2.6.21.xx or higher, that is when the problem appears! Using 7.10 herd4 I had to add the command "all_generic_ide" (my quotes) to the boot options in order to get the desktop or alternate cd to boot without the tty error. The command does not work in 7.10 Herd5. For that I had to use "modprobe all_generic_ide". After installing, I added "modprobe all_generic_ide" (minus the quotes) to my kernel options in /boot/grub/menu.lst and computer starts normally on every boot. If i remove that command, back to the busybox mess.  I only run one OS (currently ubuntu 7.10 herd 5) on my computer at a time. I do not dual-boot and I do not even have windows at all. No disks, nothing. Nothing but F/OSS for me. With the Mepis live cd the same tty problem arises. None of the kernel commands works at all to try to get it to boot. So I left it sit there and a few minutes later the desktop magically appeared and everything operated perfectly! With the sidux live cd, nothing at all works. Leaving ubuntu and sidux sit there did not produce a desktop as Mepis did. It just sits there with the busybox prompt madly blinking and there is nothing to be done to get it to boot. So, with kernel 2.6.22.xx on three different distros, I get three different things occurring. That is why I beleive it to be a problem with the kernel and NOT the distros. 
My system consists of an EliteGroup K7SEM board with SiS chipset and 1300mHz AMD Duron processor. 512 MB RAM. / partition on a 40 GB drive, /var partition on another 40 GB drive and /home partition on an 80 GB drive (yes, all my partitions on different drives). CD/DVD burner on second IDE slaved to 80 GB drive. All IDE drives no SATA/PATA. My BIOS does not even offer the option for SATA/PATA. I have tried using one hard drive on primary IDE and CD on second IDE channel to see if multiple drives were causing tty snafu, but result was the same no matter how I arranged the drives master/slave on either IDE channel.

---

### Post by yutango on 2007-08-31
:)Thank you very much! Your fix works very well !

---

### Post by element_G on 2007-09-01
Hello fellow forum posters. I've just recently built a system with the following hardware:

CPU: Intel Core 2 Quad Q6600
Mobo: ASUS P5K SE
RAM: 2x Kingston 1GB 667MHz PC2-530 CL5
Video: eVGA e-GeForce 8600GT 256MB (PCI-E)
HDD: 2x Seagate 500GB 7200RPM 16MB SATA II
DVDRW: LG-HT-DT-ST-DVD-RAM GSA H54N

And I'm getting the
/bin/sh: can't access tty; job control turned off
when I try to boot either the ubuntu or kubuntu live CD's (I have made sure to burn both as slow as my laptops burner can: 10x and checked the MD5's)

The initial fix posted in the first post of this thread does not work for me, I've read the rest of this thread and tried using all the other solutions (such as  noacpi pnpbios=off  choosing install from driver cd etc). I have disabled my floppy through the BIOS as I dont have a floppy drive. I had to disable the floppy because the live CD was reporting a file I/O error at fd0

I've learned that the '/bin/sh: can't access tty; job control turned off' error is genrally related to hardware, so I hope I've given enough info, I would dearly love to have ubuntu on my box.

Edit: I will try installing Edgy and then upgrading, I'll try Dapper if I need to. If any of those are successful then I'll edit this post again.
Edit2: I have tried booting both the Dapper and Edgy live CD's. On Dapper I get a message: "Uncompressing Linux... Ok, booting the kernel." and then it stops (no signs of life from the PC)
On Edgy I get the same "/bin/sh: can't access tty; job control turned off" and after trying the posted solutions I am still stuck. I am now going to give the alternate cd a go.
Edit3: Tried the kubuntu Feisty alternate CD, and it errors out saying that it can't load the correct modules for my CD-ROM meaning the installation failed, I do not have a floppy drive so I can't load drivers that way and I have tried all the options for manually selecting a CD-ROM module and mount point.

**Edit4: I've got the live CD to start by first disabling my non-existent floppy drive through the BIOS and then using the options: "all_generic_ide"  and "irqpoll"   (without the quotes) for the liveCD**

---

### Post by frychiko on 2007-09-01
This problem started to happen to me as soon as I replaced my motherboard.

Ubuntu live CD gives me the tty message. 
DVD drive disappeared in my currently installed Ubuntu 6.10
GParted cannot find any harddrives, bootable drives

I can't even get past step 1 of the stated solution as the keyboard freezes before I can input those two commands at the shell. Someone else had this problem too as I can see.

Yeah and I'm using SATA drives too.

---

### Post by ahrs19 on 2007-09-01
I have somewhat similar problem too. I tried to install ubuntu 7.04 on my new dell xps 1330. I booted it from CD and selected to "start or install ubuntu"  after let say 30 sec. I got this can't access tty; job...
I pressed ctrl-Alt+f1 and got these messages:
" cp: unable to open '/root/var/log' : No such file or directory
mount: mounting /root/dev on dev/.static/dev failed: No such file or directory 
mount: mounting /sys on /root/sys failed : No such..
mount: mounting /proc on /root/proc failed: No...
Target  filesystem doesn't have /sbin/init

 BTW I have already installed vista but I have plenty of unallocated space on my hard. I will try to follow this fix as soon as i get home. Just hope it will work.
Thanks in advance

---

### Post by B0rsuk on 2007-09-01
> **hbjason said:**
> This is basically the same thing I did to get my install to work... just remember that you need to add the option [COLOR=Blue]break=top[/COLOR] to the LiveCD boot options (using F6) and start booting, when you are kicked out of the boot and into a command prompt type:
[COLOR=Blue]modprobe piix
exit[/COLOR]

You will then be booted into the LiveCD where you can run the install.


**It doesn't work for me  !**  I'm trying to install Kubuntu Feisty (7.04)

Perhaps I'm not doing it right ? I pressed F6 added break=top right before -- , and enter. It went to the console much faster than usual. I typed
modprobe piix
(no feedback messages)
exit

It went on loading the system, and then ... back to console. I typed the commands, but it doesn't boot anyway !

My hardware:
Asus P5K SE
Seagate 250GB 16MB cache SATAII
DVD-+RW LG GSA-H54LBB LightScribe

I tried it with HDD plugged and unplugged.

---

### Post by Rumpty on 2007-09-01
I also get the error message about "can't access tty; job control turned off" when trying out the Ubuntu Desktop 7.04 i386 CD. And there are no SATA drives on this computer.

That this whole thread exists at all is ludicrous. I thought the experience installing from this CD was supposed to be simple. Anyone trying Ubuntu for the first time will be absolutely discouraged.

I had no trouble with the Kubuntu Alternate CD for Feisty, either AMD64 or i386 version. Just thought I would try straight Ubuntu and the Gnome desktop. What a disappointment.

---

### Post by Rumpty on 2007-09-02
I tried the Ubuntu Desktop 7.04 i386 CD in my older computer (celeron CPU, 440BX chipset MB) and all went well, no "can't access tty, etc" So, my apologies for criticism in my previous post. However, on the new computer, I had to put a floppy disk in the drive to make the installation work. After that, no problems.

---

### Post by ahrs19 on 2007-09-02
Thank you dannyboy79 your solution worked for me and the installation started, but now I have another problem Xserver-Xorg failed some  description provided after that is this:
Module loader present
Markers: (--)probed, (**)from config file, (==)default setting,....
(==)log file: ' /var/log/Xorg.O.log'....
(==) using config file: '/ect/X11/Xrog.conf'
I have dell xps 1330 with intl. integrated X3100
Thanks for help

---

### Post by B0rsuk on 2007-09-02
[highlight]**Caution ! Attention ! WNIMANIJE ! Uwaga !**[/highlight]

If for some reason the original solution doesn't work for you (it didn't for me) try this:

Use livecd . Instead of pressing enter (boot and install) press F6 . Add this option to other boot options:
```
generic.all_generic_ide=1
```

It sure worked for me ! Livecd worked just fine.
 No other fix helped. I've found it somewhere on this forum, If I remember correctly someone had a problem with his P35 chipset MSI motherboard and fixed it this way. He said the problem is likely caused by pata CD/DVD drive not being recognized correctly by the installer, and it supposedly can't find the kernel image or something.

All people are welcome to try the above workaround.

-------

Once I tried installing, I had a problem with partitioning my sata hdd. It would say 'can't have the end before the start !' (I use manual install because I'm weird). I figured out it's not the position on the drive etc that causes the problem, but .... size. On my 250GB drive I was unable to create partitions 220GB big, but 200GB and smaller worked fine.

I still have a minor problem related to my DSL modem connection. Once in a while it doesn't get up properly after restart.

My hardware:

Asus P5K SE motherboard
C2D E6750 CPU
EVGA 8800GTS 320MB GPU
DVD-+R/RW LG GSA-H54LBB LightScribe (drive)
Seagate Barracuda 250GB 16MB cache SATA II

---

### Post by ilovespammerz on 2007-09-02
Hi guys, this is the first time I've ever used ubuntu. When I install 7.04 using the live cd I got the can't access tty error but then I used dannyboy's solution and it let me install. However, everytime I boot up now, it still give me the can't access tty error. However, all I need to do at the prompt is type exit and it will boot normally. 

So my question is, does anyone know how to modify it so it can automatically boot for me?

---

### Post by frychiko on 2007-09-03
> **B0rsuk said:**
> [highlight]**Caution ! Attention ! WNIMANIJE ! Uwaga !**[/highlight]

If for some reason the original solution doesn't work for you (it didn't for me) try this:

Use livecd . Instead of pressing enter (boot and install) press F6 . Add this option to other boot options:
```
generic.all_generic_ide=1
```


**Unknown command "generic.all_generic_ide=1" ignored..**

I get a message similar to this.. any typos in your command??

---

### Post by EXCiD3 on 2007-09-03
This is what todak said earlier: > For that I had to use "modprobe all_generic_ide". After installing, I added "modprobe all_generic_ide" (minus the quotes) to my kernel options in /boot/grub/menu.lst and computer starts normally on every boot.

Did you try that?

---

### Post by frychiko on 2007-09-04
I pressed F6 at the install menu, inserted the above command at the beginning, then on the next screen I was asked to insert a driver cd and press enter, so nope that didn't work.

Is this with an alternate install CD or the main install CD?

---

### Post by numeritos on 2007-09-08
It seems the option break=top is being ignored:

The boot line is the following:

casper initrd=/casper/initrd.gz break=top

I still get the error of the thread title

---

### Post by numeritos on 2007-09-08
> **B0rsuk said:**
> [highlight]**Caution ! Attention ! WNIMANIJE ! Uwaga !**[/highlight]

If for some reason the original solution doesn't work for you (it didn't for me) try this:

Use livecd . Instead of pressing enter (boot and install) press F6 . Add this option to other boot options:
```
generic.all_generic_ide=1
```

It sure worked for me ! Livecd worked just fine.
 No other fix helped. I've found it somewhere on this forum, If I remember correctly someone had a problem with his P35 chipset MSI motherboard and fixed it this way. He said the problem is likely caused by pata CD/DVD drive not being recognized correctly by the installer, and it supposedly can't find the kernel image or something.

I love you mate!! After fighting so many hours to be able to boot, this solved the problem!! Have you got any idea if this will go away after I install Kubuntu and reboot?

---

### Post by commonplace on 2007-09-08
> **numeritos said:**
> It seems the option break=top is being ignored:

The boot line is the following:

casper initrd=/casper/initrd.gz break=top

I still get the error of the thread title

break=top should be the very first thing in the boot line.

---

### Post by FuturePilot on 2007-09-08
> **frychiko said:**
> **Unknown command "generic.all_generic_ide=1" ignored..**

I get a message similar to this.. any typos in your command??

It should be
```
all_generic_ide
```

---

### Post by runtimedata on 2007-09-08
I had the same problem installing Ubuntu Fiesty on a new notebook.  I determined that all the hardware was running OK by installing XP first, however when using the Live CD it always bombed out with the Busy Box message.  

I tried using the Ubuntu Alternate CD and all worked the first time with no problems. It may be worth a try for you.

---

### Post by tifosiv122 on 2007-09-09
I am a newbie to Ubuntu (and linux) and I was having the same problem as described by the OP. I followed the instructions yet I still cannot boot from the HDD after the install (I did the post install commands as well). I did notice that when it gives me the error and puts me at a command prompt (not sure the verbage) if I type 'exit' it puts me into the desktop and the install is fine.

What can I do to fix this issue?

I'm using an older system (P3 800, 256, 20) {I believe} just to see if I like linux. The HDD is IDE and set to master, it's also a one channel IDE cable. 

Any thoughts?

Thanks in advance,
Erik

---

### Post by aldeby on 2007-09-12
This is just to confirm that as of Ubuntu gutsy gibbon tribe 6 (september build available at [http://cdimage.ubuntu.com/daily/current/]("http://cdimage.ubuntu.com/daily/current/") ) the **piix** issue does not occur any more with SATA HDD. 
cheers

---

### Post by Holly on 2007-09-12
The same problem, followed the instruction as:

"At the LiveCD initial boot screen:
o Select F6 for more options
o Add the following option to the beginning of the options list:
break=top
o Press enter to start booting
Ubuntu will start booting, but kick you out to a command prompt; at the prompt type these two commands:
modprobe piix
exit"

but after enter to reboot, i cannot type in anything.

Dell Desktop Inspiron
Intel Core2 Duo processor E6550
DDR2 SDRAM
Serial ATA II Hard Drive
Microsoft Windows Vista Home Premium Edition
Integrated NIC card
128MB NVIDIA GeForce 8300GS
Internal PCI 802.11g wireless network

---

### Post by swarp on 2007-09-21
hello, everyone.
i've got MSI EX600-019 notebook and tried to install ubuntu 7.04 to it. but got the "can't access tty; job control turned off" problem. i've tried and "break=top" option, and modprobe and all_generic etc.. but nothing helped. :(
please help. 
btw, the same cd worked on my older vaio notebook without any problem.

configuration is here
[http://global.msi.com.tw/index.php?func=proddesc&prod_no=1200&maincat_no=135](http://global.msi.com.tw/index.php?func=proddesc&prod_no=1200&maincat_no=135)

---

### Post by anatole on 2007-10-21
> **Holly said:**
> 

but after enter to reboot, i cannot type in anything.


are you using an usb keyboard? if so, try a classic (was that ps/2? i cant remember, anyway, the one with the purple circle plug) one, seems like at that part of the boot process the system does not have usb support. this was the problem for me, i felt pretty weird when i figured it out :D

btw, i've had this problem for long, with the new gutsy release, all_generic_ide seems to to the job for booting the livecd, we'll see about the install soon, i guess...

---

### Post by mrbo on 2007-10-24
Hello! I didn't read all the posts in here but I had the same problem, try to disable all SATA enabled stuff in the bios, it helps on my laptop (HP 6710b) I installed gutsy without any problems!

---

### Post by eyesojfustice on 2007-10-25
hello,

I just installed a new hard drive and ordered an Ubuntu 7.04 Feisty Fawn CD. I put the CD in the drive, rebooted and entered the Ubuntu Boot menu which gives several options:

Enter Live CD
Install with update
.
.
Other Options (F6)
etc.

I get this error after a couple of symbols later:
 /bin/sh: can't access tty; job control turned off

What do you tell a fresh off the boat newcomer like me... in simple and clear English. I'm trying to install Linux to learn about it after installing it... not do this dance that can potentially lead to ultimate frustration and abandonment. Please help and remember, I really know nothing. I started a day ago.

---

### Post by eyesojfustice on 2007-10-25
> **eyesojfustice said:**
> hello,

I just installed a new hard drive and ordered an Ubuntu 7.04 Feisty Fawn CD. I put the CD in the drive, rebooted and entered the Ubuntu Boot menu which gives several options:

Enter Live CD
Install with update
.
.
Other Options (F6)
etc.

I get this error after a couple of symbols later:
 /bin/sh: can't access tty; job control turned off

What do you tell a fresh off the boat newcomer like me... in simple and clear English. I'm trying to install Linux to learn about it after installing it... not do this dance that can potentially lead to ultimate frustration and abandonment. Please help and remember, I really know nothing. I started a day ago.
[B]
Please note PC specs:

Dell 4600 Series
80GB Hitatchi IDE hard drive [master]: IC35L090AVV207-0
newly installed Western Digital IDE hard drive [slave]:  WDC WD800JB-00JJC0
NVIDIA GeForce4 MX 440 with AGP8X
Intel Pentium 4 CPU 2.40GHz
768 MB of RAM
[/B]

---

### Post by teooleole on 2007-10-26
hello to everyone
I have tried everything that is posted and I mean everything but everytime I boot I must type
modprobe piix
exit

how can I bypass this for the sytem to boot up automatically?
please help!

---

### Post by 1stimer on 2007-10-28
Hello everyone,

I have followed the directions that Dannyboy79 gave however after it kicks me to the command prompt it gives me the following message:

Loading, please wait...
Spawning shell within the initramfs

busybox 1.1.3 (debian 1:1.1.3-5ubuntu7)
built-in shell (ash)

(initramfs) _



At this point I am not able to type the two command prompts: modprobe piix and exit

and if I wait then eventually the screen just turns black
can someone tell me what to do?

---

### Post by LaLLe on 2007-10-29
I've setup an old celly 1000 on an asus tusl2-c motherboard. The fix works wonders for 7.04 but doesn't change a thing when i have installed 7.10.

The paradox is that I only have wifi on the box and i can't connect in 7.04 even though it finds the wifinet it just shows the rotating info bar when trying to log on an then doesn't. Its a pc54g card from msi. But the wifi works perfectly in the 7.10 live enviroment. Actually its more stable and faster than windows. Kudos for that.

Any idea for a linux beginner would be appreciated :)

---

### Post by xyphur on 2007-10-29
Okay, so I'm back to the same old problem... on the same system as before (IBM eServer xSeries 232, dual cpu, 6 SCSI drives, single IDE DVD, etc)...

This time, I'm using a 7.10 FINAL LiveCD in an attempt to do a fresh install on an empty drive. No luck. Same busybox error, and here's the catch - Dannyboy's instruction to use 'modprobe piix' results in that module not being found (guess it's not part of the Gutsy release?) ...at any rate, so far nothing posted as a solution here has worked. Edgy works, which is how I ended up with Feisty on this machine (dist-upgrade thru Update Manager)

I'm not giving up that easily this time. No more dist-upgrade nonsense. This has to be fixed. This is a major MAJOR issue.

---

### Post by Steak100 on 2007-10-30
> **1stimer said:**
> Hello everyone,

I have followed the directions that Dannyboy79 gave however after it kicks me to the command prompt it gives me the following message:

Loading, please wait...
Spawning shell within the initramfs

busybox 1.1.3 (debian 1:1.1.3-5ubuntu7)
built-in shell (ash)

(initramfs) _



At this point I am not able to type the two command prompts: modprobe piix and exit

and if I wait then eventually the screen just turns black
can someone tell me what to do?

I had similar issue and solved it on my dual core PC by changing the SATA controller mode on the BIOS from RAID to IDE.  I hope this helps.

---

### Post by robozoid on 2007-11-05
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/98911](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/98911) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi all,
 I'm sort of desperate at this point. I had a working Edgy system, and upgraded to Feisty via the dist-upgrade option in the software manager. Once I did this, I found that I could no longer boot in via the 2.6.18 and 2.6.20 kernels: the machine would throw me into the busybox prompt. However, 2.6.17 was working fine.

Since I was upgrading rather than using a LiveCD, I wasn't sure how to use the instructions provided by dannyboy. [At the ubuntu bugs site I found another claimed fix]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/98911"): namely to uninstall mdadm (I'm not using RAID: I have a single SATA drive). 

Much to my chagrin, now NONE of my kernels are working: they are all booting me into the busybox prompt, and I have no idea how to rescue my system. I'd appreciate any suggestions. I am afraid of doing a reinstall of Feisty from a CD (I can burn one at work), since I'd probably lose all my data (or not?)

Any help would be greatly appreciated. I'm fairly comfortable with navigating my way around a linux box, but am a complete newbie at dealing with the internals

---

### Post by 1stimer on 2007-11-07
> **Steak100 said:**
> I had similar issue and solved it on my dual core PC by changing the SATA controller mode on the BIOS from RAID to IDE.  I hope this helps.

 I am sorry I really dont know what that means I wanted to ask how do I change the SATA controller mode on the BIOS from the RAID to IDE

---

### Post by wwvadude on 2007-11-10
**This post could be related to an Ubuntu bug filed at**: [http://ubuntuforums.org/showthread.php?t=421588&amp;highlight=busybox+error](http://ubuntuforums.org/showthread.php?t=421588&amp;highlight=busybox+error)  [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				The fix posted by Dannyboy for "cannot access tty: etc." does not work for me. I have an ATA drive and have tried the fix with the 32 bit and 64 bit versions of Ubuntu 7.04 or Kubuntu 7.04 and 7.10 for either version.

When I follow his suggestion on entering:
   modprobe piix
   exit

it takes me back to the same error message.

Any ideas out there:

wwvadude
I posted a solution to this problem which works with Ubuntu and Kubuntu 7.04 or 7.10 - see posting #90

---

### Post by thib on 2007-11-11
Hi,

I would like to buy an MSI ex600. But I want to know how it works with ubuntu gusty. I wanna be sure that it is ubuntu compatible before buying it. 


Pleaze tell me about your experience with this laptop under gusty.

Thanks in advance.

Thibault

---

### Post by Steak100 on 2007-11-12
> **1stimer said:**
> I am sorry I really dont know what that means I wanted to ask how do I change the SATA controller mode on the BIOS from the RAID to IDE

If your hardware and BIOS support this mode, then all you have to do is go to your BIOS and look for the "SATA controller" settings, then change the mode there from RAID to IDE.

---

### Post by mcgerard on 2007-11-20
I was getting this error message when trying to install XUbuntu. However this thread gave me some clues. My CD-ROM drive was installed as slave on secondary IDE, the secondary master was an Iomega Zip drive. I disconnected the Zip drive, made the CD-ROM the master and installation of XUnubtu then completed.

---

### Post by polhen on 2007-11-21
hi everybody !

i am new to linux...but i have installed ubuntu ver.7.04 on my raid controller drive...
but there is a problem i am recieving error message..."can't access tty; job control turned off" on the booting time...
i did follow all the fixes on this pages, but nothing has worked...

any help will be appreciated...

regards
pol

---

### Post by polhen on 2007-11-22
hi everybody...

following my question regarding the error massage on booting ubuntu 7.04 "can't access tty; job control turned off" i have found that it cant be installed on the raid controller drive...
i have changed my drive to ide ...and everything worked...
someone wrote "I had similar issue and solved it on my dual core PC by changing the SATA controller mode on the BIOS from RAID to IDE. I hope this helps."
i strongly believe...that will help solve the problem...

regards
pol

---

### Post by wwvadude on 2007-11-25
I had the same problem and nothing on this site worked. However, the following did work very well.
Boot from your Ubuntu or Kubuntu (7.04 or 7.10 - it works with both). When you see the F-options at the bottom of the screen push F6 and add the following to the "END" of the boot options list:

     generic.all_generic_ide=1

You will have to do this every time you  "boot" from the disk but if you want to install then you can proceed easily from there.

Got it from my son but don't know where he got it.

---

### Post by Burn_Out on 2008-01-18
hi all,
first of all: sorry for my awful english!
anyway i'm here cause i need help with my laptop.
it's a HP dv series 6635el, now with gutsy running but i have got a lot of problems: i often find compiz zombie, no sound device detected after installing new alsa 1.0.15 (before was only muted), sometimes pc takes more then 10 seconds to open home folder (always after session start. after reading your posts i decided to downgrade to feisty but when i try the "break=top" way, after typing "update initramfs -u" and rebooting my screen comes blank, i can see the dvd loading but after a while it stops, i don't know why or when because the screen is always shutdown.

thanks a lot, i hope someone will understand my english :P

---

### Post by Mynd on 2008-02-11
I have installed Ubuntu on a new machine with a sata drive and followed the directions specified here to a T I think.  I am not a guru but I can get around on Ubuntu ok.  

Each time I reboot I still get the error, but it goes right to the prompt where I type in 

modprobe piix
exit 

then I get into ubuntu just fine.  I have edited modules to include the modprobe piix from just piix in hopes that would get me past the request for those options above. 

I was hoping someone might be able to help me fix this so I don't have to type anything in.  

Thanks in advance to any and all help received.  I appreciate your time.

Kind regards, 
Mynd

[http://www.myndpollution.com](http://www.myndpollution.com)

---

### Post by Mynd on 2008-02-12
I have change everything to where it should be and now when the machine boots all I have to do is type exit at the promp and the machine boots fine.

Anything else I can add to that file to make it so I don't have to type exit?

---

### Post by ROBarber on 2008-02-25
Hi guys.
After a long time when  everything was just fine, this evening was a disaster. When the system was on boot stage, my little daughter pres some keys, and to be honest :D, I don't know what the combination, but the result is a disaster. I get this error with job control turned off. The idea is that fdisk shows 

/dev/hda1 with boot attribute 
/dev/hda2 swap
/dev/hda3 Linux where is /home.

the fstab shows only those lines.

unionfs / unionfs rw 0 0
tmpfs tmp tmpfs nosuid,nodev 0 0
/dev/hda2 swap swap defaults 0 0

inittab doesn't exist at all as the /boot/grub/menu.lst.
in the /boot directory i only have some config files for the kernels. in the dev/disk/by-uuid directory I can find some referral to uuid of the partitions. My HD is a Samsung ATA-66 device.

If there any possibility to restore to the previous data that makes the system works?

Thanks a lot.

EDIT: I took a look in the wrong place for the beginning. The problem is that somehow the /sbin directory was erased from the beginning.
It seems that I have to reinstall the OS from the scratch.

---

### Post by pudland on 2008-03-12
FYI,
dannyboy79's post work perfect for my system:
Toshiba Satellite A205-S5809
Intel Pentium DC T2330 @ 1.6 GHz
2.0 GB memory
120 GB HD
Dual Boot windows VISTA (dont ask me why I kept it, I'm ashamed!!!)

BTW, it has Intel® 965 Express Chipset family graphics controller, which i have yet to mess with.
I like my eye-candy!!!

The audio prefs have something to be desired also.  Work in prog.

---

### Post by patrick712 on 2008-04-06
Hello All,

Brand newbie here to post my install solution to the Busybox TTY error. I tried combinations of Hard Drives, RAM stick memtests, different burn speeds, different kernels, different installs (freespire, PClinuxOS, Ubuntu), boot command line adjustments (all of them - modprobe piix, acpi=off irqpoll, quiet splash, etc), live cd install versus harddrive install, BIOS tweaking, floppy drive on/off disk in/out, USB disable, blank disc in CDRW, and on and on and on.......(keywords to help others)

Doesn't help laptop people or others necessarily but if you have an option, try it.

Tried a different optical, a dvdrom as opposed to cdrw, and that did it alone!

I didn't have to RTFM, but i had to read a lot and learn a lot - like wax-on wax-off Linux OS install training. Now i have to learn how to use it,

Cool 

Patrick

---

### Post by jimlad888 on 2008-07-22
Hello,

I am new to Ubuntu, in fact i am a complete newbie when it comes to Linux and Unix. I am having the same problem as discussed in previous posts but i still cannot figure out how to fix the problem.

I installed Ubuntu on a 40 gb hard drive a while ago and it was working fine until recently. There was only one partition for the installation and it took the whole hard drive. When I boot with out the live CD I used to get the message:

    BusyBox v1.1.3(Debian 1:1.1.3-3ubuntu3) Built-in shell(ash)
    Enter 'help' for a list of built-in commands.

    /bin/sh: can't access tty; job control turned off
    (initramfs)

If I press alt+ctrl+F1 I get:

    starting up ...
    Loading, please wait...
    kinit: name_to_dev_t(/dev/disk/by-uuid/c2ba9a55-3e43-4c87-b7fb-4a1ce7a65925) = hda5(3,5)
    kinit: trying to resume from dev/disk/by-uuid/c2ba9a55-3e43-4c87-b7fb-4a1ce7a65925
    kinit: No resume image, doing normal boot...
    mount: Mounting /dev/disk/by-uuid/05965430-300b-41e9-9c5c-d819c4eb2afb on /root failed: Invalid argument
    mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
    mount: Mounting /sys on /root/sys failed: No such file or directory
    mount: Mounting /proc on /root/proc failed: No such file or directory
    Target filesystem doesn't have /sbin/init

If I load with the live CD it works but I can not access the hard drive with the previous installation. I get a message saying that cannot mount drive. 

Is there anyway I can get the original partition working again without installing it again because I have university work on there that I want to keep. If possible could you give me a step by step way with enough detail so that even a complete newbie like me could understand.

If you could do that it would be much appreciated.

Thank you

---

