---
title: "Total disaster on install"
date: 2011-11-23
forum: Installation &amp; Upgrades
---

### Post by dgundling on 2011-11-23
I have really made a mess. My goal was to have Ubuntu 10.10, 11.04 and 11.10 on a single hard disk in separate primary partitions. If all went well I intended to also add WIN98SE in its own partition. I have reached the point where I can't even access the HD. Ubuntu in any one of the three versions will not boot from the "live" CD. Tried the WIN98SE installation disk to see if it could allow me access to the HD in order to repartition, no go. Tried partition magic and only get errors. I am perfectly willing to wipe the HD, if I can get to it, and start over. Any one have an idea on how I might get to the hard drive? 
 
Thanks.

---

### Post by oldfred on 2011-11-23
Windows has to be in a primary partition. Not sure about  Win98 and how it works anymore. 

With the 4 primary partition limit you cannot have all the Ubuntu's on primary partitions. Plus you should have some shared data partitions. Or you need several logical partitions in addition to the primary.

Does this work on your drive from the liveCD of Ubuntu?

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste contents of results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Install these before running script:
sudo apt-get install mawk

---

### Post by dgundling on 2011-11-24
Thanks for the reply. I think I can have all the Ubuntu's on a primary partition. 10.10. 11.04, 11.10 and WIN98SE is a total of 4 OS's, yes? There are 4 partitions available. The problem at the present time is that I have no means to get to the HD. "live" CDs aren't. No partioning software that I have tried will get me to a state where I can completely erase the HD so as to start over.

---

### Post by BC59 on 2011-11-24
> **dgundling said:**
> I intended to also add WIN98SE in its own partition. 

I'm wondering......what... why Win98????  You cannot even use USB, there are millions of incompatibilities....why?

Do you use a SATA HDD? Your RAM is DDR2 or 3? How you could install Win98?

---

### Post by oldfred on 2011-11-24
+1 BC59

Does BIOS still see drive ok?

---

### Post by darkod on 2011-11-24
Few more points:
1. Not being able to boot with the ubuntu cd does not have anything to do with the hdd. It can be completely dead, the computer should still boot the cd. Look into that problem first because that will allow you to partitions the hdd (provided you can use it).
2. Yes, 4 primary partitions are allowed for 3 ubuntu OSs + Windows but if you plan to use swap partition that's a fifth as minimum. Anyway, ubuntu runs just fine from logical (extended) partitions, why insist on primary?

The others have already expressed their concerns about Win98, I won't even get into that. :)

---

### Post by dgundling on 2011-11-24
Thanks to all that replied.
 
To answer the question on WIN98SE, I want to install it because of some old software I have that runs on it. BTW, before an attempt to use upgrade manager to go from 11.04 to 11.10, I had WIN98SE, 10.10, and 11.04 installed and able to run using the same system and HD. The upgrade caused the initial scrambling of the HD and it has gone down hill since. 
 
Had not thought to check the BIOS to see if it sees the HD. Will do so.
 
I have a spare HD and CDROM drive in case I need to replace what I have. I expect I will have to replace the HD at a minimum as it appears. at the moment, that there is no way I can get to it.
 
None of my 3 "live" Ubuntu CDs will get to the point where I have a choice beteween installing or running from the CD.

---

### Post by BC59 on 2011-11-24
> **dgundling said:**
> Thanks to all that replied.
 
To answer the question on WIN98SE, I want to install it because of some old software I have that runs on it. BTW, before an attempt to use upgrade manager to go from 11.04 to 11.10, I had WIN98SE, 10.10, and 11.04 installed and able to run using the same system and HD. The upgrade caused the initial scrambling of the HD and it has gone down hill since. 
 
Had not thought to check the BIOS to see if it sees the HD. Will do so.
 
I have a spare HD and CDROM drive in case I need to replace what I have. I expect I will have to replace the HD at a minimum as it appears. at the moment, that there is no way I can get to it.
 
None of my 3 "live" Ubuntu CDs will get to the point where I have a choice beteween installing or running from the CD.

You can run old programs in newer Windows versions by using the **Program Compatibility Wizard** There is no need to install Win98.

---

### Post by ubume2 on 2011-11-25
> **oldfred said:**
> +1 BC59

Does BIOS still see drive ok?

While you are in BIOS, check your RAM also.

From your previous posts in June, (if this is the same computer), your problems were possibly beginning then.  HD? RAM? CD Drive?

---

