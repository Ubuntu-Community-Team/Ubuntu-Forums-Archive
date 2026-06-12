---
title: "Ubuntu won't start from USB drive"
date: 2010-09-04
forum: Installation &amp; Upgrades
---

### Post by DaNuke on 2010-09-04
I have just downloaded Ubuntu 10.04 Lucid and I tried installing it on my desktop computer from a live USB stick created with Universal USB Installer under Windows 7. The startup menu loads fine, but then I select "Run Ubuntu from this USB" or "Install" and Ubuntu freezes on the startup screen after about 30 seconds - 1 minute. The problem is my computer because Ubuntu Lucid does starts properly on another machine when booted from the same USB drive. I can also start correctly other live distros such as Parted Magic or Clonezilla.

Any idea?

---

### Post by garvinrick4 on 2010-09-04
> **DaNuke said:**
> I have just downloaded Ubuntu 10.04 Lucid and I tried installing it on my desktop computer from a live USB stick created with Universal USB Installer under Windows 7. The startup menu loads fine, but then I select "Run Ubuntu from this USB" or "Install" and Ubuntu freezes on the startup screen after about 30 seconds - 1 minute. The problem is my computer because Ubuntu Lucid does starts properly on another machine when booted from the same USB drive. I can also start correctly other live distros such as Parted Magic or Clonezilla.

Any idea?
Try Startup Disk Creater in Ubuntu and do not forget to slide scale over to use 4 gig of persistence. Is in ubuntu software center.

---

### Post by c2tarun on 2010-09-04
for step by step guide to boot from a usb drive
 
visit:  [http://tricksfind.blogspot.com/2010/08/how-to-create-bootable-usb-pen-drive.html](http://tricksfind.blogspot.com/2010/08/how-to-create-bootable-usb-pen-drive.html)
 
 
and why are you not tryin to burn a cd and install from it.

---

### Post by gibbogle on 2010-09-04
Don't burn a CD - I just did that and it's not possible to boot from the CD.

(intramfs) Can not mount /dev/loop0 ...

---

### Post by DaNuke on 2010-09-04
I just tried the following:

[LIST=A][*]Start Ubuntu Lucid with a drive created on my netbook with Ubuntu's own tool.
[*]Same as before, but with the persistency filesystem set to maximum possible size.
[*]Burn the disc image to a physical CD and start Ubuntu Lucid from it.
[*]Write the same Ubuntu Netbook Edition image I used to install Ubuntu on my netbook and start it.[/LIST]

All of them have failed. We can now rule out the possibility of the bootable media not being correctly created, and chances are it's a problem between Ubuntu and my computer. Any ideas?

---

### Post by siddhanathan on 2010-09-04
> **DaNuke said:**
> I just tried the following:

[LIST=A]
[*]Start Ubuntu Lucid with a drive created on my netbook with Ubuntu's own tool.
[*]Same as before, but with the persistency filesystem set to maximum possible size.
[*]Burn the disc image to a physical CD and start Ubuntu Lucid from it.
[*]Write the same Ubuntu Netbook Edition image I used to install Ubuntu on my netbook and start it.
[/LIST]

All of them have failed. We can now rule out the possibility of the bootable media not being correctly created, and chances are it's a problem between Ubuntu and my computer. Any ideas?

It could be possible that the boot(startup) settings of your netbook are changed... If it does not boot a perfectly fine CD then consider getting the boot settings checked by an expert (or check it yourself only if your sure of what your doing) ..

In my laptop I have to manually select boot options if I want to boot from CD/USB/network... I trigger this by F2 key during boot... Check your netbook specs if there is something like that to trigger...

Best of luck :)

---

### Post by DaNuke on 2010-09-04
^ The netbook starts the Ubuntu USB drive just fine. It's the desktop computer what I can't get to start from the USB drives.

Either way, I'll pull out my last resort and install Ubuntu from a Feisty Fawn disc I have lying around, and see if I can later download the distro upgrade all the way up to Lucid Lynx. Wish me luck :3

---

### Post by DaNuke on 2010-09-06
Update: I did the previous method of installing an old Feisty release on my computer and then upgrading it to Lucid. I first upgraded it to Gutsy without problems (apart from the issues mentioned on the wiki), then to Hardy without problems, but then I tried upgrading to Lucid and it failed: the installer starts eating all the computer's memory, up to the point where one by one the running processes start falling apart until the system gives up and throws a kernel panic, leaving behind a broken Linux that can't even start.

Since I will be busy this week I will be taking it slowly. I'll start by trying the Ubuntu Alternate installation disc, and see if this one will start on my computer.

---

