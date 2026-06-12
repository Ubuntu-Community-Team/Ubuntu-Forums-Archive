---
title: "Moving away from dual boot / grub set up?"
date: 2010-01-27
forum: Installation &amp; Upgrades
---

### Post by Nightstrike2009 on 2010-01-27
Hiya folks

I am planning to move my main OS from Windows to Ubuntu (Yeah I am that impressed:KS) but I wish to move windows to my current smaller hard drive until I find all ubuntu replacement programs i can use then eventually eject the windows drive.

The problem is has we all know who dual-boot you have to install windows first before ubuntu as the windows mbr is when grub is stored and gets wiped when you install windows.

It must be possible to add windows as secondary OS while keeping / or reinstating grub must it not it surely (eg on 10.4LTS release it would be ok, but if i installed windows vista or 7 on my secondary hardisk it would destroy grub). 

Can anyone advise me on how you would go about this procedure ?

---

### Post by etnlIcarus on 2010-01-27
Depends on which version of GRUB you're using. If you're using GRUB 1 (henceforth known as GRUB Legacy), it should be as simple as adding:
```
title		Microsoft Windows
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```
To the end of your /boot/grub/menu.lst file (assuming Windows is on a bootable partition, on your primary slave).

If you're still using 9.04, then you've got GRUB Legacy, which is good, as I'm still getting my head around GRUB 2.

---

### Post by Nightstrike2009 on 2010-01-27
Thanks etnlIcarus:

I am able to provide further info now Ubuntu boots fine (my main priority) but the windows entry doesn't appear at boot up at all just goes straight to ubuntu (my eventual aim).
[B]
Gparted reports for Linux Drive:[/B]
/dev/sda1  ext3 mount point /   921.41GiB
/dev/sda2  extended              10.10GiB
/dev/sda5  linux-swap            10.10GiB

**Gparted reports for Windows Drive (not mounted):**
/dev/sb1    ntfs                 152.66GiB
unallocated unallocated            7.84MiB

From this I would say that windows drive is present just missing a grub legacy boot entry, how would I add this to my grub legacy menu? is it the same code as mentioned in above post? my /boot/grub/menu.lst file is blank to start with.

If I can resolve this it will be great practice as what has happened is exactly why I posted this in the first place. :-)

PS: Sorry if i sound a bit stupid with this just want to get it right 1st time. :-)

---

### Post by etnlIcarus on 2010-01-27
The example in the code tags should be sufficient. Just open /boot/grub/menu.lst with a text editor as root and copypasta the above to the end of the file.

---

### Post by Nightstrike2009 on 2010-01-27
Cheers etnlIcarus

I've entered terminal with > Code:
sudo gedit /boot/grub/menu.lst

and added your > Code:
title		Microsoft Windows
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

then saved and exited, I'm going for reboot now, if this works thanks your a Lifesaver. Hope I can return the favour on the forums if you need help one day :-)

---

### Post by Nightstrike2009 on 2010-01-27
Unfortunately it failed, I have to hit "ESC" key just to access grub boot menu, there is no windows entry detected still. :-(

It maybe worth mentioning that My Linux Drive is SATA and my windows Drive IDE, (2 separate drives completely) would this make a difference?

> **By myself earlier:**
Gparted reports for Linux Drive:
/dev/sda1 ext3 mount point / 921.41GiB
/dev/sda2 extended 10.10GiB
/dev/sda5 linux-swap 10.10GiB

Gparted reports for Windows Drive (not mounted):
/dev/sb1 ntfs 152.66GiB
unallocated unallocated 7.84MiB

Anybody got any suggestions?

---

### Post by SteveHillier on 2010-01-27
First up I don't know much about GRUB but some thought to consider.

1.  You could try removing the Ubuntu drive (ie just unplug the interface cable) leaving a disk for Windows to install on to.  Then using threads from the forum you could find out what you have to do to put GRUB on that disk

2.  You could try reversing the order of the disks but this might be more risky than thought 1 and you would still have to manipulate GRUB as before.

3.  Installing XP normally gives you an option to decide which disk to use for the install but it might still assume that it has MBR in the first disk for it's sole use.

4.  Vista just makes assumptions and I wouldn't risk it with Vista

5.  If it were me (and I have lots of hard disks to use) I would not do anything to my current unless I had a restore image somewhere to recover from.  Try Ghosting the existing image to a new (fresh) disk then if it doesn't work you can Ghost it back again.

PLEASE NOTE I don't know for certain if any of these will work.  Just do whatever you need to do to protect the data you want to keep.

---

### Post by Nightstrike2009 on 2010-01-27
I have a third external Hard drive so my data is safe :-)

