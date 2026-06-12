---
title: "can't boot from CD"
date: 2011-04-21
forum: Installation &amp; Upgrades
---

### Post by haapsalu_sall on 2011-04-21
I have the book Ubuntu Linux Bible which has a CD of 10.04. It will start to boot, then stop, just a black screen. Beginning Ubuntu Linux for 9.04 has a DVD and the book says if this happens (installation doesn't finish), reboot, press F4, select safe graphics mode. Will this work with the CD? If not, what do I do to finish the installation?

I've had to reinstall Ubuntu a couple of times (like last night when I didn't turn off tapping in Xfce, I turned off the touchpad -- and I don't own a mouse) and I'm tired of installing 9.04 and upgrading to 10.04. 

Thanks.

---

### Post by oldfred on 2011-04-21
I think it was 10.04 where my nVidia started to do that. Since I was installing from USB, I could see flash drive still installing but monitor went to sleep.

[http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/](http://pricklytech.wordpress.com/2010/07/31/ubuntu-10-4-lucid-black-blank-screen-during-installation-live-cd/)
[https://wiki.ubuntu.com/X/Troubleshooting/Nouveau](https://wiki.ubuntu.com/X/Troubleshooting/Nouveau)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)
Check BIOS for settings:
try to boot with acpi=off or nomodeset=0 on the boot line
[https://help.ubuntu.com/community/BinaryDriverHowto](https://help.ubuntu.com/community/BinaryDriverHowto)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

I had to do this with my Nvidia 9600GT:
To install Ubuntu, boot from the cd press any key at accessibility circle and keyboard, press F6 and then select the nomodeset option.
USB boot - At the menu press tab on the first option to edit the boot options and replaced the 'splash' option with 'nomodeset'. 
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)
[https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18](https://bugs.launchpad.net/ubuntu/+source/casper/+bug/661939/comments/18)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

---

### Post by haapsalu_sall on 2011-04-21
I just looked at the first, but I will read and try them. Many thanks! :D

I think this is solved, but want to wait until I have time to try it out before I mark the thread.

---

### Post by haapsalu_sall on 2011-04-25
Well, solved, I guess, but not the way I wanted. I tried the first link, which is very similar to the book, so I went with the three ways the book describes. Nothing worked.

1. (all from p. 64 Beginning Ubuntu Linux) after the preliminary steps, you end up with the boot options that start with file=/cdrom... Delete the word splash from the end of the line. This brought the *install Ubuntu* icon to the screen, but nothing happened when I clicked on it.

2. Get to the same screen as above, after F6 select *nomoeset*. I got this to boot, but then I guess it got corrupted. I couldn't get online and the screen fuzzed out. Restarted the computer a couple of times, but the problem just went downhill.

3. Added to the end of the boot options from #1:

i915.modeset=0 xforcevesa 

The book adds fb=false, but the website didn't have this, so I left it off (if you're rofl at this point, please share! I am new to all of this, quite willing to experiment, and laugh at myself as well).

I got this to boot, but everything was larger than life -- rather like you'd see on a computer for someone with visual problems. The internet started ok, and I installed the updates and rebooted. Sigh. I was in no graphic mode, which, while it looked intriguing, I had no idea what to do with. 

So I reinstalled the 9.04 DVD (another sigh) and upgraded to 10.04. (I have a 10.04 DVD which won't load and am awaiting a replacement. Or, I will learn to make my own, because I'd really like to do a clean install).

I want to go back and read all the links given above.

---

### Post by oldfred on 2011-04-25
Download & install instructions. To confirm you downloaded it correctly you should do the MD5sum, or after burning CD run the verify (but if bad, CD is coaster). You should burn CD at slowest speed your CD writer allows.
Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

You need to know what video card/chip you have to know which settings may be best.

Check your chipset with:

lspci -nn|grep VGA

From my laptop:
fred@fred-LT-A105:~$ lspci -nn|grep VGA
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller [8086:27a2] (rev 03)

---

### Post by haapsalu_sall on 2011-04-25
> Check your chipset with:

lspci -nn|grep VGA

Am I doing this from the terminal?

I don't know if this makes a difference (I'm assuming it does) but the CD was part of another Ubuntu book I bought.

---

### Post by oldfred on 2011-04-25
Yes that is a terminal command.

It is always good practice to have  a liveCD or repair CD for the current version of every operating system you have installed. I like to also have a few others that are considered rescueCD or smaller Linux versions that may boot if resources are limited. Like gparted liveCD, system rescue, Knoppix, Slitaz etc.

---

