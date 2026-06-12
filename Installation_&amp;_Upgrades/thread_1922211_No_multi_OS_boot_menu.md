---
title: "No multi OS boot menu"
date: 2012-02-08
forum: Installation &amp; Upgrades
---

### Post by fredcarru on 2012-02-08
Hi,
    I have been using Ubuntu 11.10 joint booted with windows XP pro for some months now, on a single 500 GB disk and 2GB RAM.
   I have now upgraded my system to 1 TB HDD and 6 GB RAM. I installed Windows XP pro on the HDD, then installed the 500 GB drive. I recovered all the s/w and user files from the 500 GB drive and got windows working as before.
   Then I installed Ubuntu on the 500GB drive, this involved deleting the Windows, Ubuntu and swap partitions and re assigning 4 GB swap and the remainder as the root partition. At the end of this I got 32 bit ubuntu and no multi boot start menu.

   Can anyone tell me how to get Windows back and install 64 bit Ubuntu?

---

### Post by Mark Phelps on 2012-02-08
If you can boot into Ubuntu OK, then do that, open a terminal, and enter "sudo update-grub".  This will regenerate the default GRUB config file -- and when you reboot, you should then be seeing a GRUB menu that allows you to select among OSs.

---

### Post by fredcarru on 2012-02-08
Well that certainly messed things up. It looked promising and said something like found windows on device ?? so I rebooted and the BIOS does it's thing beeps once then turns the VGA off and sleeps! 
I can only boot from the installation CD

---

### Post by oldfred on 2012-02-08
The sudo update-grub would not cause that problem as all it does is rewrite the grub menu. Some other updates occurred or you somehow changed which drive you booted from.

You may be able to make minor fixes or if not run the boot info script it offers and post link.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by fredcarru on 2012-02-08
All I did was run the sudo update-grub and reboot. I'll try your sugestion tommorrow.

---

### Post by fredcarru on 2012-02-09
It seems I can boot from the CD but not connect to the internet. Ubuntu repeatedly repors "Wireless network disconnected".
  So I've backed up important files from the windows drive to an external disk and will reinstall windows tomorrow.

---

### Post by oldfred on 2012-02-09
The liveCD has almost all wired Ethernet drivers but cannot have all the different wireless drivers. You should connect with a wired connection until your install is fully updated.

---

### Post by fredcarru on 2012-02-10
I have re-installed windows then Ubuntu, Update ubuntu 11.10 to ubuntu 11.10, but it again failed to boot, Bios then 2 beeps an line feed and then VGA off,

I've re-installed windows and run the ubuntu install but chose "do something else" and the disk status screen gave

/dev/sda
   /dev/sda1 NTFS
/dev/sdb
  /dev/sdb2 ext4
  /dev/sdb1 swap


Device for bootloader
/dev/sda

Is that correct?

---

### Post by oldfred on 2012-02-10
With multiple drives it is better to install the grub2 boot loader to the same drive as the system. Then if Ubuntu drive does not work, you can in BIOS change to boot the Windows drives as the Windows boot loader is still in the Windows drive.

Grub2's menu will let you boot Windows also, so you set BIOS to boot sdb or the Ubuntu drive and then can boot either system.

How large is your sdb drive. There used to be a bug in grub that it could not boot from very large / (root) partitions. I usually suggest / be only 10 to 25GB and the rest of the drive be /home or if dual booting also/or have a shared NTFS data partition.

---

### Post by fredcarru on 2012-02-11
sda is 1 TB
sdb is 500GB
are you saying I should change the device for bootloader to sdb?

When I first installed ubuntu windows and ubuntu were both on sda partitioned 350 GB windows 150 GB ubuntu. This automatically then split ubunto into 4 GB swap and the rest for the root filling system and created a muti os boot menu containg
Ubuntu
Ubuntu memory test
Ubuntu memory test console based
Windows XP

This worked fine until I installed the  new drive and repartitioned sdb into 4 GB swap and the rest for Ubuntu so I don't think the problem's with grub.

---

### Post by fredcarru on 2012-02-11
I've downloaded the 64bit version. When I chose "erase existing ubuntu and install new" it charged off copying files rather then allowing me to select partitions etc.

Do I need to "do something else" first to select sdb as the boot loader?

---

### Post by darkod on 2012-02-11
As far as I know, to have the option to select where the bootloader goes you need to use the manual option (Something Else).
The auto methods select by themselves, but in most cases it should be on the same hdd with the auto methods.

---

### Post by Ceratopsia on 2012-02-11
Install all your drives memory and everything you want in and try booting with Your windows Xp disk on you computer. Install Windows with maybe SP1, no updates not anything extra, no extra drivers nothing and not connected to the Internet. reboot your computer with the the Xp Windows disk.  Let the The system Drivers load until you get to recovery mode and press the R Key for recovery, at the prompt in the recovery mode read the directions. Type help and look at your options. Find fixmbr command and fix boot. At the prompt all usable drives to include the windows system drive use the commands fixmbr first and then fixboot.  You need to fix the MBR first, if the boot is also screw then the fixboot will fix it all so.  Don't install a drive after you installed windows.  Install windows and partition your drives the way you want them. Then reboot your windows that is installed on your computer to make sure your system boots up. Restart your computer and boot from the Ubuntu CD and install when it come to the partition of the Ubuntu use the partition on the windows disk or the extra drive that was partitioned and see if it works 
 
Save all of your work or what ever you want to save somewhere else keep that info before you start. 
 
I hope this will help you.  No water was polluted, trees cut down, or other types of aggression were committed against any animal or human in the writing of this help file... 8o)  

If you have read all of this and it has helped you then you have put a smile on my face and is Thank you enough. If this didn't help you then my apologies. 

Ceratopsia

---

### Post by fredcarru on 2012-02-13
I've installed 64bit Ubuntu to sdb with the device for bootloader as sdb.

If I reboot and leave it to load I get Windows. If I change the device to load from to sdb I get Ubuntu.

In neither case do I get a multi os boot menu.:confused:

I can't seem to change the BIOS to load from sdb but this bios has an option to press F11 to boot from other drives without changing the BIOS.

Thanks for the help espcially oldfred
I'm happy with this and will mark it as solved.:)

---

### Post by Ceratopsia on 2012-02-13
:)

---

### Post by oldfred on 2012-02-13
If you can choose to boot sdb from f11, you must have a BIOS setting somewhere. Some BIOS have you choose hard drive and then have a menu under hard drive on which hard drive. Some have which hard drive choice on a totally different page than the device to boot from. 

This will update grub to let you boot Windows from the grub menu.
```

sudo update-grub
```

---

### Post by fredcarru on 2012-02-13
Hi oldfred,
I tried that

fred@fred-desktop:$ sudo update-grub
[sudo] password for fred: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.0.0-12-generic
Found initrd image: /boot/initrd.img-3.0.0-12-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
done

But no multi boot, but at least it didn't damage either boot.

My bios has a BOOT section that lets you choose between drives but the only hard drive shown is called SATAM3 (sda) if I press enter a new menu opens that lets you choose between SATAM3 and SATAM4 but save and exit doesn't then boot to SATAM4 I can't be bothered to sort this one out as the only user who want's to use Ubuntu is me.
Ta all the same

---