Gparted reports on windows drive information tab:
> 
File System: nfts
Size: 152.66 GiB

Path:/dev/sdb1
Status: Not Mounted

First sector: 63
last Sector:  320143319
total sectors:320143257

WARNING: Unable to read the contents of this file system! Because of this some operations may be unavailable. 

Is this "Not Mounted" something to do with it not detecting my windows drive?

Thanks SteveHillier for trying to help but I don't wish to try any of the above, I need to further my knowledge of grub manual configurations. I understand your advice though thanks for trying to help out. :-)

PS: I could back away from this and just virtualise Xp in "Virtual box" but it lacks functions and this issue affects a friends PC too, so I searching for a final solution to this (Without reinstalling Ubuntu at all), thanks for all help so far, I am confident we can resolve this with the right information eventually and will post here if I reach a working conclusion first.

---

### Post by etnlIcarus on 2010-01-27
I'm not sure. You'll have to start reading the GRUB documentation.

And easy cheat out of this might also be your BIOS. With my Award BIOS, I can just hit F11 at boot and it'll bring up a menu, allowing me to choose which drive to boot from, without making any permanent changes to the boot order, or any physical changes to my hardware configuration.

---

### Post by wkulecz on 2010-01-27
IMHO dual boot is nothing but trouble.  I've setup multi-boot systems many times over the years and its nothing but grief after the boot loader changes: lilo to grub, now grub to grub2.

I'd never setup dual boot when either system is important to have working.

The safer option is to get a removable drive carrier and a spare caddie for each OS you need.  Then swap in the drive you need to boot.

Windows is fragile, the activation since XP make it downright brittle.

--wally.

---

### Post by binary10 on 2010-01-27
It's ok to manage multi booting but tbh you just need to watch installs / upgrades of grub, and have the mapping correct in /grub/device.map

On my laptop(s) I've been running Ubunutu/kubuntu mix for two years now. By default they came with Windows which I've left alone for re-sale/re-distribution.

I resorted to putting dos grub into the windows (vista) boot mgr as an option with a simple menu option to do the following: 

title boot ubuntu usb 
find --set-root --ignore-floppies /grub/stage2
chainloader +1
boot

find --set-root --ignore-floppies /grub/menu.lst
configfile /grub/menu.lst
boot


Then on my usb ubuntu drive has a boot partition in which resides the real /grub/menu.lst

And in turn the /grub/menu.lst has references (uuids) to my specific bootable ubuntu usb drive ( and backup ubunutu drive). The fstab of my drive mounts partitions using labels not hard points.

This makes my usb drive highly movable (laptop to laptop, which has been put to the test when I had quickly migrate from my work laptop to my kids laptop due to hardware failure). I just disconnected the usb drive off of my work laptop (a samsung ati) and plugged it onto the kids one (a lenovo) and off it went.Never gone back to the samsung :(.

In addition you can boot the usb drive directly (from the bios) if you can't install the dos grub under windows.

In order to get the chainloader working, I had to make sure that I did a grub-install on the usb drive (or backup usb drives) to make sure that they are bootable, this is why you need to watch the device.map file.

---

### Post by Nightstrike2009 on 2010-01-27
I used to dual boot windows xp and ubuntu with no problems at all but the ubuntu and windows is proving a lot harder.

1) As I workaround I would be happy to use a usb stick to boot the windows partition as a bootloader, negating the need for dual boot but still giving me access to a windows partition, Is this possible?

2) Should I just bugger this one off and virtualize windows xp in "Virtual Box" as I know how to use that and only want windows for video editing, sonicstage for an mp3 player (The later I could just buy a new one) and checking an epson sx100's ink levels? (I can live without windows otherwise)

---

### Post by binary10 on 2010-01-27
Both options would seem a bit of a trouble heading over the hill.

1. usb stick to boot your windows. might cause problems later on.
2. video editing under a virutualized xp under virtual box seems like it would be damn slow.

i'm just trying a couple things (bootwise) under virtualbox (master drive x, secondary fresh ubuntu) to emulate a possibility, if anything turns out good I'll update

---

### Post by binary10 on 2010-01-27
deep joy - I installed 9.10 along on my test xp vm, so I'm just handling the fun of grub 1.97beta4. I'm going to park my test for now.

