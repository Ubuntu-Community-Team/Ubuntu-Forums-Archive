---
title: "?: XP/Ubuntu 10.10 dual-boot separate drives"
date: 2010-11-21
forum: Installation &amp; Upgrades
---

### Post by Splat_NJ on 2010-11-21
Hello folks. I'm only a week into Ubuntu/Linux but liking it big time. I  have a problem trying to dual-boot with XP and Ubuntu 10.10.

I have a PC with three IDE hard drives. XP Pro on first hd(/dev/sda) on  partition /dev/sda1,  storage partitions on the second hd, and now  Ubuntu 10.10 installed on third hd (/dev/sdc), on partition /dev/sdc1.  My swap, /home, and /usr are all on their own partitions on the third  drive. Everything works ok except I do not get any type of boot menu for  either OS. Upon install I had the boot loader installed to the first hd  /dev/sda. The pc would not boot further then "Grub." and blinking  cursor, no matter hitting the shift key, F12, any other keys. I then  reimaged the XP partition. The pc would boot directly to XP.

I then reinstalled Ubuntu onto the sdc1 partition. The swap, /home, and  /usr partitions set up the same way again. This time I installed the  boot loader onto device sdc. If the Bios is set to boot from the XP  drive then it boots to XP. If I change Bios to boot the third (Ubuntu)  drive the pc boots to a blank screen. If I boot holding the shift key  then I get "Grub loading." in top left of screen and blinking cursor.  Nothing else happens, and no drive activity. I've read up all day today  since this morning about restoring Grub and I'm still at a loss. Any  help is really appreciated.

---

### Post by oldfred on 2010-11-22
Lets confirm what is installed where - see below first as script will only help if not able to get to grub menu:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the post's menu and then paste the contents between the generated [ code] here [ /code] tags.

But if grub has not found the XP partition yet, it does not show the menu and continues loading. Many are having issues with Video drivers. If you hold shift key from BIOS until menu appears when booting sdc do you get the menu? If so try one of these depending on video card.

On first boot after install, press e on getting the GRUB bootloader. Use shift from BIOS if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by Splat_NJ on 2010-11-22
> **oldfred said:**
> But if grub has not found the XP partition yet, it does not show the menu and continues loading. Many are having issues with Video drivers. If you hold shift key from BIOS until menu appears when booting sdc do you get the menu? If so try one of these depending on video card.
On first boot after install, press e on getting the GRUB bootloader.

Hi Fred. Thanks for replying. I'll have to run the script after work today. For now let me say the video card is an old ATI Radeon card. Pressing the <e> key upon booting (after setting Bios to boot from the Ubuntu hd) does nothing. Pressing <shift> upon boot I get the "Grub loading." with blinking cursor at top left of screen and that's it.

If need be for troubleshooting I'll reinstall Ubuntu tonight and press the <e> key upon first reboot and see what happens.

---

### Post by awam66 on 2010-11-22
Hello splat,
If you are not getting the grub boot menu then there is no point in pressing "e". It looks like your grub installation is failing in some way. Are you sure grub is correctly installed on the master boot record of your first disk?

---

### Post by Splat_NJ on 2010-11-22
> **awam66 said:**
> Hello splat,
If you are not getting the grub boot menu then there is no point in pressing "e". It looks like your grub installation is failing in some way. Are you sure grub is correctly installed on the master boot record of your first disk?

I did try an install putting the boot loader on the XP drive, sda, but that only gave me a "Grub." on the screen and nothing else.

---

### Post by oldfred on 2010-11-22
You want to hold the shift key until the menu appears then you use the e for edit to edit the boot lines.

You never want to install grub to a windows partition. Grub2 is really only intended to install to the MBR of a drive. Windows has most of its boot code in its partition boot sector and if you install grub into that you overwrite the windows code. You then have to repair windows. We need to see boot script then to know what is where.

---

### Post by Splat_NJ on 2010-11-22
Ok, back from work, guys, and I reinstalled Ubuntu to the third hard drive (/dev/sdc1), putting the boot loader on /dev/sdc and everything works now if I change my Bios to boot from that third hard drive. BUT, still no boot menu if I change back my Bios to the default of booting from the first drive which is XP. I guess I have to edit XP's boot.ini file or............?

---

### Post by oldfred on 2010-11-22
This should find working windows:

sudo update-grub

If it does not find windows perhaps the comment about installing grub to the windows partition damaged it. If you run the boot info script we can suggest the best way to repair it.

---

### Post by Firem4nJoe on 2011-03-11
Yeah, I'm having the same 'separate HDD dual boot not working' issue also. But as this is really my first day on Ubuntu (10.10) I need step by step idiot-proof instruction as one would give a 5 year old.

If it makes any difference I'm running Win XP Pro SP3 on the other disc and here's my rather basic hardware info:

Abit SG-72 Motherboard
Intel P4 CPU
256MB Radeon 9200se VGA
1GB DDR RAM
80GB PATA HDD (XP)
320GB PATA HDD (Ubuntu)

If someone could direct me to the Multi-Boot for Noobs section I would greatly appreciate it.

Thank you :)

---

### Post by Firem4nJoe on 2011-03-11
Just came across this helpful tutorial [http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot](http://screencasts.ubuntu.com/Installing_Ubuntu_with_Windows_Dual-Boot)

---

### Post by Splat_NJ on 2011-03-11
I never tried further to get the dual-boot menu option working. What I did was to install Ubuntu to another drive, then assign its boot loader to that drive(not any partitions). This way Ubuntu and Windows are separated. If I want to boot to Ubuntu I need to enter my Bios and switch the boot drive to the Ubuntu drive, or change it back to the XP drive to boot XP. I'd rather have a menu option to choose which OS but this has been working fine for me since I'm mostly using Ubuntu.

---

### Post by oldfred on 2011-03-11
With SATA drives and new BIOS you can select any drive as a boot drive.

But with PATA drives and older BIOS only the primary master drive is bootable. You can install different systems on different drives, but only the drive with the jumper pins or location on cable select that is master will boot.

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by Splat_NJ on 2011-03-11
> **oldfred said:**
> With SATA drives and new BIOS you can select any drive as a boot drive.
But with PATA drives and older BIOS only the primary master drive is bootable. You can install different systems on different drives, but only the drive with the jumper pins or location on cable select that is master will boot.


IOW, you can install Ubuntu to the secondary IDE port/connector's master drive, true, but it cannot be installed to boot from any slave drive. Thanks for clarifying that, Fred.

---

### Post by Firem4nJoe on 2011-03-11
Thanks guys, 

I did at first have both drives as Master but the computer just sat there trying to think about it for ages. What I'm doing right now is simply having one drive plugged in at a time.
I'm considering wiping XP off the 80gig and moving Ubuntu onto it so I can just use the 320gig as storage again with Ubuntu instead of XP seeing as I do have XP on a laptop.

I just don't like machines defeating me lol.

---

