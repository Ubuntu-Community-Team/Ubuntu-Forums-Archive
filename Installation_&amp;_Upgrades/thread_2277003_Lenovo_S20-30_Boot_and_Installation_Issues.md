---
title: "Lenovo S20-30 Boot and Installation Issues"
date: 2015-05-06
forum: Installation &amp; Upgrades
---

### Post by Paul_DiBlasi on 2015-05-06
I own a new LenovoS20-30 laptop which came with Windows 8.1 preinstalled with the harddrive partitioned. I want to convert this laptop to Ubuntu 15.4. withNO dual boot. I want it to be an exclusive Linux machine. This laptopcan boot off the E Drive with a USB Drive.


[LEFT]I useda brand new Kingston 4 GB USB Drive. I followed Ubuntu installationinstructions to the letter [/LEFT]

1. I went toPendrivelinux.com and downloaded the Universal USB Installer V1.9.5.9to my USB Drive.


2. I went to Ubuntuand downloaded Ubuntu Linux V15.04 to my USB Drive.


3. Using TheUniversal USB Installer I installed Ububtu Linux 5.4 on my USB Drive.


4. My BIOS isupdated to the latest BIOS from Lenovo's Website, which was posted onMarch 9, 2015, Filename/BIOS Version: accn22ww(v2.08&v1.1).


5. My BIOS isconfigured to boot from the USB Drive first


6. When I reboot theUSB Drive is not recognized as a boot drive and the system stillboots into Windows.


Again, I want toboot up and install Ubuntu Linux 15.04 and have the system be anexclusive LINUX machine. I have an identical Lenovo S20-30 rynningthe standard Windows 8.1 and want to compare functionality andperformance running the same applications on identical machines.


Has anyone installedUbuntu Linux on a Lenovo S20-30 before?


What do I need totroubleshoot and check?


I am an experiencedWindows person but new to Linux so please be gentle and don't assumeI know much about Linux. That's what this is all about, I want tobecome Linux expert and hope I can one day soon be fully on UbuntuLinux and never look back

---

### Post by oldfred on 2015-05-06
The Ubuntu installer should boot with secure UEFI boot on or off in UEFI mode or in CSM/BIOS boot mode. You should see two choices in UEFI boot menu. If not you may have to turn on in UEFI a setting that allows booting external devices or other UEFI settings. 

Or your flash drive is not configured correctly. Did you verify ISO download was correct?
We also have seen issues with some brands of flash drives, different installers, and different ports on the computer.

Even though differnet models, issues are often common by brand.
 T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

You do want to be sure to install Ubuntu in UEFI mode. And best to use Something Else install option.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screeens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

            UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

---

### Post by Paul_DiBlasi on 2015-05-07
---------------------------------------------------------------------------------------
05/07/2015


Dear oldfred:


I want to thank youso much for your support post. Your post triggered me to go back intomy BIOS and look at the configuration very carefully setting bysetting. I was finally able to find the best combination of BIOSsettings to get my Lenovo S20-30 to boot up from my USB Drive andUbuntu 15.4 is fully installed now as the ONLY operating system on myS20-30.


To express mygratitude to you and to pay it forward to any other Lenovo S20-30users wishing to do the same, below, I have painstakingly documentedevery BIOS setting below along with the settings I changed tosucessfully boot up from my Ubuntu Boot USB.


So now its time tolearn learn learn Ubuntu. Thank you again and I hope my post belowproves helpful to others.


---------------------------------------------------------------------------------------
05/07/2015


Here is someadditional BIOS Information


Information: 
Product Name: LenovoS20-20
BIOS Version (Mostcurrent): ACCN22WW(V2.0)
EC Version:ACEC22WW(V1.1)
CPU: Intel CeleronCPU N2830 @ 2.16GHz
Windows License: WIN


Configuration: 
USB XHCI Controller: Enabled
Wireless: Enabled
SATA ControllerMode: AHCI
Power Beep: Disabled
BIOS Back Flash:Disabled
Hotkey Mode: Enabled


