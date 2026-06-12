---
title: "Problems dual booting Ubuntu 7.10 and WinXP Pro"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by kablack7 on 2008-02-18
Hello everyone, I'm new here, and also new to Ubuntu.

I recently decided to try Ubuntu, and to see what it offers. I decided to install it on my 80 gig backup drive alone, since I didn't want to put it on my RAID-0 array (which is what windows is installed on).

I booted from the Live CD, and installed Ubuntu on the 80 gigger with no problem. However, when booting, I don't see the GRUB screen after the POST screen, it just automatically boots into windows without giving me the option to boot Ubuntu. A friend of mine just installed Ubuntu in the same fashion, with no problems. The only difference is he installed Ubuntu on the same HD as his windows installation, and created a separate partition, whereas I have Ubuntu installed on its own harddrive. 

Sorry if this question has been addressed before, but I couldn't find any posts with similar problems. Most of the fixes I've found for repairing GRUB have been from the Ubuntu terminal screen, which isn't much help to me, since I can't even boot into Ubuntu. 

System specs:

2x250 gb harddrives in RAID-0
1x80 gd harddrive backup
AMD athlon X2 5400+
2 gigs ram
nVidia GeForce 8600 GT
ABIT KN9 SLI mobo
Windows XP professional, Ubuntu 7.10

---

### Post by njparton on 2008-02-18
Grub (the linux bootloader) will probaby have been installed to the master boot record on your 80GB drive.

In the BIOS, select this hard drive to boot first, not your raid array as it is currently.

However, if you're using software raid and not supported hardware raid then ubuntu won't have detected your windows installation so grub won't contain an entry for it.  You'll have to manually boot between the two.  Not many onboard software raid chips are supported by linux unfortunately.

---

### Post by kablack7 on 2008-02-18
I thought of this, but in my BIOS, the only option I have in the boot order menu is "Hard disk", it doesn't list the individual drives.

---

### Post by AgentZ86 on 2008-02-18
> **kablack7 said:**
> Hello everyone, I'm new here, and also new to Ubuntu.

I recently decided to try Ubuntu, and to see what it offers. I decided to install it on my 80 gig backup drive alone, since I didn't want to put it on my RAID-0 array (which is what windows is installed on).

I booted from the Live CD, and installed Ubuntu on the 80 gigger with no problem. However, when booting, I don't see the GRUB screen after the POST screen, it just automatically boots into windows without giving me the option to boot Ubuntu. A friend of mine just installed Ubuntu in the same fashion, with no problems. The only difference is he installed Ubuntu on the same HD as his windows installation, and created a separate partition, whereas I have Ubuntu installed on its own harddrive. 

Sorry if this question has been addressed before, but I couldn't find any posts with similar problems. Most of the fixes I've found for repairing GRUB have been from the Ubuntu terminal screen, which isn't much help to me, since I can't even boot into Ubuntu. 

System specs:

2x250 gb harddrives in RAID-0
1x80 gd harddrive backup
AMD athlon X2 5400+
2 gigs ram
nVidia GeForce 8600 GT
ABIT KN9 SLI mobo
Windows XP professional, Ubuntu 7.10

Hi, I hope I can help.

If your windows is on another drive or array, that most likely this is your boot device, and it would typically boot to the first bootable device which in this case would be your windows installation.

Is your raid array, a scisi array ? or ide ? or is it soft raid ? this will also make a difference.

When booting you can go into the setup configuration/bios of your computer and select the boot device, or to change the order of the boot device so that it will boot to your Ubuntu drive. And it may be entact and boot directly to the 80 gig drive now. 

If it's a scissi controller you may have to disable it until you can find out whats going on with your installation.

But mostly and typically the installation is done on your main boot drive and let grub take over the boot, however you have to partition the drives and also create a swap partition, not big deal, but you may have to resize your raid drives a bit to make some room for the Ubuntu, that is the most typical way to install Dual boot. I"m not sure what your friend has done, but are you sure he installed grup to the backup drive or to the main boot device ?

You will get the boot screen which asks you if you want to boot to windows or ubuntu etc. And once you get that you can adjust your boot/grub/menu.1st to change the order of booting so that windows will always boot if no buttons are selected. If that's what you want it to do, otherwise leave it and it will boot to Ubuntu and you have to manually select Windows in order for it to boot to windows.

Anyhow I would try the setup/configuration in your bios also you may be able to select F12 during bootup and you can select your boot device such as CD/IDE/Raid/floppy etc.

I hope this helps

---

### Post by AgentZ86 on 2008-02-18
> **kablack7 said:**
> I thought of this, but in my BIOS, the only option I have in the boot order menu is "Hard disk", it doesn't list the individual drives.

Try to select F12 during boot up you have have to press it a few time to get the boot device screen to come up.

Also there may be a section in the IDE device or Advance portion of your bios. Try looking around some more for something about boot order, or boot device etc.

There should be somthing that allows you to select the CD to boot or some other device. That would be very unusual if there was not boot order selection.

However if you have all scisi drives this might be done from within your scisi controller.

Anyhow, thats about all I know.

