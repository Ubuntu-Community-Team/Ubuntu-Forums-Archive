---
title: "Installing from CD - Pops out and boots to Windows"
date: 2014-01-23
forum: Installation &amp; Upgrades
---

### Post by Randy_Allen on 2014-01-23
I am loving the Ubuntu experience so far. I have been unable to get my computer to boot to my USB no matter what I do in the BIOS. I loaded 12.x using WUBI as a dual boot, but when I went to upgrade, it stopped working. 
I have been trying to load 13 from a DVD. It starts into Ubuntu. I tell it to install.  I go through all of the steps until it asks if I want dual boot. After selecting that, it runs a bit, and pops the DVD out. The screen is black. When I hit enter it goes back into windows. 

Any help (with either issue...not booting from USB or why installation stops) would be great! 

Thanks

---

### Post by sudodus on 2014-01-23
Welcome to the Ubuntu Forums :-)

Wubi will not be further developed, so that might the reason it does not work after the upgrade.

-o-

It will be much easier to give good advice if you tell us about your computer

- brand name and model
- CPU
- RAM (size)
- graphics chip/card

and your currently installed system

- Windows version

---

### Post by Randy_Allen on 2014-01-23
Thanks Sudodus!

I am running an HP G72 laptop
Intel i3 2.4 GHz processor
4 GB Ram
Graphics is simply the i3 built in
64 bit Windows 7 OS

When I realized the Wubi was kind of installed through windows, I wanted to get away from that anyway, and cleared it off to reload. 

Thanks for any help!

---

### Post by sudodus on 2014-01-23
Such a modern computer should be able to boot from a USB pendrive. I would try to boot from that instead of the CD/DVD drive. You should use an Ubuntu 64-bit system version 13.10 or 12.04 LTS. Check that the download was good with [md5sum]("https://help.ubuntu.com/community/UbuntuHashes").

Install the iso into the USB drive according to this link

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

There are many methods. I prefer to clone the iso file using mkusb according to the [URL="http://ubuntuforums.org/showthread.php?t=1958073"]Ubuntu Forums tutorial "Howto make USB boot drives"
[/URL]

---

### Post by Randy_Allen on 2014-01-23
Yeah- I know it should! I just installed Ubuntu on a friends comp from USB using the same pendrive (so I know it works) but no matter what I do in BIOS I cannot get it to boot to the USB. 
I have tried 32 & 64 bit 13.10 and 32 bit 12.04

---

### Post by Randy_Allen on 2014-01-23
Oh...and I checked all 3 to md5sum, and they all checked out.

---

### Post by sudodus on 2014-01-24
Is the computer booting with BIOS or UEFI?

Are you running a 64-bit version of Ubuntu? That is necessary with UEFI?

New to middle-aged HP computers are sensitive to the system on the pendrive. You might need to chainload from another pendrive with a system that works. See this link [Howto help USB boot drives]("http://ubuntuforums.org/showthread.php?t=2196858")

---

### Post by Bucky Ball on 2014-01-24
Try this. Hit F12 at boot instead of trying to change it in the BIOS. This should bring up a screen with options of which device you'd like to boot from.

I mention this because I had the same problem recently. Wouldn't boot when BIOS changed, but when I chose USB from the F12 boot menu, voila, worked. Hope it does for you, too.

PS: It is usually F12, but might be something diff for your machine.

---

### Post by mastablasta on 2014-01-24
DVD is also fine. but you need to boot from it. you have enough ram to go use "try it" and then while inside the OS click the install icon. you can then browse while OS installs or listen to some music or whatever ;-).


another thing careful with parittions. make sure you backup you windows stuff and also if you have mbr partitioned drive you can have max 4 partition so likely you need to change one of the default partitions into secondary/extended one.

---

### Post by Randy_Allen on 2014-01-25
Sorry - been busy with the kids and snow!

Sudodus - Computer is booting BIOS. I am trying to install 64 bit (although I tried 32 bit also just to see). I will try a different pendrive. Maybe it is an issue with the HP...the other system I installed with the same pendrive was a Dell. 

Bucky Ball - that is the ESC on my system.  In the boot options there the USB drive doesn't even come up, so I go into the BIOS from there.  

MastaBlasta - that was my initial problem.  Ran it from DVD, told it to install, it pops the DVD out, I hit enter, and it simply goes back into Windows. 

