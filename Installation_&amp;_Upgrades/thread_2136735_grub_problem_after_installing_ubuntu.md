---
title: "grub problem after installing ubuntu"
date: 2013-04-18
forum: Installation &amp; Upgrades
---

### Post by lidengdeng on 2013-04-18
Hi,

I got a grub problem while installing ubuntu 12.04.

At first, win xp ran on my pc and it has drivers of C/D/E. Then I free driver C and install ubuntu 12.04 on it by setting up swap area and root /. The installation goes well until almost the last step which prompts error "executing update-grub failed". After restarting the system, it goes to the black screen with:

Error: ELF header smaller than expected
grub rescue>

I followed this instruction [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

After clicking the "Recommended repair" button, I got the message "Please close all your package managers (Software Center, Update Manager, Synaptic, ...). Then try again. But I'm not running any package managers!

Here is the Boot Reapir link:

[http://paste.ubuntu.com/5719103/](http://paste.ubuntu.com/5719103/)

Thanks for the help

Li

---

### Post by oldfred on 2013-04-18
Boot-Repair could not run any updates as sda1 was mounted read-only for some reason. It may need fsck?

You also overwrote c: or your Windows boot partition. Was that your intent? Ubuntu will read the other NTFS partitions but if you keep NTFS you should really have Windows or a Windows repairCD as you may  need to run chkdsk occasionally on the NTFS partitions and you cannot do that from Linux.

Lets run this to see if it clears the read-only issue.
       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sda1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sda1

Manually fix grub install:
      
 [https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")
Grub2 info & full chroot version - also see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 and later with grub2) by talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

      
 #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda1 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda1 if not correct:
sudo fdisk -l
#confirm that linux is sda1
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda

# If no errors on previous commands reboot into working system and run this:
sudo update-grub

---

### Post by lidengdeng on 2013-04-19
Thanks for your reply.

I got some important documents in D and E drivers, but my windows dumped.. That's why I wanna to install ubuntu on C driver and keep D and E.

When installing ubuntu, it takes a long time at the step "Looking for other operating systems". Will it detect my windows OS because of NTFS format of D and E? C has already been formatted.

And if both D and E are formated and used in ubuntu, will I get the same grub issue?

---

### Post by lidengdeng on 2013-04-19
Thanks for your reply.

I got some important documents in D and E drivers, but my windows dumped.. That's why I wanna to install ubuntu on C driver and keep D and E.

When installing ubuntu, it takes a long time at the step "Looking for other operating systems". Will it detect my windows OS because of NTFS format of D and E? C has already been formatted.

And if both D and E are formated and used in ubuntu, will I get the same grub issue?

---

### Post by oldfred on 2013-04-19
The os-prober scans all partitions looking for operating systems. If you only have one, you can turn that off until you install another. If it is running slow, it may be normal as NTFS does not mount as quick as native Linux formats, but a chkdsk may speed it up. 

       In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or turn off executeable bit
sudo chmod a-x /etc/grub.d/30_os-prober
sudo update-grub

---

### Post by lidengdeng on 2013-04-19
But where I can run the command?

gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true

I am using usb stick for installation. Should I change the /etc/default/grub file on the usb before installing ubuntu?

Thanks,

---

### Post by darkod on 2013-04-19
No need to do anything for os-prober during the install, oldfred is talking about once you have the system installed I guess.

But it didn't install correctly, out of what ever reason. There is no /boot/grub/grub.cfg on sda1 and no kernels.

I would try the install again. Select the manual method, select sda1, Change button, then set Use As ext4, mount point /, and tick the format box.
The device for bootloader should be /dev/sda.

Let the install finish and see if it works.

---

### Post by lidengdeng on 2013-04-19
> **darkod said:**
> No need to do anything for os-prober during the install, oldfred is talking about once you have the system installed I guess.

But it didn't install correctly, out of what ever reason. There is no /boot/grub/grub.cfg on sda1 and no kernels.

I would try the install again. Select the manual method, select sda1, Change button, then set Use As ext4, mount point /, and tick the format box.
The device for bootloader should be /dev/sda.

Let the install finish and see if it works.

As you said, I re-install it for a few times by select sda1 as mount point1 with ext4. The device for bootloader automatically choose /dev/sda. 

The installtion always resulted in update-grub failed error, and rebooting goes to the screen with "grub rescure" command.

---

### Post by oldfred on 2013-04-19
Do you have a BIOS with bitlocker or simlar method to lock BIOS and prevent writing into MBR? 

Sometimes BIOS settings make a difference.

---

### Post by lidengdeng on 2013-04-20
Thanks for the pointer. But where can I change the setting by unlocking and allowing writing into MBR?

> **oldfred said:**
> Do you have a BIOS with bitlocker or simlar method to lock BIOS and prevent writing into MBR? 

Sometimes BIOS settings make a difference.

---

### Post by oldfred on 2013-04-20
Not all BIOS have that type of setting. 
Have you gone thru all the BIOS settings for anything that looks like it may lock BIOS or motherboard manual.

Also was drive ever RAID? Or dynamic partitions in Windows. Or gpt partitioned previously? Various settings remain on drive and grub may see them and not want to damage system because it does not know if valid or not.

---

### Post by lidengdeng on 2013-04-26
Thanks all.

I resolved it by deleting all partitions, and the re-installation works perfectly.

An experienced guy told me that there were some I/O errors in the background of my previous installation, and suggested me to either check the hardware or delete the old partitions.

---

