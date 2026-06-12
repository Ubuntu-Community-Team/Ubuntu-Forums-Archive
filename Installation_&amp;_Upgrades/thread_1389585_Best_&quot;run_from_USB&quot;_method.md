---
title: "Best &quot;run from USB&quot; method?"
date: 2010-01-24
forum: Installation &amp; Upgrades
---

### Post by valnar on 2010-01-24
I see there are a couple methods out there to install Ubuntu on a USB stick.  Which is the best one?  I want to be able to run it completely from there and install my own software from APT.  I don't care about installing Ubuntu *from* that USB stick.

Which is the method I want?

---

### Post by rogue_0111 on 2010-01-24
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by garvinrick4 on 2010-01-24
The largest you can get to be persistent (hold changes) is 4 gig and will work as a Live Cd and a system. I have tried 16 gig and formatted as ext 3 with /boot, / and swap and it does work
but will load grub2 in any machine you use it in. It has to have an MBR and finds the one on current machine. If you have grub2 and are going to use it just on your machine it is great. 
A 4 gig in fat32 made on Ubuntu's USB Startup Disk Creator works great all you need is a downloaded .iso file from Ubuntu and tell it to use 4 gig of persistence with a sliding scale and start. When done boot into it make changes. Then set in preferences not to download anymore
updates. Tell Firefox to stay basically in Private Browsing in edit/preferences, there is a setting so it does not save junk and I am at 52 meg left and holding and it works just fine. That is with a under $10, 4 gig flash drive. The greatest for Live CD also boots quick. Live CD takes forever to boot. And actually works real nice as a system. 9.10 with install and update and upgrade and added everything but compiz. When done sudo apt-get clean, to clear up cache, space is premium. Of course 4 gig style on fat32 does not effect MBR at all.

---

### Post by hemimaniac on 2010-01-24
I have always used unetbootin for usb installs and it has never let be down when putting a linux distro on a computer with no optical drive.

You can have a look [here]("http://unetbootin.sourceforge.net/")

---

### Post by valnar on 2010-01-24
I've seen both the Pendrivelinux and UNetbootin methods.  What is the difference?

---

### Post by hemimaniac on 2010-01-24
The plus to the UNetbottin (imho) is the fact if you dont have an .iso downloaded already. it will allow you to select one from the drop down, or you can use your own. For me, the biggest attraction, is 1-2 clicks its over, reboot have fun.

---

### Post by C.S.Cameron on 2010-01-25
If you want to be able to update and upgrade your stick I would suggest a full install, ie disable your hard drive, plug in your thubdrive and install from the Live CD.
A persistent install takes less space and doesn't have many disadvantages, two methods below, both allow over 4GB persistence.

This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext3 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, removed CD, rebooted.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Changed desktop background, connected to wireless and installed FontForge.
Rebooted, changes were persistent.

Have tried dozens of times using usb-creator to install to a 4 gig Kingston, without success.
This is what finally worked:
Booted Live CD.
Plugged in flash drive.
Started Partition Editor
Created 1 GB FAT32 partition, (on the left side of the bar).
Created a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw".
Created a partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started "Create a live usb startup disk", (usb-creator).
Selected minimum Stored in reserved extra space, (128 MB).
Pressed "Make Startup Disk.
When usb-creator finished, ran "gksu nautilus"
Selected disk and deleted the casper-rw file.
Shutdown, removed CD, rebooted.
Changed desktop background, connected to wireless and installed FontForge.
Rebooted, changes were persistent.

---

### Post by snowpine on 2010-01-25
I did a full install of Ubuntu 9.10 to an 8gb thumb drive (using the "regular" Ubuntu installer). It works fine; Ubuntu doesn't really "care" what kind of drive it's running from. Be very careful not to accidentally install GRUB to your internal hard drive!

---

### Post by valnar on 2010-01-25
C.S.Cameron, Thanks for the extensive write-up!

So what is the difference between your method, installing it "regular" on a USB drive and the [[COLOR="Red"]Pendrivelinux[/COLOR]]("http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/") way, which also creates a persistent version?


I probably won't be writing much to the USB disk, or even using it that regularly, but I do want to be able to update it and install a couple applications for a rescue purposes.