### Post by dgundling on 2011-11-27
I am beginning to suspect that I have a hardware problem. I installed a new CDROM drive and a new hard drive. Tried the 10.10 distro. Got error messages like: Process:258): GLib -warning xc: getpwid_r( ) : failed due to unknown user id (0). This with a new HD with nothing on it. In the past, the install CD  didn't need a password.
 
Another error message I received was:  INITranfs) mounting/dev/loop0 on// file system. squashfs failed: input/output error can not mount /dev/loop 0 (/cdrom/casper/filesystem, squashfs) on // filesystem squashfs. Have no idea what that means.
 
Played around in the Bios with changing the boot order. started with my IDE HD first with my new SATA HD second. Tried switching things around but couldn't move the SATA HD to the first position as long as the IDE drive was plugged in. Plugged the power back into the IDE drive and the computer stayed happy. Tried a live CD of Ubuntu 10.10. Install ran into an error and stopped. Tried again but this time I ran from the CD without trying to install. I was able to get to both HDs. I reformatted the IDE HD leaving only a single Linux partition. Put a single Linux partition on the SATA drive also. Tried install again and got an error message. Tried running from the CDROM again and it wouldn't load.
 
Any suggestions?
 
Thanks.
Dave

---

### Post by dgundling on 2011-11-27
BC59,
 
I have a WIN98SE game which will not run under XP using the compatability wizard when XP is using the NTFS file system.

---

### Post by BC59 on 2011-11-28
Well there is another solution. You can install Win98SE on a virtual machine:

"Installing Windows 98 SE on Virtualbox"

