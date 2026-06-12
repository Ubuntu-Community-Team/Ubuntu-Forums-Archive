---
title: "Installation of dual-boot messed up BIOS boot-sequence"
date: 2014-03-22
forum: Installation &amp; Upgrades
---

### Post by n0c0d3 on 2014-03-22
I just bought a new PC and my intention was to install Win 7 (a version that came with my laptop over four years ago) and the latest version of Xubuntu. At first I used a LiveCD of Gparted (the latest version) to create the necessary partitions: a primary NTFS partition for Windows and an extended partition which I divided up into a NTFS part and an ext4 part where Xubuntu was supposed to be installed. All that seemed to have gone well.
Then I installed Win7, not really any problems here (besides the annoying long time it took and numerous reboots for all the updates to finish). But so far so good.

Now I wanted to install Xubuntu from the DVD I burnt. What surprised me was that the Windows installation was not recognized (but this is probably because it had its own primary partition), but I thought this may not be necessary to install a dual-boot and I installed Xubuntu to the Ext4 partition (I selected Ext4 and used the "/" for some location of which I always forget the function, but you'll hopefully understand what I mean), after having nibbled a bit of it for some swap-space. This all seemed to have gone well, until I rebooted. I didn't get the Grub dual-boot menu to choose from Windows or Ubuntu. In stead it booted directly into Windows. As it happened before to me when installing a dual-boot, probably because its boot-secors have been messed up a bit and have to be written to disk again, I got an error (I forgot the details), but I chose to use the last working version or something like that. Windows booted normally from there. I rebooted again, still no grub and no possibility to enter into Xubuntu, but Windows booted normally this time.

So I decided to re-install Xubuntu again. I got some other options as Xubuntu was recognized to be installed, and I chose to install it in its entirely over the previous Xubuntu install. As far as I know I used the Ext4 partition again. Things went fine until I rebooted again. Again no Grub, but now the PC booted directly into Xubuntu. So I installed Gparted to see how the HDD looked like and now the Ext4 partition had taken over the entire HDD, except for the NTFS part of the extended partition. The primary NTFS partition and with that the painstakingly installed Windows-installation seem to have vanished into thin air. I may have made a mistake somewhere, but I really don't know what it might have been. I hardly can imagine not to have highlighted the Ext4 line, but this is the most likely mistake I think I could have made, so Xubuntu more or less just took over the entire HDD.

But now comes the real problematic part. I thought to start over from scratch and remove all partitions, format the entire HDD in NTFS, install Windows and then partition the HDD from the Xubuntu-LiveCD. So I wanted to boot the Gparted CD to remove all partitions, but no joy. The PC boots directly into Xubuntu. The same for the Xubuntu LiveCD and the Win7 CD. I checked if I could change the partitions from within Xubuntu, but except for the extended NTFS partition (which now has magically changed into a FAT32 partition) I can't do anything. So I restarted again and tried to enter the BIOS-settings to check and change the boot-sequence if necessary, but no matter what I try, I can't get in there. According to the boot-screen I have to press the "Del" key, but I simply do not get into the BIOS. I didn't change it myself (I'd not yet entered that menu as things had gone well so far), but somehow after the second install of Xubuntu the PC won't boot from CD anymore. This is not okay!

The options I get in the boot-screen are:
Del: BIOS/Q-Flash
F9 : System Information
F12: Boot-menu
End: Q-Flash