Security: 
Supervisor Password:Not Installed
User Password: NotInstalled
HDD Password: NotSet
Secure Boot: Enabled
Secure Boot Status:Enabled
Platform Mode: UserMode
Reset to Setup Mode: <Enter>
Restore FactoryKeys: <Enter>


Boot:
Boot Mode: <UEFI>is set now. The only other option to select is <Legacy Support>See the note below 
USB Boot: <Enabled>


Note for Boot Mode:the information window states: Windows 8 or 8.1 64 Bit please useUEFI Boot Mode. Other Legacy OS please use Legacy Support Mode


Additionally I havereset the Bios to <Legacy Support> with the same result whenbooting up


When selecting BootMode of <Legacy First> I am presented with two choices for“Boot Priority”. 
1. <Legacy First>
2. <UEFI First>


[LEFT]Withthe following note: Determine <EFI Device> first or <LegacyDevice first>. If <Enable> it is the <EFI Device first>,If <Disable> it is the <Legacy Device First>

I didcold boots with each combination selected:
UnsuccessfulBoot configuration to boot from the USB Drive: <LegacySupport><UEFIFirst>[/LEFT]

Successful Bootconfiguration to boot from the USB Drive: 
<Legacy Support>
<Legacy DeviceFirst>
---------------------------------------------------------------------------------------

---

### Post by kagashe on 2015-05-07
This is another case of Universal USB Installer from Pendrivelinux.com producing Ubuntu USB Stick which is not detected as EFI USB Stick and requiring <Legacy Support>
<Legacy DeviceFirst> BIOS Settings. The earlier case was reported on [this thread]("http://ubuntuforums.org/showthread.php?t=2276449").

The person posting the other thread has not replied.

Preparing EFI Bootable USB stick using Ubuntu 15.04 ISO on Windows is very simple. Just extract the ISO on USB stick (formatted in FAT32) using 7-zip on Windows.

Kamalakar

---

### Post by oldfred on 2015-05-07
Glad you got it working.

But I expect you could have installed in UEFI mode, as Ubuntu has the Microsoft key for secure boot if desired and works on most systems. 
But settings in UEFI/BIOS are a lot more complex with UEFI than with BIOS. And every vendor is a bit different even though UEFI is a 'standard'.

---

### Post by Paul_DiBlasi on 2015-05-10
kagashe,

Thank you for the insights. I hope that one day I can get my printer and scanner working well with Ubuntu to get my other laptop running pure Ubuntu and off Windows. But until I can get my Brother HL-1110 and Canon LIDE 210 Scanner successfully working with Ubuntu, I am stuck with Windows to print and scan.

But for primary everyday usage so far Ubuntu so outpeforms Windows in every way. so I will just try to resolve those two issues.

Thank you again, Paul

---

### Post by pdc on 2015-05-11
Hi Paul

according to this [http://www.sane-project.org/sane-mfgs.html#Z-CANON](http://www.sane-project.org/sane-mfgs.html#Z-CANON) your 210 should be fully supported by sane; if you open xsane ..................it should find the 210 ................. are you finding it does not?

_____________________

for the Brother HL-1110 ..........if you go here [http://support.brother.com/g/b/downloadlist.aspx?c=eu_ot&lang=en&prod=hl1110_us_eu_as&os=128](http://support.brother.com/g/b/downloadlist.aspx?c=eu_ot&lang=en&prod=hl1110_us_eu_as&os=128) and click to download and SAVE the Driver Install Tool

you will have downloaded linux-brprinter-installer-2.0.0-1.gz into your Downloads folder so if you open a terminal ( holding down 3 keys: control and alt and t together) ....... and paste in these commands 

```
cd Downloads
```

```
gunzip linux-brprinter-installer-2.0.0-1.gz
```

```
sudo bash linux-brprinter-installer-2.0.0-1 HL-1110
``` then the final command will ask you for your sudo password and should download and install the needed drivers; and; register the printer on your system;

near the end of the install script, it will ask about the Device URI: if it is a usb connect, say NO 

-_____________

any joy?

---