---

### Post by Nightstrike2009 on 2010-01-27
Before I got into this mess, I had ubuntu 9.04 with virtualised Windows Xp and Ubuntu 10.4LTS alongside a dualboot with a real windows xp.

This is driving me nuts i can see the damned xp partition in gparted but grub can't see it and sonicstage dont work on virtualbox so thats that out too. :-(

---

### Post by Nightstrike2009 on 2010-01-27
Right some progress to report:

I've issued the command in terminal (I had the l (letter L) down as a 1 before, doh!)

> sudo gedit /boot/grub/menu.lst

Added:
> title		Microsoft Windows
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

to the end of the list as suggested by etnlIcarus.

When I press "ESC" key on boot "Microsoft Windows" entry is there but reports:
"NTLDR is missing" 

any ideas?

---

### Post by SteveHillier on 2010-01-27
> **Nightstrike2009 said:**
> When I press "ESC" key on boot "Microsoft Windows" entry is there but reports:
"NTLDR is missing"

Oh b....r, NTLDR is the operating system loader so without it you cannot get windows to load.  Normally when I have come across this problem it has meant a rebuild although having said that sometimes running chkdsk from the recovery console will fix it.
I have never tried to do it but I would assume if you had a backup copy and can put that back on the original location you might get round it.  It depends how much time you can spend on it.
As this can take longer than a rebuild and because I charge for my time for clients the rebuild option is earier for them in the long run.
Good luck.

---

### Post by presence1960 on 2010-01-28
> **Nightstrike2009 said:**
> 

**_The problem is has we all know who dual-boot you have to install windows first before ubuntu as the windows mbr is when grub is stored and gets wiped when you install windows._**

That statement just is not true. You do not have to install windows first to set up a dual boot or multi boot. When you install windows after linux on the same hard disk all that happens is windows overwrites GRUB on the MBR with the windows bootloader. Once windows is installed all one needs is the Ubuntu Live CD to reinstall GRUB to MBR.

For GRUB Legacy 0.97 use this procedure:
1. Boot your computer up with Ubuntu CD
2. Open a terminal window or switch to a tty.
3. Type sudo grub. Should get text of which last line is grub>
4. Type "find /boot/grub/stage1". You'll get a response like "(hd0,1)". 
   Use whatever your computer spits out for the following lines.
5. Type "root (hd0,1)", or whatever your hard disk + boot partition 
   numbers are for Ubuntu.
6. Type "setup (hd0)", to install GRUB to MBR
7. Quit grub by typing "quit".
8. Reboot and remove the bootable CD.

For GRUB2 see here: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Don't contribute to propagating probably the biggest fallacy on this forum. Do not remain in the dark find out by educating yourself & then others. 