Also if you do decide to install on the raid, resize and create your desired partition a ext3 and a small swap, but don't let ubuntu take over your whole drive etc. only install on you created partitions once you resize them. with the tool thats on Ubuntu or Gparted Live CD or whatever tool you use for partitions

Also you may want to try just unplugging the raid to see if your installation will boot to the hard drive now just to see.

---

### Post by kablack7 on 2008-02-18
Got it... sortof

There was an option in my BIOS that I was missing, where I could set my 80 gig harddrive as the primary boot harddrive.

However, with this harddrive set as such, after the BIOS screen, I get a message saying "failed to load Operating System"

Should I just try a reinstall? Or is there something else afoot here?

edit: it's an SCSI RAID-0 array, don't know if that makes a difference

---

### Post by njparton on 2008-02-18
Reinstall with the 80GB hard drive as the first booted device and to be safe unhook the drives attached to the SCSI device (that way your windows MBR won't be overwritten by mistake).

You'll then have to boot between ubuntu and windows using the BIOS boot menu which is usually accessed via F12 during boot up as indicated above.  I do this as my windows software raid array isn't recognised by ubuntu during installation.  I leave my PC to boot into windows (for the purposes of my girlfriend) and I boot into ubuntu via F12.

---

### Post by kablack7 on 2008-02-18
> **njparton said:**
> Reinstall with the 80GB hard drive as the first booted device and to be safe unhook the drives attached to the SCSI device (that way your windows MBR won't be overwritten by mistake).

You'll then have to boot between ubuntu and windows using the BIOS boot menu which is usually accessed via F12 during boot up as indicated above.  I do this as my windows software raid array isn't recognised by ubuntu during installation.  I leave my PC to boot into windows (for the purposes of my girlfriend) and I boot into ubuntu via F12.

I tried that, and I still get the "Error loading operating system" error after the BIOS POST screen. I am forced to reboot, and change the boot order back to my RAID array to load windows.

---

### Post by kablack7 on 2008-02-18
Any other ideas? Has anyone else ever gotten this "Error loading operating system" message before?

---

### Post by kablack7 on 2008-02-18
Okay, I made a little progress. I found something online that got me to boot into the Live CD, and enter this code:

```

>sudo grub
>find /boot/grub/stage1
>root (hd,0,0) <(using harddrive that the find command displayed)
>setup (hd0)
>quit

```

This was supposed to tell grub which disk Ubuntu was on, or something. However, now when I try to boot onto the Ubuntu harddrive, I get this message:

"Error 21, selected drive does not exist"

I've tried googling this, but all the solutions seem to involve problems with master/slave drives on IDE cables, and this doesn't apply to me since I'm using SATA drives.

Could it be because I have a RAID-0 array?

---

### Post by AgentZ86 on 2008-02-18
> **kablack7 said:**
> Any other ideas? Has anyone else ever gotten this "Error loading operating system" message before?

Yes this is typical when the bios does not find an os, and does not boot up.

I would reinstall the Ubuntu on the 80 gig drive now, and allow grub to be installed to the mbr of that hard drive, and you should be able to boot to Ubuntu.

I hope this helps.

---

### Post by njparton on 2008-02-19
For some reason grub or ubuntu is getting confused during install because of you set up.  It could be the way you have the bios set up or your disk configuration.

Make sure you just have the 80GB drive plugged in, it's set as the first boot device and grub is installed to hd0 or sd0 during the installation process.

---

### Post by kablack7 on 2008-02-19
Is it possible to safely detach and reattach my RAID array without destroying it? 

I don't want to lose everything I have on the array. Can I just unplug the drives, and plug them back in again when Ubuntu is installed?

It's an SCSI RAID-0 array.

---

### Post by njparton on 2008-02-19
Unplug the SCSI card would be the safest way and leave the drives attached.

If it boots up without any drives attached then you may have problems when you re-attach them.

---

### Post by dstew on 2008-02-19
Your error 21 message is due to a configuration problem with your menu.lst file. Since you got the grub menu, grub is installed correctly. You just need to correct this file. We can help.

First, you can try a temporary correction by editing the menu commands right from the grub menu screen. If your edit works, you will get into your Ubuntu system, and you can easily make the change permanent from there. To edit a menu item, at the grub screen, press 'e'. Look at the menu commands. The root statement should have the argument (hd0,0). If it does not, select it with the up/down arrow, press 'e' again to edit it, then 'enter' to save the change, than 'b' to boot. As I recall, the root that you used when you installed grub was (hd0,0). However, if you installed grub with any drive unplugged, then plugged it in again, you might have the opposite problem. In that case, the correct root might be (hd1,0). If Ubuntu boots with the new root argument, edit the file /boot/grub/menu.lst to make the change permanent.

I would strongly advise against unplugging and plugging disks when installing grub. That confuses the installer a lot.

---

### Post by zipperback on 2008-02-19
Check the following link.
[http://ubuntuforums.org/showthread.php?t=642627#6](http://ubuntuforums.org/showthread.php?t=642627#6)

I posted links to several how to pages.

- zipperback
:popcorn:

---

