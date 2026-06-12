---
title: "Linx 7 Ubuntu"
date: 2015-01-07
forum: Installation &amp; Upgrades
---

### Post by Yizi on 2015-01-07
Hi all, has anyone been able to install Ubuntu or any other Linux distro on Linx 7 tablet? Hardware seems to be sufficient enough to do the basic tasks..

---

### Post by gwilki56912 on 2015-01-31
Hi,
I am trying to do the same. The Linx 7 is a great little tablet. Intel quad core, 1GB RAM, 32GB SSD, 7" touchscreen, all for 65 quid. Shame it comes pre-loaded with Windows 8.1 :mad:

So far the Linx tablet refuses to boot from anything other than the internal SSD.
I have managed to get into the BIOS, disable secureboot, disable fastboot and enable the USB memory stick as the primary boot media, but it refuses to boot from it. The USB stick (created with UnetBootin) has Ubuntu 14.10 32-bit on it and boots perfectly fine on my netbook.
I have also tried the same with an external USB DVD drive, but no joy.

If anyone has any ideas, please let me know.

---

### Post by grahammechanical on 2015-01-31
Does this device have a BIOS boot system or a UEFI boot system? Machines with Windows 8 pre-installed usually have a UEFI boot system and Windows 8 that has been installed in EFI mode. That means that to install Ubuntu we must also run the Ubuntu live/install session in EFI mode and install Ubuntu in EFI mode.

It has also been noticed that some manufacturers are fixing the UEFI boot system so that the device will only boot Windows. I do not know if this is the case with this particular device but it could be so. Why have you choosen Ubuntu 14.10 32 bit and not 64 bit? Just curious.

Regards.

---

### Post by gwilki56912 on 2015-02-04
Hi,
I tried Ubuntu 32-bit because I incorrectly assumed it had a 32-bit Intel Atom processor (like my netbook) as it has Windows 8.1 32-bit pre-installed. I also made the incorrect assumption that the "Legacy USB" setting in the BIOS meant that it could boot from non-UEFI media.

I have been doing some digging around on the internet and found that the Linx 7 has UEFI ONLY booting and that although it has a 64-bit Intel Atom processor it only has a 32-bit UEFI BIOS. This means that it can only boot a 32-bit UEFI media, which is fine for 32-bit Windows 8, but not for Ubuntu as the 32-bit version does not support UEFI. This appears to be also true for the majority of the other popular Linux distributions.

I have since proven the above when I followed the instructions I found for installing Ubuntu on an Asus 32-bit Win8 tablet. These instructions included a specially built 32-bit EFI boot file, which although did not function correctly on the Linx 7 did allow it to boot to Grub from the USB stick.

Now I have discovered the reason for the Linx 7 not booting from a standard USB stick all I need to figure out is how to create my own build of the 32-bit EFI file for Ubuntu. I think it would even be possible to boot the 64-bit Ubuntu installer from a 32-bit UEFI USB stick. More googling required...

I will post any future success.

---

### Post by rihard2 on 2015-02-10
Hi all,

I am new to the forum and I have registered to answer this question. I also recently bought this "**LINX7**", an inexpensive 8" Inches Windows 8 tablet based on the Intel Bay Trail architecture (Atom 1.33 ghz Quad Core) and wanted to see if I could boot my favourite OS, so I wanted to share my experience with the hope of being of help to others who want to experiment with it as well.  

