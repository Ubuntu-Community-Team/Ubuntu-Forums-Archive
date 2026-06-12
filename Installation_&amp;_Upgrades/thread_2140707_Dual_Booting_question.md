---
title: "Dual Booting question"
date: 2013-04-30
forum: Installation &amp; Upgrades
---

### Post by Newb13 on 2013-04-30
So I recently decided to try Ubuntu. Naturally, I didn't just go rushing into it without testing it as a "secondary OS" for a month first, as I always do, by dual booting it with my Windows 7 Ultimate X64 (Had it installed before Ubuntu). Problem is, after I finished installing it on a separate hard disk, I rebooted my computer, hoping it would ask me which OS I want to boot into, which unfortunately did not happen, and instead continued to boot into my Windows 7. I'm not really sure what to do/what caused it, could anyone please help me? =P

Thanks in advance.

P.S: Don't know if it matters much but I didn't make any 'swap' drive thing, just root.

---

### Post by oldfred on 2013-04-30
Swap is usually a good idea, but if you have over 4GB of RAM you may never use it. If your normal work load is to load every application, have many tabs in Firefox and then edit large videos you may need swap.

Did you change BIOS to boot Ubuntu drive? When you installed did you install grub2's boot loader to the MBR of the Ubuntu drive? You can quickly test if you have a one time boot key (f12 on my system) and see if it boots.

If changing drive does not work, post link to BootInfo report.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Newb13 on 2013-05-04
> **oldfred said:**
> Swap is usually a good idea, but if you have over 4GB of RAM you may never use it. If your normal work load is to load every application, have many tabs in Firefox and then edit large videos you may need swap.

Did you change BIOS to boot Ubuntu drive? When you installed did you install grub2's boot loader to the MBR of the Ubuntu drive? You can quickly test if you have a one time boot key (f12 on my system) and see if it boots.

If changing drive does not work, post link to BootInfo report.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)


Well, the way you say it I don't really need swap. When I boot my computer, hit F12 and then go to boot options and from there to hard drive, there is only 1 option and it boots into Windows 7 :\

---

### Post by darkod on 2013-05-04
Most system in the quick boot menu under HDD would boot only the first hdd specified in the options. Go into bios and take a look in your hdd order. There are two types of settings for boot, one is for device type, and the other should be for hdd order to make a difference between multiple hdds. In this hdd order you need to switch the second hdd to first position.

---

### Post by Newb13 on 2013-05-09
> **darkod said:**
> Most system in the quick boot menu under HDD would boot only the first hdd specified in the options. Go into bios and take a look in your hdd order. There are two types of settings for boot, one is for device type, and the other should be for hdd order to make a difference between multiple hdds. In this hdd order you need to switch the second hdd to first position.

But when I hit F12>Boot from HDD the only options I have are either the one with Windows on it or something else that asks me to put a system disk in...
I can still see from Disk Management that the partition exists (has no name for some reason), but it still won't ask me which system I want to boot into when I start my computer.

---

### Post by pfeiffep on 2013-05-09
@Newb13 - the F12 is a selection for that session only,; what darkod suggests is entering bios on your machine - possibly F2 or F10 and changing to boot order there. If you installed Ubuntu on a drive that's listed there then grub2 OS prober will more than likely enable you to choose Ubuntu or Windows

Please follow the other advice provided by oldfred earlier!

---

### Post by darkod on 2013-05-09
The system disc message might be related to the disk not having a boot flag. Linux doesn't use boot flags but many manufacturers make the boards to expect a boot flag because they are Microsoft oriented.

Boot the ubuntu cd in live mode, open Gparted and select the ubuntu hdd, right click the root partition and select Manage Flags. Set the boot flag on it, in case no partition has a boot flag. In the partitions list you can see the flags on the right. Click the green button in Gparted and then close it.

Reboot and try again F12 and the second hdd option.

But note that changing the bios setting is still recommended, the F12 is a one time deal. If you finally manage the machine to boot the grub2 bootloader you want it to happen everytime by default, without using F12.

---

### Post by ladasky on 2013-06-11
> **oldfred said:**
> Swap is usually a good idea, but if you have over 4GB of RAM you may never use it. If your normal work load is to load every application, have many tabs in Firefox and then edit large videos you may need swap

I thought that the entire current contents of the system RAM were stored into the swap space by the Suspend feature?  So if you use Suspend (admittedly, I don't, although I keep promising to look into its merits), you would want a swap space as large as your RAM.

---

### Post by oldfred on 2013-06-11
System is mostly powershut down but RAM stll has power, so it does not use swap.
Hibernate is a full shutdown and does use swap.
[http://manpages.ubuntu.com/manpages/hardy/man8/pm-action.8.html](http://manpages.ubuntu.com/manpages/hardy/man8/pm-action.8.html)

---

### Post by ladasky on 2013-06-12
Sorry oldfred, you're right, I meant Hibernate.

---

