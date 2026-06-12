---
title: "I'm having problems reinstalling Ubuntu Desktop with a dvd?"
date: 2016-04-10
forum: Installation &amp; Upgrades
---

### Post by 1two3 on 2016-04-10
I have an Acer aspire laptop and I've already gone to bios and changed to legacy UEFI and made booting from DVD/CD first priority. 
I installed ubuntu desktop 14.04 64bit with LVM and encryption which I am considering to have been a bad choice because I'm having a lot of problems restarting/booting the computer and I have to disconnect any usb devices during booting and it always takes me to the grub2 menu and if I simply choose to boot Ubuntu then it gets stuck on a black screen. I need to either hit shift directly after choosing Ubuntu in the grub2 menu or press 'e' on the grub2 menu and change the letters 'ro' to 'rw'. When doing either of these methods, it is random chance that the computer successfully boots, sometimes I need to do this many times before it finally takes me to the PW field to decrypt the disk. 

That's why I want to try reinstalling without LVM and encryption incase this is what is causing the problems. 

But if I put the DVD that I burned Ubuntu to into the computer then at booting I get stuck on the first screen which is the Acer logo and a small text "Press F2 to enter settings.." F2 is where you go if you want to reach the bios etc. but it doesn't matter what I press, as long as I have the dvd inserted to the computer I'm stuck on the acer logo screen. 

I hope that someone will be able to help me :-)

---

### Post by mörgæs on 2016-04-11
Have you tried 15.10 or 16.04 (development)?

---

### Post by 1two3 on 2016-04-11
> **mörgæs said:**
> Have you tried 15.10 or 16.04 (development)?

Haven't tried those.. might be a good idea if I can't get 14.04 to work  without LVM and encryption but I think if I were to burn 15+ to a dvd  and insert it then I would probably have the same problem as I'm having  with the 14.04 dvd.. just stuck at acer logo startup screen.

edit: Oh, you mean maybe my only way out of this is to use Software & Updates to update to 15+? 
Good idea but would the LVM and encryption get removed if I were to make such an update? I kind of regret installing Ubuntu with LVM and encryption.

edit2: I've been googling about 16.04 and it says it's an LTS version but if it's an LTS then why is the latest LTS version still 14.04?

---

### Post by mörgæs on 2016-04-11
> **1two3 said:**
> I kind of regret installing Ubuntu with LVM and encryption.

Then a fresh install is the way to go.


> **1two3 said:**
> 
I've been googling about 16.04 and it says it's an LTS version but if it's an LTS then why is the latest LTS version still 14.04?

16.04 will be officially released in two weeks time so officially 14.04 is the latest LTS but there is no reason not to try 16.04 now, at least in a live boot. 

I recommend booting from USB, not from DVD.

---

### Post by 1two3 on 2016-04-11
How do I find the iso to burn to a DVD?
 I also only have one USB stick available to burn to that I already have an old tails os on, Do I just manually select all and delete them from the USB first before burning ubuntu 16.04 to it? 

