---
title: "Clean Install Trusty 14.04 error: malformed file"
date: 2014-04-19
forum: Installation &amp; Upgrades
---

### Post by brosskgm on 2014-04-19
error: malformed file
Press any key to continue ......

I had this problem a week or so ago with beta 2 and it's still present in a clean install downloaded
today Sat 19 Apr 2014 08:13:38 AM MDT

500Gb HD, 2.5 Dual Core Intel 64bit 4 gig ram.

I'm running a dual drive system 12.04 on one, 14.04 now on the other. During install I found that the
blank drive had to be set to primary drive and second drive un-pluged before the DVD would boot
fully and allow the install.

The error doesn't happen right away, but after 4 or 5 reboots and the screen gives a boarder around it, the error
is in the upper left corner before anything else.

Press enter and it continues and boots.

Thanks
Bob Ross

---

### Post by bapoumba on 2014-04-19
[http://ubuntuforums.org/showthread.php?t=2215960](http://ubuntuforums.org/showthread.php?t=2215960)

Others have seen it, I saw it once. No real idea, sorry.

---

### Post by Navneet_Kumar on 2014-04-19
it maye be due to the following 2 reasons:
1.corrupted download of iso file.
2.or any problems during making of bootable usb i.e copying the files to the usb...........hope this helps.

---

### Post by brosskgm on 2014-04-19
12.04 still works great. Maybe something to do with installing one of these Virtual Box & Extensions,
 Arduino? These are the only thing I installed and there was no updates beyond it installing updates
during the install. I formated the drive again. I'll try again tomorrow and test after each
program installed.

> **bapoumba said:**
> [http://ubuntuforums.org/showthread.php?t=2215960](http://ubuntuforums.org/showthread.php?t=2215960)

Others have seen it, I saw it once. No real idea, sorry.

---

### Post by raccoonstrait on 2014-04-20
I saw this message at the begining of bootup. The message dissapeared after I ran boot-repair. Not sure if that is actually related.

---

### Post by brosskgm on 2014-04-20
I already deleted the drive. Found a few other issues with 14.04 that I decided to wait a while. I'm sure a lot of this will get worked on as time goes forward. 12.04 is running fine. VirtualBox from the software center is not right and it doesn't detect any USB devices (Yes all extensions etc.. installed) then I install from the web site and they only cover to 13.10, it detects a few USB devices but does not allow them to be clicked, they are grayed out. So maybe I might have been rushing it to update. Might be best to wait.

---

### Post by bapoumba on 2014-04-21
> **raccoonstrait said:**
> I saw this message at the begining of bootup. The message dissapeared after I ran boot-repair. Not sure if that is actually related.
Had I seen it afterwards, that is what I would have done.

---

### Post by RickKnight on 2014-04-23
> **brosskgm said:**
> error: malformed file
Press any key to continue ......

Thanks
Bob Ross

I have this same problem. After doing a clean install of 13.10 on a new system, I got tired of the upgrade nag and decided to upgrade to 14.04. When the upgrade was finished the error message showed up and the boot splash screen went away.

Thanks,
Rick

---

### Post by brosskgm on 2014-04-23
I never tried 13.10 I stuck with the 12.04LTS for the last several years and when 14.04LTS was released I installed to a clean drive.

After the 4th install the error went away. The only thing I did different was burn to DVD at 4 speed. Awful slow, and I not sure that was the problem but after the install and installing all the software it didn't do it. But the drive was cleaned again because VirtualBox is not detecting the USB devices connected to the system anywhere. 14.04 finds them all.

VirtualBox only show a release for 13.10 so there could be an issue they need to work on. Even after following the processes to make sure they are read doesn't work. 

I even installed 12.04 on the hard drive and installed VirtualBox and it found the USB devices. Go figure that one out.

As soon as someone tells me what the difference for the VirtualBox USB devices between 12.04 and 14.04 I'll be done.

I liked 14.04 but I have a few programs and two scanners that Ubuntu doesn't have drivers for.


> **RickKnight said:**
> I have this same problem. After doing a clean install of 13.10 on a new system, I got tired of the upgrade nag and decided to upgrade to 14.04. When the upgrade was finished the error message showed up and the boot splash screen went away.

Thanks,
Rick

---

### Post by Oldster on 2014-04-25
I'm seeing this as well every few boots. I upgraded from 12.04LTS.

---

### Post by brosskgm on 2014-04-25
I didn't use the upgrade. Those always seemed to have some issue of certain files not put in that should have or that something will stop working.

So far after download yesterday and fresh install for the 5th time, 18 cold boots, a few warm boots so far and no more error.

This is what I did. Don't know if it has anything to do with it but this finally stopped the error for me.

Format drive as master boot - 500Gb

Burn DVD iso at 8 speed. Takes longer, and did a verify on the burn. Maximum, 18, 16, 12 brought error.

When installing made drive being installed to as #2 - double checked in bios

DVD #1
Drive #2

Removed any additional drives until install complete. Unplugged all non essential devices.

Rebooted a couple times after install before anything was done. Ran update and got a
 couple security patches and system updates.

Rebooted a couple more times.
 
This install went much quicker than the previous 4 did.

Even VirtualBox saw all connected devices this time.
Previous times it would not detect connected usb devices.

Rebooted after VirtualBox. No error.

Started installing the few I needed and copied all mail and browser ./directories over, re-booted
and all worked great and no more error. About 6 hours total install/switch over time.

---

### Post by bapoumba on 2014-04-25
Saw it last night, so that is the second time here. Hitting space bar got me booted up.

I have been considering doing a fresh install from some time now. Upgraded from two releases back so far. My partitions are a little messy, and I want an additional distro so another reason to do it.

---

### Post by spacesamurai2 on 2014-04-29
I have been updating mine since 9.10 (Karmic Koala) and just saw this issue now. Looks like the bug report is in:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1311247](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1311247)

---

### Post by bapoumba on 2014-04-29
> **spacesamurai2 said:**
> I have been updating mine since 9.10 (Karmic Koala) and just saw this issue now. Looks like the bug report is in:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1311247](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1311247)
Ah, good find, missed it the other day.. I clean installed two days ago, will see if it happens again.

