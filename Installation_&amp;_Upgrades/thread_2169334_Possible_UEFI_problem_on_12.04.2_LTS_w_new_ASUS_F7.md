---
title: "Possible UEFI problem on 12.04.2 LTS w/ new ASUS F75V Notebook. Black hanging screen."
date: 2013-08-21
forum: Installation &amp; Upgrades
---

### Post by shaolin730 on 2013-08-21
Hello folks, I saught help first in the Ubuntu IRC channel but was unable to fix my problem.  Please bear with me as I'm not a Ubuntu or linux expert & I may need a little explaining.

Anyhow, I'm having trouble getting a dual install of Windows 8 & Ubuntu 12.04.2 LTS on a new Asus F75V Notebook.  Here are the specs of the laptop, specifically the video card:

Intel Core i5 @ 2.6 GHz 
6 GB DDR3
750 GB HD
nVidia Geforce GT 610M w/ 1 GB vid. memory (dedicated card)
**will provide any other info if needed**

I've instaled Ubuntu on almost a dozen machines in the past & have never run into problems.  However, after struggling to get Ubuntu installed in the frist place because of UEFI settings (SecureBoot, FastBoot) I finally got it installed yesterday & it was working perfectly for the night.  However, upon turning my laptop on in the morning it stopped booting in to Ubuntu.  Here is what it does:

After pressing the power button the purple screen/Grub boot loader pops up asking me to select a kernel or OS to boot with the usual options: 

Ubuntu w/ linux 3.2.0-24-generic
Ubuntu w/ linux 3.2.0-24-generic (recovery mode)
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)
Windows Recovery Enviorment
Windows 8 Loader

"Previous Linux versions" is not listed because this was a fresh install & there are no earlier versions on the HD.  If I select to boot in to Ubuntu as normal it flashes to the purple splash screen w/ the Ubuntu logo & the loading bar for a second then VERY QUICKLY switched to a black screen & hangs there until I shut the PC off.  Which by the way I have to do with CTL-ALT-DLT, pressing or holding the power button does nothing.

I'm fairly positive I have SecureBoot, FastBoot & other UEFI settings disabled as I cannot boot into Windows 8 unless I go back into the BIOS & turn them back on.  I've tried checking the disc for errors off a USB stick & done all I can (I think) in recovery mode.  I'm about to try setting NOMODESET & will post the results.  

Anyone have any ideas!?!?  Sorry for the college essay, just trying to give a proper idea of the issues I'm having.

~Dave

---

### Post by oldfred on 2013-08-21
Best to see details. Maybe you have installed in BIOS mode, but also can be video issues. 
Boot-Repair can convert a BIOS install to UEFI and add correct chain load entries to Windows to make dual booting easier.
But either UEFI or BIOS with nVidia you need nomodeset.
I only have an older system and with nVidia have to use nomodeset until I get proprietary nvdia drivers installed.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Flash drive Installer with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

      
 How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by ubfan1 on 2013-08-21
Are you sure you installed the 64 bit Ubuntu 12.04.2 release?  The default kernel for the 12.04.2 is in the 3.5 series, not the 3.2.

---

### Post by oldfred on 2013-08-21
Good point ubfan1. 

I only have BIOS but my install is 12.04 and not 12.04.2 and I still have 3.2 as I have not upgraded that. 

And UEFI is only supported in 12.04.2 or later. With many of the very new hardware the very newest kernel is needed which is in 13.04 or even newer will be in 13.10 but we cannot really suggest 13.10 unless also testing and willing to have breakage.

---

### Post by shaolin730 on 2013-08-21
I'm fairly sure I installed the 64 bit version.. that's the image I downloaded & created my USB boot drive from.

oldfred:  sorry it took me a while, had to take of something at home.  I just finished downloading Boot Repair but when I sart the program it gives me a pop-up: "EFI Detected. Please Check Other Options".  Is this something to worry about?  Going to proceed w/ the instructions on the link you posted to get that report but I wonder if this is a concern..

---

### Post by shaolin730 on 2013-08-21
Here is the link to the BootInfo report.  

