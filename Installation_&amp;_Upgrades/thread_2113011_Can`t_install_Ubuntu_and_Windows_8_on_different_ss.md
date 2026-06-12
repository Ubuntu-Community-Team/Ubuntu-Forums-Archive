---
title: "Can`t install Ubuntu and Windows 8 on different ssd"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by edd13 on 2013-02-06
Hi

I would like to request some help as I just started to get familiar with Ubuntu.
I have a desktop and I have 3 HD installed, 2x ocz ssds and 1 normal HD.
My mobo is asus P8Z77-V LX UEFI and I am running windows 8 installed on 1 ssd.
I am struggling to install Ubunt 12.10 on the other ssd. I can not boot from the hard drive even when I change its boot sequence.
I am able to instal Ubuntu, create 3 partitions ( swao, root and home). I can install Ubuntu through usb and run it normally from the USB but can open it from the ssd.
I want to have both OSs install but in different ssds.
Could anyone help me understand why this is not working?

What Am i doing wrong? I know I am missing a step but can`t get it right.

Thank you

---

### Post by darkod on 2013-02-06
In ubuntu live mode install and run boot-repair. In most cases it will sort it automatically for you.

Alternatively, if you only want to see details, just create the bootinfo summary without running the recommended repair, and post the link here, so we can have a look at the details.

Looks like grub2 did not install correctly on the MBR of the disk. I have seen few threads here, I wonder if it's some sort of a bug.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Mark Phelps on 2013-02-06
In my experience, when you want different OSs installed on different physical devices, the best course of action is to have ONLY the device you want to install to connected to the PC during the installation.

So, if you have only the planned Ubuntu SSD connected, when you install, GRUB will automatically be written to the correct drive -- the only one present.

IF you have additional drives connected, GRUB automatically writes to the "first" drive it sees -- which may not be the same as the drive you used for installing Ubuntu.

---

### Post by darkod on 2013-02-06
> **Mark Phelps said:**
> 
 when you install, GRUB will automatically be written to the correct drive -- the only one present.


In general yes, but this might be a bug of some sort. I have seen more threads of grub2 not being on the MBR at all after installing 12.10, on any disk MBR.

And when disconnecting disks you have to make sure you know how to connect them back, especially since windows will mind if you connect it back as second disk when it was first (and only) when you installed it.

I still support having all hardware connected when installing, but i also support using manual partitioning so you have more control of partition sizes, location, and bootloader location. That way you don't have to chase up anything.

At least linux allows you to select where to put the bootloader, something that windows never allows you.

---

### Post by edd13 on 2013-02-06
> **darkod said:**
> In ubuntu live mode install and run boot-repair. In most cases it will sort it automatically for you.

Alternatively, if you only want to see details, just create the bootinfo summary without running the recommended repair, and post the link here, so we can have a look at the details.

Looks like grub2 did not install correctly on the MBR of the disk. I have seen few threads here, I wonder if it's some sort of a bug.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I have tried this repair tool yesterday and could not go to the second stage after typing the commnands and installing it. i could not open the repair toll or find it anywhere.
I will try again and will follow your recommendations.

Thanks for your time and understanding.

Much appreciated

---

### Post by edd13 on 2013-02-06
> **Mark Phelps said:**
> In my experience, when you want different OSs installed on different physical devices, the best course of action is to have ONLY the device you want to install to connected to the PC during the installation.

So, if you have only the planned Ubuntu SSD connected, when you install, GRUB will automatically be written to the correct drive -- the only one present.

IF you have additional drives connected, GRUB automatically writes to the "first" drive it sees -- which may not be the same as the drive you used for installing Ubuntu.

I will try this alternative as well and will let you know.

Thanks for you cooperation

---

### Post by darkod on 2013-02-06
> **edd13 said:**
> I have tried this repair tool yesterday and could not go to the second stage after typing the commnands and installing it. i could not open the repair toll or find it anywhere.
I will try again and will follow your recommendations.

Thanks for your time and understanding.

Much appreciated

If it really installed, just open the Dashboard (click the ubuntu logo, the first icon in the Unity interface on the left), and start typing boot-repair. It will find it for you.

Note that everything you install in live mode is temporary, so if you reboot you need to install it again (unless you are working from a usb stick with persistancy).

---

### Post by oldfred on 2013-02-06
It would be best to get BootInfo report from Boot-Repair.

We need to know if you have installed in UEFI mode or BIOS mode for both Ubuntu & Windows. Both must be in same mode to easily dual boot. Otherwise you have to go into UEFI/BIOS and turn UEFI on or off and choose to boot other system every time.
But you can just post this to see configuration. If Windows is UEFI then you need Ubuntu in UEFI. Windows only installs in UEFI mode with gpt partitioning. And UEFI installs have a efi partition as the first (or maybe second) partition.

Run this for all three drives, sda, sdb & sdc, post in code tags to preserve formatting.
       sudo parted /dev/sda unit s print

Less detail but it will show all drives:
sudo parted -l

---

### Post by edd13 on 2013-02-08
> **darkod said:**
> In ubuntu live mode install and run boot-repair. In most cases it will sort it automatically for you.

Alternatively, if you only want to see details, just create the bootinfo summary without running the recommended repair, and post the link here, so we can have a look at the details.

Looks like grub2 did not install correctly on the MBR of the disk. I have seen few threads here, I wonder if it's some sort of a bug.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Hi

I have tried different options and i can not still run Ubuntu 12.10 from the ssd.

I did disable Intel rapid Smart technology (RST), Intel Smart Connect Technoly and it did not work.

Also changed the CSM to enabled ( it was AUTO) and boot device control to UEFI and LEGACY OpROM.

Secure Boot is disabled and I changed the OS type to OTHER OS and also tried WINDOWS EUFI MODE and nothing has changed.
The setup mode is EZ MODE.

I also repartition Ubuntu and created 4 partitions: /boot, swap, / and /home. I managed to install the boot-repair and went though the repair and it did not work.

I also disconnected all hard drives to install ubuntu and it did not work.

I am running Windows 8 coz I can not run Ubuntu from my SSD and since I have made all this changes I now get a FATAL ERROR when running from Ubuntu from usb modprobe fatal error.

I don`t know waht to do...Any clues???

