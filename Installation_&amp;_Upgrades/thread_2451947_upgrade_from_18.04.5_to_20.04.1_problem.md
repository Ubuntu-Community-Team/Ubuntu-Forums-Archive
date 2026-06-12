---
title: "upgrade from 18.04.5 to 20.04.1 problem"
date: 2020-10-13
forum: Installation &amp; Upgrades
---

### Post by jgw on 2020-10-13
I have read several threads with upgrade problems.  Mine might be slightly different.  This is the 3rd machine I have upgraded and I have also installed one on another machine.  This one is odd.  I choose to upgrade from the update program (which worked just fine on the last two I did).  This one, however, installed all the software and was installing.  Then the screen went blank but the disk activity light was active so I left it alone.  Then the activity light went dark but blinked every now and then.  After about a half hour of this, I tried to re-boot and that failed so I figured I had a serious problem.  So, I had 20.04.1 on a stick and so I plugged that one in and booted up with it.  It went to the standard installation questions which I answered.  The last one had three choices; erase the drive and start over, erase existing 20.04 and start over or something else (forget).  I chose to erase the existing 20.04 (which would have been the failed update).  I just checked and its currently doing all the erasing and then will probably start reinstalling all the 20.04 stuff and then install same.  Hopefully that will work out and I won't have any more problems.

I am writing this one because I did notice that problems with installing this one seems to have problems now and then and so I thought I would post this in case anybody had any suggestions about what I have done or what I should be doing.

Since I have written the above this has happened.  I got notified that the upgrade was finished and I should re-boot.  I did that.  The machine went blank and did nothing.  So, I removed the memory stick, turned off the machine, turned it back on and started a new boot.  I just let it alone and then I got a red screen with the outline of a cat (a good sign!)  It then asked me some other question and, then, it came up!  I think its done!  Oh, not really, it also told me that there was update stuff to load and install (300+mb I think) and its doing that right now.  

I think its going to be fine with really not that many problems.  I am posting this because it may be helpful for somebody else and am going to mark it as done.

Thank you..............

---

### Post by briandu2 on 2020-10-13
May I suggest the following when you install again:

Using a small spare drive I installed Ubuntu again and it erratically  worked until I re-installed it again with the following partitions using  **gdisk**
/dev/sb1 as EFI   +512M
/dev/sdb2 as fs_boot +512M
/dev/sdb3 as fs_root (the rest of the drive)

new install Ubuntu with other (manual partitions) and formatting sdb1 as EFI, sdb2 as /boot and sdb3 as /root.
Once installed and rebooted then went  	Code:
 	cd /boot/efi/EFI/ubuntu 
 and executed  	Code:
 	mv shimx64.efi shimx64.efi_old 
 and  	Code:
 	cp grubx64.efi shimx64.efi 
; then reboot and all the strange messages  such as "Failed to set Mok........" at bootup disappeared.

This seems quite robust and consistently boots up directly or using the  Mac alt key choices.   Point is it works properly and no problems.

---

### Post by jgw on 2020-10-14
My problem has been trying to recover to where I was in 18.04.5   then I remembered I had been backing up all the time to my second drive.  I went to the last backup and restored my entire home page!  (there was a lot more I could have restored but this, I think, was enough and, hopefully, I didn't overwrite anything important)  So far its all there although I still have to reinstall stuff but its sure better than nothing!  I am getting there!

Thanks for the reply!

---

### Post by jgw on 2020-10-17
Thanks for the reply!

I am pretty much back to where I was with 18.04.5  (stuff keeps on popping up).  That being said the machine seems to be booting up quicker than before the upgrade.  On the other hand some things take longer to do, like loading programs.  I just thought I would time loading up thunderbird and it actually didn't take all that long after all.  

I am going to set this as solved.

---

### Post by marchello_lippi2 on 2020-10-18
Hi, I'll use existing thread. Please let me know if I need to start the new one though.

I got some issues, one is ethernet connection loss after upgrade, other are rather minor. 

So, I can't connect using ethernet anymore. Don't know how to debug it. Looks like all settings are the same. 
I'm not completely blocked though, because I have wi-fi usb dongle which works fine. 
Also I have still 16.04 LTS on my second hdd, just tried it and ethernet does work there. Please advise where do I start digging the problem with ethernet... 
    
   [I]   Upd: regarding ethernet: turned on automatic negotiation and it solved my problem.
[/I]
Minor things are: 
- can't set wallpaper on each of my screens and desktops (it's lubuntu btw); I have two monitors and could set 4 different wallpapers back in 18.04, now I can set only one; I can live with that, this is just nice to have;
- one of monitors is shifted up a bit and I can't see top of my screen, don't know how do I shift it down a bit now;

