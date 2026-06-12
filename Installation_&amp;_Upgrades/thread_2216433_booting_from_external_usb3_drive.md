---
title: "booting from external usb3 drive"
date: 2014-04-11
forum: Installation &amp; Upgrades
---

### Post by gdesilva on 2014-04-11
Hi,

I have come across this strange problem when trying to boot from an external USB3 drive. I haven't seen this problem with external USB2 drives.

Here is the background - note that the external USB3 drive is plugged into a USB2 socket in all cases.


1. On a integrated HP Desktop

[LIST]
[*] Installed Ubuntu 13.10 Desktop on the USB3 drive using the LiveCD. Installation was successful. 
[*]try to boot from the USB3 drive 
[*]grub-rescue error message stating that /boot/grub/i386-pc/normal.mod not found - boot fails. 
[*]booted from LiveCD and checked and normal.mod file does exist in the path listed. 
[*]re-installed grub manually on the USB3 drive - still the same message appears. 
[*]could not proceed further testing as this was done at a friend's place. 
[/LIST]

2. On a Dell laptop 

[LIST]
[*] Installed Ubuntu 13.10 Desktop on the USB3 drive using the LiveCD. Installation was successful. 
[*]try to boot from the USB3 drive 
[*]grub-rescue error message stating that 'boot sector not found' - boot fails. 
[*]unplugged the USB drive and rebooted the machine 
[*]plug back the USB drive when the BIOS screen appears 
[*]Now I can boot from the USB3 drive 
[/LIST]

3. On an newer HP Desktop
[LIST]
[*]Tried the process above but cannot boot from USB3 at all. 
[/LIST]

I did some research on this and noted that this could be due to xhci-hcd module not being loaded. But there is no such module in /boot/grub/i386-pc to load using grub command line options. I haven't tried this with USB3 ports - just that I do not have one and I have tried this with a Seagate and a Toshiba USB3 drives.

Any suggestions?

Thanks.

---

### Post by oldfred on 2014-04-11
Did you install in UEFI mode? And on some systems are booting in BIOS mode?

 /boot/grub/i386-pc/normal.mod not found
Not booting in UEFI mode
Manual boot works
set root=(hd0,gpt8)
set prefix=(hd0,gpt8)/boot/grub
insmod linux
linux /vmlinuz root=/dev/sda8 ro
initrd /initrd.img
boot

This could also be a hard drive, just happens to be a flash drive.

 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

Best to see details.
      
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by sudodus on 2014-04-12
Some new and middle-age HP computers have difficulties booting from grub on USB drives. See this link
[URL="http://ubuntuforums.org/showthread.php?t=2196858"]
Howto help USB boot drives[/URL]

One solution can be to chainload the system you want to run, either you build chainloading into your installed system (in an internal drive), or you boot from a good booter (for example the Chainloader software in the link), and chainload from it to the system you want to run.

---

### Post by TBeholder on 2014-04-12
One of problems with such setups is that "/dev/sda8" and possibly "hd0" are not fixed, and depending on a lot of things starting from BIOS and your drive's bells & whistles booting with inserted or removed LiveCD or LiveFlash may change the identifiers.
Same applies to /etc/fstab mounting correct partition - you may need to start gparted on LiveCD, look up UUIDs in partition properties and change lines like "**/dev/sda1**  /  ext4 defaults" to something like "**UUID=12345678-abcd-1234-abcd-1234567890ab**  /  ext4 defaults"
So even if unlikely, check such things when there are boot issues after installation or adding new drives. I ran into this once, with LiveFlash drive inserting itself before /boot flash drive - with USB it's going to happen as often as not, obviously.

---

### Post by gdesilva on 2014-04-12
Thanks for all the responses. I will check out suggestions each of you have made. I have been doing more tests over the last day or so. Here are my findings so far.

1. very very old Dell GX260 - no problems at all. Recognized as a boot device and boots normally
2. old Dell Dimension 9150 - no problems. 
3. old Dell Inspiron 9450 - if the drive is plugged in when power is turned on, I get 'boot sector not found' message. However, if I plug the drive just when BIOS screen comes up no problem in booting.
4. HP 8200 - not recognized as a boot device irrespective of what I do. I have UEFI disabled on this system.

