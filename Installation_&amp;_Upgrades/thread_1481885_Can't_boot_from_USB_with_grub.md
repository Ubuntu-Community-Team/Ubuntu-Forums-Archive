---
title: "Can't boot from USB with grub?"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by kananesgi on 2010-05-13
I'm sorry if this has been asked and answered before. I found a little info in the ubuntu help info but their method (using the grub command line to find the USB, then using chainloader +1 to boot from it) did not work. Their method of using a minimal linux kernal sounds extraordinaraly complex, and perhaps not even possible since I do not have a CD drive in this computer.
 
The problem is, I cannot boot my netbook from the USB anymore. The netbook is an EeePC 900HD, which ran WinXP originally. I was able to access the BIOS before installing UNR and set it to boot from the USB before the HD. However, it now appears that this grub thing has replaced the netbook's original BIOS and now I cannot boot from the USB anymore. Using Google, I found info in the Ubuntu documentation that details how to boot from USB with grub, but their method did not work. When I use the grub commands to identify the various HDs, I get the following:
 
"root (hd0,0)" returns "error: no such partition."
"root (hd0,1)" returns "(hd0,1): Filesystem is ntfs" [THIS IS MY WINDOWS XP PARTITION]
"root (hd0,2)" returns "(hd0,2) : Filesystem is unknown" [I THINK THIS IS MY UBUNTU PARTITION"
"root (hd1,0)" returns "error: hd1,0 cannot get C/H/S values." [THIS SHOULD BE MY USB]
 
If I do a "find /[TAB]" command on hd0,1 it returns the directory structure of the WinXP partition. However, if I run that command on any of the others, it does nothing, just loads another command line with "find /" already typed.
 
Is there any way to get rid of this grub thing and get my old BIOS back? Or, is there an easier way to make grub read from the USB? Seems like this should be an innate function of grub, since many Linux distros can boot from USB. Doesn't seem right that's it's such a pain in the rear to get it to boot from USB. I would not have done a regular install of ubuntu if I'd known it was going to get rid of the BIOS menu.
 
The reason I am trying to do this is I want to replace the current UNR installation with Xubuntu. The little machine just can't really handle UNR right now. I didn't know that before installing it.

---

### Post by wilee-nilee on 2010-05-13
Grub cannot erases or do anything to bios if it had your computer would be a door stop in other words bricked. So what is it that you want in the end? the post has really no usable information in it. So tell us your final goal and post this boot script so we can see whats there. Post it in code tags by highlighting the text in the reply window then tick on # in the reply panel the submit reply.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
So I would load the thumb again with any of the usb loaders, or use a live cd from a external cd reader.

I recognize that you think that the bios is toast, but if it was your computer wouldn't run at all.

---

### Post by kananesgi on 2010-05-13
> **wilee-nilee said:**
> Grub cannot erases or do anything to bios if it had your computer would be a door stop in other words bricked. So what is it that you want in the end? the post has really no usable information in it. So tell us your final goal and post this boot script so we can see whats there. Post it in code tags by highlighting the text in the reply window then tick on # in the reply panel the submit reply.
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
So I would load the thumb again with any of the usb loaders, or use a live cd from a external cd reader.
 
I recognize that you think that the bios is toast, but if it was your computer wouldn't run at all.
 
I thought it was relatively obvous what my goal is. I WANT TO BE ABLE TO BOOT FROM THE USB AGAIN. I was able to before installing UNR. Now, I cannot make grub use the USB. I cannot load the computer from the thumb because grub won't do it, and that's what I want to fix. Either that, or get my old BIOS menus back (hit F2 to enter setup), since I was able to load from USB with it. Right now, the first thing the computer displays during bootup is grub, and there is nothing there I can find to boot from the USB.
 
I apologize if I'm a little terse here. I'm busy and I thought I explained the problem pretty well in the first post. Was hoping to have some better solution suggestions today.
 
I'll look at the boot script to see if it can help.

---

### Post by oldfred on 2010-05-13
I found this on the ASUS forum:
[http://vip.asus.com/forum/view.aspx?board_id=20&model=Eee+PC+900%2FLinux&id=20091001094759687&page=1&SLanguage=en-us](http://vip.asus.com/forum/view.aspx?board_id=20&model=Eee+PC+900%2FLinux&id=20091001094759687&page=1&SLanguage=en-us)

Have you tried all those settings in BIOS? BIOS is before any grub boot.

---

### Post by frostschutz on 2010-05-13
> **kananesgi said:**
> "root (hd0,1)" returns "(hd0,1): Filesystem is ntfs" [THIS IS MY WINDOWS XP PARTITION]

Then you are not booting from USB, but from your internal HDD. I think Grub can not see USB disks unless it's directly booted from one, so install GRUB on a USB stick, and boot from USB. Then the USB stick will be hd0. At least, that's how it works for me (I have an 8GB stick with amd64/x86/netbook Ubuntu and other Linux Live CDs on it).

---

### Post by kyphi on 2010-05-13
To boot from a USB stick you have to create a bootable USB stick first which includes the operating system that you want to use.

To access the boot screen on the Eee PC, insert the bootable USB stick (with the operating system), start the Eee PC and repeatedly press "Esc" until the boot screen appears.  Then select the USB device and press Enter.

I have two Eee PCs (701 and 1000H) running Lucid Lynx UNR without any problems whatsoever.

There is nothing wrong with your BIOS and GRUB is innocent.

If you want to install Xubuntu, use the method outlined above.  Download Xubuntu first and then create a bootable USB stick.  Programs such as ImageWriter or Startup Disk Creator will do that for you.

---

### Post by kananesgi on 2010-05-14
> **kyphi said:**
> 
To access the boot screen on the Eee PC, insert the bootable USB stick (with the operating system), start the Eee PC and repeatedly press "Esc" until the boot screen appears. Then select the USB device and press Enter.

 
This is what I was looking for. 
 
I already created a bootable USB. I implied that before with the fact that I was booting from the USB before installing UNR. The problem I've been having is that the very first thing the computer displays is grub. Before, it displayed a splash screen with "hit F2 to enter boot menu" or bios, something to that effect, where I was able to tell it to boot from USB before HD. What I've been trying to find out was how to tell the darn thing to boot from the USB again. As it is, it's booting from the HD before I ever have a chance to tell it to boot from USB. Thing is, I had it setup to always boot from USB first, so that if a bootable USB was inserted, it would boot from it without asking. However, now grub is the first thing I see and it never tries to boot from the USB. Either grub or UNR itself must have altered something here since it automatically did it before, and now won't.
 
I'll try hitting ESC during boot and hopefully that will get me back to the bios/boot menu. I'm trying to install Xubuntu because the UI of the Lucid Lynx UNR is running extremely slowly. For example, if I hover over one of the icons on a menu, it takes the computer about 3 seconds to catch up and highlight that icon. I think this is because this particular EeePC uses a flash HD. WinXP was preinstalled because the flash HD could not handle Vista. It's a very low power system, but it ran extremely fast with XP. I was hoping to get that performance or better with Ubuntu and was quite disappointed when I found it so slow.
 
Thanks for all the help here folks. I really want to make this work well. I'm just having some very frustrating problems with it and this is (obviously) my first experience with Linux. So far, I've had almost nothing but trouble (between this netbook and my laptop - Toshiba L505D) and it's really aggrivating me.

---

### Post by kananesgi on 2010-05-14
Another question.
 
If I reformat the partition that Lucid Lynx was installed on using Windows, will that get rid of grub and return me to my original bootup sequence? Or will that cause the computer to no longer boot properly? I really am starting to think I should have simply created a new partition and used wubi to install UNR via Windows. Also, can I install Xubuntu with wubi (or some other method via Windows)?

---

### Post by oldfred on 2010-05-14
No every boot loader that is in the MBR requires additional files that are in the install partition. You need to reinstall a windows boot loader if you just want to boot windows. From a windows cd it is fixboot. You can install a generic windows boot loader with Ubuntu (or most linux)

Restore basic windows boot loader - universe enabled
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr

the windows boot loader in the MBR just really looks for the partition with a boot flag (active ) to continue the boot.

If you are really a windows only person wubi will let you try Ubuntu, but it is not meant for long term use. It requires the windows boot loader to boot first and is running as file in the NTFS partition, so if your windows ever has issues so does the wubi install.

---

### Post by snowpine on 2010-05-14
Next time you turn on the eee, press F2 really, really quickly and you should get into the BIOS (keep rebooting and trying until you get in). Once you are in the BIOS, look for anything called "boot booster" or "quick boost" and make sure it is disabled. This should prevent the straight-to-grub problem in the future. At least this works on my Asus eee 900ha which I would imagine has simliar BIOS to your model.

You already got some good advice on booting from USB once you're into the BIOS, so I'll stop talking now, good luck! ;)

---

### Post by kananesgi on 2010-05-15
> **snowpine said:**
> Next time you turn on the eee, press F2 really, really quickly and you should get into the BIOS (keep rebooting and trying until you get in). Once you are in the BIOS, look for anything called "boot booster" or "quick boost" and make sure it is disabled. This should prevent the straight-to-grub problem in the future. At least this works on my Asus eee 900ha which I would imagine has simliar BIOS to your model.
 
You already got some good advice on booting from USB once you're into the BIOS, so I'll stop talking now, good luck! ;)
 