If we MUST install windows first before Linux, can you explain this [link's]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows") existence in our community documentation? Or these below?

[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

[http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm](http://apcmag.com/how_to_dual_boot_linux_and_windows_xp_linux_installed_first.htm)

There is nothing to fear except fear itself. Maybe you were told that you had to install windows first or maybe that is how you learned. But it is not a necessity. Step out and learn new tricks. Does someone like myself who has 3 linux OSs installed (lucid alpha. karmic & sabayon) have to remove all three to add windows? Thank God I didn't have to do that. I just installed windows then put GRUB back on the MBR.

---

### Post by etnlIcarus on 2010-01-28
NTLDR Missing means either:

- The NTFS partition on the Windows HDD isn't bootable (this should be easily fixed with gparted. Just right-click the NTFS partition and choose, "Make bootable").

- One of the boot files on the NTFS partition has been deleted or corrupted (this can usually be fixed by setting the Windows HDD as your primary boot device and using a boot disk and any number of tutorials on the web).

- You haven't set the correct boot order in your BIOS and GRUB is telling your BIOS to look in the wrong place for Windows (Repeatedly press the Delete key when booting, then make sure the Windows IDE HDD is actually a boot option as is at a priority one-below the SATA Ubuntu HDD).


Also might be worth replacing, "root (hd1,0)", with, "rootnoverify (hd1,0)", in your menu.lst. I have no idea if this'll make any difference but it's worth a shot.

Also, if you want the list to show up be default, without having to quickly his Esc to choose your OS, look for:
```
hiddenmenu
``` in your menu.lst and prepend a # to that line.
Also look for a line called:
```
timeout
```
and set it's value to your desired amount of time.
```
timeout 10
```
should be sufficient.

---

### Post by presence1960 on 2010-01-28
> **Nightstrike2009 said:**
> Right some progress to report:

I've issued the command in terminal (I had the l (letter L) down as a 1 before, doh!)



Added:


to the end of the list as suggested by etnlIcarus.

When I press "ESC" key on boot "Microsoft Windows" entry is there but reports:
"NTLDR is missing" 

any ideas?
Let's not guess about your setup & boot process, which if done will mess your system up even more. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal (Applications > Accessories > Terminal) and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Nightstrike2009 on 2010-01-28
I give up on this now, I experimented but admit defeat now dual-booting Vista & Ubuntu 9.04 (Grub drove me that daft I nearly stopped using ubuntu alltogether. Not impressed at grub's auto detection in legacy version, I hope grub 1.97b (grub2) is better.

Grub2 isn't an option for me sadly as 9.10 doesn't support my 3G modem because of a kernel bug. Thanks for all the help, but losing too much time on this project and just happy to dual-boot once more. 

All this project has taught me is that ubuntu needs a lot more work before it can replace Windows as a main OS (for people migrating from windows that need usable alternatives for all windows programs), maybe one day it will be but that day isn't today, certainly not with its working in one vers, then broken in next attitude.(at least not for me anyhow). :-(

I don't mean to upset anyone thanks for trying to help out, I'll leave this thread open if anyone finally susses it out then maybe they can post up here. I am just glad grub's auto-detect failings  didn't drive me away from ubuntu totally and I am happy to dual boot once more. :-)

PS: I suppose I could be classed as a noob been using Ubuntu since 7.04, and most of my experience is from Windows, think we take things for granted in windows that aren't there in other OS systems and make the mistake Linux is like Windows. It isn't its completely different and takes time and patience to learn how to use it. I am blaming Grub for rubbish auto-detection but I guess the real reason is my lack of experience with Ubuntu.:-(

PPS: This working in one version, broken in next attitude sucks, Ubuntu should take more time making sure its stable enough (like debian) than rushing out botched beta type versions like 9.10. for gods sake thats why most windows migrates are trying Ubuntu for better STABILITY.

---

### Post by etnlIcarus on 2010-01-28
I'd blame the technical support, more than GRUB (honestly, virtualisation?). Usually, GRUB [Legacy] doesn't have any trouble detecting OSes on other physical HDDs at the time of install - assuming you didn't disconnect the Windows HDD when installing Ubuntu.

And there's nothing stopping you from installing Grub[2] separately, FTR.

---

### Post by Nightstrike2009 on 2010-02-01
The stupid thing was with Windows on the SATA2 drive it was ok (as ubuntu was when it had it to itself too)and ubuntu on the IDE drive, dual boot was fine.

The problem occured when trying to place both OS's on the main SATA2 drive that had been partitioned into two parts beforehand. The host OS was detected but not the guest one e.g. Windows no Ubuntu, Ubuntu no Windows.

I think it was the SATA2 guest OS detection failing that forced me to abort this project or it should have worked (at least in theory).  

I may wait for Ubuntu 10.4LTS before attempting to dual-boot again (or dual boot an Ubuntu 10.4 alpha in the time being).

PS: I find this sickenly ironic that I was ready to move over to a full ubuntu system and once again a flaw that should not exist has pushed me back to using a Windows OS has Host OS. 

The fact is until things like stability in new releases are fixed and features taken for granted in windows are added, ubuntu will be a second os on a lot of systems which is a shame has I think it a great OS. It just needs to concentrate on reliablity and stability instead of experimental new features most of us dont even need, most pc users don't care how it works, they just want it too work, In my opinion anyhow.

---

### Post by presence1960 on 2010-02-01
If you would have run the boot info script as requested it is quite possible we could have gotten it working. But nevertheless you have thrown in the towel.

---

### Post by mrgeee on 2010-02-02
Let's say I have 9.04 CD and not 9.10. Will the Live CD Grub Reinstallation instructions outlined here work?

> **presence1960 said:**
> For GRUB2 see here: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)


---

### Post by presence1960 on 2010-02-02
> **mrgeee said:**
> Let's say I have 9.04 CD and not 9.10. Will the Live CD Grub Reinstallation instructions outlined here work?

9.04 Live CD does not support GRUB2. It supports GRUB Legacy 0.97. AFAIK you will need a 9.10 Live CD for GRUB2.

---