Unfortunately, I do not have access to my friends HP machine at the moment - the problem was uncovered when I was helping him install Ubuntu. On this machine, grub-rescue puts out the error message '/boot/grub/i386-pc/normal.mod file not found' although it does exist on the drive.

I will pursue with your suggestions and post the findings here in a day or so.

Many thanks for your suggestions.

---

### Post by gdesilva on 2014-04-13
Hi,

Since it appears that the issue is mainly with HP systems I thought of trying out sudodus'  suggestion first.

As mentioned in the link, I tried the 40_custom method. Edited 40_custom file as per instructions but when I select the entry to boot I get, 
'hd1' cannot get c/h/s values' message.

Will try boot repair as suggested by oldfred and post the results later.

Thanks guys.

PS. BTW tried out on a newer Dell Inspiron laptop and it booted without any problems.

---

### Post by sudodus on 2014-04-13
Too bad the 40_custom method did not work for you.

- Did you remember to run ```
sudo update-grub
``` after editing the 40_custom file?

- Did you try with some other than hd1 device? You can modify that manually while in the grub menu:

. Select the relevant grub menu line
. Press **E** to edit the commands (and modify the device from hd1 to some other possible choice).

Start using it with ***ctrl + X***

-o-

Anyway, good luck trying all the advice suggested. Oldfred has much longer experience than I, and his advice is generally very good.

---

### Post by gdesilva on 2014-04-13
@sudodus, yes I did run 'update-grub' after editing the 40_custom file. And also tried different device numbers - just out of sheer desperation!

Yes, will try Oldfred's suggestions next.

There are some differences between the Toshiba USB3 drive and the Prolific USB3 Docking device - the latter showing extra capabilities in Windows device manager. Also did a comparison using 'lsusb -v' and noticed that Toshiba has a max power figure of 500mA as opposed to 100mA on the Prolific. There were one or two other differences but I have no clue as to what they are. My hunch at this stage is that it may be related to power but I may be totally off the track here.

---

### Post by oldfred on 2014-04-13
The old machines were booted in BIOS mode as that is all they have.
Your new machine may boot in either UEFI or BIOS mode and HP's seem to have more issues than some others.

Have seen others with external drives that are slow in coming up to speed and causing issues, often better to have external power if that is an option.

Hard drives have not used c/h/s values since drives when over 8 GB in the late 1990s. Back then we had to manually set those values in BIOS to match hard drive. May be an old message for some other error.
If new system UEFI/BIOS should be in AHCI if possible. There maybe other UEFI/BIOS settings for the drive.

---

### Post by gdesilva on 2014-04-14
@Oldfred,

Just tried to do the manual boot as mentioned earlier in your post but 'insmod linux' command fails with 'cannot get C/H/S values' message and could not proceed any further.

What is interesting is that on the HP in the Boot menu, I selected the Legacy Boot option and here my USB3 drive is not even listed. I only have the internal SATA0 and the DVD drives to choose from. I have installed Ubuntu Studio on the internal HDD and have been dual booting with Windows without any issues. I can use my USB3 HDD Docking device, install any Linux OS on it an boot from it without any problems. 

Given the USB3 Drive is not even detected at BIOS perhaps this may be a hardware issue?

I appreciate your views on this.

Many thanks.

---

### Post by oldfred on 2014-04-14
If in legacy mode it may be a hardware issue.
But many with UEFI have settings that hide devices.
All UEFI systems will only show secure boot devices when secure boot is on. But legacy has no secure boot so that should not be an issue.

What mode is drive seen as? Should be AHCI, but could be Large or LBA. But not RAID nor IDE. And IDE is the old system with c/h/s values but that is all automated with LBA or later drive configurations.
Does system also have Intel SRT? That is a sort of RAID.

With UEFI you do have to have the 64 bit version, but old systems may have needed the 32 bit version. So is it the 64 bit installer?

Others with HPs, various models, but most seem to have similar issues. Maybe someone posted a detail. I do not remember all the details.
 HP Envy 17  zero brightness, use f3 to change