I didn't try F9-Q-Flash, as it seems to have something to do with updating the BIOS or something like that, and so far I'm not intending to do so. This is what the motherboard manufacturer has to say about it:
[http://www.gigabyte.com/MicroSite/121/tech_qflash.htm](http://www.gigabyte.com/MicroSite/121/tech_qflash.htm)

I did try all other three options to see if the do something, but no joy. I've even pressed those keys, especially the Del-key as to according my experience it can sometimes be pretty hard to get into the BIOS, so often and probably way too long while Xubuntu was already booting that now even Xubuntu is showing errors.

The most urgent thing is I want to be able to boot from CD/DVD again as I hopefully can start over from there again. As things look now, I'm pretty much stuck here with just Xubuntu and as long as I can't boot from CD/DVD and I won't even be able to install it again if something happens to this installation.

So I hope someone has a clue as what could have gone wrong, how the Xubuntu installation might have changed or damaged the boot-sequence in the BIOS and how to change/repair this.

Thanks for any help in advance. The situation looks pretty dire as it is now.

Bart

---

### Post by slooksterpsv on 2014-03-22
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Reboot off the Live DVD and run Boot-Repair; have it only get the info and post the results of the app back here.

---

### Post by n0c0d3 on 2014-03-22
> **slooksterpsv said:**
> [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Reboot off the Live DVD and run Boot-Repair; have it only get the info and post the results of the app back here.

I know I've typed up a long story (not to get questions like "why did you do that") and I'm sorry for that. But I explicitly stated that I can't boot from any LiveCD anymore and that is just the problem I'm looking for to be solved.

---

### Post by slooksterpsv on 2014-03-22
I apologize I misread. So you're in Xubuntu now? If you are run the boot-repair.

If not in Windows run diskmgmt.msc take a screenshot and post that screenshot here.

Note: I just woke up so it's taking me a minute to decipher text haha.

---

### Post by n0c0d3 on 2014-03-23
> **slooksterpsv said:**
> I apologize I misread. So you're in Xubuntu now? If you are run the boot-repair.

If not in Windows run diskmgmt.msc take a screenshot and post that screenshot here.

Note: I just woke up so it's taking me a minute to decipher text haha.

I hope you had a good sleep ;-) Here it's 5 in the middle of the night. Or is it the end of the night? I need some sleep... 

I installed boot-repair and got the following report:
[http://paste.ubuntu.com/7139229](http://paste.ubuntu.com/7139229)
I hope you can make sense of it,. because I for sure can't.

I also got some pop-up message about EFI and things I don't understand, but that's all too long to copy and type from one computer to another right now.
I rebooted, got a Grub-menu, but I can't navigate in it with the up-/down-arrow keys. Luckily is starts automatically in the right selection.

And still no possibility to boot from CD or DVD. Pretty messed up... sigh...

Edit:
In the Grub-boot menu, there of course is no Windows option. Only Ubuntu-related stuff, some "EFI" entry and a "System Setup", which I can't navigate to to enter.

---

### Post by slooksterpsv on 2014-03-23
According to that, there is no Windows partition, which means during the install the option for Use Entire Disk may have been selected which deleted all Windows and Recovery (if any) partitions.

---

### Post by n0c0d3 on 2014-03-23
That's what I suspected already. But the problem that I can't even boot from CD or DVD since I installed Xubuntu remains. This is weird as boot from CD seemed to be the default from the start and I didn't manually change it.
I want to be able to boot from CD again and I don't really care about what's on the HDD now or was there before. That may all be removed, as long as I can boot from DVD again. And it's really weird I can't enter the BIOS-settings either. I did try to enter the BIOS once before, but when that didn't work out I just thought my timing was off when I tried and didn't try it again until I needed to.

I really hope someone can figure out what could have gone wrong here. This is a new PC and it looks like to be fubar already...

---

### Post by slooksterpsv on 2014-03-23
When you say it won't boot from the CD are you able to tell it to attempt to boot from the CD? If so and it won't boot, drive could have went bad.
Otherwise let's do this:
See the Qt app in my signature? Let's download it and change the boot order to boot from the CD first. To download it you'll need to run the following in a terminal:

pkexec apt-add-repository ppa:slooksterpsv/efibootorder
pkexec apt-get update
pkexec apt-get install efibootorder

Under the Applications->System menu there is a program called efibootorder - run it. Click on pull EFI System information, click on the CD and move it up to the top as far as it will go, click on Save.

Make sure the Windows 7 DVD is in the drive and reboot. Keep tapping F12 (just in case) and keep pressing it repeatedly (like 3 times a second). If the boot menu does come up make sure it says the DVD drive. Now when it's loading the DVD you'll need to keep pressing any key on your keyboard cause Windows 7 sometimes won't load unless you tell it to boot from the dvd. Usually it prompts - Press any key to boot from dvd... 

If all of that fails let me know. If you have a thumbdrive we can look into making a bootable Windows 7 USB install key (pain to make it in Linux, but worth it).

---

### Post by n0c0d3 on 2014-03-23
As i described in my initial post it won't boot from any CD. I tried the Gparted, Xubuntu and Win7 CD's. To no avail. So I don't think it's the CD and the CD-player doesn't make any funny noises trying to read them either. I can read the CD from within Ubuntu, so the player seems to be working fine as well.

The rest of your story will take some time to try, but I'm off to sleep now. I'll let you know. Kinda hard to tell if things went right or wrong when you have to tap a key three times a second at just the right moment though. But I will try and see what comes out of it tomorrow. I really hope it'll work.

Thanks for your support so far slooksterpsv. I really appreciate it.

Bart

---

### Post by n0c0d3 on 2014-03-23
Fortunately I can exchange files between computers over FTP through my HD-DVD-recorder, which can act as a kind of file-server, when they are all connected to my router, without having to configure shared folders on the computers. This makes copying commands much easier and safer (no typo's).

I was thinking maybe my keyboard was not recognized during system-boot and therefor I couldn't enter the boot-menu and Grub entries. But with this EFI-thingy of yours I can fortunately get in. I'll explain what I did.

In Xubuntu in installed your efibootorder program.

I got (amongst others) two "CD/DVD Drive" options to choose from. One normal and one UEFI entry. The UEFI was pre-fixed "Boot0001*" and the normal has the prefix "Boot0003*". I chose the normal one and moved it as high as possible, which was the second position .The topmost position is "EFI Boot Options". I saved and rebooted with Windows in the DVD-drive.

I did the F12 and yes Yes YES!!! It worked.
Now, according to the menu I get, the bootorder seems to be:
- CD-DVD
- HDD
- 3*
- 4*
* 3 and 4 are my HDD, but now has "ubuntu" in front of the type-code of the HDD.

I exited the boot-menu without saving anything and then the Windows-CD booted as it was supposed to (no extra key- and fingertip punishing tapping and pressing required).

But now I have another problem, and that is that when I try to boot without the (Windows) DVD I get the message that there's no boot-device. When I reboot pressing F12 I get this "new" boot-menu and I can get in the BIOS-settings. My "old" boot-screen seems to have disappeared and the PC doesn't seem to search for a secondary boot-option.

I didn't continue to install Windows yet, as I did some searching for this EFI stuff and came across this: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
I still have to read it more carefully as I' think it's better to to resoleve the current problems first, but it seems I have to disable Quickboot/Fastboot. In the system boot-menu (F12) Fast Boot is currently set to "Ultra Fast".

In the BIOS the bootorder is different than in this efibootorder program you told me to use. Here the DVD is set to 1 as well (at least "top-most", but the HDD (general, no ubuntu in front of it and maybe this is the FAT32 partition that I think is still there) is set to 4 and both "Ubuntu" entries are set to 2 and 3. When I navigate to one of those ubuntu-entries and enter to be able to set it to another bootorder, there the order is like in your efibootorder-utility. Also, when I reboot and press F12 to get this new boot-menu the order is:
1: DVD
2: HDD (the general entry)
3: Ubuntu-HDD
4: Ubuntu-HDD

Also in the BIOS, when I go to save and exit, there's this " Boot Override" section where the order is also as above, even though I previsouly Saved it as follows:

1: DVD
2: Ubuntu-HDD
3: Ubuntu-HDD
4: HDD (general)

When I go to one of the entries in this Save& Exit section and press Enter the system reboots in what I chose. When I choose one of the Ubuntu-options I boot into the Grub-menu and now I can navigate with the arrow-keys there. This navigating also works again when I boot Ubuntu directly from the F12 boot-menu.

The Grub entries are:
- Ubuntu (Which boots Xubuntu)
- Advanced options for Ubuntu (which has the kernels to choose from inside it)
- EFI/ubnutu/MokManager.efi (then I get somethign I don't understand so I got out of it asap)
- System setup (which brings me right into the BIOS settings).

But still when I boot without bootable DVD I get this message that there's no boot-device. I have to reboot, press F12 to get this new boot-menu and then I can choose what entry to boot from. If I choose one of the Ubuntu-entries I get this Grub-menu and I can boot Xubuntu. But of course it's not really convenient to have to press F12 every time immediately after a startup or reboot.

So I'm a bit confused as to how I should set things up to be able to get things working as they should (when there's no DVD inside the drive it should automatically pick the next option and so on), install Windows and then Xubuntu as dual-boot. And in the bootorder menus there are two equal Ubuntu-entries. What should I make of this? 
Then there's this Fast Boot. Should I disable it before I even install Windows, or only after that (but maybe it's too soon to talk about this yet)?

I'm sorry for another lengthy story. But I feel it's better not to leave anything of what I see, encounter and have done out to give you a full view on the situation, and I type things pretty much as I go along. And I don't want to mess up things more than they are now already.

I'm happy I can now at least boot from DVD again, but I hope you can help me with the rest of the problems as well and kind of guide me through as I have no real clue what to do next.

Thank you for your help so far!

Bart

---

### Post by oldfred on 2014-03-23
Your original description and current issue are the same or related.

You have a gpt partitioned drive. Windows only boots from gpt partitioned drives with UEFI.

The standard Windows 7 DVD is BIOS only, so it cannot install in a gpt drive. But if you force it to install, it converts drive to MBR(msdos) but leaves the backup gpt partition table. Linux tools then see MBR and gpt and get confused on which you have or want and give up. You can use fixparts to remove the backup partition table.
Or you can convert your Windows 7 DVD to a flash drive and add some changes to make it a UEFI installer.

Only run this if you have used Windows to convert a gpt partitioned drive to MBR. Otherwise it may cause issues. And then be sure to install Ubuntu in BIOS boot mode.
       FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Both Windows and Ubuntu will only boot from MBR with BIOS.
Both Windows and Ubuntu boot in UEFI mode from gpt and Windows has to have gpt for UEFI boot.
Ubuntu will boot in BIOS or UEFI if correct support partitions are on drive. You need an efi partition for UEFI boot or a bios_grub partition for BIOS boot for grub to install correctly.

You need to be consistent in booting live installers as how you boot installer for both Windows and Linux is how it installs or boot in BIOS, it installs in BIOS, or boot installer in UEFI and it only installs in UEFI boot mode.


 Prepare an usb thumb drive, to boot windows 7 in UEFI mode
[http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
[http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177](http://forums.lenovo.com/t5/tkb/articleprintpage/tkb-id/Beta_OS@tkb/article-id/177)
[http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx](http://technet.microsoft.com/en-us/library/hh304353%28v=ws.10%29.aspx)


 Converting to or from GPT
[http://www.rodsbooks.com/gdisk/mbr2gpt.html](http://www.rodsbooks.com/gdisk/mbr2gpt.html)

      
 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)

---

### Post by slooksterpsv on 2014-03-23
> **n0c0d3 said:**
> ...
But now I have another problem, and that is that when I try to boot without the (Windows) DVD I get the message that there's no boot-device. When I reboot pressing F12 I get this "new" boot-menu and I can get in the BIOS-settings. My "old" boot-screen seems to have disappeared and the PC doesn't seem to search for a secondary boot-option.


We will need to change in the BIOS the boot order and set it back to what you want to initially start. This could be an issue with Fast Boot, I'm not entirely sure. We can also use the app I had you download to change it. I'm thinking it may be an issue with FastBoot first.

> 
I still have to read it more carefully as I' think it's better to to resoleve the current problems first, but it seems I have to disable Quickboot/Fastboot. In the system boot-menu (F12) Fast Boot is currently set to "Ultra Fast".



That's a good idea, that Fastboot can be a bit troublesome

> 
In the BIOS the bootorder is different than in this efibootorder program you told me to use. Here the DVD is set to 1 as well (at least "top-most", but the HDD (general, no ubuntu in front of it and maybe this is the FAT32 partition that I think is still there) is set to 4 and both "Ubuntu" entries are set to 2 and 3. When I navigate to one of those ubuntu-entries and enter to be able to set it to another bootorder, there the order is like in your efibootorder-utility. Also, when I reboot and press F12 to get this new boot-menu the order is:
1: DVD
2: HDD (the general entry)
3: Ubuntu-HDD
4: Ubuntu-HDD

Also in the BIOS, when I go to save and exit, there's this " Boot Override" section where the order is also as above, even though I previsouly Saved it as follows:

1: DVD
2: Ubuntu-HDD
3: Ubuntu-HDD
4: HDD (general)

When I go to one of the entries in this Save& Exit section and press Enter the system reboots in what I chose. When I choose one of the Ubuntu-options I boot into the Grub-menu and now I can navigate with the arrow-keys there. This navigating also works again when I boot Ubuntu directly from the F12 boot-menu.

The Grub entries are:
- Ubuntu (Which boots Xubuntu)
- Advanced options for Ubuntu (which has the kernels to choose from inside it)
- EFI/ubnutu/MokManager.efi (then I get somethign I don't understand so I got out of it asap)
- System setup (which brings me right into the BIOS settings).


The EFIBootOrder app uses EFIBootMgr which looks at the NVRAM for whats stored for the Boot Order. This can be different, and may not work on all machines. If you can get in and change the boot order in BIOS, that's great! That's better because we for sure know the BIOS will change it. Ubuntu will put 2 Ubuntu options, it happens, just ignore it. That's fine. You can use the F12 if you wanna switch between Windows and Ubuntu.

> 
But still when I boot without bootable DVD I get this message that there's no boot-device. I have to reboot, press F12 to get this new boot-menu and then I can choose what entry to boot from. If I choose one of the Ubuntu-entries I get this Grub-menu and I can boot Xubuntu. But of course it's not really convenient to have to press F12 every time immediately after a startup or reboot.

So I'm a bit confused as to how I should set things up to be able to get things working as they should (when there's no DVD inside the drive it should automatically pick the next option and so on), install Windows and then Xubuntu as dual-boot. And in the bootorder menus there are two equal Ubuntu-entries. What should I make of this? 
Then there's this Fast Boot. Should I disable it before I even install Windows, or only after that (but maybe it's too soon to talk about this yet)?


First before I dive into my idea let's start with the following:
Due to Fastboot I think instead of going to the next boot option, it just halts on the current one and gives you that error. I'm not sure exactly, whenever a boot option isn't available on my EFI computers it went to the next one. It could be a bug that needs a BIOS update or what not. But my idea may give us more of a theory. 

With Ubuntu in general if you want to dual-boot that will have to be the way to do it for now. I believe there's a way to get Windows 8 to recognize Ubuntu, but I haven't given it much time or effort to look into.

I have an idea with the issue you're facing with booting from the DVD. You said it's a Windows 7 DVD? With Windows 7 EFI and GPT is supported but only if you have UEFI v2.0+ - [http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html](http://www.sevenforums.com/tutorials/186875-uefi-unified-extensible-firmware-interface-install-windows-7-a.html)
UEFI is only available on windows 7 with 64-bit installations which means there's 1 of 3 things happening:
1. UEFI isn't v2.0 or greater (if it's a newer PC, I highly doubt this).
2. The Windows 7 DVD you're using is 32-bit - which won't work with UEFI (again doubtful, but a possibility)
3. The DVD drive is going bad or the BIOS needs an update where its having trouble booting off of DVDs.
4. Just thought of this - if Secure Boot is enable, I don't know if Windows 7 supports secure boot or not.

Those are my 3 items. (now 4)

You can disable secure boot and fast boot, but leave UEFI on. If you disable UEFI and switch to legacy OS, you won't be able to get back into Ubuntu as the computer knows how to load using the first sectors and if there's no MBR for Windows or Grub it'll fail.

The Fastboot/quickboot option, disabling that may help cause it could be attempting to parse the DVD information faster than it can read it causing a Boot Error.

---

### Post by n0c0d3 on 2014-03-23
Thanks for your replies guys. But I'm confused what to do now.

First some more info on my system and Windows version.
I bought the computer last week. It's entirely new and has this motherboard: [http://www.gigabyte.com/products/product-page.aspx?pid=4568#sp](http://www.gigabyte.com/products/product-page.aspx?pid=4568#sp)
There's nothing mentioned about EFI besides "Use of licensed AMI EFI BIOS". In the BIOS itself I can't find anything about the version either. The BIOS version is "F5" and the BIOS-date is 08/03/2013, the BIOS-ID is 8A02AG0K.

The Windows CD's I have is Windows 7 Home Premium 64 bits. It was installed on my laptop when I bought it. There was no installation/recovery medium delivered with it, but it offers you to burn a 3 CD Win7 recovery, which I did and am using now on my new PC. As UEFI seems to have been released in 2010 and my Win7 is from 2009 it is most likely not prepared for UEFI. When installing Windows I got errors on some bus, the network- and USB (3.0)-drivers as they were not included in the CD's. Unfortunately Windows Update and Driver-update functionalities didn't find any updates for them either. I had to go to the motherboard website to download and install them to correct them (which was successful).

In the BIOS there is a "secure boot" entry, but it seems to be fixed as I can't navigate to it to change it. It is set to "Disabled".
I can't find any UEFI-setting in the BIOS at all. I think I have left no stone unturned, I think, so I wouldn't know how it is set or how to change the setting.

But as I said I'm confused as to what to do now and have a hard time to distill a plan-of-attack out of both your posts. Oldfred said my problems. I assume he means the not going for the next boot-options when there's no bootable DVD in the player and the initially not being able to boot from DVD anymore are related.
Does this mean you think it can be resolved by installing Win7 from a thumbdrive? I get somewhat scared when reading the warning on the Sevenforums-page you both posted. When I do something wrong it makes my system unbootable.
And I read the links Oldfred posted, but it's all pretty much. I'll have to be very careful not to make mistakes. And besides that, I have 3 recovery CD's. When installing Windows all three are needed, so will there be asked for number 2 and three when I install from thumbdrive?

So I'm left with a number of questions. What is really necessary to have a dual-boot system that will also boot without the F12-menu and searches for a next option when there is no DVD inside the player? Like, would I have to convert to GPT?

So combining both your posts, what is the best plan of attack? Should I start with disabling Fast Boot? Then maybe try to install Win7 from DVD as Sevenforums describes (Step 2), or should I really create a bootable thumb-drive with Win7 on it? (the Lonovo way). I really don't know if my first install changed the HDD to MBR or not and such and consequently have to use fixparts. But wouldn't it not be more easy to just boot from my Gparted CD and wipe off all partitions and just start over with a blank disk?

I hope you guy can give me advice to what is the easiest and hopefully safest way to get things done. I don't mind if you both discuss the options in this thread to get to an agreement on which path to follow, as long as you don't start shouting at each other of course ;-)

Thanks guys.

Bart

---

### Post by slooksterpsv on 2014-03-23
> 
And I read the links Oldfred posted, but it's all pretty much. I'll have to be very careful not to make mistakes. And besides that, I have 3 recovery CD's. When installing Windows all three are needed, so will there be asked for number 2 and three when I install from thumbdrive?


You'd have to do it from the CD/DVD's; I don't think you can take the CD's/DVDs and put them on thumbdrives.

> 
So I'm left with a number of questions. What is really necessary to have a dual-boot system that will also boot without the F12-menu and searches for a next option when there is no DVD inside the player? Like, would I have to convert to GPT?

If you did MBR, you could have GRUB handle all the boot options, which you'd still have to press up or down and select which OS to boot from, but you'd get a timeout. To do this you would have to disable Fastboot first, then disable Secure Boot, and then change from EFI to Legacy OS in the BIOS. Your disk drive is GPT - [quote=pastebin]GPT (GUID Partition Table) detected on '/dev/sda'![/quote]

So you'd have to reformat and make it MBR.

If you change all of those options, you may not be able to boot back into Xubuntu until you reinstall it or install Windows. Also I'm not sure if the CDs you made would work or not in MBR/Legacy OS mode.

> 
So combining both your posts, what is the best plan of attack? Should I start with disabling Fast Boot? Then maybe try to install Win7 from DVD as Sevenforums describes (Step 2), or should I really create a bootable thumb-drive with Win7 on it? (the Lonovo way). I really don't know if my first install changed the HDD to MBR or not and such and consequently have to use fixparts. But wouldn't it not be more easy to just boot from my Gparted CD and wipe off all partitions and just start over with a blank disk?


Best thing to start with that won't hurt anything is to yes disable fast boot, and try booting from the DVD. The bootable thumbdrive, if you have a retail copy and valid retail license, we won't look into unless that doesn't work.

**Extra Info:** With newer computers the licensing system for Windows 8 and 8.1 (and possibly newer versions of 7) is that the CD-KEY for the computer is a volume license key but is embedded in the BIOS. You can use a linux command to pull the CD key but it won't do any good as there's no available non-retail ISOs to be able to use the key. Believe me I've tried. You have to have what originally came with the computer to use the key that came with your system. Now Windows 7 I can't be for sure on, but Windows 8/8.1 i know that's a for sure thing.

---

### Post by oldfred on 2014-03-24
I also believe you cannot use a Windows 7 recovery set of DVDs on another system. The OEM or vendor serial number will not work on another system.

You have to have a full install and a new license to install a Windows on a different computer. As mentioned the license you have built into your system is just for the version of Windows the system came with.

---

### Post by n0c0d3 on 2014-03-24
I bought this computer without any OS at all. I'm going to run Xubuntu and use Windows only when I really need to. I had that "laptop" version of Win7 already installed on this new PC and I got no warning that it couldn't be installed for licensing reasons or whatever, so I assume there's no problem here. It's one of the earliest versions of Windows 7, from just a few months after Win7 was released.

I disabled Fast Boot and the Windows-CD still boots. It doesn't resolve the issue that it doesn't automatically search for another boot sector though (but it may search for it but it doesn't recognize it as oldfred explained). I still get the error-message that there's nothing to boot from when there's no DVD in the player.

So to make the HDD "MBR", what should I do? Is there an option in Gparted to do that? And what should I do now? Just blank the HDD by removing all partitions with Gparted and then create an MBR (how?), install Win7 on the entire HDD and then continue from there?
And this secure boot, as I mentioned already, is disabled in the BIOS and I wouldn't even know how to enable it as it only seems to be a notification in the BIOS to which I can't even navigate.

I really need some step-by-step guidance here, as this is all new territory for me, with this MBR and UEFI on such. I'm used to "just format the damn thing" and it works ;-) Will this explanation: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) be of any help in his case?

Thanks again for your support guys.

Bart

---

### Post by oldfred on 2014-03-24
You have to decide if you want UEFI or BIOS. Your system will boot with either but to easily dual boot you should use the same boot mode for both installs.

If you want to install Windows in BIOS/MBR you will have to reformat drive to MBR as the Windows installer will not work. It also needs to see either unallocated space and available primary partitions or you have to create a NTFS primary partition with the boot flag for Windows to install.

If you can even convert your Windows to flash then you have to have gpt partitioning. Not sure if an old copy of Windows 7 will work or work well. You may have to search for newer drivers. Originally Microsoft wanted vendors not to even offer Windows 7 drivers for new hardware so users could not down grade from Windows 8.

Gparted defaults to MBR(msdos), but you can change to gpt. But if drive is already gpt you may have to change to MBR. That will erase drive, so if you have any data make sure you have backups.

---

### Post by n0c0d3 on 2014-03-24
Well, it seems UEFI has certain advantages. But I think it's best to do what's the safest (I don't want to destroy the BIOS or whatever that's called nowadays) and easiest (If I for whatever reason need to re-install the whole bunch due to some HDD-failure or whatever, then I don't want to go though this whole mess again. But maybe it's like once I know how to install the UEFI-way it's as easy as I was used to. I currently only have one thumb-drive and I need it for other stuff as well, and don't feel like buying another one only to have Win7 on it in a sleeping state for years until I might have to use it again, which may (hopefully, but that may be wishful thinking) be never.

But if Gparted used MBR/BIOS by default, then the HDD probably should already formatted like that as I initially (before even installing Windows) used Gparted to partition the disk. I can't remember what option I used from the menu you posted this picture of. I most likely used MSDOS as that's the only thing I'm familiar with. I can't imagine to have used "gpt" as that sounds too obscure to me. Still, according to Slooksterpsv in post #14, the disk is formatted GPT. 

I prefer to install Windows from the CD's. I already have those, they worked before, and, from what I've read, creating a flash-drive is not all that easy (I can make lots of mistakes) and then there's this problem of the need for three CD's that are necessary to install Windows.

So if creating a bootable thumb-drive is necessary to create a UEFI install, then probably I should go for MBR/BIOS. And to create a UEFI-system I need to pick the "gpt" option in Gparted  and if I want to go for MBR/BIOS then I should MSDOS again?

And I don't care about what's currently on that HDD, it may be completely wiped clean. There's nothing of importance on it or anything that I can't find again within minutes. The nastiest thing already happened and that is that I need to install and update and consequentially reboot this entire Windows-monster countless times again, which is going to take me hours and hours, and even more hours again. And I don't even know what changes there are made to the UEFI/BIOS after installing Xubuntu, after which the problems started.
 Actually I'd prefer to reset the entire PC to how it was before I inserted the  Gparted drive and made changes to the system, but I don't think that's  possible now anymore.

What do you guys make of all of this (ie. what would you do if this was  your PC and wanted to create a dual-boot system with the Windows version  I have)?  My gut-feeling says it would be best to use gpt and UEFI, but only if I don't need to create a bootable flash-drive to do so. But I may be wrong and I do not have the knowledge to make an educated choice.

As I said, what really I need is some step-by-step guidance. Like:
1) (e.g.) Use your Gparted disk to format your HDD to partition it so and so with options so and so, then,
2) (e.g.) Install Windows from you recovery disks, then,
3) (e.g.) Insert the Xubuntu-LiveCD, choose "other options" and format the drive like so and so and place Xubuntu on partition so and so.
4) (e.g.)  If it worked well, enjoy , because it all worked out, else
5) Go berserk, stamp you feet and cry for a couple of minutes, get yourself together and report back to see what went went wrong and how to correct it.

The end-result should be that when there's no bootable CD inside the player when I (re-) boot I get this Grub-menu from which i can choose what to boot (Ubuntu/Windows/etc.). When there is a bootable DVD inside then it should boot from that.

I know it's taking a lot of of your time as well, but i really wouldn't know where else to go.

Thanks again!
Bart

---

### Post by oldfred on 2014-03-24
If drive was gpt, it will not automatically convert to MBR. You would then have to specify that.

I might delete all partitions and use gparted to convert to MBR. And then see if Windows will install. And work.
Then use Windows tools to shrink NTFS partition to make room for Ubuntu. Always reboot immediately after a NTFS partition resize so Windows can run chkdsk and update itself to its new size.

Then you should be able to install Ubuntu into the unallocated space.

I find flash drives a lot faster to use for installing. And you really need a working repair CD or flash drive to fix Windows easily. And your current version Ubuntu live installer to fix Ubuntu if needed. 

I have many flash drives now, but my problem was (is) that a Microcenter is only a few miles away and at checkout counter they have the house brand flash drives. Every visit I find prices are cheaper or now the new USB3 flash drives are almost as cheap. They also are about 10% faster even with my old USB2 ports.

---

### Post by n0c0d3 on 2014-03-24
So you'd recommend me to go for MBR, despite the advantages of UEFI (faster boot, better driver support and such)? Why?
And how do I specify that I want the disk to be formatted with MBR? Do I use this msdos-option in the Gparted-menu you posted a picture of earlier for that or is there some more trickery involved to get that done?

And it's not the money (but I'm not particularly swimming in money either). I know flash-drives are cheap nowadays. But how do I put 3 CD's on one flash drive? According to slooksterpsv this might be a problem. And besides that, Microsoft doesn't deserve a flash-drive to be designated to their monopolist OS and strategy ;-) But can I even install Windows (and of course Xubuntu with dual-boot) with UEFI if I install from DVD, or do I explicitely need to install from flash-drive to get that done? And the installation-speed doesn't really matter to me. INitial installation doesn't take that long, the biggest time-consumer are the updates that come after that, and they don't come on CD or Flash-drive.

