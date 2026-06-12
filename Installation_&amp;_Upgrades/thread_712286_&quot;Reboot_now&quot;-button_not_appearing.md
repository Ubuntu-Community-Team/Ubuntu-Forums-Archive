---
title: "&quot;Reboot now&quot;-button not appearing"
date: 2008-03-01
forum: Installation &amp; Upgrades
---

### Post by charmsdark on 2008-03-01
I'm trying to install Ubuntu 7.10 on my Philips Freevents X50 laptop. 
It boots off the live cd ok, and everything works ok when running off the live cd. I run the installation and that seems to run through ok, but then at the end there's no "restart now" button appearing. After the progress bar has gone to 100% it just disappears and I get dumped back to the desktop. The only difference is that there's a "/target" drive icon on the desktop.
If I reboot it normally (from the icon in the top right hand corner of the screen) it asks me to take the cd out after it's gone out of the GUI, but then comes up with an "error loading operating system" message.

I should probably also mention that when it starts off the cd it comes up with the following text at the top before it starts loading all the files (this is before it goes to the desktop of the live cd).
[6.508000] 8139cp 0000:01:06.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[6.508000] 8139cp 0000:01:06.0: Try the "8139too" driver instead

I've tried neemz's guide in this thread [http://ubuntuforums.org/showthread.php?t=287939&page=2](http://ubuntuforums.org/showthread.php?t=287939&page=2), but instead it comes up saying it can't install some software packages.

Any help in this matter is greatly appreciated. 
It just annoys me that the installation seems to run through ok, but then doesn't want to reboot..

---

### Post by Pumalite on 2008-03-01
Post your specs and tell me what iso are you using.

---

### Post by charmsdark on 2008-03-01
Specs are:
CPU   	 Intel® Pentium® M 740 (1.73 GHz Dothan) 
Chipset 	Intel® i915GM chipset 
Memory 	512 MB DDR SODIMM PC2700  
Hard Drive 	60 GB Hard Disk Drive SATA
CD / DVD Drive 	Dual layer DVD±RW 
Monitor 	12.1" TFT (native resolution 1024x768 ) 
Video / Graphics Card 	Integrated Intel® Graphics Media Accelerator 900 (up to 128MB) 
Sound Card 	Realtek AC'97 audio 
Modem 	Motorola SM56 modem  
Network Card 	Realtek 8139 Family PCI Fast Ethernet (Onboard) 
Network Card 	Intel® Pro 2200BG wireless LAN 
Firewire Card 	OHCI compliant IEEE 1394 host controller (onboard) 
PC Card 	1 x Type I / Type II PC Card 
Card Reader 	O2Micro Flash Card Reader 

The iso I'm using is "ubuntu-7.10-desktop-i386.iso".

I've tried downloading the iso from two different mirrors, and the most recent one I burned at 8x (the slowest speed the cd burner in my desktop pc will do).

I tried leaving the pc for several hours after the installation seemed to have completed, but that made no difference.

I tried following the instructions in the following post ([http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)) to re-install the GRUB, but when getting to the "find /boot/grub/stage1" it comes back with "Error 15 file not found". So I followed the instructions in the same post there to mount the harddrive in Ubuntu Live CD, and it seems that the files are on the harddrive but there's no folder for GRUB in the /boot folder.

---

### Post by Pumalite on 2008-03-01
You have an unfinished installation. You better install with the Alternate CD:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below sign 'Start Download'
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on iso, burn at 4x or less as 'image', not 'data', in good quality CD-R media, check CD integrity before install.

---

### Post by charmsdark on 2008-03-02
> **Pumalite said:**
> You have an unfinished installation. You better install with the Alternate CD:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark box below sign 'Start Download'
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum on iso, burn at 4x or less as 'image', not 'data', in good quality CD-R media, check CD integrity before install.


First of all, thank you for the speedy reply. :)