Thank you

---

### Post by edd13 on 2013-02-08
> **darkod said:**
> If it really installed, just open the Dashboard (click the ubuntu logo, the first icon in the Unity interface on the left), and start typing boot-repair. It will find it for you.

Note that everything you install in live mode is temporary, so if you reboot you need to install it again (unless you are working from a usb stick with persistancy).

Hi

I have tried different options and i can not still run Ubuntu 12.10 from the ssd.

I did disable Intel rapid Smart technology (RST), Intel Smart Connect Technoly and it did not work.

Also changed the CSM to enabled ( it was AUTO) and boot device control to UEFI and LEGACY OpROM.

Secure Boot is disabled and I changed the OS type to OTHER OS and also tried WINDOWS EUFI MODE and nothing has changed.
The setup mode is EZ MODE.

I also repartition Ubuntu and created 4 partitions: /boot, swap, / and /home. I managed to install the boot-repair and went though the repair and it did not work.

I also disconnected all hard drives to install ubuntu and it did not work.

I am running Windows 8 coz I can not run Ubuntu from my SSD and since I have made all this changes I now get a FATAL ERROR when running from Ubuntu from usb modprobe fatal error.

I don`t know waht to do...Any clues???

Thank you

---

### Post by edd13 on 2013-02-08
> **oldfred said:**
> It would be best to get BootInfo report from Boot-Repair.

We need to know if you have installed in UEFI mode or BIOS mode for both Ubuntu & Windows. Both must be in same mode to easily dual boot. Otherwise you have to go into UEFI/BIOS and turn UEFI on or off and choose to boot other system every time.
But you can just post this to see configuration. If Windows is UEFI then you need Ubuntu in UEFI. Windows only installs in UEFI mode with gpt partitioning. And UEFI installs have a efi partition as the first (or maybe second) partition.

Run this for all three drives, sda, sdb & sdc, post in code tags to preserve formatting.
       sudo parted /dev/sda unit s print

Less detail but it will show all drives:
sudo parted -l

Hi

I have tried different options and i can not still run Ubuntu 12.10 from the ssd.

I did disable Intel rapid Smart technology (RST), Intel Smart Connect Technoly and it did not work.

Also changed the CSM to enabled ( it was AUTO) and boot device control to UEFI and LEGACY OpROM.

Secure Boot is disabled and I changed the OS type to OTHER OS and also tried WINDOWS EUFI MODE and nothing has changed.
The setup mode is EZ MODE.

I also repartition Ubuntu and created 4 partitions: /boot, swap, / and /home. I managed to install the boot-repair and went though the repair and it did not work.

I also disconnected all hard drives to install ubuntu and it did not work.

I am running Windows 8 coz I can not run Ubuntu from my SSD and since I have made all this changes I now get a FATAL ERROR when running from Ubuntu from usb modprobe fatal error.

I don`t know waht to do...Any clues???

