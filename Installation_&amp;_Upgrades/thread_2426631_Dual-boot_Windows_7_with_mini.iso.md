---
title: "Dual-boot Windows 7 with mini.iso"
date: 2019-09-11
forum: Installation &amp; Upgrades
---

### Post by Clueless Wonder on 2019-09-11
Hello!  I attempted my first dual-boot install and am not getting the grub boot menu.  Any help would be much appreciated.

My machine is a Dell Optiplex 3010 running Windows 7.  I first shrunk the partition from within Windows to make room for the Ubuntu install.  Then, using the mini.iso (18.04), I went through the steps, manually partitioning the freed space to allow for /, home, and swap.  I selected nothing in the Task-sel list as I want to install LXDE-Core afterwards. Then, when it got to the bootloader step, I choose manually the option of my Sata hard drive (vs the USB I was doing the install from), which was sda.  There were only the two choices.

After I restarted, it went directly to Windows.  When I choose Restart, so I could check the BIOS, Windows informed me it need to do some updates.  I then went to BIOS to check some settings (I don't have expertise in BIOS) and saw that the Boot Sequence showed Legacy (not UEFI) selected (if that helps explain what is the problem).

Is the problem due to that I am using mini.iso and didn't install a DE?  Is there a way to now access Terminal so that I can install the DE?  Or is it possibly something else?

I have tried to give all the info I am aware of and realize I may be missing some things.  Please let me know if you need any other information and thanks so much for reading!

---

### Post by yancek on 2019-09-11
Is your windows 7 a default Legacy/dos install?
Or is it an EFI install?
Did you install Ubuntu in Legacy mode or EFI?
Yo need both OS's the same.

You can boot the install usb and open a terminal and run this command and post the output here to get help:  ```
sudo parted -l
```
That's a lower case Letter L in the command.

If you have only one hard drive (the sata you refer to) you would install the Grub bootloader to /dev/sda.

Did you read the instructions at the Ubuntu site below on installing using the mini.iso?

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

---

### Post by Clueless Wonder on 2019-09-12
Hi Yancek!  Thanks for the reply.  I didn't receive a notification, so I didn't know I had a reply.  

I am not sure if the Windows 7 is a default Legacy install.  A friend gave me the PC.  I am thinking maybe so because when I go into BIOS, Legacy is already selected and I see the Boot Order options.  If I select, EFI, they all disappear.  Does it sound like it is Legacy from that information?

When I installed from the Mini.iso, I didn't go into BIOS and change anything.  Does that mean it installed in Legacy?

Can you tell me how I can open a Terminal from booting the Mini.iso install USB?  I haven't done that before.

And, yes, I did read the instructions and have successfully installed before from the Mini.iso...just not a dual boot.

Thanks again for your help!

---

### Post by mastablasta on 2019-09-13
quite possible that it is in legacy. this can be confirmed if you run boot info script and get a report : [https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

mini iso doesn't do UEFI.

> **mini system in UEFI mode**

[COLOR=#333333][FONT=Ubuntu]While the minimal iso image is handy, it isn't useful for installing on UEFI-based systems that you want to run in UEFI mode. The mini iso lacks the proper files for booting the computer in UEFI mode. Thus, the computer will boot in BIOS compatibility mode, and the installation will be in BIOS mode.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]You can use an **Ubuntu Server amd64 iso file** (64-bit) for 'mini installations' in UEFI mode. There is a compressed image file **dd_text_16.04-UEFI-n-BIOS-4-pendrive-7.8GB.img.xz** of such an installed system, that can be used as a start of a custom installation.[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]See this link: [/FONT][/COLOR][Installation/UEFI-and-BIOS/stable-alternative]("https://help.ubuntu.com/community/Installation/UEFI-and-BIOS/stable-alternative")[COLOR=#333333][FONT=Ubuntu].[/FONT][/COLOR]

---

### Post by Clueless Wonder on 2019-09-13
Hi MastaBlasta -

thanks for the detailed reply.  Living up to my username, I must admit I know nothing about UEFI or Legacy.  In fact, this is the first computer I have had newer than 2003 and hadn't seen those options before in BIOS.  I did a bit of research and tried what you recommended.  Using a USB drive with Lubuntu on it, I chose the Live option and got an error message of Uncompression Error....System Halted.  I did some research on that and there appears to be a lot of possible causes for that.  So, I then tried a Puppy CD I have and was able to get to the desktop.  I opened a terminal and typed 
sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt-get update.  I returned with Command not Found for 
add-apt-repository, which I am guessing is because I am using Puppy and not Ubuntu.  So...I am thinking to try to make
an Ubuntu CD and see if I can boot with that.  If/when I am successful, I will report back.

One other question...I really like using mini.iso and the server file directions look really complicated.
Is there any drawback to just staying in Legacy?  How do I designate which one I am installing to?  I didn't see any
questions pertaining to Legacy or UEFI during install of the Mini.iso.  Is it something I need to make sure is 
set in BIOS prior to install?

And Yancek (or Mastablasta, if you know) - when I was booted in Puppy, I ran the parted -l command.  I wasn't
able to figure out how to copy and paste at the time (hope to do that later), but noticed that the Windows partition
had Bootable Flag with a Y and the Ubuntu partition did not.  I didn't choose it (I usually do, but wasn't sure
if I should in the dual-boot process).  Could that be the problem?  Could it be as simple as reinstalling and choosing that?

Thanks to you both!

---

### Post by oldfred on 2019-09-13
I do not think mini.iso supports UEFI.
You can add UEFI support.
[https://ubuntuforums.org/showthread.php?t=2419997&p=13862419#post13862419](https://ubuntuforums.org/showthread.php?t=2419997&p=13862419#post13862419)

How you boot install media, UEFI or BIOS is how it installs. 
You get UEFI & better driver support if you install the server ISO, and then you can choose to not install any server software and install whatever other software you want.

Lots of links on UEFI info in link in my signature.

---

### Post by Clueless Wonder on 2019-09-14
I am able to boot with another Lubuntu USB I have.  However, I can't get a wired internet connection.  I think this is too much effort to maintain a Windows 7 dual boot.  I think I will reformat, wipe out Windows 7 (which I don't really have any interest in), and just install from the mini.iso.  

OldFred, I would prefer to keep this simple and Legacy is fine for me.  Can I install the mini.iso 64-bit on Legacy?  How do I make sure it is going to Legacy and not UEFI?   Is it just a matter of going into BIOS, make sure Legacy is selected, and then reboot and install?

Thanks again!

---

### Post by oldfred on 2019-09-14
How you boot install media from one time boot key in UEFI/BIOS is how it installs.
Most installers will have two boot modes in boot menu for flash drive if UEFI Secure Boot is off and allow USB boot.
If using CSM/BIOS/Legacy mode, you have to have UEFI secure boot off.

And if mini.iso only has BIOS mode, you should only get the BIOS boot option.

You can use the newer gpt partitioning if not installing or having Windows in BIOS boot mode. Windows in BIOS mode must have MBR partitioning. 
If you use gpt with BIOS, you must also have a tiny 1 or 2MB unformatted partition with bios_grub flag for grub to install correctly. 

       GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

---

### Post by Clueless Wonder on 2019-09-15
Hi Old Fred -

thank you for your detailed and thorough answer.  There is a wealth of knowledge in your post that I am enjoying reading through.

I apologize for my ignorance...can you clarify what you mean by "one time boot key"?  I have been working with Lubuntu and mini.iso for years, so have some experience, but it is all with old computers.  This is my first computer that has UEFI as an option.

Also, as I mentioned a few posts earlier, I ran the parted -l command and noticed that the Windows partition
had Bootable Flag with a Y and the Ubuntu partition did not.  I didn't choose the Boot Flag option during the mini.iso install process (I usually do, but wasn't sure
if I should in the dual-boot process).  Could that be the problem of why I didn't get the grub menu?  Could it be as simple as reinstalling and choosing that?

---

### Post by yancek on 2019-09-15
When you want to boot from a DVD or USB rather than the hard drive, you access the BIOS setup to select a different boot option; DVD or USB which will or should boot the DVD or USB one time.  It is not a permanent change.

You can only have one partition marked with the boot flag and this is necessary for a windows OS and not for any Linux, at least any Linux I have ever used.  It should make no difference in your case.

---

### Post by mastablasta on 2019-09-16
the major difference between server and mini iso is the iso size. so some files are already included in the server version that are missing from the bare bones / mini version. since they are included they help the PC boot kernel that can use those items.

as mentioned just like in mini iso you also can select what to install in server iso. so you can just add windows manager and display manager for an easier load ([https://en.wikipedia.org/wiki/X_display_manager](https://en.wikipedia.org/wiki/X_display_manager)).

---

### Post by Clueless Wonder on 2019-09-16
> **yancek said:**
> When you want to boot from a DVD or USB rather than the hard drive, you access the BIOS setup to select a different boot option; DVD or USB which will or should boot the DVD or USB one time.  It is not a permanent change.

You can only have one partition marked with the boot flag and this is necessary for a windows OS and not for any Linux, at least any Linux I have ever used.  It should make no difference in your case.

Thanks Yancek.  I am aware of the BIOS set-up change for accessing USB, but didn't realize that was what Old Fred was referring to when he said "one time boot key."  Thanks for the clarification.  And, also for answering my question about the bootable flag and how that isn't necessary with linux.

And thank you Masta Blasta, for the added information about server.iso vs. mini.iso.  It helps deepen my understanding of the two.

I think I have exhausted this topic and appreciate everyone's assistance.  I will now mark this solved.

---