I did what you suggested. I downloaded the alternate iso, did a MD5SUM check on it before burning it. I ended up burning it on my boyfriends PC (as mine doesn't seem to want to burn anything any slower than 8x) and managed to burn it at 4x. I also ran the integrity test of the cd from the initial menu when booting off the CD.


When booting off the CD the following is the chain of events: 

Selected "text installation".
Selected language (english), ok.
Scanning cd, ok.
Loading additional components, ok.
Detecting network hardware, ok.
Configure network, choose between "intel pro wireless 2200bg" or "realtek rtl-8139/8139c/8139c+".
Selected the realtek one, ok.
Config network with dhcp, ok.
Entered host name, ok.
Detecting disks and all other hardware, ok.
Starting up partitioner, ok.
Selected "manual" and then "guided - use entire disk", ok.
Partitions to create on disk "SCSI1 (0,0,0) (sda) - 60.0GB ATA TOSHIBA MK6025GA"
#1 primary, 57.5gb, b, f, ext3, /
#5 logical, 2,5gb, f, swap, swap
Selected "Finish partitioning and write changes to disk".
Confirmed partitioning of disks, ok.
Configured clock to utc, ok.
Cet up one user and password, ok.
Installing the base system, ok. (took quite a while at 82%, installing the kernel - retrieving and installing linux-generic..)
Configuring apt, ok.
Select and install software (jumps a bit back and forth in the first 6%). 
Configure xserver-xorg at 6%. Asks for resolutions for X server to use. Selected 1024x768, 800x600, 640x480.
Installed xserver-xorg, ok.
Then comes up with "Please wait..." at 6%.
After 3-4 minutes (CD spinning all the time) the progress bar jumps to 85% and then comes up with error message saying:
```
[!!] Select and install software
Installation step failed
An installation step failed. You can try to run the failing item again from the menu, or 
skip it and choose something else. The failing step is: Select and install software
<Continue>
```
Selected continue, I then get to "[?] Ubuntu installer main menu" with the "Select and install software" step highlighted.
Tried running it (software install) again. Same thing happens.
Selected the next step in the list which is "Install the GRUB boot loader on harddisk".
Installing grub boot loader. Selected to install it to the MBR as Ubuntu is the only installation on the drive. Didn't set GRUB password.
Get back to main menu with "Select and install software" highlighted. Tried running that again.
Same thing happens again. It jumps to 85% and then comes up with the error message again.
Selected "finish the installation" from the "[?] Ubuntu installer main menu".
Finishing installation, comes up with message:
```
[!!] Finish the installation
Installation complete
Installation is complete, so it is time to boot into your new system. Make sure to remove 
the installation media (cd-rom, floppies), so that you boot into the new system 
rather than restarting the installation.
<Go back> <Continue>
```
Selected continue. PC reboots, GRUB comes up counting down and then it starts.
```
Starting up...
Loading please wait...
[6.508000] 8139cp 0000:01:06.0: This (id 10ec:8139 rev 10) is not an 8139C+ compatible chip
[6.508000] 8139cp 0000:01:06.0: Try the "8139too" driver instead
```
Then a load of more text that rolls by really quickly.
What I can then see on the screen is the following: 
```
/dev/sda1: clean, 23525/7028736 files, 377394/14040802 blocks
[OK]

* Checking file systems...
fsck 1.40.2 (12-Jul-2007) [OK]

* Mounting local filesystems... [OK]
* Activating swapfile swap... [OK]
* Checking minimum space in /tmp... [OK]
* Configuring network interfaces... [OK]
* Setting up console font and keymap... [OK]
* Loading ACPI modules... [OK]

* Starting ACPI services... [OK]

* starting system log deamon...
ubuntu 7.10 ida-laptop tty1

ida-laptop login: [OK]

* Doing Wacom setup... [OK]

* Starting kernel log deamon... [OK]

* Running local boot scripts (/etc/rc.local) [OK]
```
And then I get the flashing little line in the bottom right hand corner.
If I press enter from there I can log in with the username and password I set up during the installation because it comes up with:
```
Ubuntu 7.10 ida-laptop tty1

ida-laptop login:
```
and the flashing little line after that.

If I log in it comes up with a bit of info about Ubuntu and then I'm at a "ida@ida-laptop:~$" prompt.
So now it looks like I've got an installation but no GUI..

I tried 
```
sudo apt-get update
```
and when I type in the password I get
```
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-en_GB
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-en_GB
Reading package lists... Done
```
I then did 
```
sudo apt-get install ubuntu-desktop
```
and then it comes up with a load of filenames (or something) and then
```
0 upgraded, 686 newly installed, 0 to remove and 0 upgraded.
Need to get 0B/459MB of archives.
After unpacking 1683MB of additional disk space will be used.
Do you want to continue [Y/n]?
```
Selected yes on that and it then comes up with
```
Media Change: Please insert the disk labelled
'Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)'
in the drive '/cdrom/' and press enter

```
I put in the "ubuntu-7.10-alternate-i386" CD that I installed from and pressed enter.
It comes up with "0% [Working]" and the CD spins up, but then I get the above message again to put in the disk.
I tried putting in the "ubuntu-7.10-desktop-i386" CD that I tried installing from initially (when it wouldn't complete the installation), but the same thing happens.
I can't get away from that message any other way than by rebooting. When I reboot it goes through the same thing and I get the console again.
I did notice when it was booting up that it was looking for a resume image or something on /dev/sda5 (the swap partition), but I have no idea if it's of any significance.


Is there any way I can install the Ubuntu desktop by downloading the files instead of the installation trying to get them off the CD? Can I add online (i.e. a URL for a) repository and install the desktop that way?

At least it feels like I'm a bit closer to a working installation of Ubuntu 7.10.

---

### Post by Pumalite on 2008-03-02
Get wired to the Internet and use the Alternate again. If it doesn't work, try:
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)
Or:
[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

---

### Post by charmsdark on 2008-03-02
> **Pumalite said:**
> Get wired to the Internet and use the Alternate again. If it doesn't work, try:
[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)
Or:
[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

I did have the ethernet cable connected when doing the install.

I did manage to "add" some repositories to the /etc/apt/sources.list file by copying the /etc/apt/sources.list.apt-setup over it (after having backed up the original sources.list file), but then it still asks for the cd when I do "sudo apt-get install ubuntu-desktop".

As for the network boots, don't they require me to actually have an installation of Linux or Windows to be able to run it?

I'm tempted to run the installation from the cd without having the network cable plugged in, just to see what happens.

---

### Post by Pumalite on 2008-03-02
Sorry, I thought you were dual booting. I'm running out of ideas here.

---

### Post by confused57 on 2008-03-02
This may give you an idea of what's happening with your Phillips pc:
[http://www.fitzenreiter.de/averatec/index-e.htm](http://www.fitzenreiter.de/averatec/index-e.htm)

---

### Post by charmsdark on 2008-03-03
Well, running the alternate installation without the network configured made no difference at all.

I've set my desktop PC to download the iso from the [http://www.fitzenreiter.de/averatec/index-e.htm](http://www.fitzenreiter.de/averatec/index-e.htm) website, but it's downloading at snailspeed as there's only the torrent version available. If only there was a http download of it and I'd have it downloaded in 10 mins.

I might run a recovery on my laptop and try the network boot option from windows and just install Ubuntu over the whole harddrive anyway. And then once the other iso has been downloaded I'll try running that.

Won't have much time to do this over the next few days tho' since I'm working the late shift, but I'll be back on it on Friday when I've got the day off. I'll keep you posted on any progress.

Thanks again to both of you.

---

### Post by charmsdark on 2008-04-02
Sorry for the late update, but I've not had much time to sit in front of my computer much recently. :(

In the end I solved it by installing Ubuntu 7.04, which ran through without a hitch, and then I updated it to 7.10.

I'm getting a new (larger) HDD and some more RAM put into my laptop soon as well, so then I'll be up for some more adventures trying to install Ubuntu 8.04 beta on it :)
If nothing else at least I know now I should be able to install 7.04 and upgrade from there. And with an 14mbps internet connection of about  it won't be a problem. ;)

---

### Post by Pumalite on 2008-04-02
Glad you got it working.

---

### Post by kewe86 on 2008-05-23
Hi charmsdark,

I have a philips x50 as well. I want to install ubuntu dual boot with windows. I have tried the new ubuntu release Hardy Heron 8.04 but that does not boot from the Live cd.

Seeing your forum I want to try the Fiesty Fawn version 7.04. Just want to ask if that downloaded smoothly? Has your philips shown any signs of errors? Any response will be appreciated. 

Thanks

---