I hope I'm not too much of a nag, but I really want to get it done right, and when possible, even understand some of the background so the next time I don't have to ask for help again and am able to figure things out myself.

Thanks,
Bart

---

### Post by oldfred on 2014-03-24
I generally go with UEFI and gpt partitioning. 
But I have been using gpt since 10.10, but then my XP would not even read any data in my gpt partitioned drives. 

UEFI is a bit more complicated and is the newer way to do things. Both vendors own UEFI/BIOS is often updated and Linux kernels & grub are updated with every new version to work better. Hardware vendors pretty much only design to work with Windows and Linux has to re-engineer drivers, so very new hardware can take a bit more before it works.

Not sure how to convert your Wikndows disks to UEFI, if the links posted above do not work for you. If you can do that, then UEFI should be better but may not be as easy.

I used to create new updated CDs for Ubuntu, gparted, parted magic, Supergrub and other repair or install utilities for every new install every 6 months. Once I found how to boot many ISO from one flash drive with grub2, it is a lot easier to just update flash drive with newest ISO. 
But you generally need a separate flash drive for Windows repair, for Windows install and you must have a set of DVDs or flash drive with your installed version of Windows to make recovery possible if drive fails or you accidentally erase it.

---

### Post by n0c0d3 on 2014-03-24
So there's not really an advantage of UEFI over MBR/BIOS if I understand you well, and it may even cause problems when running Ubuntu. In that case I better go for MBR. I always have a currently installed version of Xubuntu that I downloaded from the website on DVD and of course I have the Win7 installation disks. When something happens to those I might be in trouble of course, but I believe I have some backups of those somewhere on an external drive (but I'd have to search for them to be sure). Besides that I have some Windows-repair disk and a NeoSmart Recovery disk for Win7/64 (which nowadays seems to be out of the public domain due to breach of MS-Licensing or something like that) that helped me out before with repairing bootsectors or something like that. I don't have all the tools you have (I'm only an amateur, but you already know that ;-) ), but when I get things working I'll look into them.

