---
title: "No dual boot menu after installing 12.10 next to Win7"
date: 2013-04-10
forum: Installation &amp; Upgrades
---

### Post by bruce73 on 2013-04-10
My system:
HP p7/1120
Win 7/64
Intel Core i3 2130
8GB RAM
Home networked (wired)

So, here's the process I went through: in Windows I shrunk my C:\ to create 25GB unallocated space. Booted up with the install CD (12.10/64bit). It installed without incident (never asked about partitions, etc., just installed).  When I rebooted, no dual boot menu -- it booted directly into Win 7.  Tried again, same thing.

It seems as if the partitions were created OK - first, 17.2GB (/ext4); second, 7.9GB (swap). They are both listed as Primary/Healthy. I suspect the inability to boot into Ubuntu has to do with that 100MB partition at the front of the drive that HP likes to create.  I'm far from an expect, though, and have no idea how to proceed (but I have a feeling this might be a common problem).  Can anyone point me in the right direction?

---

### Post by oldfred on 2013-04-10
Some later Windows 7 systems had UEFI installs. Also some are UltraBooks that use RAID so grub does not install correctly, or if you used Windows in MBR and created more than 4 primary partitions, you may have dynamic partitions which do not work with Linux.

To see what the issue is, post link:
       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by bruce73 on 2013-04-10
Ok, here you go:


[http://paste.ubuntu.com/5696758](http://paste.ubuntu.com/5696758)

---

### Post by oldfred on 2013-04-10
I do not see anything wrong, it looks just like grub2 did not install grub to MBR. Do you have a BIOS setting to lock MBR, a few systems do?

Boot-Repair reported this, but all your drives are MBR not gpt.   
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.
 SecureBoot enabled.

Is this a new system that had Windows 8? As only those systems normally have secure boot. But since you are BIOS, you do need to not boot any Linux or Windows repairCDs or live installer in UEFI mode. That might convert something you do not want.

I do not like Boot-Repair suggestions either. You do not want grub in all MBR, nor a boot flag on a non-bootable partition. Normally Boot-Repair's auto analysis is correct, but from liveCD just manually install grub to MBR.

      
 #Comments are anything after the #, enter commands in terminal session
#Install MBR from liveCD/DVD/USB, Ubuntu install on sda6 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda6 if not correct:
sudo fdisk -l
#confirm that linux is sda6
sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#  The above command should work but they now suggest this command for grub 1.99 with Natty 11.04 or later - uses boot not root.:
sudo grub-install --boot-directory=/mnt/boot /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

While I prefer to have grub in the MBR of the same drive as Ubuntu, you could install to sdb and change BIOS to boot from sdb. Then you still have the Windows boot loader in sda, if you want to directly boot it from BIOS or one time boot key. But you should have no issue booting Windows from grub menu.

With large drives I prefer to have an operating system on every drive. I follow this logic, but use Ubuntu which needs a bit more space.
      
 Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest install from drive to drive.

But if you have Windows repairCD and Ubuntu live flash drive, you do have other ways to boot if a drive fails.

---

### Post by bruce73 on 2013-04-10
No, this machine came with Win 7 pre-installed.  I never moved on to 8. I ran fdisk and got:

sda6 (Linux) 
sda7 (Linux swap) 

So it looks like I'm good to go. Should I run the first two commands and see if that works before running the third?

edit: I'm so impatient (it's a curse), I went ahead and ran those commands. Because the second was also suggested by someone else, I tried that first, but got the error: Device unspecified. So I ran your first one and that worked.  I now have the grub menu: Ubuntu, advanced options, Windows 7, Windows recovery. Thank you!  Shall I stop while I'm ahead?

---

### Post by oldfred on 2013-04-10
The real question. Does it boot.

From inside Ubuntu you can install grub to sdb or any drive:
       sudo grub-install /dev/sdb

That works because it knows where is it mounted, so you do not have to mount it first like from a liveCd.

---

### Post by bruce73 on 2013-04-10
Yes, what I meant was I have the grub menu when I boot and I can boot into Ubuntu or Windows, no problem. Thanks again.  Now, on to the next task of finding drivers for my Brother MFC-J430W. :)
BTW, how do I mark this as SOLVED?

---

### Post by oldfred on 2013-04-10
Currently with the new version of the forum software the plug-in for solved is not installed. This is the work around. Also in my signature. :)

>  Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button. 



---

### Post by Zill on 2013-04-11
> **bruce73 said:**
> Yes, what I meant was I have the grub menu when I boot and I can boot into Ubuntu or Windows, no problem. Thanks again.  Now, on to the next task of finding drivers for my Brother MFC-J430W...
I am pleased you have resolved the grub problem. :-)

Before we get bogged down with manually searching for a printer driver I do suggest you simply connect the MFC-J430W to the computer with a USB cable.  Then see if any driver is offered and, if so, just accept the defaults.  It is possible that a slightly different model number may be offered but this may still work properly so this is always worth trying.

---

