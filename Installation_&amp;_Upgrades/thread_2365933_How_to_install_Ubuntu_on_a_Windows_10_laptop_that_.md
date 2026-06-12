---
title: "How to install Ubuntu on a Windows 10 laptop that can't boot from external devices?"
date: 2017-07-12
forum: Installation &amp; Upgrades
---

### Post by slex-dir on 2017-07-12
The short story. I have a laptop that comes with Windows 10. I want to install Ubuntu, but I can't boot from either a USB flash or an external CD (the laptop doesn't have its own CD drive). 


The long story. It is a Toshiba R500 laptop. I bought it on the internet second hand. It's an old laptop and the hardware (2 GB of RAM) is not enough to run Windows 10 well. I bought the laptop for the transflective screen, because it is easier on the eyes, I don't really care about RAM and CPU power this much, because I intend to use it for surfing and office work. So the configuration is OK for that, as long as it has some light distro on it. I thought that installing Linux will be easy, but it turns out the boot order is set to the primary hard drive first and I can't change it from the BIOS, because it requires a master BIOS password and the previous owner wouldn't tell it or just doesn't know it. I gave the laptop to a repair service shop and they said that once the hard drive (SSD) is removed, it boots from a flash drive. They couldn't do anything about the BIOS and the boot order. 

So I am trying to figure out how I can install Ubuntu, starting the installation from within Windows 10 somehow and doing the partitioning and the changes to the master boot record this way. I am also willing to format the hard drive entirely, which I presume will allow me to boot from a USB, once the operating system is removed from the hard drive. I have no idea how to do it, given that I am within a Windows 10 environment.

Any suggestions?

---

### Post by yancek on 2017-07-12
> 
So I am trying to figure out how I can install Ubuntu, starting the  installation from within Windows 10 somehow and doing the partitioning  and the changes to the master boot record this way. 

It is difficult  to boot any "installed" Linux from the windows bootloader.  I don't know of any way you can boot a Linux iso directly or extracted from windows.  If you had a Linux distribution installed with the Grub bootloader, you could then easily boot Linux or windows that way.  If you have a default windows 10 install, the MBR doesn't come into play because it is probably UEFI (you would have to check that) and if so it goes from the BIOS directly to the EFI partition on the drive and not to the MBR.

Best solution would be to get the BIOS password from the previous owner but I expect that is long forgotten.  Don't know why s/he wouldn't give it to you otherwise?

---

### Post by slex-dir on 2017-07-12
He said it should boot fine from external CD, because that's how he installed Windows 10 (originally the laptop is with XP). He said he knew of no BIOS password. I don't know if it has EFI, it is an old computer (make 2007) and it has an original BIOS. If it is a feature of the BIOS, probably it is not there.

Right now I think that probably if I can wipe out my HDD, I will be able to boot from USB, but all the partition managers I tried can't do this from within Windows.

---

### Post by 2011spook on 2017-07-12
> **yancek said:**
> It is difficult  to boot any "installed" Linux from the windows bootloader.  I don't know of any way you can boot a Linux iso directly or extracted from windows.  If you had a Linux distribution installed with the Grub bootloader, you could then easily boot Linux or windows that way.  If you have a default windows 10 install, the MBR doesn't come into play because it is probably UEFI (you would have to check that) and if so it goes from the BIOS directly to the EFI partition on the drive and not to the MBR.

Best solution would be to get the BIOS password from the previous owner but I expect that is long forgotten.  Don't know why s/he wouldn't give it to you otherwise?

from the original post im willing to bet its installed by bios, and NOT UEFI due to the fact he stated old laptop 2gig ram and win10 run like crap,
if thats the case were not looking at any secure boot BS.
so with a locked bios(never buy a computer with a locked bios) this is what you could do, plug the hard drive into another computer as in make sure this would be the only HD plugged in install ubuntu on it, then move the HD to the laptop.
if im right and this is a laptop without UEFI and secure boot. this will work.
is it a pain... yeah.
but your only other option is shorting the bios chip to reset the password, which could brick the laptop if you screw it up... and that is very easy too do.

basically in the future never buy a computer with a locked Bio's
may sound like a killer deal. but your basically buying a crippled computer.

---

### Post by CatKiller on 2017-07-12
Potentially, you might clear the password (and reset everything else in the BIOS to default) by unplugging the laptop, disconnecting the battery, and removing the CMOS battery. I have no idea how accessible any of those components are on that model.

---

### Post by yancek on 2017-07-12
If the computer is 10 years old and originally had xp, then it almost certainly isn't UEFI.  If the person from whom you purchased the machine says there is not BIOS password, I would suggest you investigate the BIOS a little more for methods to boot from a usb hd.  A lot of machines which came with xp were not capable of booting from a usb but you need to check the BIOS options.

---

### Post by slex-dir on 2017-07-13
He said he doesn't know, but there is such a password. I've also tried to boot from an external USB CD, the same result.

I managed to remove Windows 10 from the console of Windows Recovery Mode with the diskpart utility. Now I no longer have Windows 10 on it, but it still doesn't boot from USB. 

When the BIOS loads it shows possible boot devices as icons and there is an USB stick. However because of the master BIOS password I can't change the boot order. Probably it is possible to put the SSD on another laptop with another BIOS and install the operating system there. I don't have a clue about hardware though.

---