I bought *[[COLOR="Red"]Image for Windows[/COLOR]]("http://www.terabyteunlimited.com/image-for-linux.htm")* which is an excellent backup/imaging alternative to the likes of Acronis True Image.  The author makes a DOS, Linux and Windows version which you can buy for the same price.  It backs up anything it can read - no separate licensing for a "server" version.  (ie.  Windows 2003 *Server* can be backed up just like WinXP, Win98 or Linux).

Even though the company offers a basic Linux disk creation tool, I want something more modern that has the latest disk drivers (SATA, AHCI), network drivers, is upgradeable and contains all networking tools necessary to backup to my Windows Servers (cifs,smbmount), etc.  I'll add the backup tool to this USB stick.  This way I can be fairly sure that if I come across a PC that needs to be backed up, this will support it so long as the BIOS can boot USB.

---

### Post by valnar on 2010-01-25
bump

---

### Post by Settwi on 2010-01-25
Okay... if you have windows, use wubi.exe and just select your 3GB flash drive as the target drive, and install ubuntu, and it should work

---

### Post by C.S.Cameron on 2010-01-25
The PendriveLinux "Persistent"' (Disk image), install takes up about 0.7GB without persistence. 
It uses an image of the Live CD. Persistence is stored in a file named casper-rw. The file system is FAT16 with a maximum file size of 2GB or FAT32 with a maximum file size of 4GB. 
It works by expanding a file named filesystem.squashfs. This is sort of like a zip file that is frozen and not effected by updates or upgrades. 
An update may work but all of the files are stored in casper-rw and will soon fill the disk. Computer Janitor may help but will not remove the updated original files from the squashfs file.
Any update to the kernel or upgrade will make the pendrive un-usable as a Live USB. 
The "Persistent" methods I have outlined use Persistent partitions that can be formatted as ext2, ext3, ext4 of reiserfs, depending on the users fancy. These are not limited to size like FAT files. 
I understand that ext2 is not a journaling file system thus doing less writing to the thumbdrive than the others, (not to worry anyway, flashdrives take years to wear out.
With home in a separate partition you should be able to upgrade to the next version of Ubuntu without loosing the data in it.

The full install takes about 2.3GB of disk space as installed. It is just like installing Ubuntu to an internal HDD, (but a little slower). 
You can use manual formatting to make partitions of your choosing, ie boot, home and swap. 
It is fully updateable and upgradeable.
If you use restricted drivers ie Nvidia graphics drivers, the flash drive may not work on every machine.
There used to be a cure for this named switchconf, (from the repositories). This could be used to select between xorg.conf at boot. It seemed to stop working about 8.10, as the restricted drivers loaded regardless of what xorg.conf said. I have not tried it with 9.10. (I think it can still be used to choose things such as Nvidia single or dual monitors.
Hope I have not confused things too much.
The full install pendrive is not as useful for installing Ubuntu to another computer
Cork

---

### Post by jenaniston on 2010-01-25
> **snowpine said:**
> I did a full install of Ubuntu 9.10 to an 8gb thumb drive (using the "regular" Ubuntu installer). It works fine; Ubuntu doesn't really "care" what kind of drive it's running from. . . .

I do run a 1GB Ubuntu 9.04 Live USB drive on university computers, etc. but 
live versions Fedora/Ubuntu will not install to my sick laptop.

So I am about to try the full install to an 8GB (or a 16GB) USB and then use that as the only working drive for the full laptop rescue.

---

### Post by C.S.Cameron on 2010-01-25
> So I am about to try the full install to an 8GB (or a 16GB) USB and then use that as the only working drive for the full laptop rescue.

If you use manual partitioning and give home it's own partition, (/home), you can always move it to it's own flashdrive if the current one gets filled up.

---

### Post by PRC09 on 2010-01-25
I am running a full install from an 8gb usb stick right now.I just removed my hard drive and used a live cd to install as normal, use the full disk option and at the final section select advanced and install grub to the usb drive.It works great from the machine it is installed from (laptop) and 1 other laptop,same manufacture but different model but will not run from my desktop at all.Just drops me to a grub prompt.I am assuming this is due to the drivers already installed for video and wireless and such.This works fine for me as the laptop I used only had a 3gb drive and is just for testing distros anyway but be aware that the install does marry itself to the system it was installed from ......

---

### Post by valnar on 2010-01-26
Cameron and all.  Thanks for the replies.  I think I have a handle on it now.

---

### Post by valnar on 2010-01-26
Well, just for testing....I tried making a USB boot disk using both the pendrivelinux and unetbootin method.  Both seemed to work fine and the Ubuntu Grub menu showed up.  It started counting down the 10 seconds to boot.

It never booted.  Even when I press enter to bypass the counter, it just resets the counter back to 10 seconds and counts down again.  ?? :confused:

Edit: Nevermind.  Bad ISO image download.

---

### Post by jenaniston on 2010-01-26
> **snowpine said:**
> I did a full install of Ubuntu 9.10 to an 8gb thumb drive (using the "regular" Ubuntu installer). It works fine; Ubuntu doesn't really "care" what kind of drive it's running from. Be very careful not to accidentally install GRUB to your internal hard drive!

> **jenaniston said:**
>  . . .live versions Fedora/Ubuntu will not install to my sick laptop . . .
. . . I am about to try the full install to an 8GB . . . as the only working drive . . .

> **PRC09 said:**
> I am running a full install from an 8gb usb stick . . . 
use the full disk option and at the final section select advanced and install grub to the usb drive.
. . . the drivers already installed for video and wireless and such . . .
 
. . . be aware that the install does marry itself to the system it was installed from ......

"install does marry itself to the system it was installed from" . . . oh well . . .

Full installing from U9.04 Live USB booted up on a campus library Dell to my 8GB USB -
but I do ***expect*** the driver problem if I then try to use it as the only working drive to rescue files off the Sharp AL27 laptop.

I figure it's worth a try though . . .

---

### Post by jenaniston on 2010-01-27
> **jenaniston said:**
> "install does marry itself to the system it was installed from" 

I figure it's worth a try though . . .

After further thought, this has a next to* **nil** *chance of working -
only by coincidence that the machine used to install the USB full OS has a "near-perfect" match
 to any other machine the USB OS is tried to run from . . .
- as the full installation will do a "checks your system hardware" when the full install to that USB is tried.

But . . . **IF** the ubuntu installation program lets you pick the partition to install to
(in my case the hard drive is "broken" but I still want to rescue files before I install *over it* later with ubuntu)
. . . and lets me pick the drive/partition to install to ( it should ),
then . . .
a LAN boot to the "thin" client laptop with an empty and ready USB partition should/would then install to the USB drive
*** and*** include those laptop system settings.

---

### Post by snowpine on 2010-01-27
That just is not true... Ubuntu auto-detects your hardware each time you boot; it does not "marry" itself to your specific hardware (like a certain other OS). You can move your Ubuntu install to a completely different computer, and it will boot fine. The only possible exception as mentioned previously is if you've installed proprietary hardware drivers and tweaked your settings (for example you might have to boot into safe graphics mode and edit xorg.conf if you boot on a computer with a different graphics card). So long as you stick with the open source drivers this should not be an issue. As I said before, I have an Ubuntu 9.10 full install on an 8gb flash drive; I can move it from my home desktop to my netbook to my work desktop with no problem, despite the vastly different hardware.

---

### Post by PRC09 on 2010-01-27
I stand corrected....I am replying from my desktop that I previously couldnt get to boot.I dont know why but it works now on all that I try it on......

---

### Post by C.S.Cameron on 2010-01-27
I sorta agree with Snowpine, (as usual), The only times I've had problems booting a full install on multiple computers is when I've installed restricted drivers.
I haven't had as good luck booting into safe graphics though.
Switchconf used to let you boot into different xorg.conf files but I don't think it has been working since 8.04 except for like selecting between single or dual monitors with the same video ard.

---

### Post by Herman on 2010-01-28
The ability of an operating system or a piece of software to 'marry' itself to a computer's hardware is a 'feature' of proprietary operating systems. 
When you sign the EULA that comes with a proprietary operating system you agree to run it only in one computer. 
This makes a lot of costs and headaches for the user, because if your hardware fails you lose your software too. 
Also if you ever need to rescue files from a disc with a proprietary operating system in it in another computer you have to be careful not to accidentally boot the proprietary operating system or it will probably 'bork' itself.

One of the advantages of choosing to use an Open Source GNU/Linux operating system like Ubuntu is that the user is free from such handicaps and limitations.
Ubuntu and Linux actually try hard to be able to boot and run in any computer and have drivers for as much hardware in the world as they possibly can, and they mostly do a very good job of that.

I first tried moving Ubuntu from one computer to another a long time ago, probably back in the 'Breezy' days but I'm not sure. 
It would boot, but getting it working properly was not always so easy for beginners. 
To get it to boot we needed to use grub's command line interface.
Then after it boots to a black screen we would run run 'sudo dpkg-reconfigure xserver.xorg' to get the video working.
Most often we also needed to editing /etc/fstab files with the new /dev/sdx,y numbers.
If the move to a different computer will be for long we would want to edit the /boot/grub/menu.lst file as well. 
But it has always been possible to boot and run Ubuntu in most computers.

When Ubuntu Hardy Heron came out it featured the then new [Xorg 7.3]("http://www.ubuntu.com/getubuntu/releasenotes/804overview#head-34da8c8d2432823a293ea6a0639fe8b9a24c0f77")  Xwindow system from [X.Org Foundation]("http://www.x.org/wiki/"), and ever since then we don't need to run 'sudo dpkg-reconfigure xserver.xorg' anymore.
Now our GRUB files and /etc/fstab use UUID numbers instead of /dev/ names, so we don't need to edit those files anymore either.
Nowadays it's simple for the user, everything just works, it's all pretty much seamless and automatic.  

I agree with snowpine and C.S.Cameron, the only times I've had problems running a full install on various different computers is when I have installed restricted drivers. 

My USB installations and even hard disk installations are easily able to set themselves up automatically for all but a few of the different computers I've tried them in.

I like to install in one single partition and set up a swap file instead of a swap area.
I set swappiness to 10 and I use ext4 and set 'noatime' in /etc/fstab' and use 'elevator=noop' as a kernel option in grub.cfg.

Those tweaks are optional but I can say I don't have any complaints about performance.
My flash memory installations are always quick and snappy with no stalling or jerkiness. 
Neither have I ever had any flash memory 'wear out' on me yet so far. 
I have a small collection of failed hard disks though.

---

### Post by AnotherMuggle on 2010-01-29
I have just used the PenDriveLinux installation method with a 4GB casper persistence loopback.

I am a relative newb to Linux but have managed to get everything working properly.  All the updates came through and applied without a problem.  I have also managed to remove the Live Session User account and create a proper user account.

I have also managed to get the touchpad working the way I like it via a hal file.  Everything seems to be sticking and working as I would hope.

Very happy indeed :D

---

### Post by jenaniston on 2010-01-29
> **snowpine said:**
>  . . . Ubuntu auto-detects your hardware each time you boot; it does not "marry" itself to your specific hardware (like a certain other OS). You can move your Ubuntu install to a completely different computer, and it will boot fine. 

Well, this has worked ***better*** than I expected - that's for sure . . . 

The full install to hard disk from a Ubuntu9.04  Live  USB  -
first booted up live version on a university campus Dell -
( which has a hard drive Windows Vista Enterprise and connected to about 100 printers all over campus)  . . . 
to a USB **/dev/sd****c** -a full install to a fresh, clean 8 GB USB OS -
did give me the grub bootloader, 
so on the laptop this USB U9.04 OS let's me choose to get into the generic recovery root terminal.

But the Jaunty desktop keyboard / mouse **do NOT work** in this "marriage"  - from campus Dell to the Sharp laptop - at least just yet. 

Secondly, the monitor screen size was NOT detected in laptop - 
although I now first change settings in Preferences when booted USB OS back into the Dell it originally installed from before going to laptop.

Still, this was ***much more*** success than I originally thought would be *probable*.

Since all I may need is the terminal to rescue files and re-partition, this is enough of a success.

Most critical of ***this*** marriage though . . . **fstab still needs to be changed** as 
this USB OS only gives 25 mounts of the USB before a forced filesystem check crashes everything - again.

 All comes to a halt after the forced filesystem check.

---

### Post by jenaniston on 2010-01-29
> **snowpine said:**
> That just is not true... Ubuntu auto-detects your hardware each time you boot; it does not "marry" itself to your specific hardware (like a certain other OS). You can move your Ubuntu install to a completely different computer, and it will boot fine. The only possible exception as mentioned previously is if you've installed proprietary hardware drivers and tweaked your settings (for example you might have to boot into safe graphics mode and edit xorg.conf if you boot on a computer with a different graphics card). So long as you stick with the open source drivers this should not be an issue. As I said before, I have an Ubuntu 9.10 full install on an 8gb flash drive; I can move it from my home desktop to my netbook to my work desktop with no problem, despite the vastly different hardware.
  Another example of some sort of ***"marriage"***  . . .

this command on the **Sharp AL27** laptop with Ubuntu 9.04 USB drive OS  . . .
```
# cd /var/lib/acpi-support/; grep '.' *-*
```yields . . .
```
bios-version:A04
system-manufacturer:Dell Inc.
system-product-name:OptiPlex GX280
system-version:Not Specified

```Yes, the USB operating system now plugged in the Sharp laptop USB port was
created with a Dell OptiPlex GX280 . . .

The laptop is totally disconnected from the Dell OptiPlex GX280 . . .
other than the Ubuntu 9.04 installation on the USB it is running on.

go figure . . . at least enough of the laptop hardware gets detected (HAL) to have made any of this work at all.

---

### Post by snowpine on 2010-01-29
Cool, glad you are doing the research Jen, I guess I had a lot of assumptions that I never really tested. :)

---

### Post by slickvguy on 2010-02-02
Installed my jaunty desktop system (old Dell Dimension) onto a USB stick. Boots perfectly on the same system. Went downstairs and booted it on one of my kid's PC's (newer Dell Dimension) - and it was a total bust. I expected the video to be messed up, but the keyboard wouldn't work properly (which makes it kind of hard to reconfigure!) and the mouse wouldn't work. It aborted the GUI (X?) and went into text mode only. I logged in but was even unable to modify xorg.conf w/ vi (between the text displaying HUGE characters with many off the screen and the keyboard not working properly) - that's how bad it was.

I haven't spent enough time with linux to know exactly what I should have done. (I used to know a lot more linux - from years ago - but I've forgotten most of it). Probably someone who knew exactly what to do to rectify the situation could have typed "blindly" and somehow gotten it going, but I couldn't. I'm planning on traveling, and will have access to various PC's and laptops. Thought the USB install was a smart way to bring my desktop with me w/o having to bring the hardware (netbook/whatever). 

