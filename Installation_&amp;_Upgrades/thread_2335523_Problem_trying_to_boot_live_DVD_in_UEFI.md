---
title: "Problem trying to boot live DVD in UEFI"
date: 2016-08-29
forum: Installation &amp; Upgrades
---

### Post by Buntu Bunny on 2016-08-29
Dell Inspiron 3650 
Windows 10

I am trying to get my live Xubuntu 16.04 64-bit DVD to boot in UEFI. So far I can only get it to boot in Legacy. I have already turned off fastboot and disabled secure boot. I found a how-to at Dell support ("[How to enable boot from DVD option with UEFI boot mode enabled. (Windows 8, 8.1 & 10)]("http://www.dell.com/support/article/us/en/04/SLN142679/EN")"), but it shows different options and menus than I'm seeing. 

I'm in the Bios Boot Menu. My problem starts at "add boot option." The tutorial shows a screen for inputting a boot option name and selecting an option from a file system list.

I don't have that. I have "file browser add boot option." 
Selecting this gives me the name of partition 1. 
Selecting this offers me <EFI>
Selecting this gives me a "select media file" list: <.>, <. .>, <Microsoft>, <Boot>, <dell>

I assumed I should select <boot> which brings me to "select media file. My choices are 
<.>
<. .>
bootx64.efi

By this time I'm so far off the tutorial that I'm confused. I've returned to the Boot Menu. 

Please give me a clue of what to do.

---

### Post by Dennis N on 2016-08-29
bootx64.efi is the boot file on removable media so select it.

---

### Post by Buntu Bunny on 2016-08-29
> **Dennis N said:**
> bootx64.efi is the boot file on removable media so select it.

Dennis N, thank you. The next screen is "Input File Name," but the Dell tutorial says to leave the file name blank. If I hit enter without entering a name, I get

WARNING: Please set Boot Option Name and File Path

"Ok" takes me back to the Boot Menu. Any clue?

---

### Post by ubfan1 on 2016-08-29
You are looking at the hard disk's EFI partition, since the Ubuntu DVD will not have the "Microsoft" or "dell" choices.  You might need to enable the DVD as a boot option somewhere, then it might appear in the file browser list.  The bootx64.efi on the DVD will be a copy of shimx64.efi, and grubx64.efi should be present in the DVD's /EFI/Boot directory too -- no Microsoft or dell.

---

### Post by Buntu Bunny on 2016-08-29
> **ubfan1 said:**
>  ... You might need to enable the DVD as a boot option somewhere...

That's what I'm trying to do. I'm in the Windows setup utility trying to get the DVD to boot in UEFI so I can install Xubuntu alongside Windows.

---

### Post by Dennis N on 2016-08-29
Are you sure you need go through all this work of adding a boot option? Have you tried just pressing F12 to get the one time boot menu? It should show any bootable device of either mode - at least on my two UEFI computers it does. Neither is a Dell, however.
Also, I looked for the manual on the Dell site, and there is no Inspiron 3650 - is it a new model?

EDIT - OK, it is a desktop. I was looking at laptops.

---

### Post by Dennis N on 2016-08-29
> **Buntu Bunny said:**
> Dennis N, thank you. The next screen is "Input File Name," but the Dell tutorial says to leave the file name blank. If I hit enter without entering a name, I get

WARNING: Please set Boot Option Name and File Path

"Ok" takes me back to the Boot Menu. Any clue?
OK, if you have tried the F12 one time boot menu suggestion and there is no UEFI DVD boot option, I would do what is says and try entering the path to the boot file - on the 16.04 Xubuntu USB installer there are two options:

**[FONT=Courier New]/EFI/BOOT/BOOTx64.EFI[/FONT]**
or
**[FONT=Courier New]/EFI/BOOT/grubx64.efi[/FONT]**

You should have the same path and file name on a DVD. I also think I read somewhere, but am not sure, that a DVD boot would use the first one. Dell is sure not being very user friendly here. I get the feeling they expect you to just be using Windows.

That is about all I can say. Others probably have more knowledge on this.

---

### Post by oldfred on 2016-08-30
My Dell also has /EFI/Boot/bootx64.efi in the ESP - efi system partition on the Internal drive. That often is on internal drives as a fallback or hard drive boot entry. But external drives only boot from bootx64.efi in the /EFI/Boot folder in the external drive.

I installed using a flash drive and believe I just used the one time boot key f12 to choose the external drive to boot from.

---

### Post by Dennis N on 2016-08-30
I am wondering if the options for booting shown in the [first illustration of the guide]("http://www.dell.com/support/article/us/en/04/SLN142679/EN") reflect your computer's choices? I notice that the UEFI choices show only 'Network Boot' by default. So from that I infer that with 'Boot List Option' set to UEFI, you will only see UEFI options in the boot manager menu? And using the guide's illustration, you would see only Network Boot? 

I will be following the discussion to see how this all turns out as others will be experiencing this too.

---

### Post by oldfred on 2016-08-30
UEFI typically discovers bootable devices and offers them to boot from.

But they must be plugged in when booting and fast boot in UEFI must be off, as fast boot assumes no system changes and just boots into operating system without checking for any hardware of configuration changes.

Then downloaded ISO must be correct and we see many users with flash drive or DVD issues where not correctly written with installer tools. If just copied as ISO, it is not reconfigured to be a bootable device. Some brands of flash drives also just seem not to work. And some USB ports do not work. You have to experiment. And some do find DVD works better, others find DVD does not work.

---

### Post by Buntu Bunny on 2016-08-30
SUCCESS! 

\\:D/

I am so relieved. I stayed up late last night researching this problem. The boot options under F12 showed the CD/DVD/CD-RW Drive under Legacy options. This morning I decided to go back to the boot menu in BIOS and use the file name from the Dell tutorial to add a boot option. It was somewhat successful because the drive was now listed under UREI options in the F12 boot menu, but selecting it booted right back to windows. I decided delete that one and try the name Window used in it's "Use a Device" menu. This time I was offered a second option at "add boot option." I could choose partition 1 or ATAPI:HL-DT-ST DVD+/-RW. That gave me the two options Dennis N mentioned.

> **Dennis N said:**
> 

**[FONT=Courier New]/EFI/BOOT/BOOTx64.EFI[/FONT]**
or
**[FONT=Courier New]/EFI/BOOT/grubx64.efi[/FONT]**



I remembered seeing BOOTx64.EFI in the live DVD sfiles, so I took a guess and chose that one. 

> **oldfred said:**
> I installed using a flash drive and believe I just used the one time boot key f12 to choose the external drive to boot from.

That's how I did it too, and this time it booted the Xubuntu DVD in UEFI. 

I know that all sounds like a rambling jumble, so I apologize for that. Thank you to everyone who helped. Without you I could never escape Windows. Considering what is saw of Windows 10, that's a life saver.

---

### Post by Dennis N on 2016-08-30
Thanks for reporting on the successful outcome. Nice work on your part.

When I looked at the UEFI settings screens in the tutorial article, it appeared to me that a user could not even boot a USB flash drive in UEFI mode without adding a boot option, as you did for DVDs. It's very surprising they would design the UEFI firmware like this without UEFI USB and DVD boot options available by default. At least they should provide some clearer directions on how to add options. This firmware seems designed to deter users from installing and using anything except just Win 10.

I hope the system works well for you.

---

### Post by Buntu Bunny on 2016-08-30
Thanks. I'm getting things set up to suit my workflow and like it so far. 

I only do this about every four years, and it seems that for the non-technical user installation is getting more and more complicated. I know the Ubuntu team works hard to minimize problems, but as has been pointed out, different makes and models present unique circumstances. I remember when Dell offered computers with Ubuntu preinstalled. How things have changed.

---

### Post by Dennis N on 2016-08-31
> **Buntu Bunny said:**
> ...I remember when Dell offered computers with Ubuntu preinstalled. How things have changed.

Yes indeed. I bought a Dell laptop with preinstalled Ubuntu 7.04 on the second day they were offered online in late May 2007. Still have it. Then a Dell desktop with preinstalled Ubuntu in 2008 - bought with the economic stimulus money the govt. sent out, so it was free. Still have that one too.

---

### Post by Buntu Bunny on 2016-08-31
You would think that the ability to easily install additional operating systems would be a huge selling point. Even Windows devotees sometimes like to have more than one version of Windows on their machines.

Anyway, for anyone with a new Dell who is reading this thread because they are having similar problems to mine, here is a summary of what I learned about a live install from a DVD. I hope it will save you some time and grief. 

1. Make your Windows backup and recovery files first. That way you can always go back to the original if you think you botched it.

2. Shrink Windows from Windows Disk Management (follow steps 1 - 4 in instructions [here]("http://www.pagestart.com/win7win10tpdb10121403.html"))

3. Disable fast startup (instructions [here]("http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html#option1"))

4. Disable secure mode (instructions [here]("http://www.windowspasswordsrecovery.com/win8-tips/how-to-disable-uefi-secure-boot-in-windows-8-1-8.html"))

5. To find out how your live installation DVD will boot, start (or restart) your computer and tap F12 at the Dell screen (Do it more than once). It will take you to the Boot Menu, where you can see what boots in Legacy mode and what boots in UEFI. Your CD/DVD/CD-RW Device will probably be under Legacy options.

*NOTE:* There is no option to change the boot order. We used to have to do that but now you arrow down to the selection you want and hit enter to boot into your selection.

6. Restart and this time tap F2 to enter bios. Select the boot page and look for "add boot option." Select this and look for something that mentions CD and DVD. I didn't have this the first time so I selected the only option offered "Partition 1." Follow the selections:
[INDENT]efi
boot
bootx64.efi[/INDENT]
When it wants a name, give it something like "CD/DVD drive"

7. Restart, tapping F12 to go to the boot menu. Check under UEFI for the drive you just added. If it's there, select. You will know you've booted in UEFI if you are presented with a grub menu (try or install). If you get the traditional little man and keyboard, you're still in legacy.

That's what happened to me so I went back to BIOS and deleted the drive I added. When I tried again, I could choose either partition 1 or a CD/DVD option. Selecting that and going back through the selections in step 6 worked. When I went back to the boot menu through F12, I was able to boot the DVD in UEFI.

I'm not sure if that will be of much use since more folks seem to use a live USB drive than DVD. All my flash drives were full of backup files from my old failing computer, so a writeable DVD was all I had at the time.

---