I think my next step is to try the chainload from another drive...now just to find what my kids have done with my various USB drives...I swear I buy a new one every couple of months!

---

### Post by Bucky Ball on 2014-01-26
> **Randy_Allen said:**
> 
Bucky Ball - that is the ESC on my system.  In the boot options there the USB drive doesn't even come up, so I go into the BIOS from there.  

Very odd, but may point to a dead USB. The USB option doesn't show if there is no USB device plugged in, even though you have one plugged in (might want to test on another machine). Doesn't account for why the disk keeps popping out though. :-k

> **Randy_Allen said:**
> ... now just to find what my kids have done with my various USB drives...I swear I buy a new one every couple of months!

You might like to start buying the four packs of dongles. Two for me, one for you, etc ... ! ;)

---

### Post by sudodus on 2014-01-26
Good luck with chainloading :-)

---

### Post by Randy_Allen on 2014-01-27
> **Bucky Ball said:**
> Very odd, but may point to a dead USB. The USB option doesn't show if there is no USB device plugged in, even though you have one plugged in (might want to test on another machine). Doesn't account for why the disk keeps popping out though. :-k



You might like to start buying the four packs of dongles. Two for me, one for you, etc ... ! ;)

This USB stick has worked to load Ubuntu on another machine. I have plugged other peripherals in to make sure USB hardware is working ok...strange.

I have 5 kids...do they sell a 20 pack?!?!?!:o

---

### Post by Randy_Allen on 2014-01-27
> **sudodus said:**
> Good luck with chainloading :-)

Thanks Sudodus...I hope to get a chance tomorrow. We'll see...might be snowed in with kids still!

---

### Post by Randy_Allen on 2014-01-27
Here is the latest: I got a new pendrive, and computer boots right to it.
I click install.
I connect to wifi.
I tell it tiinstall inside win 7
When it rebooted, it goes right back to the try or install.

Is there something left from when iinstalled it with wubi that keeps it from installing?

---

### Post by sudodus on 2014-01-27
You should ***not*** install from inside Windows, instead you should boot from the pendrive or chainload from one pendrive (the chainloader) to the other (with the Ubuntu system) without starting Windows.

Or do you mean 'install alongside Windows'?

What menus do you see during booting? Please describe them!

-o-

If you have installed Ubuntu, but still have a boot order to give priority to the USB pendrive, you should either remove the pendrive (while the computer is shut down), or change the boot order in the BIOS/UEFI menu system. Then the computer should boot into the new system (a grub menu with several options, among them Ubuntu and Windows and memtest).

---

### Post by Randy_Allen on 2014-01-27
I am now booting to Ubuntu form pendtive without starting windows.
Interestingly it says "install inside windows." I understood it to be "alongside"

When it rebooted it just goes right to windows if I pull usb out, or right to the try or install if I leave USB in, it goes right back to try or install.

No grub menu comes up.

---

### Post by Bucky Ball on 2014-01-27
You have installed Ubuntu to the hard drive on its own partition? Have you 'Tried Ubuntu' and you can get to a desktop okay? You should see an icon on the desktop 'Install'.

Wubi is being phased out and not supported. Don't install 'inside' Win.

---

### Post by Randy_Allen on 2014-01-27
> **Bucky Ball said:**
> You have installed Ubuntu to the hard drive on its own partition? Have you 'Tried Ubuntu' and you can get to a desktop okay? You should see an icon on the desktop 'Install'.

Wubi is being phased out and not supported. Don't install 'inside' Win.

Not using WUBI now. I had used it and removed it previously. 

I boot with the USB drive to Ubuntu. Get the option to try or install. I can try and get a desktop just fine. 
When I click install it asks me if I want to install in windows (attachment is a pic of screen)
I tell it to install, and it goes blank.  If I leave USB in, it boots back to "try" or "install."  If I pop USB out before it comes back up, it simply boots into Windows with no GRUB. 

[ATTACH=CONFIG]249781[/ATTACH]

---

### Post by Bucky Ball on 2014-01-28
You are installing from the regular install disk? It doesn't look like it as you have options greyed out, 'Something Else' for instance. You sure you're not using a Wubi disk as these options would logically be unavailable if you were?

---

### Post by sudodus on 2014-01-28
Could it be that there is an MSDOS partition table and  4 primary partitions? When running live 'Trying Ubuntu', you can open a terminal window and run