:KS Good News for [COLOR=#000000]gwilki56912[/COLOR]: after some googling and a lot of attempts, I was able to boot the tablet from the USB drive, the trick seems to be setting the correct screen resolution from GRUB! 

:mad: Bad news: I haven't finished installing the OS yet, only used it Live from the USB stick and most hardware doesn't seem to work so far. I still have to find out how I will boot from the internal storage after installation! 

[B]The following hardware did not work in my test: 
[/B]

[LIST]
[*]Sound
[*]Battery level indicator always showing 100 %
[*]Wifi / Bluetooth
[*]Touchscreen
[*]Screen Orientation detection
[*]Screen brigthness settings
[/LIST]

How to boot Ubuntu Linux on the Linx7 tablet

**Requirements: **


[LIST]
[*]a 2GB (or more) USB flash drive with a Live image of Ubuntu 14.04 (don't ask me how to make one :) )
[*]an USB Hub with at least 3 USB ports
[*]an USB Keyboard
[*]an USB mouse
[/LIST]

[B]Step by Step: 

[/B]
[LIST]
[*]Create a Live installer for Ubuntu (64 Bit!! I have used the 14.04 LTS 64 Bit for this experiment!) on a USB Flash Drive. See[ instructions]("http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-ubuntu") on Ubuntu Website.
[*]Once that's done, there are 2 very important steps that you need to take to be able to boot from that USB drive: using the a 32 bit EFI bootloader and editing grub as explained below:
[/LIST]


[LIST=1|INDENT=2]
[*]Download the file "bootia32.efi" from [this link ]("https://github.com/jfwells/linux-asus-t100ta/blob/master/boot/bootia32.efi")(click "view raw" to start the download! It will be just 621 KB :) )
[*]Place that file into the EFI / BOOT folder inside the USB Stick
[*]Go to the boot / grub directory in the USB Stick, open the file grub.cfg with a text editor.
[*][COLOR=#ff0000]The grub.cfg file will contain a line called "Try Ubuntu without installing". There is a "splash" option that needs to be replaced with[/COLOR] [I]**video=VGA-1:800x1280e reboot=pci,force**
[/I]
[*]Save the file and exit. Without telling GRUB the correct resolution for the LINX7 tablet, it will just show a black screen and it will look like it is not booting. You can also just press "e" at the GRUB boot menu, and add that line manually at boot up, instead of modifying the GRUB configuration file, but I think it's more handy to edit the configuration beforehand.
[/LIST]

[COLOR=#0000ff]Note: If you intend to proceed installing the OS in the internal eMMC storage, open the Windows Management Console and shrink the Windows 8 volume, so on the free space you can create a partition that will be used for Linux (you could create also 2 at this stage, one for the OS and one for Swap). You can format them to EXT4 during with GParted / via the Ubuntu Installer. [/COLOR]

[B]The next steps will be all about rebooting the device into the UEFI configuration utility in order to disable the Secure Boot and to select our Flash Drive as the boot device :) 

[/B]
[LIST]
[*]Connect the USB hub, the keyboard, the mouse and the USB flash drive.
[*]Now you need to restart the tablet in order to change the UEFI settings:
[*]You should be able to access the Configuration Utility by holding DEL or ESC at boot.
[*]If you cannot access the UEFI settings by holding DEL or ESC at boot, try like this:
[/LIST]

[LIST=1]
[*=1][I]On Windows, swipe on the right edge, tap Settings -> Change PC Settings -> Update and Recovery. 
[/I]
[*=1][I]Tap the Restart Now -> Troubleshoot -> Advanced Options -> UEFI Firmware Settings -> Restart 
[/I]
[/LIST]

[LIST]
[*]Now you should see a BIOS-Like interface. Using the arrow keys on your keyboard, go to Security tab -> Secure Boot Menu.
[*][COLOR=#ff0000]Set "Secure Boot" as Disabled. [/COLOR]
[*]Press ESC and now go to the Boot tab. Set "Quiet Boot" and "Fast Boot" to disabled.
[*][COLOR=#ff0000]Boot options priority: set "UEFI: General UDisk 5.00" (or the correct name for your USB flash drive with Ubuntu!) as the first one.  [/COLOR]
[*]Save Changes and Exit.
[*]The tablet will now reboot and will show the GRUB Menu
[*]Select the first option "Try Ubuntu without installing".
[*][COLOR=#ff0000]Be Patient: the boot process will be slower than the average boot up on a laptop and much slower than booting the preinstalled Win8. It will take 1 or 2 minutes before showing the boot messages, and another 1 or 2 minutes before the X server starts (but that might depend also on the speed of the USB stick you will be using! [/COLOR]
[*][COLOR=#000000]There you go, the desktop of our favourite OS is now displaying on our little inexpensive tablet! :) [/COLOR]
[*]The display will be in "Portrait" mode and the Orientation won't change automatically. To change the orientation:
[/LIST]

[LIST=1|INDENT=3]
[*]Open System Settings -> Display ->
[*]Change the setting under "Rotation" to Anticlockwise.
[/LIST]

I am now trying to install Ubuntu into the internal storage of the tablet. The installation is very slow as I'm using a slow USB stick..... 

I still have to find out how I will boot Ubuntu after installation.

Some fresh imagery as proof of Linux Ubuntu 14.04 64 Bit booting on the LINX7 Tablet via USB Stick (and installation in progress) :lolflag:

[ATTACH=CONFIG]259901[/ATTACH] [ATTACH=CONFIG]259902[/ATTACH]  [ATTACH=CONFIG]259903[/ATTACH]  [ATTACH=CONFIG]259904[/ATTACH]  [ATTACH=CONFIG]259905[/ATTACH]

Hope this will be of help for whoever wants to try!! I will post updates after the installation is done and when I will find out how to boot! 
Sorry for the leght of the post !!! 

Cheers! ):P

---

### Post by sammiev on 2015-02-10
If you can get it to install, it may find a lot of the drivers as it updates.

---

### Post by gwilki56912 on 2015-02-11
Thanks Rihard2 for the informative post. I will give it a try and let you know how I get on.

---

### Post by rihard2 on 2015-02-11
:guitar: Bingo! 

**Installation: Successful!**
**Boot of the installed system: Successful** (only using the USB key, using the C command to point GRUB to the installed vmlinuz and initrd - I'm adding a menu entry with it in the grub.cfg of the USB key so it will be easier to boot later). 

First impression: it looks nice and fast! Obviously much better than the live environment! 

I have installed GRUB in the 100mb EFI partition (created by windows) and there is an entry for Ubuntu in the EFI configuration, however that's pointing to the 64bit loader and won't load at all - I have tried to change it to point to bootia32.efi, I get a GRUB console.... I have to find a way to fix that! If anyone knows how to do that, it will be great! :) 

Will keep you posted! :)

Edit: almost getting there! As I stated earlier, booting bootia32.efi shows a GRUB command line when selecting "Ubuntu" as boot option in the EFI firmware configuration, and if I tell GRUB where the configuration file is, it loads the GRUB menu with 3 entries (although this menu is totally garbled with weird characters). So basically, ignoring the screen corruption, the whole thing is working except that it's not loading the grub.cfg automatically...  So I will try to make a simpler configuration file to avoid screen corruption and I will find out how to load it automatically to show the menu entries...

---

### Post by gwilki56912 on 2015-02-12
Hi,
Following Rihard2's post, I have managed to boot from a USB stick of Ubuntu 14.04 64-bit, but it just boots to a blank display. I get to grub and select "Ubuntu", I get a few lines of text and the screen flickers on and off for a fraction of a second then nothing. The USB drive LED flickers for about another 3 minutes and then stops, but nothing but a blank display. I have changed the grub.cfg file to include ***"video=VGA-1:800x1280e reboot=pci,force",*** but still just a blank display. I tried pressing escape during boot to see what was going on behind the blank display, but this makes no difference.

I was going to try with a different USB stick and USB hub later today just incase there is an issue with them.

---

### Post by gwilki56912 on 2015-02-12
ooh! Also, I have found that pressing F7 on power up you get a BIOS boot menu. Saves having to go into the BIOS to change boot order.

---

### Post by rihard2 on 2015-02-12
> **gwilki56912 said:**
> Hi,
Following Rihard2's post, I have managed to boot from a USB stick of Ubuntu 14.04 64-bit, but it just boots to a blank display. I get to grub and select "Ubuntu", I get a few lines of text and the screen flickers on and off for a fraction of a second then nothing. The USB drive LED flickers for about another 3 minutes and then stops, but nothing but a blank display. I have changed the grub.cfg file to include ***"video=VGA-1:800x1280e reboot=pci,force",*** but still just a blank display. I tried pressing escape during boot to see what was going on behind the blank display, but this makes no difference.

I was going to try with a different USB stick and USB hub later today just incase there is an issue with them.

OK, try with another USB key, and see if it boots fine on another computer. Just in case, instead of modifying the GRUB cfg, you could simply press "e" when GRUB shows up.
And then add the video option to replace "splash". You can also remove "quiet"

I still haven't found a way to fix the GRUB issue after installation, I tried to reinstall GRUB but it messes things up.

---

### Post by gwilki56912 on 2015-02-16
Still no joy with other USB stick. I have ordered another hub to try. It should be here later this week.

Instead of Grub, have you tried rEFInd? I have used this once before on an awkward Acer Netbook and it looks pretty good.

---

### Post by gwilki56912 on 2015-02-23
Ha Ha! Change of USB hub did the trick. I have managed to boot into Ubuntu 14.04 64-bit and install it to my internal SSD. However, now it will not boot.
I assume it is the same issue as with booting the USB stick.....64-bit UEFI OS with 32-bit UEFI BIOS. I guess I will need to modify the 64-bit boot sector for 32-bit.
Will have to do more googling.

---

### Post by rihard2 on 2015-02-27
Hi,

sorry for the late reply, I recently moved home and have no broadband at home (I'm browsing via mobile right now). 

I had installed Grub in the Windows EFI partition. If you copy the bootia32.efi file there (from Linux) and rename it to replace the 64 bit version that you find there, 
then you will be able to boot into grub, but only to the command line. From there, you can tell Grub where is the root partition and the initrd, and it will boot fine.

In alternative, you could also tell grub where the configfile is, that will actually display the regular Grub menu and consequently boot up fine. 

I will give you specific commands as soon as I get the chance. 

There is one problem I have noticed: basically when you are using the USB flashdrive, it will be seen as HD0, while the internal eMMC will be seen as HD1. When you reboot and remove 
the flashdrive, the eMMC will become HD0. That will cause some trouble to Grub that will not understand where the configuration file is. I haven't had time
to play with it and find a way to automatically boot Linux or to simply load the configuration file. 

A utility to repair the boot has only messed the whole system as it changed the kernel and other stuff. 

Otherwise everything works, the UEFI firmware does show the entry for Ubuntu (added by the installer) and the Booia32.efi will boot too, except that Grub isn't showing that menu 
because it won't load the configfile automatically. 

PS: I connected my phone via USB and connected to the internet fine from that install of Ubuntu, however it wouldn't find / install any updates or drivers for any hardware. 

Let me know if you have any news :) 

Cheers

---

### Post by keithdcoles on 2015-04-01
All,

On a different approach I have had great success using VMware on the linx's existing Windows 8 installation. Currently using the 32 bit Elementary OS flavour of Ubuntu and it works very well. 

Current VM settings are Operarting System Ubuntu (32 bit), fixed drive of 10Gb, 2d accelleration on, 512mb base memory. The touch control is a little flaky but works exceptionally well with a BT mouse and Keyboard. All the captures work fine (Mouse, Keyboard, USB, Networking ect.). 

Initially it was sluggish until I installed the VMWare extensions (Which Elementary went off and found on its own with its update manager)

Wont run anything intense (Works fine for Libre office and 2d games such as freedroid and supertux 2) but its only around only slightly less than what I would expect of the unit running it direct.

Gives the option of both Windows (Hate point one) and Linux :-)

Regards,

Keith.

---

