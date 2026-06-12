---
title: "What problems will happen by dual-booting? How do I avoid bootloader problems?"
date: 2012-08-16
forum: Installation &amp; Upgrades
---

### Post by needhelplinux on 2012-08-16
I have Ubuntu 11.04. It will soon be unsupported, so I have to upgrade. My computer is slow, so I want to try Lubuntu 12.04.

I created a new partition with gparted. Before I install Lubuntu in the new partition, I would like to know what conflicts will happen with the bootloader.

I have read a lot by searching through websites, but I am unsure.

My Ubuntu version already has the Grub bootloader installed. If I install Lubuntu in the second partition, do I simply add the Lubuntu installation as another option in the old Grub bootloader? Will having two Grub bootloaders cause my computer to mess up? How do I install Lubuntu without installing another Grub bootloader? Is there a setting I can use with the Terminal to allow Lubuntu to install while just using the old bootloader from the Ubuntu partition?

I've read that I should install Lubuntu's bootloader in the Master Boot Record. I have no idea what the Master Boot Record is, and I don't know the difference is between installing a bootloader in a Master Boot Record or installing it in a root folder instead. What should I do?

When I created the second partition with Gparted, I didn't set it as a Boot partition yet. Do I set it as a Boot partition with Gparted or will the installation of Lubuntu automatically set the partition as a boot partition?

I've read many different things by searching through many websites, but I would just like a clear explanation of how to not cause problems or conflicts by having two Grub bootloaders. I could try it out before asking people, but I'm afraid of messing something up and not being allowed to access my original Ubuntu installation. I have my files backed up on an external hard drive, but I don't want to lose my installation settings in Ubuntu.

Thank you for taking the time to answer my questions.

---

### Post by oldfred on 2012-08-16
The MBR is the first sector on the hard drive and is what BIOS jumps to, to continue booting. As only one sector it does not have much code, so it really is just a pointer to more code somewhere else on drive. MBR also has partition table.

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

If you only have one drive, then you only have one MBR. Usually the last install takes over and installs its boot loader to the MBR. With grub2's os-prober you can find all your other installs and it will add them to the menu.

Windows uses the boot flag, so you do not have to change that. Window boot code in the MBR looks at the partition table and finds the boot flag. It then jumps to the Windows partition to continue to boot.

Most desktops do not need a separate /boot partition. Some older computer may. It depends on BIOS.

---

### Post by needhelplinux on 2012-08-16
I don't have Microsoft Windows on this hard drive. I don't have access to Microsoft Windows.