[http://www.youtube.com/watch?v=Ubb1p5lC2Qg](http://www.youtube.com/watch?v=Ubb1p5lC2Qg)

---

### Post by dgundling on 2011-11-28
More info. Used Microsoft's Memory test and my RAM checked out OK. Checked BIOS and both my IDE and my SATA hard drives show up. Was able to make either the SATA or the IDE drive the boot hard drive. Stuck the 10.10 Live CD in the newly installed CDROM drive and was able to start the install process. Install went all the way through until it reached the point where it said a restart was required. Then I got the following error message           [1005,576144] end c request; I/O error, dev sr0, sector 535760.     (Actually I got a whole page of the same error message but the number after the 1005 kept changing.
 
Shut down and then rebooted hoping to reach the SATA drive which was where 10.10 supposedly installed. Another error message      Reboot and select proper boot device or insert Boot media in selected boot device.       BIOS was set up to Boot from A drive, then CDROM, and last the SATA drive. Tried reinserting the 10.10 CD and got the same error message.
 
 
Shut down again and tried a reboot with the 10.10 CD in the CDROM drive. Was able to use Ubuntu 10.10 running from the CDROM drive.  
 
Am I likely to have a mobo or cpu problem?

---

### Post by oldfred on 2011-11-28
Is not the error on sr0, from the CD.

You can run a test of the CD from the CD. Press any key at accessibility circle and keyboard(first little icons at bottom of screen), and a menu should come up.

---

### Post by dgundling on 2011-12-17
Oldfred,
 
Thanks for the reply. Sorry for the delay in responding. I had a thought that moving the computer from a 40 to 50 degree environment to a 70ish degree environment might help. I knew it would help me to feel more inclined to work the problem. Had to buy and assemble a computer cart and fix the house wiring so that the plug I wanted to use was grounded. Haven't tried your suggestion for checking the CDROM drive but will do so. BTW, after I got the computer set up in the house one of my 10.10 installation attempts decided to work. I have a 10.10 installation on my SATA drive and one on my older IDE drive. Both will boot but only the SATA drive vrsion will function normally. My check case is to try to play Mahjong. With the IDE drive as the boot source I can play the game once and then the computer locks up. Only a reboot frees it up. Same thing happens with the IDE drive version if I go to Firefox. I can use it for one action and then the computer freezes up.
 
I am going to try to add a 11.04 installation to the SATA drive. Will try your suggestion to click on the icons at the bottom of the installation screen for a check on the CDROM drive.
 
Dave

---

### Post by dgundling on 2012-01-04
Further update. I have 2 CDROM drives and 5 UBUNTU CDROM installation disks. When hooked up to another computer both CDROM drives work fine. When placed in the CDROM drive of another computer all 5 UBUNTU CDROMs boot ust fine. No UBUNTU installation CD will boot on the computer inquestion using either CDROM drive. The only thing that will almost boot is an old WIN98SE installation disk. I t installs until it gets ready to boot from the hard disk and then locks up. I am trying to figure out if the problem is a motherboard issue or something else. Would appreciate any ideas.  Thanks.

---

### Post by oldfred on 2012-01-05
With 2 CD drives does it get confused between them?

Years ago with an early CD with burning capability, I did have issues reading CDs unless they were burned on the same drive. So hardware may be an issue.

How much memory do you have. Ubuntu needs 512K or alternate install or Lubuntu need less to install. Or try some of the lightweight versions of Linux like Puppy, Slax, or Knoppix.

---

### Post by dgundling on 2012-01-05
> **oldfred said:**
> With 2 CD drives does it get confused between them?
 
Years ago with an early CD with burning capability, I did have issues reading CDs unless they were burned on the same drive. So hardware may be an issue.
 
How much memory do you have. Ubuntu needs 512K or alternate install or Lubuntu need less to install. Or try some of the lightweight versions of Linux like Puppy, Slax, or Knoppix.
 
 
Oldfred,
 
Thanks for the reply. Itried the computer with each of the two CDROM drives individually installed and then with both of them on the same IDE cable. 
 
I have 1 GB of RAM installed. You may recall that at one time I had 10.10 and 11.04 and WIN98SE running happily. Each was installed in its own partition.
 
I am strongly suspicious that I have a mother board problem.
 
Dave

---

### Post by Rebelli0us on 2012-01-05
I'd install just **one** Ubuntu and run win98 in a virtual machine.

---

### Post by dgundling on 2012-01-05
Thanks for the reply. However the problem is that I can't install any version of Ubuntu. None of the 5 distro disks that I have will load at all on the machine I want to use. I have 2 CDROM drives which I have tried both separately and with both installed on the same IDE ribbon. Neither worked. THe same distros and CDROM drives, when used with my other computers, work fine.

---

### Post by oldfred on 2012-01-06
Have you changed drive configuration?

with pictures:
[http://en.wikipedia.org/wiki/Parallel_ATA](http://en.wikipedia.org/wiki/Parallel_ATA)
[http://en.wikipedia.org/wiki/Serial_ATA](http://en.wikipedia.org/wiki/Serial_ATA)
Some history:
[http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html](http://www.pcguide.com/ref/hdd/if/ide/confCS-c.html)
If you have the more modern 80 conductor 'cable-select' type of IDE ribbon cables, make sure the blue plug is connected to the motherboard, the grey plug is plugged into your slave drive (if any), and the black plug is plugged into your master hard drive.

If you have the old kind of IDE ribbon cables, check that one hard disk is set as 'master' and the other is set as 'slave' if there's another drive on the same cable.

---

### Post by Rebelli0us on 2012-01-06
> **dgundling said:**
> Thanks for the reply. However the problem is that I can't install any version of Ubuntu. None of the 5 distro disks that I have will load at all on the machine I want to use. I have 2 CDROM drives which I have tried both separately and with both installed on the same IDE ribbon. Neither worked. THe same distros and CDROM drives, when used with my other computers, work fine.

Reset BIOS, then boot Windows CD and Ubuntu Desktop CD, if neither OS can see the disk then the problem is hardware and not OS-related.

---

### Post by dgundling on 2012-01-06
> **Rebelli0us said:**
> Reset BIOS, then boot Windows CD and Ubuntu Desktop CD, if neither OS can see the disk then the problem is hardware and not OS-related.
 
Have reset BIOS many times. Ubuntu desktop CD won't boot at all. WIN98SE CD will start to install but not complete the process. It quits at the last reboot before opening the desktop.

---

### Post by dgundling on 2012-01-06
OldFred,
 
I have the older cable. Have checked the master/slave switch. Bios sees the drive (or drives when I tried more than one HDin the installation.

---

### Post by oldfred on 2012-01-06
Some very old or very new systems require extra parameters to boot.

If just video issue then it usually is nomodeset, but sometimes other parameters are required.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place

---

### Post by dgundling on 2012-01-06
Oldfred,
 
Thanks for the sugestion but the problem is that I can't get Ubuntu to boot from any distro CD that I have. Not sure what you mean by the "accessability circle". Is that the little circle with the stuff going around within it when Ubuntu boots? If so, I don't get that far.

---

### Post by oldfred on 2012-01-06
If booting from a CD, it should immediately show two tiny icons at the bottom of the screen.  Press any key immediately and you should get a menu. Under f6 are parameters to set. Do not remember anymore all the other f keys.

see the screens you should get Advanced Welcome page:
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
many other options
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)

---

### Post by dgundling on 2012-01-07
Does anyone know of an PCI IDE controller card that works with Ubuntu? Thought I might give that a try since there is a strong indication that the onboard (Intel D865GVHZ Desktop Board) has died.
 
Thanks.
 
Dave

---