```
sudo parted -l
``` and post the output for us to see the partitions.

Then it will be easier to give good advice. I (or someone else) will probably ask you to run a few more commands, depending on the output of the
***'sudo(space)parted(space)(minus)(ell)(Enter)' ***command. Copy and paste, and put within code tags (**[COLOR=#ff0000]Go Advanced[/COLOR]**, and click the **#** icon at the top of the editing window).

---

### Post by Randy_Allen on 2014-01-28
```
Model: ATA ST9500325AS (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  210MB  209MB   primary  ntfs         boot
 2      210MB   483GB  483GB   primary  ntfs
 3      483GB   500GB  17.2GB  primary  ntfs
 4      500GB   500GB  108MB   primary  fat32        lba


Model: PNY USB 2.0 FD (scsi)
Disk /dev/sdb: 8167MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      28.7kB  8167MB  8167MB  primary  fat32        boot, lba


```

---

### Post by Randy_Allen on 2014-01-28
I am a pretty quick learner, but I have no clue what that means at this point! Fun learning!
Sorry if this is a pain!

---

### Post by Bucky Ball on 2014-01-28
My money's on an EFI issue. sda4, the FAT32 marked lba, is probably an EFI partition.  

```
4      500GB   500GB  108MB   primary  fat32        lba
```

If you installed Win7 yourself then it possibly created these four partitions all by its self. If it was  pre-installed I have little doubt it did. 

Could you boot into the BIOS and check if the disk is set to boot in EFI mode (if you have already, apologies). 

While you are in the BIOS, if it is set to EFI, some BIOSs allow you to boot the optical drive in EFI also. You might try that.

---

### Post by Randy_Allen on 2014-01-28
According to disk management, none of the partitions are EFI.

---

### Post by Bucky Ball on 2014-01-28
It won't necessarily say it's anything. They like to make it confusing. Have you been to the BIOS and checked whether the disk is set to boot EFI like I asked? That is a surefire way to find out.

---

### Post by Randy_Allen on 2014-01-28
There is no UEFI or EFI in the BIOS at all. 
Win7 was preinstalled when I purchased this machine. 

Is this possibly something hanging on from when I had installed 12.04 in WUBI?  I uninstalled it using windows control panel like it said...is there something else that I should have cleared out.

---

### Post by Randy_Allen on 2014-01-28
Not sure if it matters - the 4th partition is the HP tools...I have my recovery disks...if this is causing the problem, I could delete that partition and extend regular partition.

---

### Post by Bucky Ball on 2014-01-29
Ah, that solves it. No, that shouldn't be a problem and I'd leave as is. ;)

That rules out EFI issue, though.

---

### Post by sudodus on 2014-01-29
You have a maxed out the partition table with four primary partitions. You need to remove one of them to create logical space for an extended partition. In that extended partition you can create two logical partitions: one partition with the ext4 file system for the root file system and and swap partition.

The hp-tools partition is small, and it is OK to move its content to a directory in the main Windows partition. Then it can be removed and you have the 'logical space'. But you need also 'physical space', so shrink the main Windows partition to create unallocated space, that can be used for the extended partition and the logical partitions for Ubuntu.

Use Windows to shrink the Windows partition (Windows tools to manage Windows file systems and linux tools to manage linux file systems when possible).

Edit: How much free space is there in the main Windows partition, **/dev/sda2**? And what is there in the next biggest one, **dev/sda3**?

---

### Post by Randy_Allen on 2014-01-29
sda2 there is 212GB free and sda3 (which is recovery) has 2.3GB


So basically, I need to copy hp-tools to a new dir in Win, then in disk management delete it, extend win partition to use that, then shrink the physical space enough to create the new partition for Ubuntu. 

When I install then, will I need to select the "Do something else" or can I simply install with the recommended settings?

---

### Post by sudodus on 2014-01-29
***Gparted*** is easier to understand than the  built-in partitioner in the installer, so I suggest that you make the  extended partition, the root partition and the swap partition with  gparted.

In the installer I think it is easier to know what you are doing when using 'Do ***something else***' at the partitioning page. Select the partitions that you have prepared with gparted.

An alternative is to use the [One Button Installer]("http://ubuntuforums.org/showthread.php?t=2172971"), it you want a tool with a simpler interface.

---