So what should I do now? Boot the Gparted CD, delete all current partitions and reformat the entire drive to NTFS, or should I just delete all partitions, reboot on the Windows-CD and let that take care of the formatting? And how do I make it MBR?

I just booted from the Gparted-CD and there are currently 3 partitions. Should I just delete them all and then create a msdos partition table (from the Device/Create Partition Table menu) and then the disk will automatically partitioned with MBR? This is really a questions I need to be answered, because otherwise I wouldn't have a clue how to make the drive MBR (I can't find a special option for that). 

And if that works I should be able to install Windows from the CD's and continue as you explained in one of your previous posts (resize from within Windows, reboot Windows, then install Xubuntu on the unallocated space)?

Or is there more to it?

Bart

---

### Post by slooksterpsv on 2014-03-24
You pretty much have it all summed up to what you need to do to convert to MBR -> install windows -> resize -> install xubuntu - enjoy! =D

---

### Post by n0c0d3 on 2014-03-24
I wish I had the same knowledge and understanding of these things as you do, slooksterpsv... What you sum up is pretty much what I did in the first place, but it ended up to be gpt. The thing is I don't know how to make it MBR. What I think I didn't do at first is creating a partition-table (the msdos option in the menu I mentioned above). So the question still remains: Does choosing this msdos-option create a MBR? And if it doesn't do that, how do I make sure I do create an MBR partition table this time. I don't want to go through all this again you know, so to me this is really important to know before I start changing and installing things.

