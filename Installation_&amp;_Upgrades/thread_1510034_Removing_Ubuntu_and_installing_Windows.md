---
title: "Removing Ubuntu and installing Windows ?"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by c0brabg on 2010-06-15
Hi guys I've decided to get rid of ubuntu since I can't get my 5.1 system to work. So here is the drill :
*I have an Ubuntu installed 
*I also have a flash and an iso image of windows XP

My question is how do I remove Ubuntu and then install windows xp.
I also want to divide my drive into C and D if possible :). 
Thx in advance :)

---

### Post by kerry_s on 2010-06-15
just burn it to cd & install, can't be easier.

---

### Post by wilee-nilee on 2010-06-15
> **c0brabg said:**
> Hi guys I've decided to get rid of ubuntu since I can't get my 5.1 system to work. So here is the drill :
*I have an Ubuntu installed 
*I also have a flash and an iso image of windows XP

My question is how do I remove Ubuntu and then install windows xp.
I also want to divide my drive into C and D if possible :). 
Thx in advance :)

If you don't have sata drivers you will probably have to make sure in the bios it is ide for the hard drive.

The flash can be loaded from a MS environment maybe, I've been able to do it once, a cd is what will be best for installing though, at this point

---

### Post by c0brabg on 2010-06-15
Ok when I tried installing windows (when logged in ubuntu, using wine) it said "No valid system partions were found"

---

### Post by mirza_farid on 2010-06-15
you can write that iso on a dvd or cd and then set thee boot setup on cd/dvd rom and restart
then windows setup running and you can creat your drives and install windows
also you can have windows and ubuntu together!
why don't you try that!?

---

### Post by wilee-nilee on 2010-06-15
> **c0brabg said:**
> Ok when I tried installing windows (when logged in ubuntu, using wine) it said "No valid system partions were found"

You can't install windows from Ubuntu you have to burn the ISO to a cd, and boot it to install, you also want to make sure you have a Ubuntu cd as well even though you may not install it is a great tool for fixing things and pulling stuff out of a unfixable MS to save data.

Do you understand the bios reference and sata or ide drives? In my last post.

You could install XP to a virtual in Ubuntu though and run both but you would want at least 2 gigs of ram in a 32bit environment.

---

### Post by c0brabg on 2010-06-15
> **wilee-nilee said:**
> You can't install windows from Ubuntu you have to burn the ISO to a cd, and boot it to install, you also want to make sure you have a Ubuntu cd as well even though you may not install it is a great tool for fixing things and pulling stuff out of a unfixable MS to save data.

Do you understand the bios reference and sata or ide drives? In my last post.

You could install XP to a virtual in Ubuntu though and run both but you would want at least 2 gigs of ram in a 32bit environment.
I know what's bios and what's a sata drive. I just want to delete the ubuntu and only have XP with a C and D drive if possible. I don't have a cd now and that is why I tried installing windows to a usb using Unetbootin (not exactly installing, more like converting) and when I booted it nothing happened.

---

### Post by JustinR on 2010-06-15
> **c0brabg said:**
> I know what's bios and what's a sata drive. I just want to delete the ubuntu and only have XP with a C and D drive if possible. I don't have a cd now and that is why I tried installing windows to a usb using Unetbootin (not exactly installing, more like converting) and when I booted it nothing happened.

I've never had a successful attempt to put Windows on a USB drive before.

**Edit** Adding on to wilee-nilee's post about virtualizing.

