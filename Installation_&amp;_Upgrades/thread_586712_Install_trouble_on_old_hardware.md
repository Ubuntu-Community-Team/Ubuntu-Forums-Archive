---
title: "Install trouble on old hardware"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by psatyshur on 2007-10-22
Hi

I am trying to install Ubuntu 7.1 on an older system and having a bit of trouble. The system I am trying to install on is:

Pentium 3 500mhz (Katmai)
[Abit BE6-II v2.0]("http://www.abit.com.tw/page/en/motherboard/motherboard_detail.php?pMODEL_NAME=BE6-II+V2.0&fMTYPE=Slot+1")
256mb PC100 SDRAM
Matrox G400 Video Card
120gb Western Digital HD

I have the hard drive attached to the HPT370 controller on the motherboard. When I try to install Ubuntu, the live CD works fine and boots to the desktop (albeit very slowly). I then tell it to install, use the entire hard drive, and select the various other options, and press okay. The install itself also seems to work fine (also really slow). When it is over, it tells me to reboot, and remove the CD. However, when I do this, it cannot boot from the hard drive. It will flash a message for a split second about grub stage1, and then restart.

Is grub not compatible with the HPT370 chip on my motherboard? Is there some special configuration that I have to do to make sure the boot loader has the drivers for this chip? or is this error caused by something else entirely?

Any help you guys can give would be appreciated.

---

### Post by luvr on 2007-10-22
> **psatyshur said:**
> Is grub not compatible with the HPT370 chip on my motherboard?
Sounds unlikely to me, since GRUB runs at the BIOS level. It just makes BIOS calls to get its job done, so if the BIOS handles the disk OK, then so should GRUB.

GRUB Stage 1 is the code that gets loaded from the Master Boot Record (i.e., the first 512-byte sector of the harddisk), so your Master Boot Record was apparently written fine. The next stage of the boot process, however, seems to be missing, so I would guess that GRUB was incorrectly installed. I have no real idea **why** it failed, but the [Ubuntu 7.10 Release Notes]("http://www.ubuntu.com/getubuntu/releasenotes/710") do say that you need at least 384MB of system RAM for the Desktop CD. Perhaps your computer simply does not have enough memory to correctly install Ubuntu 7.10 from the Desktop CD?

Note that the minimum amount of memory for Ubuntu **_7.04_** was 256MB, so you may have more luck with that. I once installed 7.04 on a system that had just 256MB of RAM, and while running from the CD was a nerve-wrecking experience and caused a few error pop-ups, once installed, Ubuntu has been runnig fine on this system ever since.

---

### Post by psatyshur on 2007-10-22
Thanks for the reply. It does appear that grub can't find the partition properly or something. Do you know what (if any) error would happen if it can't find stage 2? I find it odd that grub does not seem to give any sort of error, it just restarts the computer.

As for grub being installed improperly, I tried reinstalling it using the directions I found on the forum here. Everything seemed to work fine when reinstalling, but it did not help.

I did notice the minimum memory requirement, and figured I would try to install anyway. There were no errors (that I could see) during the install, so I figured it had worked. I will try installing 7.04 when I get home later and see how that goes.

---

### Post by logos34 on 2007-10-22
With an old machine like that I'd seriously consider [Xubuntu 7.10]("http://www.xubuntu.org/").  It will run a lot quicker.

If you go with 7.04 ubuntu, you might want to use the text-mode Alternate dekstop CD--it requires less ram.  
ubuntu-7.04-alternate-i386.iso

---

### Post by psatyshur on 2007-10-22
Thanks for the heads up on Xubuntu. I will give that a shot as well. Hopefully one of the two will allow me to get this working. The only OS I have been able to get to work on this computer is Windows 98, and I would like to get away from that one if possible.

---

### Post by luvr on 2007-10-24
> **psatyshur said:**
> Do you know what (if any) error would happen if it can't find stage 2? I find it odd that grub does not seem to give any sort of error, it just restarts the computer.
I'm not sure about the errors that GRUB should report if it cannot find its stage 2 (or stage 1.5) code; and yes, it **is** odd that it doesn't report an error, but simply reboots instead.

It may be a good idea to try and install GRUB from a less resource-hungry (e.g., character-mode) environment; I usually boot the Slackware CD or the System Rescue CD, in order to install a GRUB version that I home-compiled from source. It may be possible to boot the Ubuntu CD into character mode, and install GRUB from there (though you may need the Alternate CD to do so).

Sorry if I can not offer more detailed help at this time, but I would have to look into the issue a little further in order to collect and share more precise information.

---

### Post by luvr on 2007-10-24
**_How to boot the Ubuntu Live CD into Character Mode:_**

[LIST]
[*]Boot from the Ubuntu 7.10 Live CD.
[*]On the boot menu, hit **F3** (*"Keymap"*), and select your keyboard map.
(You may skip this step if you use the default U.S. English keyboard map.)
[*]Hit **F6** (*"Other Options"*).
A *"Boot Options"* line will be displayed.
[*]Go to the end of the boot options line.
The line will end with the text:
> quiet splash -- 
[*]Remove this text, and replace it with:
```
nosplash single
```
[*]Hit the <ENTER> key.
[*]Let the boot process complete.
The system will display a command-line prompt, at which you can type commands.
[/LIST]

**_How to reinstall GRUB from this Character-Mode Session:_**

[LIST]
[*]Type the following command to enter the GRUB shell:
```
grub
```
The system will display the GRUB prompt:
> grub>
[*]To verify where the grub directory is located on you harddisk, let GRUB search for your *"menu.lst"* file. Type:
```
find /boot/grub/menu.lst
```
The GRUB shell should tell you on which partition it finds the file-e.g.:
> (hd0,2)
It identifies the partition in GRUB notation. If, for example, it displays **(hd0,2)** then your *"menu.lst"* file sits on the first harddisk (i.e., harddisk number 0), on its third partition (i.e., partition number 2). This will usually be the partition on which you installed Ubuntu.
[*]The partition identified above, will be what GRUB calls the *"root"* volume--i.e., the partition from which GRUB will read the files that it needs in order to complete its boot process. To tell GRUB about the *"root"* volume that you want it to use, type:
```
root (hd*_0_*,*_2_*)
``` (You should, obviously, replace the disk and partition numbers with the correct values, as identified above).
[*]You will most likely want to install the GRUB boot loader on your *Master Boot Record*--i.e., on your first harddisk, which, in GRUB speak, is **(hd0).**
To reinstall GRUB onto the *Master Boot Record* (using the *"root"* volume that you have just identified), type:
```
setup --prefix=/boot/grub (hd0)
```
[*]Next, quit the GRUB shell:
```
quit
```
[*]Reboot you computer, and see if GRUB works now.
[/LIST]

---