On Ubuntus website I can only find Ubuntu Desktop 14.04 LTS and 15.10 non-lts. 
I tried looking in updates-manager after checking non-lts in Software & Updates and it downloaded some updates but it was just non-lts updates for 14.04 because after restarting the computer (which went perfect, I got a bit excited because it didn't even take me to the grub2 menu, just straight to the password field for decrypting the disk ubuntu is installed on. I thought the update fixed my booting problem so I tried shutting down the computer then starting it up again but on first try it got stuck on a black screen after the acer logo screen and before the grub2 menu screen. 
Second try I tried just selecting Ubuntu on the grub2 menu screen but it got stuck on black screen after that.
Third try I tried hitting shift directly after Ubuntu on grub 2 menu screen but got stuck again.
4th time I tried hitting 'e' and then changing 'ro' to 'rw' which doesn't always work but this time it did. 

So I still have problems with booting and I don't see any way to get Ubuntu Desktop 16.04 64bit?
If I google then there's some results about domains such as ubuntumaniac, ubuntu-mate etc but I would prefer downloading from an official source?

I hope booting from usb will work too when booting from DVD doesn't.

Edit:
I also don't understand why I have so much problems with Ubuntu? 
It's completely screwed up even directly after a very standard install of an LTS version?
I can't imagine I did anything wrong and my hardware shouldn't be causing a problem either I think?

Acer aspire latop
intel core i5
nvidia geforce GT 630M
8GB DDR3 Memory

---

### Post by oldfred on 2016-04-11
If you left fast boot on in UEFI, you may have issues getting into UEFI menu.
Fast boot is a new UEFI setting that skips all old UEFI/BIOS hardware and system changes. It assumes everything is exactly the same and immediately boots. Helps make for very fast boots, but may not give time to even press a key to get into UEFI.
Some just need to cold boot, if laptop you may have to remove battery. And hold power switch for 10 sec or so to drain any left over power.
Others have to jumper pins on motherboard. Some have a reset switch on bottom of case. And some have to remove coin battery on motherboard to totally reset.
If you reset or update UEFI/BIOS all setting are changed back to defaults. I had many setting I had to change, so I documented those.

Every two years a new LTS is released.
[https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

For 16.04 you have to download beta or daily which should be all the changes to date. It will not be on main page until released.
 Daily builds
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) 

Probably better to use UEFI.

 GPT Advantages (older but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)
UEFI Advantages
[http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604](http://askubuntu.com/questions/647303/uefi-or-legacy-which-is-advised-and-why/647604#647604)
[http://askubuntu.com/questions/446968/legacy-vs-uefi-help](http://askubuntu.com/questions/446968/legacy-vs-uefi-help)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface) 

But Acer are unique that they require UEFI supervisory password and setting trust on Ubuntu/grub UEFI boot files. But at least they support a way. Many vendors only boot Windows and we have to have a work around.

      
 Acer Very latest UEFI/BIOS works, downgrade not required:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer E5-573G, downgrade UEFI, supervisor password & trust on Ubuntu efi boot files.
[http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912](http://askubuntu.com/questions/706912/getting-a-black-screen-when-installing-or-live-booting-ubuntu-any-version-in-m?noredirect=1#comment1039248_706912)
Acer Aspire E15 will not dual boot, many details
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)
Acer Aspire E 15 Downgrade to older UEFI, password & trust (ACPI issues?)
[http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062](http://ubuntuforums.org/showthread.php?t=2298380&p=13403062#post13403062)
Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
One of several with more details:
[http://ubuntuforums.org/showthread.php?t=2297947](http://ubuntuforums.org/showthread.php?t=2297947)
[http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](http://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)

---

### Post by buzzingrobot on 2016-04-11
Just some guesses here, but...

Something seems to have gone fundamentally wrong with your current installation. Without access to the machine it's probably impossible to diagnose correctly.

One reason for seeing a black screen on boot, not the only reason, is a video driver problem. Ubuntu, like other Linux distributions, will use an open source driver for the video card the kernel detects on boot.  For Nvidia cards, that driver -- called Nouveau -- sometimes does not work correctly.  A workaround is to edit the grub2 menu and add "nomodeset" as a kernel parameter.  This should allow the machine to boot to a degraded, low resolution, but usable, display.  At that point you should install the proprietary Nvidia driver recommended in the "Additional Drivers" tool and reboot.

A machine will typically default to offering a prompt for the BIOS when it cannot locate an operating system where it expects to find one. So, be sure the BIOS  is configured appropriately, Boot without the DVD, enter the BIOS setup menu, and reset everything to the default settings. (There's typically a setting to do that.) "Save and Exit" and let it reboot and then re-enter the BIOS setup. Reconfigure carefully to support the non-UEFI legacy mode (may be more than one setting) and verify that you have set up the boot drive priorities as you wish.

Even if the boot problem happens still, you will have eliminated an incorrect BIOS configuration and a video driver issue as causes.

The system is most likely refusing to boot from the DVD and dumping you into the BIOS because it is either not finding the DVD drive at all or not finding a bootable image on the DVD.  It is also possible that an occasional hardware failure is happening. Or even that the actual DVD is not seating  correctly in the drive.  It's not possible to say from here.

Download a new install image, verify the checksum, burn it to either a DVD or USB stick, and try again. Personally, I see no real advantage to LVM on a single-drive installation.  Whether to encrypt the drive is your choice but it does add another layer of complexity when you are still trying to diagnose the problem.

When you do try an install again, detach all USB devices that are not necessary to support the install.

The 16.04 images are available at [http://cdimages.ubuntu.com/daily-live/](http://cdimages.ubuntu.com/daily-live/)  and will be available at ubuntu.com after it is released.  I'd be surprised, however, if the release version you use has anything to do with these issues.

---

### Post by 1two3 on 2016-04-11
My video card is NVIDIA GeForce GT 630M with 1GB Dedicated VRAM and the driver that's currently in use is the Nouveau one from x.org something. 
Hardware and this stuff is something I'm really not that good at so I don't know if it's correct when it says in my bios "Video memory: 128mb"? 

Because something else that's a problem with my ubuntu install that I didn't have before when I was using windows 8 is that now if I for example am watching youtube videos it sometimes slows down the computer massively, even after closing the youtube tabs it might not stop hogging the CPU, it's not a memory issue either.. it's definetely something about the CPU but this is secondary concern right now tbh, I just want to have booting working properly and be able to reinstall Ubuntu Desktop 14.04 64bit LTS without LVM and encryption. 

Just wanted to mention that. 

I also did as you suggested buzzingrobot and reset the bios settings and then I changed from UEFI to legacy bios and made boot from dvd #1 priority and the HDD as secondary priority. 
Didn't make any difference though. 

Had to reboot the computer 3 times before it successfully took me to the decrypt ubuntu password screen after the grub2 menu. 

oldfred's reply is a bit difficult to go through since it lists a lot of choices and I also am worried about opening up the laptop and removing battery etc because when I tried that before a year ago I somehow damaged the computer and had to get it repaired. 

One of his links suggest I should update the bios version to the latest, I'm worried about doing this too with the way I've been having so many strange problems, if the bios update would go wrong in anyway that would make my computer unbootable forever, I would have to buy a new laptop then, right? 

Here's all the info about my computer:

Acer aspire V3-571G
NVIDIA GeForce GT 630M with 1GB Dedicated VRAM
Intel Core i5-3230M 2.6GHz (3.2GHz)
8GB DDR3 Memory

bios info:
Video memory: 128mb
Quiet boot: enabled
Network boot: enabled
F12 boot menu: disabled
Supervisor pw: set (I have to type a password to enter bios)
secure boot mode: standard (can't edit this)
boot mode: legacy bios
secure boot: disabled
boot order: 
1. atapi cdrom : matshita dvd-ram uj8e1
2. HDD0
3. USB FDD
4. Network Boot
5. USB HDD
6. USB CDROM

bios version: 2.15
VGA bios version: Intel v2137
VGA bios version (peg): nvidia N13P-GL REV70.08.B9.00.0D

Do you the next step is to update my bios?
Can I have step by step instructions for this? Just in case because this is really scary to do :S

Oh, I also am not sure how to disable fast start up, when I google it says something about doing it from firmware but not sure what that is exactly.
I don't have windows installed on a dual boot or anything like that, I only have Ubuntu installed.

---

### Post by oldfred on 2016-04-11
You need to go to Acer for UEFI/BIOS updates.
[http://www.acer.com/worldwide/support/](http://www.acer.com/worldwide/support/)

Drill down to correct country & model number.
They should have instructions on updating UEFI/BIOS, but usually requires Windows, or a separate DOS bootable flash drive with update.

---

### Post by 1two3 on 2016-04-11
> **oldfred said:**
> You need to go to Acer for UEFI/BIOS updates.
[http://www.acer.com/worldwide/support/](http://www.acer.com/worldwide/support/)

Drill down to correct country & model number.
They should have instructions on updating UEFI/BIOS, but usually requires Windows, or a separate DOS bootable flash drive with update.

I downloaded it and read the readme.. It said must be installed in windows.. didn't mention anything about using a DOS bootable flash drive with update but I googled that and found this guide:

[http://www.howtogeek.com/136987/how-to-create-a-bootable-dos-usb-drive/](http://www.howtogeek.com/136987/how-to-create-a-bootable-dos-usb-drive/)

I'm just wondering if I'll even be able to boot the DOS USB Drive when I can't boot with a dvd inserted or if I have my iphone connected via usb i won't be able to boot either?

---

### Post by oldfred on 2016-04-11
If Acer does not have that option, not sure if Bootable DOS flash drive will work. Every vendor is different.

Most of my motherboards, allow three ways, Windows, DOS flash drive or even read directly from UEFI/BIOS a FAT formated flash drive with new file on it.

---

### Post by 1two3 on 2016-04-11
> **oldfred said:**
> If Acer does not have that option, not sure if Bootable DOS flash drive will work. Every vendor is different.

Most of my motherboards, allow three ways, Windows, DOS flash drive or even read directly from UEFI/BIOS a FAT formated flash drive with new file on it.

Sorry, I'm not sure what you mean?
If you mean why I'm not able to boot from DVD.. I used to be able to before I installed Ubuntu.. I don't know what Ubuntu has done to my computer but I can right now only do two things.. boot into ubuntu (sometimes need to restart several times and I also need to change 'ro' to 'rw' everytime which is annoying.. or if I eject my iphone usb and dvd then I can also boot into my bios settings.. but I'm not able to any more to boot from cd/dvd.. I would guess I would be unable to boot from USB as well especially since I can't have the iphone's usb inserted during booting.

---

### Post by oldfred on 2016-04-11
I have never rebooted with iphone plugged in.

But I have had USB change the old by device settings. On my desktop, I did not use SATA ports in order. So flash drive that was sdf when plugged in, would be sdb when I reboot. Since Ubuntu normally uses UUID, I could boot. But had to be careful on any commands using device like /dev/sdc, as which drive is it really?

---

### Post by 1two3 on 2016-04-12
I'm really sorry but I'm still not sure what exactly you mean.. keep in mind hardware and hardware settings and all these kind of things we are talking about is something I normally never have to bother with.. Everything I'm discussing about bios settings etc is the first time for me after doing some googling about it and so on. 

Can you try explain again?
What is it that you are suggesting that I do now? 
It sounded like a good idea to update the bios but I don't think it's possible since I need to be able to boot from USB DOS flash drive but since I can't boot the computer not even into bios settings when I have a CD/DVD or my iphone plugged in via usb then I feel quite pessimistic about that I will be able to boot the USB DOS Flash drive with updates after I made it.

---

### Post by 1two3 on 2016-04-13
I know everyone here most likely have busy lives with their work, family, etc so I really appreciate the time you give to help me :)

I'm just really stuck and it's almost as bad as I have to throw away this expensive laptop now because Ubuntu really screwed up my computer.
I'm a bit frustrated but mostly just sad, why don't Ubuntu put some big warning signs about how incompatible Ubuntu is and how much problems and difficulties there are to install??

Is there any more info I can give that could help? 
Or does no one here know what to do either? 
Is my only choice to throw away this computer and buy a new one? :(

---

### Post by mörgæs on 2016-04-13
You are already receiving plenty of help. 

Please state in detail how 15.10 and 16.04 works, installed and / or in a live boot. 

If you install then always do it from scratch, never do an online upgrade when you have problems.

Edit: Also, what is the purpose of booting with an Iphone attached?

---

### Post by 1two3 on 2016-04-13
> **mörgæs said:**
> You are already receiving plenty of help. 

Please state in detail how 15.10 and 16.04 works, installed and / or in a live boot. 

If you install then always do it from scratch, never do an online upgrade when you have problems.

Edit: Also, what is the purpose of booting with an Iphone attached?

I'm really sorry if I'm missing something really obvious here but how do I install 15.10 or 16.04? 
I need to burn the image on to a DVD or a USB HDD, right?
The problem is that my computer isn't able to boot when I have either of these things inserted in to the computer.

---

### Post by oldfred on 2016-04-13
If a new user, not sure you should have used LVM with encryption. I avoid it, as LVM to me is an advanced partitioning system and requires special tools (learning something more) and additional maintenance (although some fixed in 16.04).
Much better to use dual boot, so you can transition slowly. Some do suggest jumping into the deep end of the pool to learn to swim, but then we lose a few.

Did you backup Windows?
Or create the vendor recovery set of DVDs or flash drive?
Or check if Acer offers replacement set of DVDs, if you did not? Some do, some charge a nominal shipping charge and some do not offer anything.

Still not sure if you can boot flash drive to update BIOS. But you first need to update BIOS, or at least check that you have newest version. If you cannot boot flash drive then you will have to reinstall Windows from your backup, just to update UEFI/BIOS.

Have you tried the full power down reboot as detailed in post #6. Or checked other options to fully reset system?
Some of the other Acer threads may have more details as I have not followed every brand's detailed hardware settings. Most Acer will be the same or very similar UEFI.

---

### Post by 1two3 on 2016-04-14
> **oldfred said:**
> If a new user, not sure you should have used LVM with encryption. I avoid it, as LVM to me is an advanced partitioning system and requires special tools (learning something more) and additional maintenance (although some fixed in 16.04).
Much better to use dual boot, so you can transition slowly. Some do suggest jumping into the deep end of the pool to learn to swim, but then we lose a few.

Did you backup Windows?
Or create the vendor recovery set of DVDs or flash drive?
Or check if Acer offers replacement set of DVDs, if you did not? Some do, some charge a nominal shipping charge and some do not offer anything.

Still not sure if you can boot flash drive to update BIOS. But you first need to update BIOS, or at least check that you have newest version. If you cannot boot flash drive then you will have to reinstall Windows from your backup, just to update UEFI/BIOS.

Have you tried the full power down reboot as detailed in post #6. Or checked other options to fully reset system?
Some of the other Acer threads may have more details as I have not followed every brand's detailed hardware settings. Most Acer will be the same or very similar UEFI.

Is the windows back the file called vmlinuz.old? How do I do to reinstall it?
If I am successful with reinstalling windows with that backup, is there anything else besides updating bios and disbaling fast start up that you would suggest?

---

### Post by mörgæs on 2016-04-14
> **1two3 said:**
> 
I need to burn the image on to a DVD or a USB HDD, right?


No, the preferred way is a USB flash drive. 
It's not a guarantee that it works in first attempt (BIOS upgrade might be necessary) but worth a try.

---

### Post by oldfred on 2016-04-14
The vmlinuz.old is a link to the second newest kernel. Can be used to manually boot without having to use full vmlinuz which includes version numbers.

When you chose the full drive LVM with encryption install that erased everything on hard drive. Your own backups would be all that is available.
You should have made full backups of Windows. With my Dell it wanted both a Windows backup, and a Dell image for restore backup. And I also used Macrium for a full backup of entire system.

---

### Post by 1two3 on 2016-04-14
hmmm, so I'm kind of screwed then, right? :/
Last time turned on the computer I had to restart it something like 15 times before it finally took me to the password screen to decrypt the disk. 
And I seem to have a lot of problems like that CPU blockage that happens sometimes when I watch youtube even though I'm using the nouveau opensource video driver and I also can't seem to get Thunderbird working: [http://ubuntuforums.org/showthread.php?t=2320108](http://ubuntuforums.org/showthread.php?t=2320108) just to name two problems.. 
I really wish I would of just kept using windows.. Ubuntu is better but it seems you really need to get a computer that's "made" for having Ubuntu run on it.. in other words, Hardware components that are highly compatible made by the most Ubuntu friendly manufacturer.

---

### Post by oldfred on 2016-04-14
From the many Acer users that have posted, it seems Acer is one of the more friendly vendors. Post #6 with the minor issue that Acer requires trust but then works. Many vendors require more complicated work arounds.

Did you check with Acer to see if they will send you a recovery DVD set?

Since UEFI stores your Windows Product key you may be able to download generic Windows. But then with Windows have issues installing any proprietary drivers. Better to see if Acer has the recovery set.

 [http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)
      Microsoft Windows 8.1 reinstall/refresh
[URL="http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media"]http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media
      [/URL]Windows 10 ISO
[URL="https://www.microsoft.com/en-us/software-download/windows10ISO"]https://www.microsoft.com/en-us/software-download/windows10ISO
[/URL]
 Erased entire drive, reinstalled Windows & Ubuntu
[http://ubuntuforums.org/showthread.php?t=2257711](http://ubuntuforums.org/showthread.php?t=2257711)

Best to always have good backups, repair disks for current version of every operating system installed or live install that can work as repair disk.
You may want to review install details in link below in my signature. And many of the linked instructions for more detail.[URL="http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media"]
[/URL]

---

### Post by 1two3 on 2016-04-14
But what good will a recovery DVD set do me if I can't boot from them? 
My warranty has ran out already as well. 

I really appreciate all the help you've given but it really seems like it's game over.. I'll have to take out a rib and buy a new laptop :<
I was really hoping to use this one for at least another year, maybe I still can but it's doubtful with all the problems I'm having with it now. 
Next time I will for sure get AMD instead of nvidia at least.. I'm also interested in Qubes OS but I think I'll need 16gb RAM to run it effectively.

---

### Post by oldfred on 2016-04-14
I do not think you should give up. It does not sound like you have gotten into UEFI/BIOS and changed settings, nor checked if Acer has DVD set for your system.

Actually nVidia is better in most cases. But many find AMD ok.
AMD is trying to provide better open source drivers but is not there yet. They say maybe by Summer. 

 [https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx](https://wiki.ubuntu.com/XenialXerus/ReleaseNotes#fglrx)
[https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-March/016315.html](https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2016-March/016315.html)
16.04 Release notes
When upgrading to Ubuntu 16.04 from a previous release, both the fglrx driver and the xorg.conf will be removed, so that the system is set to use either the amdgpu driver or the radeon driver (depending on the available hardware). 
With 15.10 Release notes
AMD's fglrx driver does not work with the current kernel
The fglrx driver is now deprecated in 16.04, use radeon and amdgpu


I am not a big fan of laptops. If you travel you may need one.
But they are not ergonomic. Screen is small and too low, so you hunch over it. And keyboard is too high, which can cause arm or hand issues. Occasionly use is ok, but regular use not recommended.

---

### Post by 1two3 on 2016-04-15
> **oldfred said:**
> I do not think you should give up. It does not sound like you have gotten into UEFI/BIOS and changed settings

I did go into bios settings and change bios mode from UEFI to Legacy Bios and turn secure boot to disabled plus make CD/DVD into first boot priority.

---

### Post by oldfred on 2016-04-15
With the new hardware generally better to turn off CSM or legacy mode and just use UEFI.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

If issues then better to turn off UEFI Secure boot.
And in UEFI turn off fast boot, otherwise you have issues getting into UEFI to change settings.

---