Oh well....so much for being able to port my Ubuntu installation to various PC's. Guess I'll have to stick to a custom live USB w/ persistence for now?

---

### Post by jenaniston on 2010-02-02
> **slickvguy said:**
> Installed my jaunty desktop system (old Dell Dimension) onto a USB stick. Boots perfectly on the same system. . . . booted it on one of my kid's PC's (newer Dell Dimension) - and it was a total bust. . . . but the keyboard wouldn't work properly (which makes it kind of hard to reconfigure!) and the mouse wouldn't work. It aborted the GUI (X?) and went into text mode only. I logged in but was even unable to modify xorg.conf w/ vi (between the text displaying HUGE characters with many off the screen and the keyboard not working properly) . . .
. . .
Oh well....so much for being able to port my Ubuntu installation to various PC's. Guess I'll have to stick to a custom live USB w/ persistence for now?
   
Not exactly sure what you mean by "custom" - 
a  live version on USB with some overlay is a pretty effortless venture - whether in Fedora or Ubuntu.

While for your purposes you consider that the "porting" to another computer experiment was a "total bust" -
I have to say for my purposes I regard it as at least a 97% success.

Of course, yes, I still am working on getting the keyboard fixed when on the laptop - there ***will*** be a way - 
but I am using that USB OS right now booted on the very campus computer installed from - 
and after some new synaptic add packages to this USB OS -
it will be back running the laptop as the only working operating system -
but even closer to the desktop working further - so maybe up to 97.9% on this round.