This got what I was looking for. I had tried it before, but I guess I didn't start hitting F2 soon enough or something. I had to try it a couple times but I finally was able to get into the BIOS setup got it to boot from the USB. I also disabled the boot boost stuff so it now displays the BIOS splash screen again. From there, I was able to delete the old UNR installation. Had some problems getting the new one installed because I tried to resize the Windows partition and didn't realize Windows was hibernating at the time. Since I'd already deleted the UNR partition, I couldn't boot anymore. That took a little time to solve, finally did with a liveUSB copy of Xubuntu and ms-sys. Got all that solved so I could easily install Xubuntu on the HD and it works flawlessly. Works as fast as Windows XP does on this little computer.

---

### Post by ftravers on 2010-07-11
I'm having almost the same problem.  I have a netbook (no CD).  However, I can setup the bios to boot from USB and I have another option to choose the boot device while booting up...however neither of these works.  

I've created two USB boot disks.  One for plain jane Ubuntu 10.04 and one for gparted, following these instructions: [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download) (I created these on a mac, though I think that should be irrelevant.)

Regardless, I always get thrown in to grub.  I had ubuntu (UNR) installed on this netbook.  I also had win xp dual booted (started with xp then added UNR)  Everything worked fine until I did something bad and hosed my UNR install.  Is there any way to remove grub...in the past, when I had a machine installed with (any) linux I'd just throw in an XP CD and I could always boot to that...or I'd put in a gparted cd and boot to that...but I can't boot to my freakin USB while grub is on there...what gives!

Is there someway from grub to tell it to boot from the USB or is it too late by the time I'm in grub.  Okay over to the gurus to answer! ;)  Thanks guys for any good advice!

---

