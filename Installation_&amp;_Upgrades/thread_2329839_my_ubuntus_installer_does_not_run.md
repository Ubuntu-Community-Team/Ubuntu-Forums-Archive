---
title: "my ubuntus installer does not run"
date: 2016-07-05
forum: Installation &amp; Upgrades
---

### Post by pb35 on 2016-07-05
Hi there,
Im trying to install an Ubuntu SO with my Win7 in my laptop(i5,4GB of RAM,64 bits). I created a bootable USB stick with Ubuntu(tried version 16.04,15.10 and 12.10). The only window i get is the one to choose what to do: install the SO, try it without installing, somthing for manufacturers(i believe), and finding defects on the disk. Every one works the same way, they run into a black screen and they never move from there. The laptop sounds like running but nothing appears on the screen. I have read some post like mine with Ubuntu older versions but i couldnt solve the problem with them.
Thank in advance for any help.

Pb

---

### Post by ubfan1 on 2016-07-05
Sounds like a video problem, what video hardware do you have?  Nvidia... usually takes a "nomodeset" edited onto the grub's linux ... line to get to the first boot, where you can then install the proprietary Nvidia drivers.

---

### Post by pb35 on 2016-07-05
You are right. I do have Nvidia. What should i edit? 
Thanks

---

### Post by yancek on 2016-07-05
When you boot and see the Grub menu screen with the Ubuntu entry highlighted, hit the e key on your keyboard.  The menu should change and you will see a line beginning with the word 'linux'.  Use the down arrow on your keyboard to get down to that line then the right keyboard arrow to get to the end of the line and just type nomodeset there, before the quiet splash entry or in place of hit.  It should show the key at the bottom of the screen to save the change.  This is a one time change and if the install works, you will need to install the Nvidia proprietary drivers.  There should also be a key on boot which tell you what to use to make change.

---

### Post by ajgreeny on 2016-07-05
Have you actually installed yet or are you still having problems getting to the live OS?

If still trying to boot properly to a live OS, wait till you see the first purple screen with man and keyboard icons at the bottom and then hit F3 to set language and F6 to go to Boot-options. Select nomodeset and then allow the system to boot, hopefully to a GUI, and though maybe at low resolution, you should still be able to install the system.

After installing, at the reboot follow yancek's instructions to edit the boot stanza for Ubuntu in the grub menu, add the nomodeset option as he says, then Ctrl+X or F10 to boot.  Now you can install the nvidia driver recommended from Additional Drivers.

---

### Post by pb35 on 2016-07-06
**yancek:**
When i press e key  i got:
```
setparams 'Try to Ubuntu....'
set gfxpayload=keep
linux /casper/vmlinuz.efi file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash ---
initrd /casper/initrd.lz
```
i tried writting nomodeset before quiet splash but got the same result.

[B]ajgreeny
[/B]I still get the problem. I dont get that far. I get the menu to choose, install try, etc as i said but then i always get the black screen. 

Thanks for the help both of you

---