[http://paste.ubuntu.com/6011818/](http://paste.ubuntu.com/6011818/)

Thank you all for the help & I appologize for being such a newb, lol.. I'm going to double check about the 64 bit now though I'm curious, ubfan1, what gave you a hint that I may not be using it?

EDIT:  I do have the 64 bit version.  I double checked in terminal w/ uname -a.  It's listed as the x86 version not the i386.

---

### Post by oldfred on 2013-08-21
It now shows the 3.5 series kernel so much better.

It looks like you have not run Boot-Repair. The Windows entries in the grub menu will not work as grub has a bug and only creates BIOS entries. Boot-Repair can fix that. You do not have signed versions of kernels so do not turn on secure boot, but should be able to choose ubuntu entry in UEFI and boot.

If you are getting black screen that is video issue. With nVidia you need nomodeset to get into system so you can install the nVidia proprietary driver. Some UEFI systems also need additional boot parameters. See post #2 for links to screen shots on how to add nomodeset. You just use e on grub menu, scroll to linux line and replace quiet splash with nomodeset.

Similar model? But it looks like a BIOS install but also has the nVidia install.
 HOWTO: Install Ubuntu 12.04.1 on ASUS G75VW-DS72
[http://ubuntuforums.org/showthread.php?t=2058444](http://ubuntuforums.org/showthread.php?t=2058444)

---

### Post by shaolin730 on 2013-08-21
THANK YOU Fred.  I have a good feeling after following these directions I will be okay & not have to return the laptop, lol.  I'll be back to post my results & *hopefully* mark this post SOLVED! :D

---

### Post by westie457 on 2013-08-21
@oldfred
Did you notice this part of the BootInfo Report?

```
[COLOR=#000000]sda4: __________________________________________________________________________[/COLOR]
    File system:       ntfs
    Boot sector [COLOR=#AA22FF]type[/COLOR]:  Windows 8/2012: NTFS
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 8
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe 
                       /wubildr /wubildr.mbr



```

Does it make any difference to the OP's issue?

Cannot remember where I read about Wubi not being compatible with a Windows 8 install.

---

### Post by oldfred on 2013-08-21
It looks like he tried to install wubi, but it will never work on a gpt partitioned drive which all UEFI system require.
Since he has the full install it will not interfere with anything, perhaps he gets two entries from BCD when booting Windows. 

Wubi should just be deleted from Windows. Not sure if auto delete in Windows works or you have to manually delete files and manually remove entry in BCD.
       Uninstall wubi:
[https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F](https://wiki.ubuntu.com/WubiGuide#How_do_I_manually_uninstall_Wubi.3F)
bcdEdit - bcbc
[http://ubuntuforums.org/showpost.php?p=11927905&postcount=5](http://ubuntuforums.org/showpost.php?p=11927905&postcount=5)
[http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu](http://askubuntu.com/questions/145444/how-do-i-remove-the-extra-ubuntu-option-on-the-windows-boot-manager-menu)

---

### Post by shaolin730 on 2013-08-21
I will uninstall wubi once I'm done getting nomodeset finished.  However, I think I may have run into a problem when setting it.  Here's what I did:

I used the directions listed under "**How to permanetely set kernel boot option on an installed OS (not wubi)**"
-After editing the grub config file from saying:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

I then saved the config file & typed "sudo update-grub" into terminal but it responded w/ an error:

/usr/sbin/grub-probe: error: canon find a devide for / (is /dev mounted?).

Then puts me back at the prompt.  Man do I feel like a complete pain in the ass.. lol.

EDIT:  when I type "sudo mount /dev" into terminal it comes back with the following 2 lines: 
mount: udev already mounded of /dev busy
mount: according to mtab, udev is already mounted on /dev

---

### Post by shaolin730 on 2013-08-21
well seeing nothing is working I'm going to Staples to pickup some blank CDs so I can make a bootable CD instead of a bootable USB.  the options screen when you boot off a UISB is different than off a CD, you don't get that menubar at the bottom of commands using the F1-6 keys.

---

### Post by oldfred on 2013-08-21
You do not need CD. With UEFI you do not get the purple screen, accessibility icons and the f6 choice, that is booting in BIOS mode which you do not want unless your system absolutely will not install in UEFI mode.

UEFI mode only gives grub menu. And even to boot installer you need nomodeset on the linux line in grub. 
Changing config file is only if you want nomodeset at permanent setting. Editing grub menu is only required until you get nVidia drivers installed. So you need to edit grub menu to boot with UEFI and then after install you will need it on first boot. Then install nVidia drivers. 

You will  want to remove the nomodeset permanent setting as that may conflict with nVidia.

You can only run the sudo update-grub from inside your install after you have booted or by chrooting into the install.

---

### Post by ubfan1 on 2013-08-21
The 3.2 kernel indicated that it was not 12.04.2 that you were installing, so I just asked to verify the necessary items, 12.04.2 and 64 bit.  Who knows how easy it is to mis-click and get the wrong download?

---

### Post by shaolin730 on 2013-08-21
Bleh, I hate being so illiterate at this stuff.  If I get you correctly I need to uninstall the previous version of Ubuntu I have installed, boot off the USB to "Try Ubuntu before installing it", then set NOMODESET, restart again & then do a fresh install of 12.04.2 LTS?  I feel like a baby right now.. (and likeley look like one too).

I just don't want this laptop if I'm gonna have to use Windows..

---

### Post by shaolin730 on 2013-08-21
ubfan1:  you're right, it is easy to make a mis-click.  I appologize if you thought I was being hostile at all, that certinainly wasn't my intent.  as far as it being the right version.. when 12.04.2 64 bit wasn't working initally because of SecureBook/UEFI I did attempt to install the 32 bit version.  however, after every attempted install I formatted the partition that I'm using for Ubuntu.  shouldn't that have wiped it clean?

---

### Post by oldfred on 2013-08-21
As long as you are not trying to instal side by side and use Something else to select same partition for / (root) and check the format with ext4, you should be fine.
But only 64 bit works with UEFI. And with some of the very newest systems the very newest version of Ubuntu is needed. The 12.04.2 actually has the same kernel as 12.10 and both of those were the first to work with secure boot. But in most cases you do not need (nor really want) secure boot. Secure boot is 90% Microsoft marketing as they have had so many security issues, but secure boot does not eliminate any of those. And all it really does is make it more difficult to install any other system.

---

### Post by shaolin730 on 2013-08-21
Okay.  I'm just a little iffy on getting nomodeset done correctly but I think I'm beginning to understand.  

And for the record, I agree 100% about secure boot.  It's just another way for MS to corner the market & further their monopoly in the PC market.  They've been using the "security" excuse for a decade+

---

### Post by shaolin730 on 2013-08-21
UPDATE (lol):  I set NOMODESET correctly, I believe.  I followed the "**How to temporarily set kernel boot options in an installed OS (not wubi)**", hit "e" when the normal Ubuntu 12.04.2 (non-recovery mode), added "nomodeset" after "quiet splash" & hit F10 to resume the boot.  Instead of flickering past the purple Ubuntu splash screen w/ the loading bar & hanging on that blank black screen now it stays on the purple spash screen, finishes the loading bar & just hangs on that screen now.  uggh.  from one issue to another.. but at least it's some kind of progress, lol.

---

### Post by oldfred on 2013-08-21
Without quiet splash you will see all the drivers and system being loaded. Often the last command posted is not the real issue but a few lines above it.

Some now systems need nomodeset and some other options. 

An older link
 [SOLVED] UEFI Boot Problems Asus
quiet splash vt.handoff=7 rootdelay=90 reboot=a,w
      
 ASUS K55A  Windows 8 & Ubuntu   Some Asus need this boot parameter pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2088499](http://ubuntuforums.org/showthread.php?t=2088499)


 Asus i3 with Intel graphics, but you have nVidia perhaps first one?
"acpi_osi=Linux"
"video=1280x1024-24@75" or whatever native resolution is

---

### Post by shaolin730 on 2013-08-21
I'm confused again (sorry).  You're saying I need to also add "quiet splash vt.handoff=7 rootdelay=90 reboot=a,w", "pci-nomsi", "acpi_osi=Linux" & "video=1280x1014-24@75" (or whatever the native res is) to the grub config?  If I don't get this working soon I'm just gonna give up & return the laptop.  I hate relying on people & bugging them like this.

also the line where I put "nomodeset" into says this (case sensitive):

linux /boot/vmlinuz-3.5.0-23-generic root=UUID=59c31fed-4a44-404d-96a8-c5ad7b3ea65b ro quiet splash nomodeset $vt_handoff

it doesn't say vt_handoff like that other Asus that got fixed..

---

### Post by shaolin730 on 2013-08-21
you know what.  I'm sick of this. I've been up since 9am EST fighting this. I'm turning secureboot & fastboot back on, booting back in to windows, formatting my linux partition & reinstalling.  I'm getting nowhere with this install but frozen black screens or frozen purple Ubuntu loading screens.  thanks for the help everyone, Fred especially.  I'll be back tomorrow, with my luck, with the same exact problem.

---

### Post by shaolin730 on 2013-08-21
formatted linux partition, turned SecureBoot & FastBoot back off, put in USB boot drive.  after booting off the USB I hit "e" with "Install Ubuntu" highlighted & added both NOMODESET & ACPI= to the grub boot config.  I then hit F10 to continue to boot.  the screen goes to the purple Ubuntu spash screen with the 5 loading dots that turn from white to orange.  they change colors for a couple cycles then it locks up with all 5 dots orange.  

any ideas?  

I'm done for tonight.. before I break something, lol.  I'll be back on tomorrow to try & fix this before resorting to returning the laptop.

EDIT:  at least I'm up to "Spilled the Beans" with all these damn posts trying to fix it.  lol..

---

### Post by ubfan1 on 2013-08-21
You can type ESC at those dots and switch to a text screen which displays errors.  Those errors may indicate the problem area.  I concur with OldFred that a newer release may work better on you new machine, with the drawback of not being supported like the long term releases are.

---

### Post by oldfred on 2013-08-21
Also with the boot options usually only nomodeset and one or at most two others are required. It just is that not every user has posted what has worked and it varies not just by every vendor but by model. And some models have different options and those cause issues. So all I can suggest is boot with nomodeset and try each of the other boot options.

Another setting that a different brand had was Intel NIC issues. So various settings in UEFI/BIOS that may not even seem related may be. But again often the user has to figure them out. Only after a lot of users have the same issue will systems automatically work better. Even BIOS which is 30 years old requires setting, often for new hardware.

>  Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.



---

### Post by shaolin730 on 2013-08-22
I may have solved my issue.  

I formatted the linux partition & went ahead with a new install.  This time I obviously disabled UEFI in disabling SecureBoot & FastBoot in order to boot off USB.  However, before selecting "Try Ubuntu without installing it" I added nomodeset to the bootlog (though I didn't take out quiet splash?  I didn't see it taken out in many of the screenshots I've seen..) before booting.  Once in Ubuntu booted off USB I instaled it from within Ubuntu via the "Install Ubuntu 12.04.2 Now!" (sp?) icon.  I've rebooted without the USB being even inserted in the PC, grabed all the updates & restarted successfully.  

I am now downloading a few key programs/files (VLC, Wine, Flash, etc) & am going to use the PC for a couple hours. _ I don't want to mark this solved just yet_ because I got it installed before but after a few reboots it started acting up & wouldn't boot into Ubuntu.

What do folks think about this approach?  Like I said, I'm pretty green when it comes to Ubuntu & Linux.. just a casual techy user that can't stand MS/Windows.  Does this sound like it may work in theory?

I'll keep folks updated.. likely with every restart, LOL!

I want to thank everyone that has posted (both here & on other threads) for their tips & ideas.  Hopefully this works but either way I wouldn't have gotten this far without your help.

---

### Post by oldfred on 2013-08-22
Did you install in BIOS mode or UEFI mode?

 Query to see if UEFI or BIOS
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"

---

### Post by shaolin730 on 2013-08-22
I'm not sure.. I type that into terminal?

---

### Post by Iowan on 2013-08-22
> **shaolin730 said:**
> I'm not sure.. I type that into terminal?

...or copy/paste (cuts down on chance of typo's).

---

### Post by shaolin730 on 2013-08-22
Thanks, lowan, I figured as much but just wanted to make sure.  Does the command change any settings?  Only reason I haven't done so already is because everything is working so far so good.  I just shutdown for 15 minutes & booted up again just now & no issues.  

If all is well when I wake up tomorrow I'll mark the thread solved.  Normally I don't shutdown my PC so often or every night, I just have recently because of the install & ensuing issues.  If I knew for sure the problem was resolved I wouldn't even shutdown tonight in order to test it before marking it solved.

---

### Post by oldfred on 2013-08-23
We also have had a couple of users run Windows updates and all of a sudden UEFI was set back to Windows as default. So at some point you may have to reset again.

Systems can reset some UEFI boot parameters and Windows know how. UEFI has the efibootmgr and shell which is a command line tool for editing UEFI parameters. Some UEFI have it installed directly and you can also access it from UEFI menu.

---

### Post by shaolin730 on 2013-08-23
Going to restart now but I think everything is all good.  However, I have no tried booting with SecureBoot or FastBoot back on.  I don't want to run that terminal command to find out if I installed in BIOS or UEFI mode because I would like to know if it changes any settings first.

edit:  Booted up nicely.  Still haven't turned SecureBoot/FastBoot on, don't really see any need to with things working okay.

Thank you to everyone that chimed in with tips to get this fixed.  I  couldn't have done this w/o you & this forum.. other tech supports  pale in comparison to this.  Thank you.

---

### Post by oldfred on 2013-08-23
Glad it is working. 

But with UEFI being new, both Windows & Linux may do things. I would have current versions of Windows repairCD or flash and Ubuntu liveUSB handy just in case.

I currently do not see much need for secure boot. Later you may want to add it. And if dual booting the fast boot or hibernation will cause issues. Only if directly booting Windows from UEFI menu and then rebooting would fast boot possibly work. But any boot into Ubuntu with fast boot on may cause Windows issues of booting.

---

### Post by shaolin730 on 2013-08-23
Thanks again, Fred.  I have the Ubuntu USB but I've got to make a Windows repair CD.  Good to know about SB not being much of a need.. although I am unable to boot into Wndow w/o it on.  I don't care about that though seeing I use Ubuntu 99.9% of the time.

---