You could install Ubuntu to that flash drive, install VirtualBox. Then use the ISO of the WindowsXP disk to install XP onto your hard disk. Make sure you follow this guide though because when you try to get into windows natively it will ask you to reactivate it because of the huge hardware change from VirtualBox to your regular hardware, specifically section 7.
[http://forums.virtualbox.org/viewtopic.php?t=9697](http://forums.virtualbox.org/viewtopic.php?t=9697)

*_Section 7_*
> Switching between VirtualBox and native boots normally would result in Windows XP deciding that reactivation is required due to the sheer number of hardware changes (e.g. chipset, graphics, audio, hdd, NIC - see this article). I have found a remedy for this (which works with my hardware setup at least). 
Activate Windows natively
Create a backup copy of %WINDIR%\system32\wpa.dbl after activation.
Set the virtual network adapter's MAC address to that of your real network adapter.
You can determine your MAC address(es) under Linux by running ifconfig.
If you have multiple network cards in your computer you will have to try each in turn (see next step):
[http://www.aumha.org/win5/a/wpa.php](http://www.aumha.org/win5/a/wpa.php) wrote:
[...] It then calculates and records a number based on the first device of each type that was found during setup, [...]
Boot Windows in VirtualBox
If you set the correct MAC address Windows should not ask for reactivation. If it does:

Shut down the guest.
Temporarily mount the Windows partition and replace %WINDIR%\system32\wpa.dbl with your backup copy.
Repeat step 2. using the MAC address of your next network adapter.

I have found that this works for me too. If it doesn't follow section 1 under DMI

---

### Post by wilee-nilee on 2010-06-15
> **c0brabg said:**
> I know what's bios and what's a sata drive. I just want to delete the ubuntu and only have XP with a C and D drive if possible. I don't have a cd now and that is why I tried installing windows to a usb using Unetbootin (not exactly installing, more like converting) and when I booted it nothing happened.

There was a thread about trying to load XP to a thumb in Ubuntu there was no real answer. But a burned cd will install and you can do a custom install and build the c, then d from XP after it is installed. 

There is also a partition manager called partition wizard that will build usable ntfs partitions I believe. Gparted wont work though from Ubuntu.

[http://www.partitionwizard.com/](http://www.partitionwizard.com/)

As I said earlier you can put XP into a virtual for now until you have a XP and Ubuntu cd. The Ubuntu is a backup fixer tool you should have to make life easier, cheap insurance so to speak. The virtual install only needs a ISO

---

### Post by c0brabg on 2010-06-15
> **wilee-nilee said:**
> There was a thread about trying to load XP to a thumb in Ubuntu there was no real answer. But a burned cd will install and you can do a custom install and build the c, then d from XP after it is installed. 

There is also a partition manager called partition wizard that will build usable ntfs partitions I believe. Gparted wont work though from Ubuntu.

[http://www.partitionwizard.com/](http://www.partitionwizard.com/)

As I said earlier you can put XP into a virtual for now until you have a XP and Ubuntu cd. The Ubuntu is a backup fixer tool you should have to make life easier, cheap insurance so to speak. The virtual install only needs a ISO

Well ok guess I am going to have to go and buy a CD

---

### Post by JustinR on 2010-06-15
My post above would help you instead of having to buy a disk. Although it requires some knowledge I could help. I've done it before and it works fine.
> Well ok guess I am going to have to go and buy a CD

---

### Post by wilee-nilee on 2010-06-15
> **JustinR said:**
> My post above would help you instead of having to buy a disk. Although it requires some knowledge I could help. I've done it before and it works fine.

Justin I appreciate your help, but at the least a person should always have a bootable install media whether it be a thumb or cd. Without these bootable media it becomes very difficult to do fixes like just reloading the MBR with two commands with both XP and Ubuntu.

If we can stay on track with just doing a virtual or a standard cd install I think the OP will be served best.

We have to be careful with a this worked for me situation when your not there to actually do it does this make sense.;)

---

### Post by JustinR on 2010-06-15
> **wilee-nilee said:**
> Justin I appreciate your help, but at the least a person should always have a bootable install media whether it be a thumb or cd. Without these bootable media it becomes very difficult to do fixes like just reloading the MBR with two commands with both XP and Ubuntu.

If we can stay on track with just doing a virtual or a standard cd install I think the OP will be served best.

We have to be careful with a this worked for me situation when your not there to actually do it does this make sense.;)

Alright I do agree - its not as much as it worked for me but that it really does work if you want it to. :smile:

---

### Post by wilee-nilee on 2010-06-15
> **JustinR said:**
> Alright I do agree - its not as much as it worked for me but that it really does work if you want it to. :smile:

No it's all good, we really want to just make sure that the OP gets from point a to b and if they want to try a custom setup now thats okay with me, but they may want to try that later.;)

I'm not trying to stop anybody from doing what works for them but to just make sure it is as the OP wants.

---

### Post by kerry_s on 2010-06-15
grab this-> [http://www.ezbsystems.com/ultraiso/download.htm](http://www.ezbsystems.com/ultraiso/download.htm)
all you need is the trial version.
run it as root through wine to burn the xp iso to a usb fash drive.

it's the only tool i've found that can properly burn a windows iso to flash drive, would be better if you you can do it from windows, but i don't know if you have windows. it's been at least a year & half the last time i used it in wine, so hopefully it still works.

---

### Post by wilee-nilee on 2010-06-15
> **kerry_s said:**
> grab this-> [http://www.ezbsystems.com/ultraiso/download.htm](http://www.ezbsystems.com/ultraiso/download.htm)
all you need is the trial version.
run it as root through wine to burn the xp iso to a usb fash drive.

it's the only tool i've found that can properly burn a windows iso to flash drive, would be better if you you can do it from windows, but i don't know if you have windows. it's been at least a year & half the last time i used it in wine, so hopefully it still works.

I will have to try that one I have been able to load a thumb in windows with novicorps win to flash 0.6 beta.

I don't use wine ever as I have virtuals of XP and licenses for XP and W7.

---

### Post by c0brabg on 2010-06-15
> **kerry_s said:**
> grab this-> [http://www.ezbsystems.com/ultraiso/download.htm](http://www.ezbsystems.com/ultraiso/download.htm)
all you need is the trial version.
run it as root through wine to burn the xp iso to a usb fash drive.

it's the only tool i've found that can properly burn a windows iso to flash drive, would be better if you you can do it from windows, but i don't know if you have windows. it's been at least a year & half the last time i used it in wine, so hopefully it still works.

Just how do I run root with wine. Launch terminal write : sudo -s and then launch program from there ?
wine: /home/aleksandar/.wine is not owned by you
That's what I get when I tried running wine as root.
EDIT : I just installed iso image on cd, now going to try out. Btw the method with the usb stick didn't work, I managed to install the program ultraiso but it wasn't working properly and couldn't detect the flash drive (my guess was that it had to be formated to fat or fat32 because mine was ntfs)

---

### Post by c0brabg on 2010-06-15
So how the hell do I format the drive, enabling it to be used by windows and removing Ubuntu, I can't find a boot program for that (except partion wizard which I can't get to work using wine) :confused:

---

### Post by JustinR on 2010-06-15
> **c0brabg said:**
> So how the hell do I format the drive, enabling it to be used by windows and removing Ubuntu, I can't find a boot program for that (except partion wizard which I can't get to work using wine) :confused:

Just use an Ubuntu live cd/usb to format the drive with Disk Utility or GParted.

---

### Post by wilee-nilee on 2010-06-15
> **JustinR said:**
> Just use an Ubuntu live cd/usb to format the drive with Disk Utility or GParted.

XP wont install into a ntfs partition built by gparted I'm not sure why, W7 does.

---

### Post by JustinR on 2010-06-15
XP Professional works fine. And even if it doesn't I though there was an option to erase an existing partition.

---