If I go to this website: [https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu](https://help.ubuntu.com/community/Lubuntu/InstallingLubuntu)

I see this:

> **VERY IMPORTANT**: If you are going to hit **Install Now** while you are on the above screen, you are going to install Lubuntu's Boot Loader ([GRUB2]("https://help.ubuntu.com/community/Grub2")) to the [MBR]("http://en.wikipedia.org/wiki/Master_boot_record") of your HDD which is sda. **By  performing this action, you are overwriting your MBR (sda) and all its  contents. This may lead to some un-bootable systems, other systems which  are installed in your machine. **

Now I'm too scared to try it. This is why I wanted to come here first. I want to get the correct way to install two operating systems on one hard drive without any chance of ruining anything.

---

### Post by oldfred on 2012-08-16
There is nothing wrong with installing Lubuntu's grub2 boot loader. If you have a liveCD we can always reinstall grub for any install.

If you do not want Lubuntu to be your primary boot loader then you can just install its boot loader to a partition. That is not normally suggested, but the installer does not seem to offer a choice not to install a boot loader.

Then in Ubuntu run this and it will find your new install and add it to your boot menu.

sudo update-grub

The primary boot loader will have that install's menu entry on top and all the other installs listed at the bottom of the menu. But you can reorganize later if you want with grub customizer (not normally installed).

---

### Post by needhelplinux on 2012-08-17
I wasn't able to get a Live CD to work.

I decided to use this guide instead: [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

I was able to get an ISO file of Lubuntu 12.04 to load in a new partition, but now I have to know how to complete the next step.

The website I linked to says this:

> **Note2:** Instead of using 'workaround', an alternative is  to modify the file /etc/mtab by erasing the line that specifies the  partition where the cdrom is mounted. This way the kernel thinks thats  the /cdrom is not mounted and will not show the advice when installing  ubuntu. I think this procedure is less dangerous than the one in the  previus note. 

I opened the "mtab" file with gksudo, now I need to know which line I should delete in order to make the kernel think the ISO file is not mounted.

Below are the contents of my "mtab" file:

> /dev/sda1 / ext4 rw,errors=remount-ro,commit=0 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/owner/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=owner 0 0

Which line do I delete to make the ISO installer think that the ISO is not mounted, in order to allow Lubuntu to install on a new partition?

---

### Post by oldfred on 2012-08-17
Your link is older, and with grub2 your can loopmount the ISO from grub and install that way. I use that method and the only somewhat tricky part is getting the path correct as grub does not see the Ubuntu mounts so everything is as it is on drive.

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

### Post by needhelplinux on 2012-08-17
Now I'm confused. Should I undo what I've done from the link in my last post? This is what I followed: [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

Should I not change anything, EXCEPT use this code:

> sudo umount -l -r -f /isodeviceShould I not change anything I've done from the above URL, and then boot into the partition with the ISO, and then use the code above? If I have the ISO file booting from a hard drive called "sda3", will I be able to install the operating system to "sda3"? Should I make another partition called "sda4" and install Lubuntu to "sda4" with the iso located in the "sda3" drive?

I cannot understand the instructions from your link here: [https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

I think it's easier for me to follow the instructions from the old website here: [https://help.ubuntu.com/community/Installation/FromLinux](https://help.ubuntu.com/community/Installation/FromLinux)

Can someone please tell me which line I should delete in my "mtab" file, in order to allow the computer to think that the ISO is not mounted? Please read my last message in this topic for more information.

Should I delete a line from my "mtab" file, or just use this code instead:
> sudo umount -l -r -f /isodevice

---

### Post by oldfred on 2012-08-17
I do not know that procedure. Procedure #2 is similar to the one with grub2 but is grub2 is even easier as you do not have to extract the kernel & init files since they are loop mounted.

Even the procedure says you may have to use backports to get the debootstrap and that was many versions ago. New ISO may not work the same. I know the grub2 procedure works as I use it.

Are you booting with grub2? If you want to post the path to your ISO, I can give you a grub2 entry to copy into 40_custom.

I mount my ISOs from this mount /media/MavData:

/media/MavData/iso

But if not mounted it really is this folder on my second drive:

/iso on my second drive hd2  in partition 4.

So this is what I boot with:

```
menuentry "Ubuntu 12.04 Precise ISO 64bit" {
    set isofile="/iso/ubuntu-12.04-desktop-amd64.iso"
    loopback loop (hd2,4)$isofile 
    linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile nomodeset
    initrd (loop)/casper/initrd.lz
}

```

---

### Post by needhelplinux on 2012-08-17
With your new instructions from [here]("https://help.ubuntu.com/community/Grub2/ISOBoot"), can I mount the ISO while it is located inside of my Ubuntu 11.04 partition or will mounting it cause my Ubuntu installation to become messed up? Should I create another partition and put the iso file into it to mount it from there?

To start from the beginning for a new person to be able to read this message and get help, here are the instructions that I think I'm supposed to do:

1. type this in the terminal: sudo mount -o loop /home/*username*/lubuntu.iso /mnt/iso/

2. add the menu entry with gksudo, and then type this in the terminal: sudo update-grub

3. restart and wait for the Grub bootloader to start, and choose the menu entry where the ISO file is located

4. Install

Are those the only things I have to do?

---

### Post by oldfred on 2012-08-17
You do not have to mount it before rebooting. You do have to decide where you want the iso file. Best (maybe required) not in partition you are installing into, but can be anywhere. It will not hurt your existing install. Example in link is in you Downloads directory.

So download iso into Downloads.

Create grub entry in 40_custom. You can copy and paste example from link if iso is in Downloads, and edit name to your login name. If your current install is not hd0,5 change that to correct partition. Be sure to include last } .

gksudo gedit /etc/grub.d/40_custom
sudo update-grub

That should add a new entry in the grub menu at the bottom and boot the ISO. I have sometimes not gotten path exactly correct and then get all sorts of errors.

> menuentry "Ubuntu 12.04 ISO" {
set isofile="/home/<username>/Downloads/ubuntu-12.04-desktop-amd64.iso"
loopback loop (hd0,5)$isofile
linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=$isofile noprompt noeject
initrd (loop)/casper/initrd.lz
}

---

### Post by needhelplinux on 2012-08-18
Thank you for helping me. I was able to get into the Lubuntu ISO with your instructions.

Now I need to know which option I should select. Should I select "Install Lubuntu 12.04 alongside Ubuntu 11.04", or should I choose "something else" and choose to install it on the empty partition?

Once I choose one of those two options, is it a good idea for me to install the new bootloader on the empty partition?

Edit:

I would look for the answers on Ubuntu's Wiki website, but I reloaded the page a few times, so the Wiki website blocked me and now says this: "You triggered the wiki's surge protection by doing too many requests in a short time."

---

### Post by oldfred on 2012-08-18
Which boot loader do you want to be in charge and listed first in the menu.  If you want to reboot into Ubuntu and update its grub, then install Lubunts's boot loader to the partition (it then is not used). If you want to boot Lubuntu directly then put it into the MBR, it will also let you boot Ubuntu.

I never like the auto install as it sets partitions sizes as it sees fit. I always want the control over sizes. But auto install is quick and easier as you do not have to think about partitions, formats and mounting / , swap. But with manual install you can add other partitions like a separate /home.

---

### Post by needhelplinux on 2012-08-19
I keep trying to install, but the installer program stops before it completes the installation without displaying an error message. The progress bar gets to the middle and then the installer just goes away.

I think I have to unmount the "isodevice".

I have to use this:

```
sudo umount -l -r -f /isodevice
```How do I unmount the "isodevice"? I tried to type this and it didn't work: 

```
sudo umount -l -r -f /home/owner/Ubuntuiso/lubuntu-12.04-desktop-i386.iso
```It said this:

```
umount: /home/owner/Ubuntuiso/lubuntu-12.04-desktop-i386.iso: not found
```How do I unmount the ISO device?

If I literally have to type "sudo umount -l -r -f /isodevice" and NOT put the actual location of the ISO in the command, then it doesn't matter because the terminal tells me this: "umount: /isodevice: not mounted"

Edit: I also tried to load the iso with the "toram" option to try to load the ISO to my computer's ram, AND I used this exact command: "sudo umount -l -r -f /isodevice", but the installer STILL closed down and went away in the middle of the installation process. I have 2 GB of ram and my computer was only using about 470 MB of ram at the time when the lubuntu installer closed itself down. It only got to the halfway point, and the installer just disappeared.

---

### Post by oldfred on 2012-08-19
Does it work ok in live mode?

Did you check that ISO is correct?

[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If grub is loopmounting the ISO, I do not think it is mounted like another mount is.
What does mount show:
```
mount
```

---

### Post by mark net on 2012-08-19
I don't have Microsoft Windows on this hard drive. I don't have access to Microsoft Windows.

---

### Post by needhelplinux on 2012-08-19
I checked the MD5sum and it was the correct value.

If I type "sudo umount -l -r -f /isodevice" in a terminal, and then I type "mount" in a terminal, this is what shows up:

```
/cow on / type overlayfs (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
/dev/shm on /cdrom type tmpfs (rw,relatime,size=738152k)
/dev/loop1 on /rofs type squashfs (ro,noatime)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
gvfs-fuse-daemon on /home/lubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=lubuntu)
```

Before I run the command to unmount the "isodevice", there is another  line in the above message that shows "sda1" as being mounted.
The extra line says this:

```
/dev/sda1 on /isodevice type ext4 (rw,relatime,user_xattr,acl,barrier=1,data=ordered)
```

Could the installer keep shutting itself down because of my computer's slow processor? While the installer is running, my computer uses 100% of the CPU. I have an hp a620n computer with an AMD Athlon XP 3200+ processor and 2 GB of RAM.

So far, I've been trying with an ISO file of "Lubuntu 12.04". I just tried with an ISO file of "Ubuntu 12.04" and the same problems happen. I also tried to install Ubuntu 12.04 with the "toram" option enabled to try to load the ISO file into my computer's RAM, but the installer still closed itself in the middle of the installation. It was also using 100% of the CPU in my computer. The md5 hash for my Ubuntu 12.04 ISO is also correct.

---

### Post by oldfred on 2012-08-19
How much RAM? And partitioning in advance so you have to swap partition can help if system is low on RAM. If specs are 512K RAM or less Lubuntu should be the choice as full Ubuntu needs more to work well.

---

### Post by needhelplinux on 2012-08-19
I have 2 GB of ram. I already added an empty partition to use for a new installation.

When I try to install Lubuntu from the Live CD, I click on "something else" in order to choose where to install it. I set the installation of a folder called "/" to install to my empty 27 GB partition. Should I set anything else up? Is that why my installation is not working? I only set the folder called "/" to be installed. I did not set anything else, such as "/boot". Should I set other folders to be installed? I thought installing a folder called "/" would include all of the other folders inside of it. For my Ubuntu 11.04 installation, I only have my normal partition with 133 GB, a swap partition with 468 MB, and a partition called "Extended" with 468 MB. I'm not sure what the Extended partition is for. (it just says "Container for Logical Partitions")

I was assuming that the Lubuntu ISO would automatically use the same "swap" partition as my fully installed Ubuntu 11.04 partition.

---

### Post by Blasphemist on 2012-08-19
> **needhelplinux said:**
> I have 2 GB of ram. I already added an empty partition to use for a new installation.

When I try to install Lubuntu from the Live CD, I click on "something else" in order to choose where to install it. I set the installation of a folder called "/" to install to my empty 27 GB partition. Should I set anything else up? Is that why my installation is not working? I only set the folder called "/" to be installed. I did not set anything else, such as "/boot". Should I set other folders to be installed? I thought installing a folder called "/" would include all of the other folders inside of it. For my Ubuntu 11.04 installation, I only have my normal partition with 133 GB, a swap partition with 468 MB, and a partition called "Extended" with 468 MB. I'm not sure what the Extended partition is for. (it just says "Container for Logical Partitions")

I was assuming that the Lubuntu ISO would automatically use the same "swap" partition as my fully installed Ubuntu 11.04 partition.

You are starting everything correctly. Yes you choose something else. Yes you choose to install on your desired partition and choose it's mountpoint as /. That is sufficient. It will use the existing swap partition but it is smaller than I'd use. But don't be changing that right now. You should have an extended partition just because you are limited to 4 primary partitions. But it sounds like the only thing in your extended partition is the swap. Still ok. Do go ahead and install the boot loader to your hard drive, usually sda. 

So what is the installation doing when it stops working? What installation task is happening? Are you sure the hard disc is not active? That the installation does for sure stop? Are you connected to the internet when you do the install?

In your 11.04 ubuntu, install boot-repair. [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) This doesn't mean I think your boot process is broken just that this can be used to pass us good details of your configuration.

When everything is done and working, you'll have Grub 2 installed in both operating partitions, 11.04 and 12.04. Whichever is the active installation at any time is determined by where the pointer in the MBR is set to. This gets set when the grub install command is run. This happens during installation of the distro and when grub 2 is updated as part of the normal update process. You can also run it yourself anytime you want. There is also a grub update command. That is run as part of the normal software update process whenever a new kernel is installed. This is what makes the new kernel show up to boot to. Because you can only have one active Grub, kernel updates to the non controlling Grub won't show up without an extra step from you. Don't worry about this for now. I run a half dozen distro's on my laptop and change them frequently so I'm well versed as are many others. We'll explain it more fully once everything is working.

---

### Post by needhelplinux on 2012-08-19
Here is a BootInfo scan of my computer with Boot-Repair:
[http://paste.ubuntu.com/1155964/](http://paste.ubuntu.com/1155964/)

When I was trying to install from booting into the ISO, I was connected to the internet.

This is what I did:

I chose to install Lubuntu 12.04 on my empty partition. I set it to use the empty partition as a folder called "/" and I chose to let the installer format the partition. I also set the partition to use a filesystem called "Ext4". I chose to let the program install the new bootloader into my unused partition.

After that, I chose to use the English language for the installation, and then I chose to use my correct time zone.

After that, I chose a username and password for the new installation. I chose a different password than the one I use for my Ubuntu 11.04 installation.

After that, the progress bar on the bottom of the installer kept going forward. Once it got to the halfway point of the Lubuntu 12.04 installation, the installer disappeared. Also, my computer was using less RAM once the installer went away, so I was assuming that the program really closed down.

Alternatively, I tried to install Ubuntu 12.04 instead. After a few tries, the installer for Ubuntu 12.04 completed the first progress bar, and a new progress bar started. That installer closed down during the beginning of the second progress bar. (I cannot remember what the second progress bar was doing. I tried to use the installer for Ubuntu 12.04 again, but it closed down before it completed the first progress bar.) Just like the Lubuntu installation process, my computer was using much less RAM once the Ubuntu installer closed down and disappeared, so I am assuming the program actually closed down.

Edit: The BootInfo log I linked to above seems to show that I have "Ubuntu 12.04 LTS" installed on my "sda3" partition, but I don't think it's true. It's probably showing up in the log because a partial installation was started, so parts of it might be installed. It doesn't show up as a menu entry on my Grub bootloader. (Yes, I did run this: sudo update-grub) It must just be in the log because of a partial and interrupted installation.

---

### Post by oldfred on 2012-08-19
It looks like neither kernel nor grub were installed in sda3. Not sure why if ISO is good, and you have plenty of RAM the installer would quit in the middle.

Did you change this not to show your name or is your name really "owner"

set isofile="/home/[COLOR=Red]owner[/COLOR]/Ubuntuiso/ubuntu-12.04-desktop-i386.iso"

---

### Post by Blasphemist on 2012-08-19
I'm still sorting through all of this as it is being done quite non standard since you are using mounted ISO's instead of installing from a live session booted to USB, CD, DVD. 

What was happening that you couldn't do a standard install? Please describe that for me and I'll keep working through the boot repair info.

---

### Post by needhelplinux on 2012-08-20
Oldfred, my username on my computer is really called "owner".

Blasphemist, I didn't install from a CD because the blank CD-RW I used to create a Live CD wasn't working. Now I think it was just a bad batch of Memorex CD-RW discs. (I've read about how bad Memorex CDs are.)

I wanted to buy a USB flash drive to create a Live USB device, but my computer's BIOS menu doesn't have a setting to boot from a USB drive. I can only boot from a CD, a hard drive, or a floppy disc. (I'm not sure why my computer's BIOS has a setting to boot from a floppy disk because my computer did not come with a floppy drive installed.)

Maybe it would be best if I buy a new batch of CD-RW discs from amazon.com and try to make another Live CD.

I found a website with instructions about how to try to boot from a usb flash drive, even if my BIOS settings won't let me, but some people in the comments section mention how the instructions didn't work for them.

In case someone wants to know, I read about it here:
[How to boot from a USB flash drive if your BIOS settings won't let you]("http://www.howtogeek.com/howto/16822/boot-from-a-usb-drive-even-if-your-bios-wont-let-you/")

---

### Post by oldfred on 2012-08-20
I have suggested plop a few times, but never tried it myself. It worked at least for some.

---

### Post by needhelplinux on 2012-08-22
oldfred and Blasphemist, thank you for taking the time to help me. I wasn't able to install the operating system while booting the ISO from the hard drive, but at least now I am able to try different versions of linux with that method.

I am going to order a new batch of CD-RW discs to make a Live CD. Hopefully, they will work this time.

Do you think it would be better to install Lubuntu 12.04, or is it better to install Ubuntu 12.04 while adding LXDE onto it? If I use Ubuntu 12.04 and add the LXDE package onto it, it will be like having Lubuntu PLUS it will be supported until 2017 with security updates.  Which way do you think is better? Lubuntu 12.04 will only be supported until October 2013.

Should I mark this topic as solved or should I leave it open in case someone else has the same problem?

---

### Post by oldfred on 2012-08-22
I know some have had issues with CD-RW. I think it depends on the CD writer and how good it is and if lens is clean. I used to use flash drives but now install from one hard drive to another with grub2's loopmount of the ISO directly.

I do not understand fully how they support Ubuntu. The underlying system is all the same in every version. So what would not be supported is the desktop. With Lubuntu install it includes a different set of default applications.

Difference between Windows manager & desktop enviroments
[http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893](http://forums.linuxmint.com/viewtopic.php?f=90&t=54945&start=0#p314893)
What is the difference between Debian, Fluxbox, XFCE,
window managers like Icewm, Openbox, Fluxbox, and Xfwm
desktop environments are KDE, Gnome, Xfce, Enlightenment, and LXDE

---

### Post by Blasphemist on 2012-08-22
I think if you will get support for a longer period and that is important to you, install Ubuntu and add LXDE.

When you boot do you see a prompt as the first thing displayed that offers a boot menu? It's F12 on my computer and it offers the ability to choose from a half dozen boot options, including USB. For me that is the only way I install these days. Unetbootin is a good app to use to create iso on the usb stick. I've had to much trouble getting a good burn from my old cd/dvd rw drive. And I can use the usb over and over and over.

---

### Post by arpanaut on 2012-08-22
There is a bug in ubiquity on the 12.04 iso that causes the installer to crash part way through on some hardware. 
The workaround is to remove the slideshow while booted to the live session,
```
sudo apt-get remove ubiquity-slideshow-ubuntu
```Then start the installation.  
For say, lubuntu you would change the last part of the command to -lubuntu.

I had this problem on my rig and this was the only way to get the 12.04 live-desktop to install.  I know ubiquity has been fixed for the 12.10 iso. and maybe this has been fixed in the 12.04.1 iso due out on the 23rd of Aug. Don't know.

Hope this helps.  The Alternate iso is another option as it does not use the slideshow.

---

### Post by needhelplinux on 2012-08-22
arpanaut, you correctly found my problem! Thank you! I was easily able to install Ubuntu 12.04 on another partition today because I followed your instructions. Now I can easily install versions of linux without needing a CD or a USB flash drive.

Blasphemist, my computer does have a choice of things to boot from when I go into the BIOS settings, but my version of BIOS doesn't have the ability to boot from a USB drive. I only have options for a hard drive, a CD, and a floppy drive.

I also didn't have any problems or conflicts with bootloaders. I chose to install the bootloader in the same partition as the new installation of Ubuntu.

oldfred, Blasphemist, and arpanaut are smarter than Bill Gates. Bill Gates will cry if he ever meets any of them. If a machine is ever connected to their minds to test their intelligence, Bill Gates will cry when he sees the results.

---

### Post by Blasphemist on 2012-08-22
> **needhelplinux said:**
> arpanaut, you correctly found my problem! Thank you! I was easily able to install Ubuntu 12.04 on another partition today because I followed your instructions. Now I can easily install versions of linux without needing a CD or a USB flash drive.

Blasphemist, my computer does have a choice of things to boot from when I go into the BIOS settings, but my version of BIOS doesn't have the ability to boot from a USB drive. I only have options for a hard drive, a CD, and a floppy drive.

I also didn't have any problems or conflicts with bootloaders. I chose to install the bootloader in the same partition as the new installation of Ubuntu.

oldfred, Blasphemist, and arpanaut are smarter than Bill Gates. Bill Gates will cry if he ever meets any of them. If a machine is ever connected to their minds to test their intelligence, Bill Gates will cry when he sees the results.

Glad to hear there was a solution.

---