---

### Post by papapenguin on 2014-06-03
I also have this error intermittently...at one point I tried CTL+ALT+DEL several times in a row to reboot and it kept giving me the error...I then gave up, pressed enter to continue and booted into system...I restarted immediately and didn't get the error message upon reboot...

---

### Post by bapoumba on 2014-06-03
> **papapenguin said:**
> I also have this error intermittently...at one point I tried CTL+ALT+DEL several times in a row to reboot and it kept giving me the error...I then gave up, pressed enter to continue and booted into system...I restarted immediately and didn't get the error message upon reboot...

Just to point out I have not seen it yet after my clean install, over a month ago. I reboot everyday.

---

### Post by Neale_Graham on 2014-07-18
I used the sudo touch /forcecheck command so force a disk check on my volumes as I have error on one of them, and I am now getting the error  malformed file... press any key to continue.
I will see if I still get the error after removing this command.

---

### Post by Mallasl on 2014-07-23
I got same errror msg. My problem was usb-device(headphones) which i unplugged and problem solved.

---

### Post by lrajat on 2014-08-03
Here is what i did.

1) sudo nano /etc/defaults/grub
2) Replace              GRUB_DEFAULT=0 with GRUB_DEFAULT=1
3) Sudo update-grub
4) Reboot
Issue fixed.
Hope this helps !!

---

### Post by oygle on 2014-09-28
Did a fresh install of 14.04.1 yesterday, applied all the updates, and am now getting this on boot ...

error: malformed file

I rebooted and got the same message. I do have a USB stick connected, it may be that ? Will try a reboot without that connected. Might try the command ..

```
sudo touch /forcecheck
```

Well, it made no difference by not having the USB drive connected. The bug is at [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1311247](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1311247)

Is there a fix for this ?

---

### Post by mazutchik on 2014-10-30
> **lrajat said:**
> Here is what i did.

1) sudo nano /etc/defaults/grub
2) Replace              GRUB_DEFAULT=0 with GRUB_DEFAULT=1
3) Sudo update-grub
4) Reboot
Issue fixed.
Hope this helps !!

string "**GRUB_DEFAULT=0**" in file **/etc/default/grub** sets the default menu entry by menu position. The first "menuentry" in grub.cfg is 0, the second is 1, etc.

**you haven't fixed issue!** you have changed the default menuentry to load on boot

---

### Post by mazutchik on 2014-10-30
there is no fix today:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1311247](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1311247)

---

### Post by joseh-furtado on 2015-04-03
Many erros about initializing Ubunt happening to me in many versions and distros. All happen after install nvidia driver. In my case is 304 version to 9500 GT. Inj malformad file case, sure thet is a logical messange, I solved unistalled and reisntalling nvidia like $ sudo apt-get install nvidia-current* using terminal in Ctrl+Alt+F1. Observed that Nvidia grafics driver change many inportant files in kernel and grub. Maybe thats the problem, kernel files and initializing files incorrected writed. I don't know exactly whats happen. But maybe thats the solution. Update linux is a more easy solution. So maybe can't update now because don't have updates. Then try to detect or remember what was instaled before this error and unistall such packages, prograns or aplications. And reinstall. It's worked to me.

---