Edit:

I just converted the entire HDD to this "msdos" partition table, and, how surprisingly, the device information in Gparted tells me it's a "msdos" partition table. Is this the same as a master "Boot record" (MBR) or should I still do more to create a MBR?

---

### Post by slooksterpsv on 2014-03-24
> I just booted from the Gparted-CD and there are currently 3 partitions. Should I just delete them all and then create a msdos partition table (from the Device/Create Partition Table menu) and then the disk will automatically partitioned with MBR? This is really a questions I need to be answered, because otherwise I wouldn't have a clue how to make the drive MBR (I can't find a special option for that). 

What you said there is what makes the MBR partition scheme.

---

### Post by n0c0d3 on 2014-03-24
Okay, I just edited my previous post and added some extra info. We crossed each other. So this msdos reference is okay, this means a MBR is created and I can now continue to install Windows?

---

### Post by slooksterpsv on 2014-03-24
Yes, you created an MBR and can install Windows - when you selected that option in the drop down under advanced there's an option for GPT which is not what we want in this case. MBR is the default.

---

### Post by n0c0d3 on 2014-03-24
Thanks. Windows is currently steaming! I already got the first "wait a moment". Many more to go...

---

### Post by slooksterpsv on 2014-03-24
At least we have Windows back on there =D - Linux should be a breeze after that. KEY WORD SHOULD lol

---

### Post by n0c0d3 on 2014-03-24
> **slooksterpsv said:**
> At least we have Windows back on there =Dl
Thats a bit overly optimistic. It is installing, but it's going to take a long time before it there in its entirety :-((

 > **slooksterpsv said:**
> Linux should be a breeze after that. KEY WORD SHOULD lol

Yes, it should be a breeze, if I don;t make stupid mistakes when I partition the rest of the drive. Maybe you could give me some advice. I want it as before: a part ext4 for Xubuntu of course, and an extra partition in NTFS format where I can store stuff outside of any OS. Those two will likely reside under the same extended partition. How should I go about to get this done when I install Xubuntu?

---

### Post by slooksterpsv on 2014-03-24
I'd create the partitions during the installation of Windows. So during the install you can create partitions as you please, so if you want Windows to have (lets divide up a 160GB drive): 80GB for the OS an apps, 40GB for your data and 40GB for Linux you could do that.

Lets say you had a 500GB you wanted to split:
300GB for Windows
140GB for Data
60 for Linux 

