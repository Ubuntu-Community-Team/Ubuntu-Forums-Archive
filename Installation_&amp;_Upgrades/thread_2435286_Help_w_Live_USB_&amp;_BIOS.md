---
title: "Help w/ Live USB &amp; BIOS"
date: 2020-01-18
forum: Installation &amp; Upgrades
---

### Post by ardvark-700 on 2020-01-18
I have an HP 6570b Probook.  I would like to reinstall Ubuntu because the laptop was purchased used.  I created a Live USB w/ Ubuntu 18.04. After creating the live USB, I checked it by putting it into my laptop.  Since an “UBUNTU 18_0” icon appears on my desktop, I’m assuming that I successfully created a Live Untuntu USB.  When I called HP, they told me that Secure Boot on the 6570b is disabled by default and cannot be enabled. I went into the BIOS & turned off Fast Boot. USB device boot under System Configuration is checked.  I changed Boot Mode from Legacy to UEFI Native (Without CSM) because I would like to do a UEFI/GPT installation.   I also changed the UEFI Boot Order so that Generic USB Device is the first item on the list.  Originally it showed OS Boot Manager.  When I tried to install  with OS Boot Manager as the first item on the list, I get the same error message below.  When I save the changes and exit BIOS, instead of starting the Ubuntu installation, I get an error message, “No bootable image found, notebook will be shut down.    Can anyone tell me what I’m doing wrong?

---

### Post by yancek on 2020-01-18
Did you verify that the download of the Ubuntu iso was uncorrupted on the the download using an md5 cheksum?
How, meaning what software did you use, did you create the Ubuntu usb?
You make a reference to windows but do not indicate which windows you are using, is it 10 or??
How do you access the BIOS to change boot options?  Not sure your computer is the same but on my HP laptop, I hit the Esc key on boot and then see several options.  These include the F9 key to do a one time change of boot options.  The F10 key makes a permanent change so what you want is the F9 key.

> When I tried to install  with OS Boot Manager as the first item on the list

The expected behavior with that selection would be to boot windows.  Do you no longer have windows installed?

---

### Post by ardvark-700 on 2020-01-18
Hi, Yancek.  Thank you for the reply!

My laptop came with Ubuntu installed.  Ubuntu is the only OS on it.  Windows is not installed, not 7, 8 or 10.

I made the Live USB a while back & can't remember whether I checked the md5 checksum or not, I'll check it right now.

I used Rufus to flash the USB on a second Windows computer that I have.

About accessing BIOS, yes, I hit <Esc> to edit/change the BIOS.  The main menu reads "F9 Boot Device Options" and "F10 BIOS setup".

I actually was trying to make permanent changes to my laptop, specifically turning fast boot off, UEFI on & secure boot off.  I've backed up everything I need & intend to delete the partitions & recreate the file structure to one that is GTP/UEFI.  But if changing "BIOS Setup" is the wrong way to install Ubuntu, I will do whatever you suggest.

A----

---

### Post by ardvark-700 on 2020-01-18
Okay, I checked the SHA256SUM for the iso file I downloaded, and the checksums match.  Is there a way to verify it after you flash the USB?

If it's helpful, I checked the menu options available when I hit <Esc> to edit the BIOS, and under <F9> Boot Device Options, the sub-menu options are * Notebook Ethernet IPV6, * Notebook Ethernet IPV4, and * Boot From EFI File.

A-----

---

### Post by oldfred on 2020-01-18
I have seen some screen shots of Rufus where it seems to create either an UEFI/gpt configuration or a BIOS/(MBR - UEFI CSM) configuration. 
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

Make sure you have an UEFI bootable configuration, not CSM.

Many older systems need UEFI update whether installing Ubuntu or not.

---

### Post by ardvark-700 on 2020-01-19
Thank you, Fred.  I will study the link you provided me tomorrow over a cup of coffee and create a new Live USB.  I'll roll back the changes on my Ubuntu laptop and use another (hopefully more reliable) utility to make the Live USB.  A-----

---

### Post by CelticWarrior on 2020-01-19
Personal opinion: Any software in Ubuntu for making live USBs is better and easier than Rufus.

The default app for that task or MKUSB are fine. Then it's recommended to disable Legacy/CSM in UEFI settings to assure the installer will boot and consequentially install in UEFI mode.

---

### Post by sudodus on 2020-01-19
Maybe the following links can help you:

[Why Doesn't a Bootable USB Boot](https://askubuntu.com/questions/1190764/why-doesnt-a-bootable-usb-boot/) - Flow chart and lists of many different possible things to check for

[help.ubuntu.com/community/Installation/FromUSBStick/tmp](https://help.ubuntu.com/community/Installation/FromUSBStick/tmp) - 'tmp' because I am in the process of revamping an old help page to make it easier to use. Any feedback is welcome (if it is useful, easy or difficult to understand, what might be modified ...)

[hr][/hr]
Now that you have verified that the iso file is correctly downloaded, I suggest that you use the reliable **cloning** method to make your USB pendrive into an Ubuntu live drive.

Just make sure that the iso file contains a current version of Ubuntu, 18.04.x LTS or 19.10. (**x** is a digit showing the 'point version' of 18.04.)

In Ubuntu you can use the built-in **Startup Disk Creator** or [mkusb](https://help.ubuntu.com/community/mkusb).

In Windows you can use [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) or **Rufus** in **'dd-mode'** (not the default mode).

The result will very likely be an Ubuntu live drive, that can boot both in UEFI mode and BIOS mode (alias CSM alias legacy mode).

 * You can try booting another computer to make sure that the Ubuntu live drive is good,
 * and after that look for problems with the problematic computer.
  - Settings in the BIOS menus
  - Try in all USB ports (also USB 2 ports)
  - Disconnect other devices, that are connected via USB. They may confuse the system.

---

### Post by P-I H on 2020-01-19
@sudodus
The [https://help.ubuntu.com/community/Installation/FromUSBStick/tmp](https://help.ubuntu.com/community/Installation/FromUSBStick/tmp) gives an [B]Internal Server Error

[/B]Worked this time, 2 hours later

---

### Post by sudodus on 2020-01-19
> **P-I H said:**
> @sudodus
The [https://help.ubuntu.com/community/Installation/FromUSBStick/tmp](https://help.ubuntu.com/community/Installation/FromUSBStick/tmp) gives an [h=1]Internal Server Error[/h]

It works for me (now, a few seconds ago). Please try again. I have not done anything special to make that address hidden; I can't explain your problem, but think it might be a temporary error.

---

### Post by ardvark-700 on 2020-01-19
Duplicate post ... info below.

---

### Post by ardvark-700 on 2020-01-19
This is my third attempt posting so that lines/ separate the information so that it is readable.  I'll wait for some guidance on how to proceed & go read the replies.  Also, when I pasted what I had typed into the box, part of what I wrote was parsed (deleted).

---

### Post by ardvark-700 on 2020-01-19
Thanks, @CelticWarrior, I've been using my Windows laptop because currently my Ubuntu laptop is bricked.   
Under BIOS SecureBoot is unchecked, Fast Boot is unchecked, and UEFI Native (Without CSM) is checked.  There was also a setting, "Support USB Legacy" that was checked (didn't work/help).  I tried unchecking it, and I still was not able to start the install process.  

@Sudodus, I will check that article.  I am also going to try my other/different USB ports.  There are no other USB devices  plugged into the laptop, but that was a good call because my Windows laptop has a wireless keyboard (w/ wireless USB transmitter).  Good advice, trying to boot on a second laptop.  I have a second HP laptop with Windows 7 only.  I tried to Live Boot using that computer, and the USB is not able to grab control of the boot process and start my Ubuntu installation.  I either still have a problem with my Live USB or else my BIOS settings.  I'm going to find another USB to format and try.  I really think it is my BIOS settings, though. 

@P-I H, I tried putting a forward slash (/) on the end of that link and it worked.  Try this ... help.ubuntu.com/community/Installation/FromUSBStick/tmp/.  Of course sudodus might have fixed it by now.  Please note that all formatting in the message above has been lost.  I'm going to try a different browser.

---

### Post by ardvark-700 on 2020-01-19
When I boot into the BIOS, there are three tabs at the top of the screen:


* File
* Security
* System Configuration


Only the System Configuration tab has options related to booting. There are 8 items under System Configuration: 


* Language
* Boot Options
* Device Configurations
* BUilt-in Device Options
* Port Options
* Set Security Level
* Restore Security Defaults
* BIOS Power On


Under Boot Options, the following items can be checked, unchecked or changed:


Startup Menu Delay (sec) ... 0
Multiboot Express Popup Delay ... 0
[ ] Audio alerts during boot
[ ] Custom Logo
[x] Display Diagnostic URL
[ ] Custom Help and URL message
[ ] Require aknowledgement of battery errors
[ ] Fast Boot
[x] CD-ROM boot
[x] SD card boot
[x] Floppy boot
[x] PXE Internal NIC boot
[x] PXE Internal IPV4 NIC boot
[x] PXE Internal IPV6 NIC boot
[x] USB device boot
[x] Upgrade Bay Hard Drive boot
[x] eSATA boot
[x] HP Application
[x] Customized Boot


SecureBoot Configuration
[ ] SecureBoot
[ ] Clear SecureBoot Keys


Boot Mode
[ ] Legacy
[ ] UEFI Hybrid (With CSM)
[x] UEFI Native (Without CSM)


UEFI Boot Order  <-- The items in this list can be moved up & down
 USB Hard Drive
 Generic USB Device  <-- I also tried this as the first item in the list
 OS Boot Manager
 Notebook Ethernet IPV6
 Notebook Ethernet IPV4
 eSATA Hard Drive
 Notebook Upgrade Bay
 SD Card
 HP Hypervisor
 Customized Boot


Define Customized Boot Option
[ ] Add
[x] Delete


Legacy Boot Order  <-- The items in this list are greyed out because I have "UEFI Native" selected under "Boot Mode"
 Notebook Upgrade Bay
 Notbook Hard Drive
 USB Floppy
 USB CD-ROM
 USB Hard Drive
 Notebook Ethernet
 SD Card
 Dock Upgrade Bay
 eSATA Drive 


*****


With the laptop turned off, I inserted the Live USB and turn it on.  I get the following message, "Selected EFI application image is not valid." I have two buttons I can click on:


* Cancel image load and boot to next boot option
* Continue loading the image


I've tried both options and neither one works (starts the Ubuntu install process).


Things I tried:


* I reformatted the USB. (twice! once fast, once slow)
* I downloaded uNetBooting and used it instead of Rufus to load Ubuntu onto my USB. 
* I Googled HP 6570b + USB + boot.  I found "HP Probook won't boot from USB even with SecureBoot disabled and Legacy mode enabled" with the guy reporting that using an older USB 2.0 allowed him to install his OS. I rechecked my USB, and there is no blue connector.  My USBs that are 3.0 have a blue connector where the USB fits into the laptop.
* In my BIOS under Device Configurations I found "USB legacy support" checked.  I unchecked it, saved it, & restarted my laptop.  It did not work (take me into the Ubuntu installation process).
* I have a second HP 8560p running Windows 7. It's a newer model.  On that laptop Legacy mode (not UEFI) is enabled.  Fast boot & secure boot are turned off, but I still was not able to boot into the Ubuntu install.  I either have an issue with my BIOS or the Live USB I created.  I've literally tried everything I can think of.  I've spent HOURS researching this and trying to find a soltuion.  I don't know what else to try.

---

### Post by ardvark-700 on 2020-01-19
I figured out my formatting problem.  I'm using uMatrix in Firefox.  uMatrix blocks scripts, frames, XHR and some other things with the goal of reducing tracking.  I had something blocked that the forum needs to function correctly ... formatting of messages, paragraphing new lines, etc.

---

### Post by GhX6GZMB on 2020-01-19
> **ardvark-700 said:**
> IUSB device boot under System Configuration is checked. 
 I changed Boot Mode from Legacy to UEFI Native.
Can anyone tell me what I’m doing wrong?

Go back to Legacy BIOS. and make certain your .iso image is OK. This works for me every time on an HP6910p.

---

### Post by sudodus on 2020-01-20
> **ml9104 said:**
> Go back to Legacy BIOS. and make certain your .iso image is OK. This works for me every time on an HP6910p.

+1. This is good advice.

Make certain your .iso image is OK: Check the iso file with md5sum.

The next step is to check that the USB boot drive is really bootable: Try it in some other PC computer (borrow a computer from a friend or colleague) to boot from your USB boot drive until it reaches the desktop environment.

When this works you can also reboot to check that all program packages are OK, "Check the disk for defects".

See the following link,

[Checking the iso file and the boot drive - detailed tips](http://ubuntuforums.org/showthread.php?t=2196858&p=13511608#post13511608)

If it is not OK, I would recommend a cloning tool.

In Windows you can use [Win32 Disk Imager](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) or **Rufus in 'dd-mode'** (not the default mode)

and try again until you can boot your USB boot drive in a[nother] computer.

[hr][/hr]
After that, when you are sure that you have bootable USB drive with Ubuntu, you can start testing different settings in your BIOS for example legacy mode (alias CSM alias BIOS mode (as opposite to UEFI mode)), and also other settings.

---

### Post by ardvark-700 on 2020-01-20
> **ml9104 said:**
> Go back to Legacy BIOS. and make certain your .iso image is OK. This works for me every time on an HP6910p.

@ml9104, I re-enabled Legacy Mode, saved my changes to the BIOS, and with the Live USB in my laptop, I booted into Ubuntu ... the one installed on my hard drive, not the Live USB version.  I'll run by the store later today and buy a new USB.  At this point, my Live USB looks to be the problem.


Below is the selections/changes I made to BIOS System Configuration > Boot Options:

Startup Menu Delay (sec) ... 0
Multiboot Express Popup Delay ... 0
[ ] Audio alerts during boot
[ ] Custom Logo
[x] Display Diagnostic URL
[ ] Custom Help and URL message
[x] Require aknowledgement of battery errors
[ ] Fast Boot
[x] CD-ROM boot
[x] SD card boot
[x] Floppy boot
[x] PXE Internal NIC boot
[ ] PXE Internal IPV4 NIC boot
[ ] PXE Internal IPV6 NIC boot
[x] USB device boot
[x] Upgrade Bay Hard Drive boot
[x] eSATA boot
[x] HP Application
[x] Customized Boot


SecureBoot Configuration  <-- Options greyed out
[ ] SecureBoot
[ ] Clear SecureBoot Keys

User Mode  <-- Options greyed out
[ ] HP Factory Keys
[ ] Customer Keys

Boot Mode
[x] Legacy
[ ] UEFI Hybrid (With CSM)
[ ] UEFI Native (Without CSM)


UEFI Boot Order  <-- Options in this section are greyed out
USB Hard Drive
Generic USB Device 
OS Boot Manager
Notebook Ethernet IPV6
Notebook Ethernet IPV4
eSATA Hard Drive
Notebook Upgrade Bay
SD Card
HP Hypervisor
Customized Boot


Define Customized Boot Option  <-- Options in this section are greyed out
[ ] Add
[x] Delete


Legacy Boot Order 
Notebook Upgrade Bay
Notbook Hard Drive
USB Floppy
USB CD-ROM
USB Hard Drive
Notebook Ethernet
SD Card
Dock Upgrade Bay
eSATA Drive

---

### Post by ardvark-700 on 2020-01-20
This is probably a stupid question, but from watching a bunch of YouTube videos, when you boot from a Live USB, so long as you have the correct BIOS settings, all you do is stick in the USB and turn your computer on, right?  There are  no special keys to hit to get your laptop to boot from the USB instead of the hard drive, right?  The only way I've been able to alter how my laptop boots up is by hitting ESC to get into my BIOS.  And sometimes if I hit ESC after the HP logo disappears I can get into a GRUB menu:

GNU GRUB version 2.02~beta2-36ubuntu3.12

Ubuntu
Advanced options for Ubuntu
Memory test (memtest86+)
Memory test (memtest86+, serial console 115200)

The first item above starts Ubunutu (the one installed on my hard drive), and the second item offers me the following choices:

Ubuntu, with Linux 4.15.0-74-generic (recovery mode)
Ubuntu, with Linux 4.15.0-74-generic
Ubuntu, with Linux 4.15.0-72-generic
Ubuntu, with Linux 4.15.0-72-generic (recovery mode)

---

### Post by CatKiller on 2020-01-20
> **ardvark-700 said:**
> This is probably a stupid question, but from watching a bunch of YouTube videos, when you boot from a Live USB, so long as you have the correct BIOS settings, all you do is stick in the USB and turn your computer on, right?  There are  no special keys to hit to get your laptop to boot from the USB instead of the hard drive, right?  

That depends entirely on the specifics of your motherboard. Some will have a setting you can use that will always check the USB before trying the hard drive, some will only boot from a USB from the single-use boot menu regardless of any other settings, and every other combination you can think of.

---

### Post by ardvark-700 on 2020-01-20
@sudodus, unless I did it incorrectly, I checked SHA256SUM for the iso I downloaded, and the numbers matched.  

What I've tried so far is:  

I reformatted my USB.  The filesystem is FAT32.  
One time I made the Live USB from the iso I downloaded and checked/verified.  
The second time, I downloaded the iso from Ubuntu's website instead of selecting the iso on my hard drive.  

Since I've tried Netbootin & Rufus and since I've tried two different iso's and since I've reformatted the USB, I'm just going to try buying a new USB.  Maybe I had the BIOS settings wrong on my second laptop (HP 8560p), but I was not able to boot from the Live USB on my second Windows laptop either.

---

### Post by ardvark-700 on 2020-01-20
@CatKiller, I will call HP Tech Support to find out if I'm missing something.  Thanks!!!

---

### Post by CelticWarrior on 2020-01-20
> **ardvark-700 said:**
> * I have a second HP 8560p running Windows 7. It's a newer model.  On that laptop Legacy mode (not UEFI) is enabled.  Fast boot & secure boot are turned off, but I still was not able to boot into the Ubuntu install.  I either have an issue with my BIOS or the Live USB I created.  I've literally tried everything I can think of.  I've spent HOURS researching this and trying to find a soltuion.  I don't know what else to try.

This tells me there's something wrong with the USB for it not being able to boot in two different computers and modes.

Something you should know is that not all USB are good for this purpose even if they work fine for saving/copying files and have no other errors to report. But it can also be the case of a an old flash drive that has intermittent errors that sometimes are "corrected", obfuscated by formatting it. If it is unusually slow when using it as a normal mass storage device.

So, to summarize the great advice you've been getting so far, especially from @sudodus (the developer of the tool I've recommended a few posts ago - MKUSB):

[LIST]
[*]In my opinion your UEFI settings are fine and you should be able to boot in the recommended UEFI mode from external media, the Ubuntu installer, as long as that media is fine (at this point I strongly believe it isn't, reason above).
[*]If you had access to a Ubuntu session, I would reiterate the recommendation for using MKUSB **in a different, known good, USB stick**. But if you only have Windows then I'll just reiterate sudodus recommendation of using **Rufus in DD mode** (this should make bootable installation media in either mode); another good tool in Windows is Balena **Etcher**.
[*]All HPs I've dealt with since 2012-13 (UEFI) have a special menu accessible with ESC at boot time where users can select several options, namely F10 to UEFI ("BIOS") settings but also **F9** to select where to boot from. This is what I always use once the UEFI settings I want are already as I want (similar to the ones you showed in a previous post). Typically it shows the already installed OS by name and the name of the USB stick; if the latter isn't shown then it wasn't reconized as bootable (= there's something wrong with it)
[*]USB 3.x ports typically are blue but that's not mandatory. Many laptops now have those ports in black and I even came across one slim notebook with two USB ports, 1xUSB2.0 + 1xUSB3.1, both black, indistinguishable one from another, but they're effectively different. This is important because, as you found out in your research, users where having trouble booting external media from USB3.x ports. Maybe it needs firmware update or it's just how it is so, try booting using different USB ports as well.
[/LIST]

---

### Post by ardvark-700 on 2020-01-20
@CelticWarrior, thank you for your patience & summarizing the good advice I've gotten thus far.  I'm feeling pretty inept, trying to do something that is really supposed to be so basic.  I'm actually going to go back & read and study every reply, and read the links that have been provided to me, even after I get over this hurdle. 

I have both laptops working again.  I just needed to roll back the changes I made to BIOS on my Ubuntu laptop.  So, yes, I absolutely will use MKUSB to burn the ISO onto the USB I bought today, a PNY USB 2.0, 16GB.  Last time I verified the ISO with Kleopatra.  In case I did it wrong, I decided to go back to the tutorial on how to verify your ISO, [https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0), and follow those instructions step by step. I'm sorry it takes me so long.

---

### Post by ardvark-700 on 2020-01-23
I want to thank @CelticWarrior, @OldFred, @yancek, @sudodus, @P-I H, @ml9104&@CatKiller for your help & assistance. Whatever I  was doing wrong, I managed to correct.  Based on the *amazing* advice I  got on this thread, I did the following:

* I downloaded a fresh copy of ubuntu-18.04.3-desktop-amd64.iso on my Ubuntu laptop.

       * I verified the iso with sha256SUMS.  The hashes matched.

       * I used MKUSB to create a Live USB with a newly purchased 16 GB 2.0 USB.

       * I  checked the manual for my laptop & identified the location of the  USB 2.0 & 3.0 ports.

* I unplugged my external wired keyboard which was  using one of the USB 2.0 ports. 

       * I rebooted  & re-checked my BIOS settings, selecting the UEFI boot option.

       * I tried booting from a different USB port. (The USB itself was 2.0, but the new/different port I used was 3.0)

@CelticWarrior, the USB ports on my laptop are *not* color coded.  I need to check my laptop user manual to see which were which.

@sudodus, thank you for the time & effort you put into creating the MKUSB utility and providing the *extensive* documentation that goes with it.  I will never use anything else to create my Live USBs.

Mostly, everyone, thank you for your patience.  I rarely ask for help.  In this case I couldn't have done it without you.  Now I know that if I mess up an installation or how I format my hard disk, I can always reinstall.  I am that much more independent and able to help myself.  I am freer to experiment and make mistakes and learn, knowing that I can reinstall Ubuntu.  

Warmest Regards,
Alexa, aka ardvark

P.S.:  Could I just ask quickly how I mark the thread [SOLVED]?

---

### Post by sudodus on 2020-01-23
You are welcome Alexa, aka ardvark,

I'm glad that we could help you solve the problem :-)

Please click on **Thread Tools** at the top of the page and mark this thread as SOLVED

---

### Post by ardvark-700 on 2020-01-23
Well, I guess I'm not out of the woods yet.  I marked this thread solved and then had to un-mark it back again.

After installing Ubuntu, my laptop was not able to reboot.  It got caught in a loop, showing the HP logo, going black, showing the HP logo, going black. I hit ESC to go into the BIOS and looked at the Boot Options, specifically, the UEFI Boot Order.  I compared it to my other HP laptop, not the same model, but there are some similarities in the BIOS of both laptops.  Since I'm not fully aware of benefits or problems of any particular order, could I get recommendations on the best order?  Currently, I have the options below in the following order:

UEFI Boot Order
    OS Boot Manager
    Generic USB Device
    Notebook Ethernet IPV4
    Notebook Ethernet IPV6
    USB Hard Drive
    eSATA Hard Drive
    Notebook Upgrade Bay 
    SD Card
    HP Hypervisor
    Customized Boot

Under Device Configurations I found USB legacy support still checked, so I unchecked it & rebooted.  I still go into the endless/repeating loop.  So do I have a problem with my BIOS setup/choices, or did I manually set up Ubuntu incorrectly?  

Here's how I set things up on the Ubuntu install:

sda1    ext4    /
sda2    ext4
sda3    swap    17300 MB
sda4    efi    533 MB

I want to install Ubuntu into sda1, which holds / (root), boot & home.
sda2 is saved/reserved for future distro testing.  I have 16 GB of memory, and since I want to be able to hibernate, I reserved 17.3 GB for swap.

I have no doubt that I'm missing something, like editing /etc/fstab or setting flags.  Until I hear from someone, I'm going to go back and read @OldFred's UEFI help file.

P.S.  I tried to boot from my Live USB, hoping to select "Try Ubuntu without Installing," but I can't get to the Ubuntu screen to select it, I'm caught in that endless loop.  So that leads me to believe I still have something wrong with my BIOS selections/choices.

A----

---

### Post by oldfred on 2020-01-23
HP has not been Linux friendly on some models. Will not boot ubuntu entry in UEFI.
Some HP users have posted that UEFI update resolved some issues.

Many HP have to use the fallback or hard drive boot entry which uses /EFI/Boot/bootx64.efi. Most systems have that file as a copy of Windows efi boot file. But grub will install its shim file as bootx64.efi as another way to boot. The fallback/drive entry is the same path & file name used for external drive boot.

Have you updated UEFI?
Can you boot a drive entry and get Ubuntu?

---

### Post by ardvark-700 on 2020-01-23
Fred, I don't have Windows on my Ubuntu laptop.  I have sudo updated && upgraded frequently, but not since this last install.  And right now, I can't get to Ubuntu, I can't login with my password.  How would I go about updating UEFI?  How would I find the right file for my laptop?  HP Tech Support offers subscription & per incident tech support, but any time you mention Linux, they say they don't support it.  

I tried to use my Live USB to boot into Ubuntu, but I'm still stuck in that loop.  It makes no sense to me that I was able to install Ubuntu onto my laptop, but that when I rebooted (as directed) I couldn't use that same USB a second time to install or try Ubuntu.

Fred, should I just give up on installing Ubuntu on my HP laptop and reinstall Windows & sell it and buy another more Ubuntu/Linux friendly laptop?  If so, what manufacturers would you recommend?  I like System76, but their laptops are totally out of my price range, even the used ones.

I really wanted to do a GPT/UEFI install, but maybe on this laptop I'll have to go back to Legacy BIOS.

A---

---

### Post by sudodus on 2020-01-24
While we are waiting for oldfred's advice I can insert what I suggest.

> 
I really wanted to do a GPT/UEFI install, but maybe on this laptop I'll have to go back to Legacy BIOS.


There is nothing wrong with running the computer in BIOS mode (alias CSM alias legacy mode), so **I suggest that you try installing Ubuntu in BIOS mode**. It is easier with an old style MSDOS partition table. GPT is also possible, but then you need an extra bios_grub partition (small, without any file system, but with a 'bios_grub' flag).

See this link about partitioning: [help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

### Post by oldfred on 2020-01-24
Most vendors have a downloadable UEFI update file that you need to save to a FAT32 partition, either a flash drive or on hard drive.
And then from UEFI you can directly read that file.

If having issues getting into UEFI, did you leave fast boot on? That normally gives no time to press any keys.
A full cold boot or power shutdown, remove battery if laptop, and hold power switch for 10 sec to drain power.l

If you decide to use BIOS boot, I would stay with gpt. 
But have both an ESP for UEFI boot and a bios_grub for BIOS boot. Then you can reinstall grub to change boot modes, if later you want to experiment again with UEFI.

---

### Post by ardvark-700 on 2020-01-24
Sudodus & OldFred, thank you for not giving up on me!  *I* haven't given up wanting to make this work!

* I removed the power cord & battery and held down the power button for > 10 seconds.
* I verified that Fast Boot was turned off in my BIOS.

The result is that even though I can get into BIOS to make changes, my laptop still won't boot into Ubuntu.

* I will go to the HP Support Forum and see if I can get my hands on an UEFI update file.
* I am going to try installing Ubuntu in BIOS mode. 
* I will read the article on partitioning.
* I am going to use gparted to create both an ESP for UEFI boot and a bios_grub for BIOS boot.  I was not able to set flags for the different partitions when installing Ubuntu.

---

### Post by tea for one on 2020-01-24
> **ardvark-700 said:**
> I tried to use my Live USB to boot into Ubuntu, but I'm still stuck in that loop.  It makes no sense to me that I was able to install Ubuntu onto my laptop, but that when I rebooted (as directed) I couldn't use that same USB a second time to install or try Ubuntu.

Power off the PC/Laptop
Insert your Live USB stick into a suitable port
Power on the PC/Laptop
Tap/press **F9** (which allows you to choose boot device)

Tap/press **F10** for UEFI/BIOS

I'm pretty sure that F9 (boot selection) and F10 (Set up) keys at power on are the usual keys for HP

---

### Post by ardvark-700 on 2020-01-24
I changed my BIOS settings

* USB Legacy Support is on
* Fast Boot is off 
* Secure Boot is off
* Boot Mode = Legacy 

* Legacy Boot Order:

..Notebook Hard Drive
..Notbook Upgrade Bay
..USB Floppy
..USB CD-ROM
..USB Hard Drive
..Notebook Ethernet
..SD Card
..Dock Upgrade Bay
..eSATA Drive


The result of my changes are that I can now boot from a Live USB.  I reinstalled Ubuntu into sda1, and I also used gparted to see what was going on with the partitions I created.  

I still am unable to start Ubuntu normally.

Here is the structure currently:

/dev/sda1, No Name, ext4, size=55GIB, used=6.74GIB, unused=48.86GIB, no flags
/dev/sda5, No Name, linux-swap, size=16.11GIB, used=0.00B, unused=16.11GIB, flag=swap
/dev/sda6, Name=EFI System Partition, fat32, size=531.00MIB, used=7.14MIB, unused=523.86MIB, flags= boot,esp

sda2, sda3, sda4 were created and are being saved for future storage, projects, distro testing, encryption, whatever, but should not have anything to do with booting or the installation of Ubuntu.

Are there any problems with the partitions I have created thus far? 
Does swap have to be last or EFI first? 
Am I missing any flags?
I don't see a column for mount points.
Do I need to edit fstab?
No reply from the HP Forum Community yet regarding updating UEFI.

Okay, I just thought of something ... I'm limited to 4 partitions in  BIOS/Legacy Mode.  Can I put sda1, sda2, sda3 & sda4 in an Extended Partition?  That would be one partition, swap as my second, ESP  as my third, and bios_grub as my fourth?  Would that work?

@OldFred wrote:
>> But have both an ESP for UEFI boot and a bios_grub for BIOS boot. Then you can reinstall grub to change boot modes, if later you want to experiment again with UEFI. 

Yes, I would still like to tackle UEFI in the future.  I still need to create a bios_grub partition with the bios_grub flag, no file system. Could I ask the size of that partiton & the location (front or end of the disk or doesn't matter)?

@sudodus, thank you for that link on partitioning.  I studied partitioning strategies for a week before I started this installation, but it's clarifying things & filling in a few of the missing pieces.

@tea for one, I will test out those keys the first chance I get!

---

### Post by sudodus on 2020-01-24
Yes it is possible. But you need no swap partition. You can let Ubuntu create a swap file instead. It is actually the standard (default) for 18.04 LTS and newer versions. (But if there is already a swap partition, Ubuntu will grab it during the installation.)

You can have 3 primary partitions and one extended partition (or 4 primary partitions but no extended partition) in an MSDOS partition table. And in the extended partition you can have many logical partitions. 

In a GUID partition table (GPT) you can have a large number of partitions and all are primary. (It is only in GPT that you need a bios_grub partition in order to boot in BIOS mode.)

**gparted** (run from the Ubuntu live drive) is a good partitioning tool.

---

### Post by ardvark-700 on 2020-01-24
@sudodus, let's see if I can speak this back to you.  I will be creating a GPT (GUID Partition Table).  Since I've been struggling with booting from UEFI, I'm falling back to booting from BIOS.  Doing so is going to require that I create a small BIOS boot partition in which I set a bios_grub flag.  But I am no longer going to need a swap partition. And since I'm using GPT, I don't need to worry about extended partitions either.  I can theoretically have the four primary partitions I wanted plus the bios_grub partition (sda1 - sda5). Please correct me if I've got any of that wrong.

Question:  I read that an ESP (EFI System Partition) can exist on a GPT disk or an MBR disk.  It looks like I'd benefit from an ESP also?  If so, I'd set the boot flag for that partition?  

Question:  Re the BIOS Boot Partition, how big should I make it? *** Does it need to be located first on my SSD?  I understand that I need to set the flag as bios_grub.

Question:  Are there any changes I need to make to my BIOS settings so that they support the approach above?

Question:  What would the mount points be for my Ubuntu partition, my ESP and my BIOS boot partition?  I'm guessing that the Ubuntu partition would be root (/).  I think I read that the mount point for ESP would be /efi/boot or /efi/boot/, but is that correct in my particular situation (not using UEFI)?  I have no idea what the mount point would be for the BIOS boot partition.

Question:  Do I need to edit my fstab?

gparted Question.  Is gparted on the Live USB I created to install Ubuntu?  I created another/different Live USB with just gparted on it.

*** I found the answer to this question ... "When creating a BIOS Boot Partition on a GPT system, you should make sure that it is at least 31 KiB in size. GPT-formatted disks are not usually particularly small, so we recommend that you make it larger than the bare minimum, such as 1 MiB, to allow plenty of room for growth."

---

### Post by sudodus on 2020-01-24
> **ardvark-700 said:**
> @sudodus, let's see if I can speak this back to you.  I will be creating a GPT (GUID Partition Table).  Since I've been struggling with booting from UEFI, I'm falling back to booting from BIOS.  Doing so is going to require that I create a small BIOS boot partition in which I set a bios_grub flag.  But I am no longer going to need a swap partition. And since I'm using GPT, I don't need to worry about extended partitions either.  I can theoretically have the four primary partitions I wanted plus the bios_grub partition (sda1 - sda5). Please correct me if I've got any of that wrong.

Yes, I think this is correct :-)
> 
Question:  I read that an ESP (EFI System Partition) can exist on a GPT disk or an MBR disk.  It looks like I'd benefit from an ESP also?  If so, I'd set the boot flag for that partition?  

Yes, Linux needs no boot flag for BIOS boot, so you can put that flag on the ESP partition.
> 
Question:  Re the BIOS Boot Partition, how big should I make it? Does it need to be located first on my SSD?  I understand that I need to set the flag as bios_grub.

The bios_grub partition need only be 1 MiB (mibibyte). (But notice that when people say 'boot partition', they mean something else. It is a partition where the linux kernel and the grub.cfg file and kernel drivers reside. But I would recommend that you do not create such a partition, but let it be a directory in the root partition. This is simpler and reduces the risk that it will get full and make updates of the kernel fail.)
> 
Question:  Are there any changes I need to make to my BIOS settings so that they support the approach above?

If you have already set it to boot in BIOS mode that is fine.

But maybe your Windows was using the internal drive as RAID or something similar. Ubuntu wants the drive to run in AHCI mode - you may need to check or modify that (this is independent of BIOS and UEFI mode).
> 
Question:  What would the mount points be for my Ubuntu partition, my ESP and my BIOS boot partition?  I'm guessing that the Ubuntu partition would be root (/).  I think I read that the mount point for ESP would be /efi/boot or /efi/boot/, but is that correct in my particular situation (not using UEFI)?  I have no idea what the mount point would be for the BIOS boot partition.

It is easiest to let Ubuntu select mount points automatically. But if you want to create partitions manually, you have to specify the mount points too. The bios_grub partition and the swap partition have no file system and hence there will be no mountpoint. The root mountpoint is / (forward slash) and I think that Ubuntu does not bother with the ESP partition  when installed in BIOS mode.
> 
Last Question:  Do I need to edit my fstab?

I would expect that you need not edit fstab. Things should be correct automatically..
> 
**

Okay, a gparted question.  Is gparted on the Live USB I created to install Ubuntu?  I created another/different Live USB with just gparted on it.

Yes, it is there in the Ubuntu live drive. You need no other drive.

---

### Post by oldfred on 2020-01-24
If drive is not gpt, you have to do that first in gparted. 
Select gpt under device, advanced over msdos(MBR) default partitioning before starting.

I have not seen a specific rule on where an ESP needs to be on a drive. UEFI says first, Windows makes it second or even third. And several users had it fairly far into a 1TB drive. You do have to have the bios_grub in the first 2TiB of a drive.
I like to make them first and used to have swap last as those were partitions I would never change and then would not be in the way if I was changing or adding other partitions.

If you have data partition(s), you will have to manually mount those. And best to just edit fstab and use a template for the format you use. Disks can do it, but it does not use the best parameters.

---

### Post by ardvark-700 on 2020-01-25
Here's what I'm leaning towards if you don't see any problems ...

/dev/sda1 ... Ubuntu installation, holding root, /boot & /home 
/dev/sda2 ... future use, another distro
/dev/sda3 ... data partition (sharing/storage/backup)
/dev/sda4 ... BIOS Boot, aka bios_grub partition
/dev/sda5 ... EFI System Partition

> But notice that when people say 'boot partition', they mean something else. It is a partition where the linux kernel and the grub.cfg file and kernel drivers reside.  But I would recommend that you do not create such a partition, but let it be a directory in the root partition. This is simpler and reduces the risk that it will get full and make updates of the kernel fail.

Sudodu, when you say, "I would recommend that you do not create such a partition," do you mean don't create a boot partition or don't create a bios_grub partition?  Because on the Arch Wiki it says, "On a BIOS/GPT configuration, a BIOS boot partition is required. GRUB embeds its core.img into this partition."

> But maybe your Windows was using the internal drive as RAID or something similar. Ubuntu wants the drive to run in AHCI mode - you may need to check or modify that (this is independent of BIOS and UEFI mode).

Sudodus, I do have Windows 7 running on a second computer, but my Ubuntu computer, the one I've been struggling with, only has Ubuntu running on it. I checked my BIOS just now, and AHCI is definitely checked.

> If drive is not gpt, you have to do that first in gparted. Select gpt under device, advanced over msdos (MBR) default partitioning before starting.

Thank you for that because I'm new to using gparted, and I wouldn't have known.

If I could go back to the swap partition for a bit, I probably need to clarify something.  I use a VPN with a kill switch.  The Windows app works flawlessly.  The Linux app isn't as robust, and every time my laptop hibernates (or when I reboot), something is lost or corrupted, necessitating my uninstalling & reinstalling the VPN software.  This is supposed to be addressed in a future update.  When I purchased it, my Ubuntu laptop only had 2 GB of swap, so not enough to hibernate.  That's why I was talking about creating a swap with 16.1 GB because I have 16 GB of RAM.  I don't know for a fact that it will correct the problem I was having with my VPN, but that was my thinking.  If Ubuntu is allowed to create the swap it needs, would I still be able to hibernate?

Oh, yes, one last question.  I read that the mount point on the ESP is typically /boot/efi.  When I install Ubuntu, will it create that file/directory/path, or will I have to create it before it will work?

---

### Post by sudodus on 2020-01-25
> **ardvark-700 said:**
> Here's what I'm leaning towards if you don't see any problems ...

/dev/sda1 ... Ubuntu installation, holding root, /boot & /home 
/dev/sda2 ... future use, another distro
/dev/sda3 ... data partition (sharing/storage/backup)
/dev/sda4 ... BIOS Boot, aka bios_grub partition
/dev/sda5 ... EFI System Partition


Sudodu, when you say, "I would recommend that you do not create such a partition," do you mean don't create a boot partition or don't create a bios_grub partition?  Because on the Arch Wiki it says, "On a BIOS/GPT configuration, a BIOS boot partition is required. GRUB embeds its core.img into this partition."

You need a bios_grub partition in order to boot in BIOS mode with a GUID partition table (GPT). What I wrote was that you should have /boot in the root partition (as you describe above).
> 
Sudodus, I do have Windows 7 running on a second computer, but my Ubuntu computer, the one I've been struggling with, only has Ubuntu running on it. I checked my BIOS just now, and AHCI is definitely checked.
That's good > 

Thank you for that because I'm new to using gparted, and I wouldn't have known.

If I could go back to the swap partition for a bit, I probably need to clarify something.  I use a VPN with a kill switch.  The Windows app works flawlessly.  The Linux app isn't as robust, and every time my laptop hibernates (or when I reboot), something is lost or corrupted, necessitating my uninstalling & reinstalling the VPN software.  This is supposed to be addressed in a future update.  When I purchased it, my Ubuntu laptop only had 2 GB of swap, so not enough to hibernate.  That's why I was talking about creating a swap with 16.1 GB because I have 16 GB of RAM.  I don't know for a fact that it will correct the problem I was having with my VPN, but that was my thinking.  If Ubuntu is allowed to create the swap it needs, would I still be able to hibernate?

In order to hibernate you need that size of swap, which could be either a huge swapfile or a partition. And with GPT, there is no problem to have an extra partition. Use what you like better. But watch out for the units. RAM is measured in Gibibytes (2^30) and drive size usually in Gigabytes (10^9). So you need 16.1 Gibibytes approx = 17.3 Gigabytes. 
> 
Oh, yes, one last question.  I read that the mount point on the ESP is typically /boot/efi.  When I install Ubuntu, will it create that file/directory/path, or will I have to create it before it will work?

I think that once you start with an own partitioning scheme, you have to specify which partition to use for system tasks, so yes, specify your ESP as you suggest

---

### Post by oldfred on 2020-01-25
You do not have to mount ESP. Install seems to automatically find and use it. In fact it is an issue with Ubuntu's Ubiquity that it always sets the first drive, usually sda or first NVMe drive as drive for ESP. Some install to an external or sdb drive and want to use an ESP on that drive, but Ubiquity will not let you without some extra effort.

The bios_grub is only 1 or 2MB unformatted with bios_grub flag.
The ESP - efi system partition is FAT32 with boot and/or ESP flags. Windows uses 100MB and Ubuntu can share that. But we often recommend larger like 500 to 600MB in case you have other systems, use other boot managers like rEFInd or even other boot loaders than grub. More for future proofing.Only if drive is small like a 32GB flash drive, may you then want smaller ESP. 
Not really recommended is a /boot partition which needs to be at least 500MB.

Both ESP & bios_grub are not required. When I was in the process of just starting to use UEFI, I included both on all new drives. But most now just have an ESP.
I like to have them first, but not required. UEFI has suggested it should be near beginning of drive. And bios_grub only has to be within first 2TB of a drive, so only very large drives have limits.

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

Backup efi(ESP) partition and Windows partition before Install of Ubuntu. Only one efi partition per hard drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)

---

### Post by ardvark-700 on 2020-01-27
Well, I did everything as precisely and carefully as I could.  I set up the following partitions in gparted:

sda1 Name=BIOS Boot, File System=ext4, Size=2MIB, Flags=bios_grub ***
sda2 Name=ESP, File System=Fat32, Size=488MIB, Flags=boot,esp
sda3 Name=Swap, File System=Linux-Swap, Size=15GIB, Flags=swap
sda4 Name=Ubuntu, File System=Ext4, Size=74.33GIB
sda5 Name=OS #2, File System=Ext4, Size=74.33GIB
sda6 Name=Data, File System=Ext4, Size=74.33GIB

*** Note:  After creating the partitions above, I got an exclamation point inside of a yellow-orange triangle on sda1.  Even though I selected unformatted as the File System for sda1, the File System changed from unformatted to ext4 when I executed "Apply All Operations."

I exited out of gparted, put in my Ubuntu Live USB and rebooted.  For Installation type I chose "Something Else" to check out the partitions I created.  My Linux-Swap showed a perfect 16.1 GB. As part of the installation, I did have to reformat sda4 and specify mount point as root (/) after getting, "No root file system is defined."  But rebooting after the install generated the following error message:

Boot Device Not Found
Please insall an operating system on your hard disk
Hard Disk - (3F0)
F2 System Diagnostics

I've obviously still missing something critical.

---

### Post by oldfred on 2020-01-27
Gparted always gives an error on unformatted partitions. So an error on the bios_grub is normal, just ignore it.
It must be unformatted, but is only used with a CSM/Legacy/BIOS type install.
You have to boot install media in UEFI boot mode and make sure UEFI has Secure boot off and CSM/Legacy turned on.

Device not found is an UEFI issue.  Often where vendors have violated UEFI standard that says NOT to use description as part of boot.

Post link to Boot-Repair;s summary report from latest install.

---

### Post by ardvark-700 on 2020-01-28
I am going to delete sda1 and recreate it so that it is unformatted because somewhere in the process of using gparted to manually create my partitions and installing Ubuntu, that partition now shows up as an ext4 partition.

> You have to boot install media in UEFI boot mode and make sure UEFI has Secure boot off and CSM/Legacy turned on.
 

I did this incorrectly.  Secure Boot is off & Legacy Mode is on.  But prior, when I booted in UEFI Mode, I got caught in a loop that I couldn't get out of.  See my Post #27.  Would changing the UEFI Boot Order help me get out of that endless, repeating loop?

Also, there is an area in BIOS ...

Boot Mode
[ ] Legacy
[ ] UEFI Hybrid (With CSM)
[x] UEFI Native (Without CSM)

I currently have Legacy selected, but you mentioned CSM.  Should I try UEFI Hybrid?  Prior to Legacy I had selected UEFI Native, but again, the result was that I got stuck in an endless loop.

Once I've got the BIOS settings right, I'll read up on how to do the Boot Repairs and paste the summary report for you to check out.

Thank you once again for helping me troubleshoot this.  Obviously I want a positive end result, but I'm learning a ton in the process.  By the time I've got this thing licked, I'm going to be a booting, installation, BIOS ninja. (smile)

---

### Post by oldfred on 2020-01-28
Your UEFI install would have not have worked if ESP was not FAT32.
If installing in BIOS mode to gpt partitioned drive you need the bios_grub partition.
In post #43 your partitions looked ok.

On one of my systems, I could never get it to boot in UEFI mode when UEFI was set for UEFI or BIOS.  The only UEFI setting worked but I had to have UEFI Secure Boot off. With UEFI Secure Boot on, there is no BIOS/Legacy boot mode.
But boot of flash drive is independant of UEFI settings. If Secure Boot is off, then you can boot flash drive in either UEFI or BIOS.

I relatively recently stopped adding bios_grub. For several years after getting UEFI system, I had both ESP & bios_grub. 

I just replaced my sda with new NVMe drive and my sdb is now sda.
```
Model: Samsung SSD 970 EVO Plus 500GB (nvme)
Disk /dev/nvme0n1: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name       Flags
 1      1049kB  538MB   537MB   fat32        esp_nvme   boot, esp
 2      538MB   32.0GB  31.5GB  ext4         focal_0
 3      32.0GB  63.5GB  31.5GB  ext4
 5      63.5GB  273GB   210GB   ext4         nvme_data
 4      469GB   500GB   31.5GB  ext4


```

---

### Post by ardvark-700 on 2020-01-28
That is incredibly helpful, OldFred!!!  I find it comforting that even with your knowledge & insight as to how things work under the hood, you have to try different variables/approaches yourself to be able to install Ubuntu & successfully boot.  In other words, I need to stop worrying about what I'm doing wrong and just figure our what's needed to get a positive result.

I will go do my homework (read, research, study), execute & report back.  That's why it takes me so long between posts.  I do my best to have at least a basic understanding of what I'm doing versus following along blindly, without a clue.

---

### Post by oldfred on 2020-01-28
If you want to get into the weeds, look at the link in my signature. Some find it too much.

---

### Post by dragonfly41 on 2020-01-28
More weeds here.

After many experiments I have resorted to using rEFInd.

[https://www.rodsbooks.com/refind/installing.html#linux](https://www.rodsbooks.com/refind/installing.html#linux)

Requirements.

Partition 1 in the external drive (holding Ubuntu) is ESP fat32 partition   with **boot, esp** flags

Install rEFInd

```
sudo apt-add-repository ppa:rodsmith/refind
sudo apt-get update
sudo apt-get install refind
```


This will install rEFInd.

Installation appears in /boot/efi/EFI/refind (alongside other boot folders).

In boot options (F2?) place rEFInd Boot Manager at top of options.


[P.S] reFIND boot manager is also listed in oldfred's corpus.

---

### Post by ardvark-700 on 2020-01-28
I deleted & recreated sda1.  I "Applied All Operations."  File  System = Unformatted, Primary partition, Size = 2 MIB, Aligned to MIB,  with 1 MIB before and 0 MIB after the partition.  After I "Applied All  Operations," I set the bios_grub flag.  Something different from the  last time I created sda1 is that the File System reads "grub2  core.img."  Last time it read "ext4."

I exited gparted, shut down  my computer & restarted it.  I went into my BIOS & changed the  boot options from Boot Mode = Legacy to Boot Mode = UEFI Native (Without  CSM).  If I don't boot successfully, I'll also try Boot Mode = UEFI  Hybrid (With CSM).  It seems that when I make changes to my BIOS, Fast  Boot defaults to ON.  I turned it back off again. Secure Boot is off.

I did not make any changes to the UEFI Boot Order.  The order is as follows: 

OS Boot Manager
Generic USB Device
Notebook Ethernet IPV4
Notebook Ethernet IPV6
USB Hard Drive
eSATA Hard Drive
Notebook Upgrade Bay
SD Card
HP Hypervisor
Customized Boot

I  saved my changes & exited BIOS.  My laptop did not start Ubuntu.   Instead I got the following message, "No bootable image found, notebook  will be shut down."

I went back into BIOS and changed Boot Mode = Hybrid (with CSM). I saved my changes & got the following error message:

Boot Device Not Found
Please install an operating system on your hard disk
Hard Disk - (3F0)
F2 System Diagnostics

At  the bottom of Message #43, you asked me to post the summary report from  Boot Repairs.  I'll do that a little later today, after I read up on  how to do that.

I checked the HP Support Forum to see if anyone  replied to my post about updating UEFI from a different HP laptop.  The  HP website scans your system to make sure they are providing you with  the correct driver or version of software for your system.  No one  replied to my message, so I cross-posted on the Notebook OS &  Recovery forum. 

And yes, I will make reviewing the UEFI Boot Intall & Repair help file my first order of business.

@dragonfly41, that's an interesting variable.  I have to play with the "Try Before You Buy" Ubuntu installation option to see if I could download rEFind.

---

### Post by dragonfly41 on 2020-01-28
> [COLOR=#000000]I have to play with the "Try Before You Buy" Ubuntu installation option to see if I could download rEFind.[/COLOR]

You can install rEFInd into a LiveUSB (although you need to do this each time since LiveUSB is non persistent). Then copy /boot/efi/EFI/refind folder from the LiveUSB over to the /boot folder in the target drive where you install Ubuntu. You can also customise the rEFInd menu by exploring refind.conf in /boot/efi/EFI/refind to add a custom menu entry.  But you will need to have handy the UUID and PARTUUID of the target Ubuntu partition using ..

  sudo blkid

Also when booting I would untick all the other boot options or try "One time boot option" and select rEFInd Boot Manager from BIOS list.

---

### Post by oldfred on 2020-01-28
The bios_grub is 1MB unformatted for BIOS boot only.
The ESP - efi system partition FAT32 is only for UEFI boot and anywhere from 100MB to 500MB or more.

HP typically wants a Microsoft entry.
But can boot the fallback or hard drive entry which is what rEFInd uses. It has you rename its .efi file to /EFI/Boot/bootx64.efi.
I have used rEFInd on one of my old too small for anything else flash drives as emergency boot. Seems to find all my installs and offered to boot them.

---

### Post by ardvark-700 on 2020-01-28
DragonFly & OldFred, thank you once again.  I have lots of great information provided by the two of you to study & act on.  All of the concepts related to Linux are new to me ... things like GRUB & bootloaders, UEFI, MRB & GPT.  Sometimes I feel like a third grader in a college-level class, with all of the other students pretty much getting it, but not me.

OldFred, did I understand you to say that one of your installations actually required getting rid of the bios_grub partition for the installation to work?  At this point, I think you and I are both leaning towards a Native GPT/UEFI without CSM for my laptop.   Am I right about that, as I start studying studying the whole rEFInd & bootloader(s) topic?

Legacy Mode was left on/selected when I tried UEFI Native & Hybrid.  Was I correct in doing that?

---

### Post by dragonfly41 on 2020-01-28
This is another case study (one of many) which draws me to the conclusion that some form of "expert system" is needed to walk the user through the entire process. Certainly I encountered my own difficulties in adding my external drives.
I will get around to experimenting with this idea. But for today I'm shutting down.

---

### Post by oldfred on 2020-01-28
I started using gpt back in 2010 for all new or repartitioned drives.
But Microsoft did not standardize on gpt until Windows required UEFI/gpt with the release of Windows 8 in 2012.
Before that gpt was used on newer Mac and Linux made gpt support available.

So my old BIOS system using gpt needed the bios_grub. So when in about 2014, I got my first UEFI system, I keep both ESP and bios_grub on all new drives, just in case I wanted BIOS or to experiment. I now normally do not add the bios_grub partition anymore.

Many users with HP have had issues.
Some give up on UEFI, others with somewhat newer HPs say the UEFI update helps.

I would suggest that you do UEFI update first.

---

