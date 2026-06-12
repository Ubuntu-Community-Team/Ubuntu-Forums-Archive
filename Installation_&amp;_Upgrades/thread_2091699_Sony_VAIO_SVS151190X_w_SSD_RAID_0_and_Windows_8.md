---
title: "Sony VAIO SVS151190X w/ SSD RAID 0 and Windows 8"
date: 2012-12-05
forum: Installation &amp; Upgrades
---

### Post by CLeCal on 2012-12-05
Hi guys I'm new to the forum because I've been reading threads for the past couple days and have not been able to find an answer for my problem.

I have a Sony VAIO SVS151190x custom ordered with Intel Core i7-3612QM w/ integrate intel HD4000, 128gb ssd (2x 64gb ssd in raid 0(I'm pretty sure it's fakeraid)), 8 gb of RAM, and nvidia 640M LE 2gb. When I got the laptop I found no need for the optical disc drive so I bought a caddy and replaced it with a 120gb Samsung 840 SSD. I upgraded from Windows 7 to Windows 8 on the main SSD (one that came with the system). The laptop has an Insyde H2O Bios.

I followed [http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/comment-page-1/#comment-14692](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/comment-page-1/#comment-14692) in combination with [http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/](http://www.linuxbsdos.com/2012/11/05/dual-boot-windows-8-and-ubuntu-12-10-on-uefi-hardware/) to try and install Ubuntu 12.04 LTS 64 bit on the second Samsung SSD (in the optical disc area) but could not get Ubuntu to boot even with EasyBCD 2.2.

I don't want to get rid of the raid setup that came from the factory with my system and I don't want to mess up my windows partition because I have very little knowledge about raid or fakeraid. I'm wondering if anyone could give me some insight into how to dual boot Ubuntu 12.04 on the second drive or install on the main drive without messing up my Windows 8. Also is it possible to use the Winndows 8 Graphical bootloader instead of GRUB2 because I like the visual look of it better but it's not a necessity if it creates too many complications. I use Windows 8 for most of my University work but for my computer science class next semester any form of linux is recommended. I also like building from AOSP for my android phone and right now I'm using a VM and it's terribly slow.

Thank You,
Christian

---

### Post by CLeCal on 2012-12-08
Sorry, I hate bumping but I really need help.

---

### Post by ronparent on 2012-12-09
Almost everything you want to do is very feasible but daunting if you are not an experienced linux user. I presume your 'second drive' is not a raid? In that case your best bet is to install to the non-raid with that drive set as boot. That way you will write the grub bootloader to that drive and leave the Win8 bootloader alone. You will have to develop some familiarity with your 'BIOS' and how to change the boot order in it.

This done successfully will leave you with a system That is unbootable with Windows unless you restore the original 'BIOS. boot order, but you will at least be still be able to boot windows by doing that.

I will only outline the steps you have to go through to make it a dual boot system. In my experience, when you install an Ubuntu system to a non Raid drive, that installed system does not automatically install the linux software you need to access the RAID drive. While booted into your new Ubuntu install on the non RAID drive you need to install dmraid to it and do an update-grub to find Win8 on the RAID drive. You will then be able to reboot into a dual boot system and have access to both Ubuntu and Win8. If you must have something like the more colorful Win8 boot menu your easiest route will be to customize the grub boot menu. 

Although what I have told you is completely inadequate it is the best I can do right now since I must leave the house for my usual Sunday morning engagement. Will look in on you later to see what is happening but a few others can jump in to answer some of your questions, Good luck.

---

### Post by darkod on 2012-12-09
To install onto fakeraid, you will need to use the Alternate Install CD, not the standard live cd.
To install on the SSD you added, you can use any cd since it's not part of the fakeraid.

But you have to be careful about one more thing. Most new machines come with UEFI boot, not the older legacy bios boot. In order to create uefi dual boot, you have to boot the ubuntu cd in uefi mode, not legacy mode.
More details about uefi dual boot:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Make sure you boot the cd in uefi mode otherwise the dual boot won't work.

---

### Post by CLeCal on 2012-12-09
I don't think I can set the second ssd to boot because the BIOS still sees it as the optical disc drive. I tried it on my first install and it didn't work. I just tried again this morning and it still booted into the windows 8 bootloader. Is there no way to have the Windows 8 bootloader handle the dualboot?

---

### Post by ronparent on 2012-12-09
I think that what you are seeing is that your system is booting on the only bootloader written to either disk, namely the Win8 bootloader written to the RAID set. That once you set the system to look first to the ssd that it will probable boot once a bootloader is written to it. That will happen if you install Ubuntu to the single ssd along with the grub bootloader.

If you are obsessed with using the win8 bootloader to boot Ubuntu while retaining the win8 look, that, this could well turn into a long involved thread.

---

### Post by darkod on 2012-12-10
> **CLeCal said:**
> I don't think I can set the second ssd to boot because the BIOS still sees it as the optical disc drive. I tried it on my first install and it didn't work. I just tried again this morning and it still booted into the windows 8 bootloader. Is there no way to have the Windows 8 bootloader handle the dualboot?

The thing is that with UEFI I don't think windows bootloader is involved at all. Not as a first boot screen. What you are seeing is probably the UEFI boot menu, not win8 bootloader. I'm not 100% sure since I don't use uefi, so don't take my word for it.

When you install ubuntu in uefi mode, there will also be choice for it in the uefi boot screen/manager.

Otherwise, windows bootloader doesn't support linux, so the only possible way would be to install grub2 on the ubuntu root partition, which is not recommended, and chainload to it from windows bootloader. But this is how it was done in legacy boot, I have no idea if uefi is the same.

You might have a point about not beeing able to boot from the second disk. I have seen it mentioned in other threads where people installed disks into the optical drive tray, and they also complained bios can't boot from that device.

---

### Post by CLeCal on 2012-12-10
> **ronparent said:**
> I think that what you are seeing is that your system is booting on the only bootloader written to either disk, namely the Win8 bootloader written to the RAID set. That once you set the system to look first to the ssd that it will probable boot once a bootloader is written to it. That will happen if you install Ubuntu to the single ssd along with the grub bootloader.

If you are obsessed with using the win8 bootloader to boot Ubuntu while retaining the win8 look, that, this could well turn into a long involved thread.

At this point I'm over the Windows 8 Bootloader but I can't boot from the second SSD at all even though I installed GRUB to the second SSD. I think on my UEFI board it defaults back to my RAID drives so I just boot Windows 8 without the option of ever entering Ubuntu.

---

### Post by ronparent on 2012-12-10
If your system has an option to set a temporary boot order you might try to select the second ssd from that (my system gets to that  thru <f12> - but there are many variations to that). Also as darkrod mentioned a UEFI boot may introduce some other variables to the process. I presume that UEFI is currently enabled?

In my newest Gigabyte (self built) system I have the option to boot either UEFI, BIOS, or an option of either. I honestly can't guess what boot options your system may have. You might explore whatever documentation you have and pass it by us.

---

### Post by oldfred on 2012-12-11
May just be best to post link to BootInfo so we can see exactly where you are at.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

    
       Sony VAIO E Series Windows 8/Ubuntu 12.10 Dual Boot, EFI help
[http://ubuntuforums.org/showthread.php?t=2087991](http://ubuntuforums.org/showthread.php?t=2087991)
Sony - manually copy grub efi files & rename to make them work post #3
[http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi](http://askubuntu.com/questions/150174/sony-vaio-with-insyde-h2o-efi-bios-will-not-boot-into-grub-efi)

Sony Vaio dual UEFI boot with manual copy of files to efi partition
 [http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/](http://www.hackourlife.com/sony-vaio-with-insyde-h2o-efi-bios-ubuntu-12-04-dual-boot/)

---