With Windows 7 and dual-booting with MBR you can only have 4 partitions. Windows, (windows will create a Q drive for it's own special purpose) so there's 2 gone, then you can only do 2 more, Data and Linux (and not have a swap drive).

---

### Post by n0c0d3 on 2014-03-24
My question was more about the technicalities of the formatting, just to make sure I do the right thing. I'm not going to do that now anyway. I've finished installing Windows (not updated yet, I want to do that after I've got Xubuntu up and running, not to waste time again). I'm currently looking for the drivers to make the cabled network-connection, usb3 and so on work. I want the basis to function. Xubuntu is for another day as well.

But my HDD is about 1TB, so I don't have to be picky. But 300G for Windows gives them a bit too much credit. I hardly ever use it anyway. On my Laptop it uses about 1G and I'm using that as file-storage as well, so if I give it 200 that's already giving it far more than it deserves. I want a 200 GB ext4 partition for Xubuntu (I always install far more than I actually use, just to see what it is, and then forget about it), the rest goes to the NTFS storage.
And for what I know Windows allows 4 primary partitions, but I can have more extended partitions. So couldn't I install Linux with its Swap on an extended partition, or another primary and the storage on another extended or something like that?
There must be a way around this restriction, and as long as dual-boot works I don't really care how it looks like. I just found this: [https://superuser.com/questions/58800/can-a-pc-with-1-hard-drive-have-5-partitions-be-able-to-boot-up-xp-vista-windo](https://superuser.com/questions/58800/can-a-pc-with-1-hard-drive-have-5-partitions-be-able-to-boot-up-xp-vista-windo) So as it can be done, but the question is what is the best way to do it...

---

### Post by slooksterpsv on 2014-03-24
You sure can install Linux inside an extended partition - that'll have to be the way you do it if you want more than 4 partitions.

As for the drivers you'll need to go here for the windows drivers: [http://esupport.sony.com/US/p/model-home.pl?mdl=VPCEB32FM&template_id=1&region_id=1&tab=download#/downloadTab](http://esupport.sony.com/US/p/model-home.pl?mdl=VPCEB32FM&template_id=1&region_id=1&tab=download#/downloadTab)


Best way to do the partitioning scheme is this:
In Windows run diskmgmt.msc (or search for). After that opens, right-click on the partition C: is on and choose Shrink. Shrink it down as much as you need for the setup you want your partitions to go - example:
1TB lets say you wanted 200GB for Windows. So shrink the 200GB for Windows and the 800GB unallocated.
Now create a partition in that 800GB for your Data drive (let's say 500) add that.
Leave the last part empty until you get into Linux.

It's been a while since I've done extended partitions, due to EFI, so that you'll have to research on how to do it during the installation, but you'll just be using the rest of the free space for the extended/logical partitions. You'll want at least 2GB for the swap. The rest for Linux (unless you want to split your home folder up too).

---

### Post by oldfred on 2014-03-25
Just to add my 2 cents to slooksterpsv which covers the issues.

I prefer smaller system partitions for both Windows & Linux. Then hard drive is not jumping all over drive for system, just for data which is not used as much.
But some Windows programs have to be in c: so you do have to make its system partition a lot larger. Plus Windows works best if the NTFS partition has at least 30% free.

Windows does require one primary partition to boot from. All other partitions can be logical. And it is important to use Windows to shrink Windows and reboot immediately so it can run chkdsk and make repairs. Also do not hibernate Windows if dual booting.
I suggest using no more than two primary partitions, use the third primary as the extended partition and make that the rest of the hard drive as the extended for as many logicals as you want. 
I do prefer to use gparted to create partitions, but then you have to use Something Else during install to manually select which partition is / and any others like /home. I do not think you can create the shared NTFS with the installer anyway and will have to manually edit fstab after install to auto mount it.

---

### Post by n0c0d3 on 2014-03-25
I'm still updating Windows... sigh... I didn't want to do it,yet, but it's something I can do at least partially while sleeping ;-)
The drivers are ready to download from the motherboard website. I've posted a link to it earlier. The driver-chapter was finished already before I started updating and all device-errors have disappeared already.
The shrinking of the Windows-volume can be done through the context-menu of the computer-icon on the desktop as well. I haven't looked into the specifics yet, so I don't know if I can make the data-partition primary from there. But is the following what you'd suggest?

HDD
> Primary: Windows (NTFS)
> Primary: Data (NTFS)
> Primary: - Xubuntu (Ext4)
                                  . . . . . . . - Swap

This is within the limits of 4 primary partitions. Of course I need dual-boot with Grub to work. Or should I create an extended partition for Xubuntu and Swap-space to accomplish that? If you don't know I'll search the web if I can find an answer. To be honest I haven't done that yet. But when I earlier put everything else apart from Windows on an extended partition it didn't work and I ended up writing ramblings in this thread. But then again, the drive had no MBR, but was gpt-formatted. Maybe the answer is on the UEFI-page of Ubuntu-help somewhere. I'll look into it when I have the time, but if you (or someone else) have an easy answer that would be appreciated.

Thanks,
Bart

---

### Post by oldfred on 2014-03-25
Windows does not convert from gpt to MBR when it installs in BIOS boot mode.
It leaves the backup gpt partition table and all Linux tools see the backup gpt and MBR and get confused on what you have or want to have and just fail.
You have to either install Windows in UEFI mode, or completely removed the old backup gpt partition table. You can use fixparts to remove gpt data. You may still have that, if you have not yet removed it.

FixParts is the easiest way to remove the stray GPT data. GPT fdisk (gdisk or sgdisk) can do it, but the procedure's a bit more involved.
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

I prefer not to use all primary partitions. Best to make at least ext4 & swap be in extended as logicals. Optional if NTFS data partition is also in extended.

---

### Post by n0c0d3 on 2014-03-25
I don't understand anything of it anymore and I think I'm one of the utterly confused. I used the "msdos" option when dis-allocating all the partitions on the drive before installing Windows. Why would there now even be any backup GPT table? Or does that just not remove this GPT backup-table? But okay, even though I don't understand I'll give it a go.

I tried to run fixparts on windows, but there seems to be some dll missing. I'm still in the midst of this seemingly infinite update and reboot loop (the number of updates I get every time are decreasing so I think I'm heading towards the finishing-line), so I'll check out if it works from the Xubuntu LiveCD after that's finished and I'll see if I can remove these gpt stray backup bastards from there.

And when that's done you propose this partitioning scheme?

> Primary: Windows (NTFS)
> Primary: Data (NTFS)
> Extended: - Linux (ext4)
 . . . . . .  . . . - Swap

And to get to there I shrink the Windows partition and create the primary Data-partition from within Windows. Then from the Xubuntu-LiveCD I use the advanced options (or whatever they're called) to create an extended partition on the unallocated space and create an ext4- and swap-partition in that  and install Xubuntu on the ext4 part,. And then we start feasting, get extremely drunk, wake up with a hangover but live happily ever after with a grub menu that recognizes Windows and Ubuntu, while still booting from DVD if I need to? Please correct me when I've got something wrong.

Thanks,
Bart

---

### Post by oldfred on 2014-03-25
Be sure to use Windows tools to shrink Windows and reboot so it can run chkdsk and make whatever repairs it likes to do for its new size.

Just do not mix up order of things. Partitioning while drunk or with a hangover can lead to major issues. :)

---

### Post by n0c0d3 on 2014-03-25
I know I have to reboot Windows after resizing partitions not to confuse Windows too much. Me being confused is already bad enough. And when I use the partitioning and resizing-method slooksterpsv (and I) already described I suppose nothing much can go wrong. But I'll create a bulleted checklist list to make sure I follow the right sequence. Maybe I should assign someone here the important task of supreme overseer with the checklist printed out and checkmark every step I take ;-)

---

### Post by n0c0d3 on 2014-03-25
Okay, I finally got to the gpt-backup removal part. I booted the Xubuntu LiveCD, installed fixparts (ignoring the warning that this is badly coded software, or something like that).
But, at least to me, the mystery deepens. This is what I got, and I don't have a clue what to do next:

> 
xubuntu@xubuntu:~/Desktop$ sudo fixparts /dev/sda1
FixParts 0.8.8

Loading MBR data from /dev/sda1

Problem: MBR partitions 1 and 2 overlap!

Problem: MBR partitions 1 and 3 overlap!

Problem: MBR partitions 1 and 4 overlap!

Problem: MBR partitions 2 and 3 overlap!

Warning: 0xEE partition doesn't start on sector 1. This can cause problems
in some OSes.
Warning: Deleting oversized partition #1! Start = 1936269394, length = 1836016416
Warning: Deleting oversized partition #2! Start = 1917848077, length = 544437093
Warning: Deleting oversized partition #3! Start = 1818575915, length = 544175136
Warning: Deleting oversized partition #4! Start = 2844524554, length = 54974

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 1953519616 sectors (931.5 GiB)
MBR disk identifier: 0x6E697373
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code

MBR command (? for help): 


It doesn't make sense to me. Overlapping MBR's and there's no partition-table when I use the Print option, and no sign of any gpt table as far as I am able to recognize it.
So it looks like I have to delay my binge until someone can help me out on how to interpret this and advises me what to do.

I added a screenshot of Gparted of how that says the disk looks like.

Bart

---

### Post by oldfred on 2014-03-25
Not sure what you have done.
You run fixparts on a drive like sda not on a partition like sda1.

[B]sudo fixparts /dev/sda

[/B] But every partition also has a PBR or partition boot record that is similar to a drive's MBR.

---

### Post by n0c0d3 on 2014-03-25
I'm sorry. That's what the website says I should do as well, but it gave me only little information, but then I didn't try the "print" command. This is what it says with the print-command:

```

xubuntu@xubuntu:~/Desktop$ sudo fixparts /dev/sda
FixParts 0.8.8

Loading MBR data from /dev/sda

Warning: 0xEE partition doesn't start on sector 1. This can cause problems
in some OSes.

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 1953525168 sectors (931.5 GiB)
MBR disk identifier: 0x0009FCF6
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048   1953521663   primary     Y        Y      0x07

MBR command (? for help): 
final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 1953519616 sectors (931.5 GiB)
MBR disk identifier: 0x6E697373
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code

MBR command (? for help): 



```

I still can't see anything about gpt-tables or anything, besides some warning that "0xEE partition doesn't start on sector 1", let alone what I should do now, or if there is anything to clean. The website isn't of much help to me either.

Bart

---

### Post by oldfred on 2014-03-25
It is not showing any gpt data. But it shows NTFS partition correctly so I would do the w just to be sure.
Then I would expect installer to see Windows correctly.

---

### Post by n0c0d3 on 2014-03-25
I w-ed and that seemed to have gone without errors, booted Windows (was OK), booted from Xubuntu-Live again and checked fixedparts again. This is what is says:

```

xubuntu@xubuntu:~/Desktop$ sudo fixparts /dev/sda
FixParts 0.8.8

Loading MBR data from /dev/sda

Warning: 0xEE partition doesn't start on sector 1. This can cause problems
in some OSes.

MBR command (? for help): p

** NOTE: Partition numbers do NOT indicate final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 1953525168 sectors (931.5 GiB)
MBR disk identifier: 0x0009FCF6
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048   1953521663   primary     Y        Y      0x07

MBR command (? for help): 
final primary/logical status,
** unlike in most MBR partitioning tools!

** Extended partitions are not displayed, but will be generated as required.

Disk size is 1953519616 sectors (931.5 GiB)
MBR disk identifier: 0x6E697373
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code

MBR command (? for help): 

```

Is everything okay to finally get onto installing Xubuntu now? I sure hope so...

---

### Post by slooksterpsv on 2014-03-26
EDIT: Wrong thread post again haha I'm so sorry!

---

### Post by n0c0d3 on 2014-03-26
Was this last post meant for me? There are no partition"S", there is supposed to be only one. And I think that partition is somehow recognized, at least by this program oldfred recommended:
```

Disk size is 1953525168 sectors (931.5 GiB)
MBR disk identifier: 0x0009FCF6
MBR partitions:

                                                   Can Be   Can Be
Number  Boot  Start Sector   End Sector   Status   Logical  Primary   Code
   1      *           2048   1953521663   primary     Y        Y      0x07

```
(I just learned I should use the code-tags, not the quote-tags to keep the spaces.)

And Gparted, from within Xubuntu, sees the partition.

But for the rest you are right. 
But boy oh boy, what fun I had. Windows had another trick up its sleeve do maintain its dominance and wouldn't let me shrink the partition and wanted to keep half of the HDD for itself. This because of unmovable files and files that didn't want to be moved. But finally I got this solved.
Then I tried to install Xubuntu, but the installer didn't recognize Windows. I tried to install anyway on Ext4, but no joy, because no Grub when rebooting. The PC booted right from Windows again. When I checked the partitions in Gparted (before rebooting) the Ext4 and Swap showed up as extended, but when I check them in Windows they both show up as primary. When partitioning them with the Xubuntu-installer I set them both to "Logic". But by now I can't see the logic of it all anymore (if I ever could anyway). Maybe it's all just quantum-weirdness ;-)

I deleted both Ext4 and Swap from within Windows and tried the Xubuntu-installer again to see if there's something I might have missed again, but again, it doesn't see the Windows partition.

And I ran chkdsk, but when I blinked my eyes it was finished and couldn't see the results. The rest of your message doesn't really make sense to me, as if it's not meant for me.

What should I do next? 

Thanks,
Bart

Edit:
Couldn't the problem lie in this:
```

Warning: 0xEE partition doesn't start on sector 1. This can cause problems
in some OSes.

```

---

### Post by oldfred on 2014-03-26
Do not use Windows partition tools on Linux partitions.
Use Windows partition tools only to shrink Windows and use gparted for anything else.
Windows never shows Linux partitions correctly, newer versions now see a partition but show it as empty and often Windows rewrites partition tables incorrectly.

If gparted or installer do not see Windows it may be that Windows still needs chkdsk, you often have to run it more than once or until no errors. Or you are leaving Windows hibernated. If Windows 8 fast boot means it always is hibernated.

You do not want the first partition to start at sector one. Not sure why you get that error. Normally chkdsk updates Windows PBR or partition boot sector which has to have same info on start & size of partition as partition table. Normal start of partitions now is sector 2048 to accommodate SSD & new 4K drives. Vista changed to that from XP's start of sector 63. Linux did not really change partitioning from 63 to 2048 until about the time Windows 7 came out.

If grub does not install correctly, use Boot-Repair to reinstall grub to MBR.
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

If any auto install options do not show Windows, create partitions in advance with gparted and use Something Else or manual install. I prefer manual install anyway since then you control size & locations of partitions. Also a bit easier with gparted.

---

### Post by slooksterpsv on 2014-03-26
EDIT: I posted this to the wrong thread hahaha.

---

### Post by n0c0d3 on 2014-03-26
I've been searching and came across a tool called testdisk. I remember to have used it before for some other problem. I'm running it from within Windows. I chose "create" (a log), "intel/PC" or something like that. Then a report showed a partition starting from 0. I'm currently running a deep search, which is taking some time.
If someone can advice me on how to use it correctly and interpret its results that would be helpful.
I'll post the results of the deep scan later.

Edit:
Sorry, I somehow didn't get a notification of your replies and didn't read them yet. I'll be on them now.

---

### Post by slooksterpsv on 2014-03-26
I apologize for posting my update in the wrong thread, I've been attempting to help on too many items huh =P

EDIT: I had to fix like 2-3 posts here sorry I'm so sorry

EDIT2: In response to the last comment:
TestDisk is amazing it will find files, folders, partitions, etc. which you can then restore that data to either the same drive or another drive.
After it's done scanning it should give you a list of what it can recover. There should be an option for files. What was it specifically you were trying to recovery (NOTE: SOME OF THE FILE NAMES MAY NOT BE ORIGINAL NAMES).

---

### Post by n0c0d3 on 2014-03-26
> **slooksterpsv said:**
> I apologize for posting my update in the wrong thread, I've been attempting to help on too many items huh =P

EDIT: I had to fix like 2-3 posts here sorry I'm so sorry

EDIT2: In response to the last comment:
TestDisk is amazing it will find files, folders, partitions, etc. which you can then restore that data to either the same drive or another drive.
After it's done scanning it should give you a list of what it can recover. There should be an option for files. What was it specifically you were trying to recovery (NOTE: SOME OF THE FILE NAMES MAY NOT BE ORIGINAL NAMES).

Can happen. I already thought that your posts had not much to do with the problem at hand here. Were you posting your replies meant for this thread somewhere else? ;-)

I thought testdisk was meant to find partitions and partitioning-errors. It's at 72% at the moment, so I think it's too far in to stop now. I'll check out boot-repair when testdisk is finished.

---

### Post by n0c0d3 on 2014-03-26
For what it's worth, here is a screenshot of the Testdisk deep scan result. Lots of Linux-entries that can't be recovered. 
[ATTACH=CONFIG]251490[/ATTACH]

I hope I don't have to run it again...

And you're right oldfred, I shouldn't have used Windows to remove those Linux-partitions. My bad. From the LiveCD Gparted shows that area as extended/unallocated, with a mdsos partition table.

I created a boot-repair info-summary: [http://paste.ubuntu.com/7159301](http://paste.ubuntu.com/7159301)

---

### Post by n0c0d3 on 2014-03-26
I accidently made "repairs". I thought the Reccomended repair button would show me what was about to be repaired, but it started doing things right away. I rebooted (Windows as well), no bad things happened. I made a new Boot Repair summary:
[http://paste.ubuntu.com/7159442](http://paste.ubuntu.com/7159442)

Edit:
Apart from the first line there seem to be no differences between those two reports. But there seems to be something installed, some bootloader:
```
=> Syslinux MBR (4.04 and higher) is installed in the MBR of /dev/sda.

```

Does this mean I can make another attempt at installing Xubuntu? I just tried the LiveCD (from the Xubuntu desktop) to see
if Windows is recognized now, but it isn't.

---

### Post by oldfred on 2014-03-26
The syslinux boot loader is a Windows type boot loader to boot Windows. It is just open source so Boot-Repair can use it where if you want the official Windows boot loader you have to use your Windows repairCD or flash drive.

It seems to say you booted Boot-Repair in UEFI mode, but drive is MBR(msdos) and Windows is in BIOS boot mode. From MBR drives you can only boot Windows and Ubuntu in BIOS mode. 
But if you boot Ubuntu in UEFI mode it may try to convert drive to gpt and wipe Windows. Windows will only boot in UEFI mode from gpt drives but has to be installed in that mode.

You need to boot installer in BIOS/Legacy/CSM or whatever is not UEFI with your system. How you boot installer is how it installs or you must boot in BIOS mode to install in BIOS mode.

---

### Post by n0c0d3 on 2014-03-26
> **oldfred said:**
> You need to boot installer in BIOS/Legacy/CSM or whatever is not UEFI with your system. How you boot installer is how it installs or you must boot in BIOS mode to install in BIOS mode.

How do I do that?
But I thought everything was already MBR after deleting all partitions with that msdos-flag before I installed Windows again.
I've got the feeling we're somehow running around in circles and I just don't know what to do to get out of this.

Maybe I should just wipe the drive, forget about Windows and dual-boot and only dump Xubuntu on it in whatever BIOS or UEFI-mode it chooses to install itself in, even though I've had other computers running dual-boot without any problems before, and sill am. But now there seems to be no solution, or I just don't understand how what you tell me can solve things and how to translate what you tell me into a practical solution. I'm ready to throw in the towel.

---

### Post by oldfred on 2014-03-27
Some examples:

---

### Post by n0c0d3 on 2014-03-27
Yay! I think I fonud them. Earlier I said no such setting are not in the boot-menu, but now I think I found them. They're in the Windows 8 Features., out of which I can choose between two Win8 settings and "Other OS". It currently is set to "Other OS", so I don't think this should be changed.

The entry I presume we need is called "Boot Mode Selection". The options I get are:
* UEFI and Legacy
* Legacy Only
* UEFI Only.

It is set to"UEFI and Legacy".  Should I make this setting "Legacy Only" to boot in BIOS-mode? And if the answer is yes, can I then install Xubuntu right away, or must there be some stray/backup partition-tables removed again?

I also have a "Storage Boot Option Control" which can be set to Disabled, UEFI Only, Legacy Only, Legacy First, and finally "UEFI First". This one is set to "Legacy Only".

Then I have "Other PCI Device ROM Priority", which gives the options "UEFI opROM" and "Legacy opROM", which is currently set to the UEFI-option.

Should I change the last one to "legacy" too, or does this one not matter for the issue at hand?


Thanks again.
Bart

---

### Post by oldfred on 2014-03-27
One user recently posted that his USB ports were set to UEFI only and his USB keyboard did not work.

You have to decide whether you want the 35 year old BIOS with MBR partitioning that is well known but very old and will have less support in the future. Or if you want the somewhat newer UEFI which it the future but many updates still being released by both hardware vendors and Linux developers. UEFI is from early 2000s, but not really used until Apple adopted it for all new systems with Intel chips and Windows with Windows 8 and all the issues of secure boot.

Then I would make settings in UEFI/BIOS match how you install systems.
I think your legacy opRom is this:
 UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 
They add another ROM chip for the BIOS. 
In a few years after users will not want or need BIOS, they will eliminate the extra BIOS chip to save a few pennies and then BIOS will not be available. This already is part of UEFI as class 3 version and a few new systems are configured as class 3 devices.

---

### Post by n0c0d3 on 2014-03-27
I think what I want is not really the issue at hand, even though of course I want to have an up-to-date system which will have no update/upgrade issues in the foreseeable future. In that case I think I should choose UEFI. But in the end what matters most is what works. You advised me earlier to use (legacy) BIOS/MBR. And I do not really have to consider whether my next PC has a BIOS-chip either at the moment. But if installing in UEFI-mode involves installing Windows from flash/USB-drive, then I'd prefer to use BIOS.

There are some other things to consider in the case Windows can be installed from DVD in UEFI Only-mode:
- Does Windows need to be installed again, or can I just set the boot-menu option to EUFI-only and install Xubuntu?
- If Windows has to be installed again: I had problems shrinking the Windows partition to make room for the rest. Can I install Windows on the current partition without it hijacking the entire HDD again?
- Do I need to remove the MBR-partition table first, (or completely reformat the drive), before installing Xubuntu, or maybe even before re-installing Windows if that is necessary?

There might be other things, but I can't come up with any at this moment.

And about the other settings. You advice me that the last two settings regarding BIOS/UEFI should follow the "Boot Mode Selection" setting. Now they seem to contradics each other in two settings as the "storage" option is set to "Legacy", while the "PCI Device Priority" is set to UEFI. The latter is a priority-setting, so it might switch mode when it doesn't find the option it is set to, so this might not matter all that much.

I hope you can answer these questions, and hopefully concoct some  step-by-step instructions as I've asked for earlier. This UEFI stuff is  entirely new territory for me and I have no clue to what implications  changing to "UEFI Only" will have, as as far as I know now the HDD is  formatted in BIOS/MBR format with that msdos-flag in Gparted.

Thanks, I highly apprciate the time you spent helping me,

A highly puzzled
Bart

---

### Post by oldfred on 2014-03-27
I cannot help specifically on all your UEFI settings. That varies so much by vendor, it is difficult to keep track. I had to take photos of my old BIOS system to remember my changes as every update to BIOS reset to defaults which did not work with my system.

I suggested BIOS only because Windows 7 DVD only installs in BIOS mode. You have to convert to flash drive and make some changes to make it work with UEFI. So with only DVD you can only use MBR and BIOS boot. Then you must install Ubuntu in BIOS mode to easily dual boot. And then could only install Ubuntu in UEFI mode on another drive as UEFI requires gpt partitioning and BIOS requires MBR(msdos) partitioning. Ubuntu will also boot in BIOS mode from gpt but Windows will not.

So to not reformat, not convert Windows DVD to flash and not reinstall, you need to boot and install Ubuntu in BIOS boot mode. 

You probably then need all settings in legacy or a dual mode, but not UEFI only mode in UEFI/BIOS. Many have posted screens with Ubuntu USB flash drive showing both UEFI and CSM/BIOS/Legacy or whatever it calls a mode that is not UEFI. Ubuntu configures system to boot either way.

---

### Post by n0c0d3 on 2014-03-27
I don't think not using UEFI will have such negative effects that it will limit my use or run into problems in the foreseeable future. (Do you agree?), so BIOS it will be as far I can see the consequences.

Now what should I do? This is what I think (there are questions as well):

1) Set the boot-settings and the other two before mentioned settings to "Legacy" (and check if Windows boots).
2) Check if the Xubuntu-LiveCD boots and now recognizes Windows. Or should I remove any backup/stray UEFI partition-tables again with that utility you asked me to use before?
3) Should I pre-format the extended partitions with Gparted to Ext4 and swap before installing Xubuntu, or can I create logic Ext4 and swap partitions in the current extended non-allocated space with the LiveCD?
4) Install Xubuntu.
5) Check if Everything is in working order (Grub-menu, Windows boots, Xubuntu boots)
6) Do the feasting. Get over my hangover and start using and adjusting Xubuntu to my liking.