Thank you

---

### Post by edd13 on 2013-02-08
> **Mark Phelps said:**
> In my experience, when you want different OSs installed on different physical devices, the best course of action is to have ONLY the device you want to install to connected to the PC during the installation.

So, if you have only the planned Ubuntu SSD connected, when you install, GRUB will automatically be written to the correct drive -- the only one present.

IF you have additional drives connected, GRUB automatically writes to the "first" drive it sees -- which may not be the same as the drive you used for installing Ubuntu.

Hi

I have tried different options and i can not still run Ubuntu 12.10 from the ssd.

I did disable Intel rapid Smart technology (RST), Intel Smart Connect Technoly and it did not work.

Also changed the CSM to enabled ( it was AUTO) and boot device control to UEFI and LEGACY OpROM.

Secure Boot is disabled and I changed the OS type to OTHER OS and also tried WINDOWS EUFI MODE and nothing has changed.
The setup mode is EZ MODE.

I also repartition Ubuntu and created 4 partitions: /boot, swap, / and /home. I managed to install the boot-repair and went though the repair and it did not work.

I also disconnected all hard drives to install ubuntu and it did not work.

I am running Windows 8 coz I can not run Ubuntu from my SSD and since I have made all this changes I now get a FATAL ERROR when running from Ubuntu from usb modprobe fatal error.