If you care to, I'd suggest that you go into the generic recovery terminal choice (2nd)
when booted on the "ported" system - your son's computer.
Scroll down some to choose root terminal, press tab to ok and press enter.

Now at the prompt at the very bottom (already in root no sudo -s needed . . .
start with a command like
```
uname -a
```Yes, the full linux is there - albeit "***only"*** as the root terminal with *full* write permissions.
With an ethernet cable and some configs ya' could ping any IP address in the world . . .
or ifconfig a wireless card yadayadayada . . .

You* probably* **CAN use vi editor** - although  it did not let me use the usual "a" for entering the INSERT MODE.
I needed to use the <insert> key instead, but DID vi edit the etc/fstab file and all others I wanted. 
 I will try to look at xorg.conf - that could be just what I need! **THANKS.**

You could synaptic add from the Dell you made the USB on -
I just did exactly that on campus with the very computer I installed from,
and in five minutes will be using those installed utilities (like sdparm)
on the laptop (but only as root terminal)

So, you can do virtually anything including check partitions on your son's computer if it has no other OS -
and eventually use exit and resume normal boot to the (very) minimally functioning desktop.

So, as I rescue files off the laptop - 
**it was a real surprise that Ubuntu offered this recovery kernel** -
 Fedora 11 or 12 USB full OS (and all Live versions Fedora or Ubuntu) just freeze on boot attempts to the laptop.

But note that this Ubuntu 9.04 USB OS will have to be re-installed [B]after 25 mounts
[/B] *unless* you reconfigure the automatic filesystem check in fstab.

In summing up, I recognize that this won't exactly serve your immediate purposes -
other than maybe forcing your son to learn linux from the command line, in this M$ Windows monopoly world.

But readers of this thread should know that a Ubuntu 9.04 USB OS works pretty darn well in at least some "porting" experiments -
 and is way ahead on this particular rescue use at least, 
certainly in comparison to the Fedora - if not also other - linux distributions.

You'll have an easy time with the live USB . . . f'sure.

---

### Post by Herman on 2010-02-02
:D jenaniston, all Ubuntu installations run fsck every 25 or 30 mounts. A file system check shouldn't be a show stopper for anyone.
The fsck program is useful for the automatic file system checks because it can easily be run from another program without the need to ask the user interactively what kind of file system needs to be checked. The fsck program doesn't actually run a file system check by itself, it's more of a file system checker manager. The fsck program detects the file system and runs the appropriate file system checking program with a safe set of options without user interaction. It works well enough if there's nothing much wrong with the file system.

If you have an ext series file system, (which most of us do), fsck will run e2fsck on our file system for us. The options fsck give to e2fsck to run with are quite safe, and while they're harmless, they're not always as effective at actually fixing anything as the file system check we can do when we run the e2fsck file system checking program ourselves directly.

If you run e2fsck yourself, you can run a more effective file system check that will still be safe, and might actually fix your file system, this one works well for me,
```
sudo e2fsck -C0 -f -v -p /dev/sda1
```Where: '/dev/sda1' represents the disk and partition number Ubuntu is installed in, please alter that as appropriate for your set-up.
Where: You run a file system check from another operating system, (live cd perhaps), on the unmounted file system.
[COLOR=Red]Never run a file system check on a file system while it is mounted.[/COLOR]

 If you don't like using the command line, a similar file system check can be run instead using GParted in the Ubuntu Live CD, (also installable in a real installation), by right-clicking on the partition and clicking 'Check'.

To avoid file system damage in the first place, try to refrain from ripping the USB from the USB port while the file system is still mounted. Always wait for Ubuntu to completely finish shutting down first, or until the file system has been completely umounted before removing the USB stick from the computer.

Regards, 
Herman :D

---

### Post by jenaniston on 2010-02-03
> **Herman said:**
> :D jenaniston, all Ubuntu installations run fsck every 25 or 30 mounts. A file system check shouldn't be a show stopper for anyone.
. It works well enough if there's nothing much wrong with the file system.
. . .

 If you don't like using the command line,. . .

I Thank You - and have read your entire post - well stated.

But the USB filesystem / operating system I am running the laptop off of is important currently   just 
to rescue files and see what I can salvage off the hard drive.

I ***love*** running off the command line - but it is ***all*** I have running really . . .

But the Debian automatic filesystem check needs to sometimes be run at the user's convenience . . .
[http://www.dslreports.com/forum/r19319435-Easy-way-to-force-or-disable-fsck-at-boot-time-with-Debian](http://www.dslreports.com/forum/r19319435-Easy-way-to-force-or-disable-fsck-at-boot-time-with-Debian)

I know the hard drive is "broken' it does not help here to let me know and totally stop a USB drive OS from booting at all . . .
 and then I have to just re-partition and re-install all over again for another 25 mounts.

So, and I'll be starting another thread later, I am researching how to also disable this using tune2fs . . .
as just the manual editing of the pass-number in the etc/fstab file (from 1 to 0) has not been enough to stop the automatic filesystem check.
[http://linux.die.net/man/8/tune2fs](http://linux.die.net/man/8/tune2fs)

Thanks again for the reply.

---