I hope you can answer the questions. And is the order correct, is there anything to add? 

Bart

---

### Post by oldfred on 2014-03-27
That should work.
So check that Windows boots.
You should only have to remove old gpt partition table once. Then drive will be MBR(msdos).

I do prefer to partition in advance, but I always want more than the default / (root) & swap with its auto sizing. But then you also have to use Something Else or manual install and choose which partition is /. If swap exists it finds it. It also speeds install slightly as it will use an existing swap.
I also like to have a shared NTFS data partition which you cannot create during install. Either before or after install if you want that also.

---

### Post by n0c0d3 on 2014-03-27
OK. I'll be onto int in an hour. I must do some other things now. Life goes on...

But one more thing: I think I should run this utility tyo remove those backup/stray boot-tables (fixparts, you told me to use earlier, in page 4 of this thread) from within the LiveCD before installing Xubuntu and creating the Ext4 ans Swap partitions? I think the other way around would be illogical (but I'm not the one to tell what's logical here). Is this correct?

And in the past I always used the Gparted LiveCD to create Linux-partions and it never gave me problems as far as I can remember, so I'll use it this time as well. I already have this Data partition (NTFS, and I think its primary). Windows has 175GB and I'll assign Linux about the same amount, which is the space currently left.

Bart

---

### Post by oldfred on 2014-03-27
No once fixparts has removed backup gpt partition table, you should not have to run it again.
And Ubuntu installer then should see Windows unless Windows has other issues or hard drive was also RAID at some point.