I don`t know waht to do...Any clues???

Thank you

---

### Post by darkod on 2013-02-08
If Intel RST was active, it might have the disks configured as sort of a raid. That's how it works. Disabling it is not enough and you have to remove the meta data from the disks so that the ubuntu installer doesn't think the disk is part of raid array.

You can do that with:
sudo dmraid -Er /dev/sdX

Use the correct disk for /dev/sdX. But only do this if you want to break up Intel RST.

Also, you can't simply enable or disable uefi boot. It depends how windows is installed. Otherwise when you put the windows disk back it won't work. This is one of the reasons I don't recommend disconnecting hardware. You need it to work with both disks, not only one. Removing the windows disk might make you believe a certain configuration will work when you put it back and then you find out it doesn't.

Like oldfred mentioned in his post, it would be helpful to get the bootinfo that boot-repair can create. That will show more details.

Please don't post the same reply multiple times, it seems you have posted the same post like 4 times already.

---

### Post by edd13 on 2013-02-08
How do i remove the meta data from the disks?

Still not clear for me what to do with bootinfo. Do I need to open terminal and type all those scripts?

I do apologise to everyone for the multiple posts it wont happen again.

Thx for yr quick reply

---

### Post by edd13 on 2013-02-08
> **darkod said:**
> If it really installed, just open the Dashboard (click the ubuntu logo, the first icon in the Unity interface on the left), and start typing boot-repair. It will find it for you.

Note that everything you install in live mode is temporary, so if you reboot you need to install it again (unless you are working from a usb stick with persistancy).

I am finding really confusing. do I really have to type all those scripts just to install Ubuntu?

I had to reset all the setting to run Windows 8 again. At the moment I can install Ubuntu.

I will download Ubuntu x64 version again from the Ubuntu website and re create a bootable usb and have another go

---

### Post by darkod on 2013-02-08
I am not sure what scripts are you talking about. For boot-repair, you need to install it (in live mode for example, because currently you don't have ubuntu installed), and then simply click the Create bootinfo button and post the link it gives you.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by edd13 on 2013-02-08
> **darkod said:**
> I am not sure what scripts are you talking about. For boot-repair, you need to install it (in live mode for example, because currently you don't have ubuntu installed), and then simply click the Create bootinfo button and post the link it gives you.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Ok. I will have another go with boot repair. I will install it again through the usb. Will let you know

Tnx again

---

### Post by edd13 on 2013-02-08
> **darkod said:**
> I am not sure what scripts are you talking about. For boot-repair, you need to install it (in live mode for example, because currently you don't have ubuntu installed), and then simply click the Create bootinfo button and post the link it gives you.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I ran the version without fully installing Ubuntu but the GRUB Option tab on the boot-repair is greyed out and on the same tab PURGE KERNEL THEN REINSTALL LAST KERNEL is ticked and greyed out as well it does not allow me to change it. So when i go to the next tab MBR OPTINS, everything is greyed out as well.

I noticed this time that when I booted my pc it did asked to to remove the installation medis (USB) and now i can see the GRU ubuntu sort of boot interface but it only sees Windows 8.

Still does not see Ubuntu 12.10. What shall I do now?

I was thinking to load again Ubuntu through the usb and try to change the partitions or maybe this time run the Full Istallation.

Any recommendations?

Tnx

---

### Post by oldfred on 2013-02-09
Without more information we cannot tell if you are seeing a UEFI menu or a grub menu. You may just have a UEFI menu with Windows or a grub menu with grub fully installed and no Ubuntu (which would be unusual).

---

### Post by edd13 on 2013-02-09
> **oldfred said:**
> Without more information we cannot tell if you are seeing a UEFI menu or a grub menu. You may just have a UEFI menu with Windows or a grub menu with grub fully installed and no Ubuntu (which would be unusual).

Hi guys

Things gor worse and now my pc is completely screwed up.

I can not run Windows or Ubuntu 12.10 now

I have got this error message when i turn my PC on: error: no such device: 9891a779-b050-4710-8026-0c11250a9b36. grub rescue.

I am reaserching some foruns and it seems that that grub or the mbr is missing or corrupted

I can not boot from any ssd drive anymore.

I can go to my bios and change all the setting but it doesn`t work. I don`t get any windows 8 logo anymore and I guess Ubuntu took (grub) took over.

My UEFI BIOS is EZ Mode
Intel RST is disabled
Intel SCT is disabled
CSM is enabled and the Boot Device Control is set to UEFI and Legacy OpROM..

Please can anyone help me to try solve this issue?

At the moment I am using another pc to communicate with you and I just inserted the usb back into the problematic pc.

I have options to install Ubuntu and Try Ubuntu and I guess i might be able to change something from there.

Any clue?

Thank you

---

### Post by edd13 on 2013-02-09
> **oldfred said:**
> Without more information we cannot tell if you are seeing a UEFI menu or a grub menu. You may just have a UEFI menu with Windows or a grub menu with grub fully installed and no Ubuntu (which would be unusual).

I chose to Try Ubuntu and I can see my W8 hd, my normal data hd, and the MBR 500mb patition + 32 root partition nad my home partition that I created on ubuntu.

---

### Post by darkod on 2013-02-09
> **edd13 said:**
> I chose to Try Ubuntu and I can see my W8 hd, my normal data hd, and the MBR 500mb patition + 32 root partition nad my home partition that I created on ubuntu.

That's fine, but when you choose Try Ubuntu and load the live session, install boot-repair and run it to create the bootinfo results we need to see more details. I already posted the boot-repair link with instructions earlier.

As you can see, in the main window there are two buttons: Recommended Repair and Create Bootinfo summary. You only need to create the summary and post the link it gives you.

Often, running Recommended Repair can also help, but if you are not sure running it, do the bootinfo first so we cna see the details.

That is what we are talking about all this time, we need more info. Telling us which partitions you have doesn't mean much, it depends in what mode the OSs are installed, whether the boot files are fine or not, etc. The bootinfo summary shows all that.

---

### Post by edd13 on 2013-02-09
> **darkod said:**
> That's fine, but when you choose Try Ubuntu and load the live session, install boot-repair and run it to create the bootinfo results we need to see more details. I already posted the boot-repair link with instructions earlier.

As you can see, in the main window there are two buttons: Recommended Repair and .

Create Bootinfo summary. You only need to create the summary and post the link it gives you.

Often, running Recommended Repair can also help, but if you are not sure running it, do the bootinfo first so we cna see the details.

That is what we are talking about all this time, we need more info. Telling us which partitions you have doesn't mean much, it depends in what mode the OSs are installed, whether the boot files are fine or not, etc. The bootinfo summary shows all that.

I have done what you said. I ran the boot-repair and chose summary. They have given me an url which is: [http://paste.ubuntu.com/1628961](http://paste.ubuntu.com/1628961)

---

### Post by edd13 on 2013-02-09
> **edd13 said:**
> I have done what you said. I ran the boot-repair and chose summary. They have given me an url which is: [http://paste.ubuntu.com/1628961](http://paste.ubuntu.com/1628961)

I ran both repair and summary. I restated my machine, removed mu usb and the bloody error: no such device: 9891a779-b050-4710-8026-0c11250a9b36 still there.

I gives me this black screen GRUB RESCUE >

Can access anything....no windows 8 no ubuntu. Ubuntu only through the usb installation....man I am getting desperate now!!!!

Is Ubuntu that hard to install...I am trying to get a flavour of it but what a fight.

I want give up but I need to get my pc up and runnig

---

### Post by darkod on 2013-02-09
First, stop touching anything any more. :)

Installing ubuntu is not hard, but you messed everything up. Now that we have the details I can see a few things that need fixing.

Soooo... Lets start.
1. Your win8 is in legacy mode, not uefi. So, go into bios and set the boot mode to legacy only, not uefi. Never change it to uefi because you don't have uefi installation.

2. Your real /boot partition is sdb1 but in your fstab you changed it to use sdb7. But sdb7 doesn't show any files, kernels, etc. So, lets try putting sdb1 back.
From live mode open the sdb6 partition and the file /etc/fstab, comment out with # at the start of the line the line with UUID=0fe08d58-c3c9-464e-988e-bafba4a198a8. Then uncomment (remove the # in front) the line for the old UUID=44c4c52d-9856-4e08-8e24-82e5d495e040. Save and close the fstab file.
EDIT PS: I just noticed in your fstab that you also have a line with UUID=....98a8 for /home. That is correct. But the last line in fstab you put the same UUID for /boot, that is the one you need to disable. You can't use the same partition for /home and /boot, I have no idea why you put that /boot line in fstab.

Now, after that is done lets deal with grub2 because it uses embedded files, and you have it on all three disks and I think you are booting from a wrong one. Reboot the machine and go into a live session again, I'll continue with grub2 in the next post.

---

### Post by darkod on 2013-02-09
So, at the end of the last post I said to reboot because that will unmount everything and it's better to work from a new live session. Boot again in a new live session, open terminal and start executing these commands:
```
sudo mount /dev/sdb6 /mnt
sudo mount /dev/sdb1 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sdb
```

Reboot, go into bios and MAKE SURE you have sdb (the second disk) as the first disk to boot from. You have two 120GB SSDs so if you can't figure out which one is the second one, try one then the other.

See if that boots into a grub2 menu and if ubuntu boots from there. DO NOT try to boot windows yet, only check if ubuntu boots.

If ubuntu doesn't boot, come back and tell us, don't try to do anything else.

---

### Post by edd13 on 2013-02-09
> **darkod said:**
> So, at the end of the last post I said to reboot because that will unmount everything and it's better to work from a new live session. Boot again in a new live session, open terminal and start executing these commands:
```
sudo mount /dev/sdb6 /mnt
sudo mount /dev/sdb1 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sdb
```Reboot, go into bios and MAKE SURE you have sdb (the second disk) as the first disk to boot from. You have two 120GB SSDs so if you can't figure out which one is the second one, try one then the other.

See if that boots into a grub2 menu and if ubuntu boots from there. DO NOT try to boot windows yet, only check if ubuntu boots.

If ubuntu doesn't boot, come back and tell us, don't try to do anything else.

Ok will try this methos now and will return to you guys ASAP.

Thank you

---

### Post by edd13 on 2013-02-09
> **edd13 said:**
> Ok will try this methos now and will return to you guys ASAP.

Thank you

Man we are getting somewhere. You are a genius.

I followed your instructions and changed the boot order chosing the right ssd ( i knew the ssd that i wanted to install ubuntu)

For the 1st time I could see the proper Ubuntu OS asking for my password etc.

It looks good. What shall I do now? Windows 8?

Thanks again

---

### Post by darkod on 2013-02-09
OK, the big job is finished. Now, as you can see, there are 3 win8 entries in the grub menu. The win8 files detected by grub are on /dev/sda1, /dev/sda2 and /dev/sdc1.

From what I can see, sdc1 should definitely NOT work.

Between sda1 and sda2, one should work and one not. Basically, try them one by one but don't be surprised if only one works. See if win8 boots successfully when you hit the correct entry.

Once you have that confirmed, if you want to we can try removing the files of the wrong entries so that grub doesn't show them, or simply leave them there and remember which one to boot for win8.

PS: If you are satisfied with the help please support my membership application by posting here:
[http://ubuntuforums.org/showthread.php?t=2113959](http://ubuntuforums.org/showthread.php?t=2113959)

---

### Post by edd13 on 2013-02-09
> **darkod said:**
> OK, the big job is finished. Now, as you can see, there are 3 win8 entries in the grub menu. The win8 files detected by grub are on /dev/sda1, /dev/sda2 and /dev/sdc1.

From what I can see, sdc1 should definitely NOT work.

Between sda1 and sda2, one should work and one not. Basically, try them one by one but don't be surprised if only one works. See if win8 boots successfully when you hit the correct entry.

Once you have that confirmed, if you want to we can try removing the files of the wrong entries so that grub doesn't show them, or simply leave them there and remember which one to boot for win8.

PS: If you are satisfied with the help please support my membership application by posting here:
[http://ubuntuforums.org/showthread.php?t=2113959](http://ubuntuforums.org/showthread.php?t=2113959)


Cool Darkod

You are right about those 3 W8 files ( sda1, sda2 and sdc1)
Let me get this right now you want me to reboot, choose the W8 ssd and try boot from it, right?
Can you explain what is the sda1 and sda2 and why they are related to W8 please? Sorry to bother you, I really want to understand everything and definitely would like to get rid of the extras files.

Please let me know as I will wait for your answer

Thanks

---

### Post by edd13 on 2013-02-09
> **edd13 said:**
> Cool Darkod

You are right about those 3 W8 files ( sda1, sda2 and sdc1)
Let me get this right now you want me to reboot, choose the W8 ssd and try boot from it, right?
Can you explain what is the sda1 and sda2 and why they are related to W8 please? Sorry to bother you, I really want to understand everything and definitely would like to get rid of the extras files.

Please let me know as I will wait for your answer

Thanks

Hi

I am now using W8 and both sda1 and sda2 lead to Windows 8.

The only problem is when I go to my BIOS and chose the original ssd that W8 was first installed I get the black screen error > grub.

If I choose the ssd that I always wanted to install Ubuntu I can run Ubuntu and Windows 8 from there. I don`t understand why my other ssd (the original does not run W8.

How can I boot w8 from the 1st ssd and Ubuntu from the second?

Tnx

---

### Post by darkod on 2013-02-09
No, you don't change the boot disk. It should stay sdb (the ubuntu ssd) in bios, because that's where the correct grub is. On sda you have broken grub so you will get error if you try to boot from it.

You don't need to switch between boot disks to boot windows, grub does that for you. As you noticed, both sda1 and sda2 entries work, so you can use which ever you want when booting. Grub is calling win8 from sda, you don't need to do that manually by selecting sda to boot from.

So, congratulations, you have your system up and running.

If you want to get rid of the sdc1 entry in the grub menu, open the sdc1 partition in ubuntu for example, and delete the /bootmgr and /boot/BCD files/folders. Those are the broken left over files. After that run in terminal:
sudo update-grub

That will get rid of the sdc1 entry and keep only sda1 and sda2 which both work as you say. That's it.

---

### Post by edd13 on 2013-02-10
> **darkod said:**
> No, you don't change the boot disk. It should stay sdb (the ubuntu ssd) in bios, because that's where the correct grub is. On sda you have broken grub so you will get error if you try to boot from it.

You don't need to switch between boot disks to boot windows, grub does that for you. As you noticed, both sda1 and sda2 entries work, so you can use which ever you want when booting. Grub is calling win8 from sda, you don't need to do that manually by selecting sda to boot from.

So, congratulations, you have your system up and running.

If you want to get rid of the sdc1 entry in the grub menu, open the sdc1 partition in ubuntu for example, and delete the /bootmgr and /boot/BCD files/folders. Those are the broken left over files. After that run in terminal:
sudo update-grub



That will get rid of the sdc1 entry and keep only sda1 and sda2 which both work as you say. That's it.

Hi Darkod

Thanks for all your help. I really appreciated it.

Let  me understand this whole process. Before I install unbuntu on my new  ocz ssd card my pc use to boot from my previous and only ssd running W8  only. Now I installed Ubuntu on the other ssd (new ssd) and GRUB took  over the system.
 Now my boot sequence has changed and I am now booting from my new ssd to run Ubuntu and W8.

Is  there a way to keep it separate though? It really annoys me when I get  that error when trying to boot from my original ssd card.

When I run W8 my Ubuntu partitions are not showing on My Computer but on Ubuntu i can see the W8 ssd + my data Hard Drive..

I am glad that my system is up and running and I thank you once again for all your help.

I will run that command to get rid of that partition sdc1 file.

Another think that I would like to ask you is about my partitions and sizes.

My ssd has 120 GB and I created 4 partitions according to some forums and this is how I partition my Ubuntu ssd:
dev/sdb1 ext2 size 476.84 Mib and this is my /boot partition
dev/sdb5 swap 7.45 GiB
dev/sdb6 ext4 29.80 GiB and this is my / (root partition)
dev/sdb7 ext 74.07 GiB

This  is how GParted is showing me. Is there better way or a right way to  create and use the right amount of GiB or MiB to create these  partitions? I don want to waste ssd space.

Thank you !!!

---

### Post by darkod on 2013-02-10
Well, simply don't try to boot from sda and you won't get any error. You can boot however you want to, but the most efficient way is to use the grub2 bootloader on sdb. For that, you will have to have sdb as first hdd to boot in bios.

The bios starts the boot process and first looks in the hdd that you set first in the order. It will find grub2 there and hand over the boot to it.

Grub2 can recognize and boot both ubuntu and windows, and is presenting you with a dual boot menu where you can select which OS you want to boot.

Using windows bootloader on sda to boot windows, and grub2 on sdb to boot ubuntu doesn't make much sense to me because every time you power on your computer you have to be ready and react fast to go into the motherboard boot menu so you can select which disk to boot.
If you really want to, you can do that. Just write a generic MBR to sda. It's best to do that from live mode using the ubuntu cd. In terminal do:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

There will be a warning message but ignore it and go on, it's normal. After that reboot without the cd and when you select sda to boot from it should load windows automatically, and when you select sdb it should present the grub2 menu.

As for partition sizes on sdb, /boot is fine although it was not necessary to use it.
The root partition could be little smaller, for example 20-25GB.
And swap can be also smaller depending whether you use hibernation or not. If using hibernation the recommendation is 1.5 x RAM so it depends on the size of RAM you have. If not using hibernation, and if you have plenty of RAM, you can make it 2GB or 4GB most.

But these numbers are not a huge difference to hwat you have right now, so repartitioning or reinstalling is probably not worth it.

---

### Post by edd13 on 2013-02-11
> **darkod said:**
> Well, simply don't try to boot from sda and you won't get any error. You can boot however you want to, but the most efficient way is to use the grub2 bootloader on sdb. For that, you will have to have sdb as first hdd to boot in bios.

The bios starts the boot process and first looks in the hdd that you set first in the order. It will find grub2 there and hand over the boot to it.

Grub2 can recognize and boot both ubuntu and windows, and is presenting you with a dual boot menu where you can select which OS you want to boot.

Using windows bootloader on sda to boot windows, and grub2 on sdb to boot ubuntu doesn't make much sense to me because every time you power on your computer you have to be ready and react fast to go into the motherboard boot menu so you can select which disk to boot.
If you really want to, you can do that. Just write a generic MBR to sda. It's best to do that from live mode using the ubuntu cd. In terminal do:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

There will be a warning message but ignore it and go on, it's normal. After that reboot without the cd and when you select sda to boot from it should load windows automatically, and when you select sdb it should present the grub2 menu.

As for partition sizes on sdb, /boot is fine although it was not necessary to use it.
The root partition could be little smaller, for example 20-25GB.
And swap can be also smaller depending whether you use hibernation or not. If using hibernation the recommendation is 1.5 x RAM so it depends on the size of RAM you have. If not using hibernation, and if you have plenty of RAM, you can make it 2GB or 4GB most.

But these numbers are not a huge difference to hwat you have right now, so repartitioning or reinstalling is probably not worth it.

I would like to thank you everyone who helped and specially darkod.

I am happy with the system and I finally understood the grub process and my system is up and running.

One last thing before a change the status to SOLVED. As I am a novice with linux especially ubuntu I would like to ask for an advice, from where do I need to start or if there`s any other website that could be handy to guide me on how to use ubuntu, paths, using terminal, cmd lines, short cuts etc.

Once again thanks for your time and help...All the best!!!

---

### Post by darkod on 2013-02-11
Uff, now you are asking for too much. :)

Online there are many websites and tutorials. I don't have any specific, I usually google what ever I need to find.

For complete overview, you might consider some book like for example:
[http://www.amazon.co.uk/Official-Ubuntu-Book-Matthew-Helmke/dp/0133017605/ref=sr_1_4?ie=UTF8&qid=1360593941&sr=8-4](http://www.amazon.co.uk/Official-Ubuntu-Book-Matthew-Helmke/dp/0133017605/ref=sr_1_4?ie=UTF8&qid=1360593941&sr=8-4)
[http://www.amazon.co.uk/Ubuntu-Unleashed-2013-Edition-Covering/dp/0672336243/ref=sr_1_6?ie=UTF8&qid=1360593941&sr=8-6](http://www.amazon.co.uk/Ubuntu-Unleashed-2013-Edition-Covering/dp/0672336243/ref=sr_1_6?ie=UTF8&qid=1360593941&sr=8-6)

Sometimes books can be found online to download as PDF, if you're lucky.

The ubuntu website has documentation too:
[https://help.ubuntu.com/](https://help.ubuntu.com/)

Select the version and then Desktop or Server depending what you need. That's a good start.

---

### Post by edd13 on 2013-02-11
> **darkod said:**
> Uff, now you are asking for too much. :)

Online there are many websites and tutorials. I don't have any specific, I usually google what ever I need to find.

For complete overview, you might consider some book like for example:
[http://www.amazon.co.uk/Official-Ubuntu-Book-Matthew-Helmke/dp/0133017605/ref=sr_1_4?ie=UTF8&qid=1360593941&sr=8-4](http://www.amazon.co.uk/Official-Ubuntu-Book-Matthew-Helmke/dp/0133017605/ref=sr_1_4?ie=UTF8&qid=1360593941&sr=8-4)
[http://www.amazon.co.uk/Ubuntu-Unleashed-2013-Edition-Covering/dp/0672336243/ref=sr_1_6?ie=UTF8&qid=1360593941&sr=8-6](http://www.amazon.co.uk/Ubuntu-Unleashed-2013-Edition-Covering/dp/0672336243/ref=sr_1_6?ie=UTF8&qid=1360593941&sr=8-6)

Sometimes books can be found online to download as PDF, if you're lucky.

The ubuntu website has documentation too:
[https://help.ubuntu.com/](https://help.ubuntu.com/)

Select the version and then Desktop or Server depending what you need. That's a good start.

Cool....Tnx!!!!!!!!!!!!!

---

### Post by oldfred on 2013-02-11
Some additional resources.

       A master thread on learning/books/terminal/bash/Linux etc
Linux Command Line Learning Resources
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)
[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)

   Thread on books:
[http://ubuntuforums.org/showthread.php?t=1874294](http://ubuntuforums.org/showthread.php?t=1874294)

---

### Post by edd13 on 2013-02-11
> **oldfred said:**
> Some additional resources.

       A master thread on learning/books/terminal/bash/Linux etc
Linux Command Line Learning Resources
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)
[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)

   Thread on books:
[http://ubuntuforums.org/showthread.php?t=1874294](http://ubuntuforums.org/showthread.php?t=1874294)

Thank you OLDFRED much appreciated!!!!

---