### Post by sudodus on 2017-07-13
> **slex-dir said:**
> Probably it is possible to put the SSD on another laptop with another BIOS and install the operating system there. I don't have a clue about hardware though.

Yes, this is possible. The Ubuntu family flavours (standard Ubuntu, Kubuntu, Lubuntu ... Xubuntu) are portable between PC computers if you avoid proprietary drivers. So you can install the operating system in another computer, and after that move the SSD to this particular one with the BIOS password.

But you should be sure to install in the same mode, and because of the age, we think it is BIOS mode (not UEFI mode).

It helps, if you remove/replace the [other] internal drive in the computer where you install the operating system. Otherwise the bootloader might be installed into the wrong drive.

If you wish, you can clone from a compressed image file of a minimal Ubuntu system, that can boot in both UEFI and BIOS mode, and after that install the desktop environment that you want. See this link,

[help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)

I would recommend a flavour of Ubuntu with a light desktop environment

- Lubuntu with ultra-light LXDE
- Ubuntu MATE with medium light MATE
- Xubuntu with medium light XFCE

and I would suggest that you try live with no internal drive (start trying with the version 16.04.1 LTS). See the following links

[Try Ubuntu (Kubuntu, Lubuntu, Xubuntu, ...) before installing it](https://ubuntuforums.org/showthread.php?t=2230389)

[How to select the version and flavour of Ubuntu](https://ubuntuforums.org/showthread.php?t=2230389&p=13540865#post13540865)

---

### Post by RobGoss on 2017-07-13
Most systems have a jumper that can be removed from the mother board, once this is done you will be able to access and change the BIOS settings

I have a few Dell Optiplex 755 I had to remove the lithium battery / Jumper, in order to change the BIOS settings, once that was done everything worked good and was able to install Ubuntu

---

### Post by oldfred on 2017-07-13
Some of my old BIOS systems had USB boot, but booting a flash drive was not one of the many USB boot options. It was under hard drive boot options.

First time I tried every USB boot option and nothing. And I knew flash drive was correct as I had booted it on another system. And then one day while for some reason I had flash drive still plugged in and rebooted and saw hard drive boot options and it was listed there.

---

### Post by RobGoss on 2017-07-13
Exploring the BIOS settings with be the best option, now that you've removed Windows it's  just a question of getting that machine to boot from a USB drive

If all else fails your only option would be booting from a DVD drive

---

### Post by johndough2 on 2017-07-13
Hi

Bear in mind I know nothing...

1. Turn off the computer.
2. While holding the F8 key, turn on the computer.
3. The Advanced Boot Options menu will be displayed.
Use the arrow keys to select Repair Your Computer and press ENTER.
4. Follow the on-screen instructions.
###########
1. Turn off your computer.
2. While holding down 0 (zero) key on the keyboard, turn on your
computer.
3. A menu will be displayed from which you should follow the on-screen
instructions.
##################
1. Load the Recovery Discs into the optical disc drive and turn off the
computer's power.
2. While holding down F12 key on the keyboard, turn on your computer -
when the In Touch with Tomorrow TOSHIBA logo screen
appears, release the F12 key.
3. Use the left and right cursors key to select the CD-ROM icon from the
menu. Please refer to the
& BIOS Setup for further information.
4. A menu will be displayed from which you should follow the on-screen
instructions
#################

OK I see lots of possibilities. (I hope there is no fingerprint security)

Install over a network, install using USB / SD /DVD combinations.

You can override the settings and manually select a boot device by
pressing one of the following keys while the computer is booting:
U  Selects the USB floppy diskette drive.
N  Selects the network.
1  Selects the built-in hard disk drive.
C  Selects the CD-ROM*
M  Selects the USB memory drive
# # #
1. Hold down F12 and boot the computer.
# # # # 
Starting the BIOS Setup Program
1. Turn on the computer while pressing the ESC key - if the Password = prompt is displayed, enter either the Supervisor Password, if one is set, or the User Password and press the ENTER key. 
2. At the Check system. Then press [F1] key. prompt, press the F1 key - the BIOS setup application will start up.
====
Clear TPM Owner
This setting is used to erase the data stored as part of the Trusted Platform Module, as would be required, for example, when disposing of the computer or when the owner of the computer changes. Once this operation
is carried out, the Trusted Platform Module configuration settings are erased such that any encrypted data can no longer be decrypted and the files can no longer be read. In view of this you must ensure that you backup
or delete the data as necessary before carrying out this operation.
The procedure to follow is as detailed below:
1. Move the cursor to the Clear TPM Owner setting and press either the Space key or BACK SPACE key.
2. A message is displayed at which you should press the Y, E, S, and ENTER keys in sequence - the Trusted Platform Module information will
then be erased.
3. The Trusted Platform Module setting will then change from being Enable to Disabled and the setting no longer displayed
##########

The idea of removing the battery, power down and hold the start button for 30 seconds seems wrong.
#######################

[B]Clearing the CMOS as mentioned in an earlier post would be favourable.

So there is a possibility of a USB floppy with a cmos clearing floppy installed, I do have one somewhere.

Remove the HDD, this apparently causes a boot from usb et al.  
If so then I would have a DVD, USB primed and ready to go.  Also the SD card could be primed.  

Then when summat boots you install to one of the other devices, or to the removed HDD in a caddy. 

AND rebuild as necessary.[/B]

I believe this is achievable.

---