### Post by ubfan1 on 2016-07-06
There are lots of more options to try, but first look in your BIOS/UEFI settings and see if any relate to the video.  If you have the options to select the type of video, (Integrated=Intel, Discrete=Nvidia, or both), try selecting Intel just to maybe avoid the Nvidia issues.  You can reset later after the installation.  Now even intel might have some options, below are a lot of things to try, one at a time, to see if they help.
For UEFI machines (with a black screen grub (grub-efi)  without any
function key options, like the older grub-pc, edit the grub menu and add
the below options on the "linux" line, then boot with F10 or ctrl-X.

Options for Video problems:

nomodeset
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

Older Intel video card:
i915.modeset=1 or i915.modeset=0
newer:
i915.i915_enable_rc6=1

video=1280x1024-24@60
video=VGA-1:1280x1024-24@60

To allow Nvidia hybrid machines to boot.
nouveau.blacklist=1

Skylake needs this (15.04...) but maybe not on newer kernels:
i915.preliminary_hw_support=1
noveau.blacklist=1 edd=on nolapic pcie_aspm=force tpm_tis.interrupts=0 
Maybe
intel_idle.max_cstate=1 nouveau.modeset=0

To slow SSDs to allow them to boot:
libata.force=noncq

---

### Post by pb35 on 2016-07-06
Sorry for making a big problem of this. I might have missunderstood something because english is not my first language.
I took some pics of my BIOS menus. I didnt find the video setting you talked about.

I tried writting the options you told me, but i wrote them before quiet splash, they may be in the wrong place.


thanks for all your help and your patient
[ATTACH=CONFIG]269996[/ATTACH][ATTACH=CONFIG]269997[/ATTACH][ATTACH=CONFIG]269998[/ATTACH][ATTACH=CONFIG]269999[/ATTACH]

---

### Post by ubfan1 on 2016-07-06
You are putting the options in the right place.  Here are some more for an Asus, try both together:
pci=nomsi  nodmraid

So there is no video option seen in the BIOS, I'd guess the default would be to use the Intel graphics with the i915 driver, but possibly the Nvidia with the open nouveau driver.  Once you get a successful boot, take a look by running the command   lshw -C video in a terminal and post the output here.

---

### Post by pb35 on 2016-07-07
An other unsuccesfull attemp. But i had a look at some youtube videos and found out that i dont get to the screen which everyone gets. When i start my laptop from the usb i get to attached pic.
[ATTACH=CONFIG]270003[/ATTACH]

---

### Post by oldfred on 2016-07-07
You have a newer UEFI based system. UEFI is the replacement for BIOS. And you can boot in either newer UEFI or older BIOS to install new systems, but need to know what current install is.

Ubuntu will install in either UEFI or BIOS, but really needs to be installed in the same boot mode as Windows.
If your drive is MBR(msdos) then Windows must be BIOS and you also probably have the 4 primary partition limit that BIOS/MBR has.
If your drive is gpt then Windows must be UEFI boot.

You get grub menu if UEFI boot and Accessibility icons at bottom for just a few seconds if BIOS. And with BIOS only while icons show you need to press any key, so you can press f6 to add nomodeset. 
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [URL="https://help.ubuntu.com/community/UEFI"]https://help.ubuntu.com/community/UEFI
[/URL]
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset and/or other boot options.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132) 

Post this to see current partitioning, when you get installer booting:
 My laptop already has 4 primary partitions: how can I install Ubuntu?
[http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu](http://askubuntu.com/questions/149821/my-laptop-already-has-4-primary-partitions-how-can-i-install-ubuntu)
Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Be sure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor utility partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by pb35 on 2016-07-08
I checked where i have my Win7 installed and i do think i have it on BIOS(in Disk Management i only have 2 partitions:Restricted for the system and the common C: and none of them is marked as EFIs). Then i tried to install Ubuntu in the BIOS by disabling the UEFI boot(check in the below image). should i make a new booteable USB  in BIOS mode and not in uefi mode?
[ATTACH=CONFIG]270011[/ATTACH]

Before finding out this i tried with some of the tips given in those posts but they did not work.
when i need to write nomodeset and its options it would be like the following code?
```
linux ....... quiet splash nomodeset apci_osi=Linux....
```

---

### Post by oldfred on 2016-07-08
Your UEFI/BIOS screen shot shows UEFI enabled.

UEFI/BIOS will normally show two boot options for an Ubuntu install flash drive. One is clearly UEFI:name and other is just name where name is label, brand or model of flash drive. For BIOS boot of Ubuntu you want the one shown with just the flash drive.

This shows the screens, so you know which way you have booted installer:
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

With BIOS boot, you have to press any key when you have tiny accessibility icons at bottom of screen, then press f6 to add boot parameters.
        
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

With UEFI boot or after install when booting with grub, you have to edit linux line:

 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
        How to add boot parameters
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by pb35 on 2016-07-11
Sorry for answering later. It was a long weekend.

Although i have a 64b system, i worked it out with a 32b bit ubuntu. It gave no problems. I have it installed but i got some other problems: my win7 does not load any more, and ubuntu runs slowly. I will open another post.

Thanks for the help and for your time!

Should i change the post to solved? Its not truthfully solved just sneaked

---