acpi=off  worked for HP2000
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)
HP p6-2326 Ubuntu and windows 8 Boot DVD
[http://ubuntuforums.org/showthread.php?t=2093445](http://ubuntuforums.org/showthread.php?t=2093445)
HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts. Key board issues try differnet USB ports maybe  front.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
HP Touchsmart 15
[http://ubuntuforums.org/showthread.php?t=2213041](http://ubuntuforums.org/showthread.php?t=2213041)

---

### Post by gdesilva on 2014-04-14
@oldfred,

Just going through your suggestions.

BIOS is set up for AHCI mode. 

Tried 64-bit installer - still no joy.

Will go through the rest and post the outcome.

Thanks

---

### Post by gdesilva on 2014-04-15
Unfortunately, the friend I am helping with this, has decided not to proceed with external boot device. He has taken back the USB3 drive so I cannot proceed with more testing!

Thanks everyone for very constructive ideas and support. I will close this thread.

---

### Post by gdesilva on 2014-05-06
I have done a few more tests on this and would like to share the outcome and seek advice on this matter.

1. I have a USB3 HDD Docking Device. When I first posted this device was plugged into a USB2 port since I did not have any USB 3 ports on my system.
2. The Docking Device when plugged into USB2 port gets recognized as a Legacy Boot Device and I can boot Linux without any problem.
3. Yesterday, I bought a USB3 PCIe card and plugged into the system.
4. This card is correctly recognized as a USB3 PCI card.
5. Then I plugged in the Docking Device into the new USB3 port on the system.
6. The device now does not appear as a bootable drive.
7. If I plug the device to USB2 port again it becomes a bootable device.

So, it appears to me that if I plug a USB3 device then for some reason it fails to be recognized as a bootable device.

I would appreciate if any one has any thoughts or suggestions on this.

Many thanks.



EDIT: Did a internal HDD boot. No problems accessing the USB3 HD Docking Device which connected via the USB3 port. Did a update-grub and tried to select the external USB drive but I get the 'Invalid C/H/S' message.

---

### Post by sudodus on 2014-05-06
It might be a hardware issue or a BIOS issue, or an issue about the cooperation between the USB3 docking device and the USB3 PCI card.

Maybe you can borrow or buy a [cheap] USB 3 pendrive to test if it will be recognized and bootable via your USB3 PCI card.

I suspect that the USB3 HDD Docking Device does not conform to the USB 3 standard.

You may find more tips in the following links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)
[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

[Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

---

### Post by gdesilva on 2014-05-07
> **sudodus said:**
> It might be a hardware issue or a BIOS issue, or an issue about the cooperation between the USB3 docking device and the USB3 PCI card.



It certainly looks like an issue with USB-SATA bridge and the USB3 PCI card.

However, came across this [http://www.sevenforums.com/hardware-devices/217521-can-t-boot-usb-3-0-flash-drive-usb-3-port.html](http://www.sevenforums.com/hardware-devices/217521-can-t-boot-usb-3-0-flash-drive-usb-3-port.html) which tends to conclude that this is a mobo restriction and nothing to do with the OS. I certainly can agree on the fact that this has nothing to do with the OS as once booted the drive becomes visible and accessible whether I run Ubuntu or Windows7. It is just that BIOS does not recognise it as a bootable device and hence the inability to boot from it.

I will try a USB flash drive as suggested but either way it appears I have come to an dead end.

I guess the morale of the story is do not try to boot off external USB3 drives unless you have USB3 support on your mobo.

---

### Post by gdesilva on 2014-05-09
I bought a 16GB USB flash drive and plugged it into USB3 port - no luck. It does appear as bootable if I plug it into a USB2 port. Once the OS (all Linux versions and Windows) is loaded it is listed as USB3 device.

All my efforts tend to indicate that this is a problem with BIOS in older machines. So, if you want a USB drive bootable and are using an old machine, I think it is safer to go for a USB2 drive.

---

### Post by sudodus on 2014-05-10
I think the problem is the BIOS ***or*** the USB3 PCI card.

My experience is that many USB 3 pendrives have faster flash memory and will be faster than USB 2 pendrives also in USB 2 ports.

See this link [https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

I hope and think that you will find the 16 GB USB 3 flash drive useful, even if you can't boot it with USB 3 speed :-)

---

### Post by gdesilva on 2014-05-11
@sudodus, yes, the flash drive will be useful anyway! I have raised a support case with HP and will post the outcome here - not holding my breath on a solution though:mad:

---

### Post by gdesilva on 2014-05-19
After many more tests and research finally I received the following response from Steve at RMPREP ([http://www.rmprepusb.com/](http://www.rmprepusb.com/)) which to me makes a lot of sense - thanks Steve. Here is Steve's response....

[COLOR=#0000ff][I]The short answer is - you cannot boot via the BIOS on any device  that is an 'add-in' device, unless that it is a PCI card that also  contains an option ROM.
[/I]


*Think about how the BIOS works...*

*The BIOS knows that it's mainboard contains a certain chipset.*
*The BIOS contains the code required to access the registers on that chipset.*
*The BIOS has to have code which allow the operator to boot from devices connected to the chipset.*
*If the chipset has an ABC chipset, then the BIOS will contain code to access an ABC chipset with ABC-type USB registers.*


*Now you connect a PCI card containing  a different (Renesas) chip. The BIOS will see a XYZ chip connected to  the PCI Bus when you switch on the system, but the BIOS does not contain  any code to access this XYZ chip - it does not even 'know' that the  chip has USB 3.0 ports connected to it. In fact, when the BIOS code was  written by the manufacturer, USB 3.0 chips did not even exist!*

*It would be the same even if you connected a USB 2.0  Renesas add-in card - the BIOS only contains code to boot from the  chipset on the mainboard, it does not contain code for the 1001  different cards that could possibly be connected to the PCI bus.*

*So you cannot expect your system to boot from an add-in card.*


***So how can you add a SATA Add-in card to a system and how come it can boot from SATA drives then?***
*You may well ask this question!*

*These  add-in cards contain a option ROM - a chip that contains extra BIOS  code. VGA cards also contain these option ROMs so that you can see the  BIOS text and setup menu etc when you switch on the computer. *

*When the computer is switched on, it looks for  Option ROMs and adds the code in the Option ROM to it's own BIOS code.  In this way, the BIOS 'knows' about the extra chips that are now in the  system.*

*Unfortunately, I am not aware of any USB 3.0 add-in  cards which have their own Option ROMs that allow you to boot from their  USB 3.0 ports. There are products such as *
[/COLOR][I][[COLOR=#0000ff]http://www.amazon.co.uk/ASUS-U3S6-USB-SATA-PCIe/dp/B002VVQ58M/ref=cm_cr_pr_product_top[/COLOR]]("http://www.amazon.co.uk/ASUS-U3S6-USB-SATA-PCIe/dp/B002VVQ58M/ref=cm_cr_pr_product_top")[COLOR=#0000ff]
[/COLOR][/I][COLOR=#0000ff]
*which contain an Option ROM, but this only allows you to boot from the SATA devices and not from the USB 3.0 devices.*


*You have these options available:*

*1. Get a mainboard\system that has a USB 3,0 chipset and ports*
*2. Plug your USB 3 devices into your systems USB 2.0 mainboard ports*
*3.  Use a Virtual Machine and connect your USB drive to the Renesas USB 3.0  port - however anything you boot to will see the USB drive as a non-USB  hard disk and not a USB 3.0 drive). It does mean that most things will  boot at USB 3.0 speeds in the VM though (see RMPrepUSb - Tutorial 4 and  the video).*


*Also bear in mind that many bootable  OS's do not contain support for USB 3.0 chips, so even if you could boot  from a USB 3.0 port, once you boot to an OS (e.g. Vista\Win7 or many  linux distros) the boot will fail because it cannot access the USb drive  on a USB 3.0 port as it does not contain any USB 3.0 drivers.*
 [/COLOR]

Hope this information will be useful to others who are experiencing the same problem.

---

### Post by sudodus on 2014-05-20
Thanks for sharing :-)

---