- don't know where do I set/unset UI applications autostart, it worked in "LX default application" (or something like this, don't remember exact name), but can't find this utility on 20.04 at all;
*    Upd: this one is fixed as well using gnome-session-properties.*

- my monitors are switched between (left became right and right became left), I can switch them manually using Arandr, but can't see where do I save it so that it persists after reboot
- got some ugly loud background noise from speakers, but it happens only when sound card is not used by any other program; as a workaround, I run Blanket with some nature noises;

- important native application (slack) doesn't work in 20.04, its window just freezes and reloading doesn't help, luckily I can use it in franz (a kind of container for different messangers)
[I]   upd: slack started working again on the next day just like before

[/I]- can't find where do I disable auto screen lock
*   Upd: found something, testing it*

- though I've sent some application windows to Desktop 2, I can still see their windows on control panel in the bottom (lubuntu has bottom control panel) and it's not tray pictograms.

---

### Post by James_Dunn on 2020-10-18
I had the same problem. I was on 18.04.01 and tried to use the software upgrade builtin. I aswseres all the questions and it downloaded the files needed and finally it did a reboot. When it came back from reboot it was a black screen with a single dash blinking in the upper left corner of the screen and was locked UP solid. I rebooted and it was the same. neither usb keyboard or usb mice worked. NO ctrl-alt-del. I had to power off manually.  I downloaded 20.04 and ran sha checksums to  ensure the download was ok. I used a Windows machine to write the iso to a bootable flash brive. When booting from the flash drive i had to reset the BIOS to boot from the usb drive. Keyboard and mouse worked fine. When it booted.it asked a bunch of questions. Keyboard and mouse worked. I formatted the main drive and installed 20.04 and then rebooted. Same result. Black screen flashing dash in upper left corner. I spend a day and a half trying many things. Jumping to the fix- The BIOS setting to enable IOMMU fixed the problem. I had to modify the grub file with the line"iommu=soft" without the quotes. Once that was in grub, I could turn disable IOMMU in the BIOS. I vaguely remember that this is a problem with Gigabyte motherboards and maybe some others. MORE IMPORTANTLY when a new release of UBUNTU is supposed to install over a working previous version completely replacing grub with an "off the shelf" version is bad news. ANY modifications to grub that exist should have been carried to the new grub!  Can't be helped if it's a fresh install, but an over write needs to be much more carefull.

---

### Post by jgw on 2020-11-01
My system now has a brand new trick.  I cannot shut it down.  This one is very strange.  Last night I pressed enter whilst I had the terminal open and it started telling me things and everything was dandy.  The it said:
Reached power off:
At this point the system is frozen.  I started pressing buttons and then it said:

20736.0758 (079) - (systems shutdown) [sinking file system and blocked devices] issuing SIGKILL to PID 18587 - can't shut down (this is pretty close but not perfect)

then I pressed some more buttons and it finally shut down!

Given all the rest of my problems I am wondering whether I should download and reinstall.  I would try, first, to not erase anything and just install and if that doesn't work erase everything, clean the drive and start over from scratch.

Anybody have thoughts on that one?  Not being able to shut down seems to be the end of the road.........

---