---

### Post by n0c0d3 on 2014-03-27
Okay, everything went fine, even Windows was recognized this time, until the last moment: After installing Xubuntu Xubuntu I rebooted and I still do not get the Grub-menu.
I took note of every step along the way. Here's the log:

- Set all boot-options to "Legacy" (Windows boots nicely)
- Reboot out of Windows with Xubuntu LiveCD: Windows is recognized!
- Quit LiveCD, then reboot in Gparted LiceCD
- Created Ext4 (sda5) and Swap (sda6) on extended partition
- Reboot Windows: OK
- Reboot Xubuntu LiveCD: Install Ubuntu -> Windows still recognized -> Something else -> Select the Ext4 partition -> Change (otherwise the mount point can't be selected), Ext4 and Mount point "/", "Format the partition" not checked.
- Select ext4 again, install Xubuntu.
- After install reboot: NO GRUB!!! Boots directly into Windows...

It's already one big leap forward that Windows is recognized. How can I have missed that option in the boot-menu in the first place...???

But now what? Should I have chosen the option to install alongside Windows after all, or can I install Grub separately or something like that?

Bart

---

### Post by oldfred on 2014-03-27
If you use manual install you need to choose correct location for grub. It defaults to sda, which should be correct. Did it give an error?
I am over installing on a partition on sdc, but combo box at bottom still says sda.

Often Boot-Repair is easiest way to reinstall grub2 to MBR.
       Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

 How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System](https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System)

Also this is a newer system? If so you may also have video type issues. I have to use nomodeset with my nVidia. But Intel often needs different boot parameters.

If you have nVidia this is how I do it. Other boot parameters are instead of nomodeset.
 On first boot after install, press e on getting the GRUB bootloader menu. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode), install nVidia driver suggested my Ubuntu

 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

---

### Post by n0c0d3 on 2014-03-27
Yippeeayay, a Major Update!!

I installed Xubuntu again, right over the previous Xubuntu-installation, as the installer opted me to choose. And guess what?

IT ALL WORKED!! I got a Grub-menu, Windows boots and sees all (NTFS) partitions are accessible. The same in Xubuntu.

Well guys, slooksterpsv and oldfred, thank you very very much for your help and persistence. It was really strange and foolish of me not to have seen those "Legacy/UEFI"-settings in the boot-menu earlier on. If I would have seen them I think this all would have been resolved much earlier.

I consider this issue solved.

Thanks again guy!
Bart

---

### Post by n0c0d3 on 2014-03-27
Oldfred, our posts crossed. It already worked by simply installing again, as I've described in my previous post.

Thanks for your help man!

Bart.

Edit:

No, I didn't get any error during that install (and fortunately not one during the last install either). I have an Intel on-board video-card.

---

### Post by oldfred on 2014-03-27
Sometimes Intel needs settings, but it sounds like yours works. 
Glad you got it working. :)

If you end up with other issues start a new thread with issue in title to attract those who may know that issue.

---

### Post by n0c0d3 on 2014-03-27
I'm glad for sure as well, after almost a week. I may be back soon because before I've never been able to figure out to share files over a network and how to set up a FTP-server. But these are of course for another category and another thread.

---

